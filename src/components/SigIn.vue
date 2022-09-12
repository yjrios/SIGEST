<template>
    <v-container fluid fill-height>
        <v-row align="center" justify="center">
            <v-col>
                <v-card
                    :loading="loading"
                    class="mx-auto"
                    max-width="450"
                    elevation="20"
                >

                <v-card-text class="px-0 py-0">
                    <v-img
                    src="@/assets/AGL-LOGO.jpeg"
                    ></v-img>
                    <span dark class="pl-2 font-italic font-weight-black">Sistema de Gestión de Documentos</span>
                </v-card-text>

                <v-divider></v-divider>
                    <!-- <template slot="progress">
                    <v-progress-linear
                        color="deep-purple"
                        height="10"
                        indeterminate
                    ></v-progress-linear>
                    </template> -->
                    <v-row class="pt-8">
                        <v-col cols="3">
                            <v-subheader>Email</v-subheader>
                        </v-col>
                        <v-col cols="9">
                            <v-text-field
                            v-model="correo"
                            placeholder="example"
                            suffix="@agroinlaca.com"
                            class="mr-2"
                            :rules="rulesCorreo"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row class="mb-0">
                        <v-col cols="3">
                            <v-subheader>Contraseña</v-subheader>
                        </v-col>
                        <v-col cols="9">
                            <v-text-field
                            :rules="rulesPassword"
                            v-model="password"
                            placeholder="Example1*"
                            class="mr-2"
                            :type="mostrar ? 'text' : 'password'"
                            :append-icon="mostrar ? 'mdi-eye' : 'mdi-eye-off'"
                            @click:append="mostrar = !mostrar"
                            clear-icon="mdi-close-circle"
                            clearable
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-card-text align="right" class="pt-0">
                        <v-row>
                            <v-col>
                                <v-tooltip
                                    top
                                    color="#FF6D00"
                                >
                                    <template v-slot:activator="{ on }">
                                    <v-icon v-on="on">
                                        mdi-help-circle-outline
                                    </v-icon>
                                    </template>
                                    'Caracteres permitidos * # ? = . - _ @ $ ! %'
                                </v-tooltip>
                            </v-col>
                        </v-row>
                    </v-card-text>
                    <v-divider class="mx-4"></v-divider>

                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn
                            color="#43A047"
                            text
                            class="font-weight-black"
                            @click="iniciosesion"
                        >
                            SIGIN
                        </v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
  export default {
    data: () => ({
        domain: '@agroinlaca.com',
        loading: false,
        selection: 1,
        mostrar: false,
        correo: '',
        password: '',
        rulesCorreo: [
        x => !!x || 'Campo requerido'
        ],
        rulesPassword: [
        x => !!x || 'Campo requerido',
        x => /^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?=-_.])[A-Za-z\d@$!%*#?=-_.]{8,16}$/.test(x) || 'La contraseña es inválida',
        x => (x && x.length >= 8) || 'La contraseña debe tener un mínimo de 8 caracteres'
        ]
    }),

    methods: {
      reserve () {
        this.loading = true

        setTimeout(() => (this.loading = false), 2000)
      },
      iniciosesion () {
        console.log('Correo ' + this.correo + this.domain + ' Clave ' + this.password)
      }
    },
  }
</script>