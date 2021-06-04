<template>
  <q-page class="column flex flex-center">
    <div class="container q-py-xl text-h4">
      {{ result }}
    </div>
    <div class="container column justify-between">
       <q-form
       class="q-pa-sm"
       @submit="calc()"
       @reset="onReset()"
       >
        <div class="q-pa-md row">
          <q-input
          filled
          v-model.number="base"
          type="number"
          label="Base"
          />
          <q-separator 
          spaced="10px"
          vertical
          />
          <q-input
          filled
          v-model.number="exp"
          type="number"
          label="Expoente"
          />
       </div>
       <div class="q-pa-md column">
         <q-btn label="Calcular" type="submit" color="primary" />         
          <q-separator 
          spaced="10px"
          color="transparent"
          />
         <q-btn label="Resetar" type="reset" color="primary" />
       </div>
       </q-form>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      model: 10,
      base: '',
      exp: '',
      result: ''
    }
  },
  methods: {
    calc() {
      if (this.exp === 1) {
        this.result = this.base
      } else if (this.exp === 0) {
        this.result = '1'
      } else {
        let valor = 1;
        for (let i = 0; i < this.exp; i++) {
          valor *= this.base;          
        }        
        this.result = valor        
      }
    },

    onReset () {
      this.base = null
      this.exp = null
      this.result = 'Insira os Valores Abaixo'
    }
  }
}
</script>
