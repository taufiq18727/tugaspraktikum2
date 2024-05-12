<template>
  <div>
    <div class="input-field">
      <label for="kilometer">Kilometer</label>
      <input type="number" id="kilometer" v-model="kilometer" @input="update('kilometer', $event)">
    </div>
    <div class="input-field">
      <label for="hektometer">Hektometer</label>
       <input type="number" id="hektometer" v-model="hektometer" @input="update('hektometer', $event)">
    </div>
    <div class="input-field">
      <label for="dekameter">Dekameter</label>
      <input type="number" id="dekameter" v-model="dekameter" @input="update('dekameter', $event)">
    </div>
    <div class="input-field">
      <label for="meter">Meter</label>
      <input type="number" id="meter" v-model="meter" @input="update('meter', $event)">
    </div>
    <div class="input-field">
      <label for="centimeter">Centimeter</label>
      <input type="number" id="centimeter" v-model="centimeter" @input="update('centimeter', $event)">
    </div>
    <div class="input-field">
      <label for="milimeter">Milimeter</label>
      <input type="number" id="milimeter" v-model="milimeter" @input="update('milimeter', $event)">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      kilometer: 0,
      hektometer: 0,
      dekameter: 0,
      meter: 0,
      centimeter: 0,
      milimeter: 0
    }
  },
  methods: {
    update(unit, event) {
      const value = event.target.value;
      this[unit] = parseFloat(value);
      this.convert(unit);
    },
    convert(unit) {
      const value = this[unit];
      const ratios = {
        kilometer: 1,
        hektometer: 10,
        dekameter: 100,
        meter: 1000,
        centimeter: 100000,
        milimeter: 1000000
      };
      for (let key in this.$data) {
        if (key !== unit) {
          this[key] = value / ratios[unit] * ratios[key];
        }
      }
    }
  }
}
</script>

<style scoped>
.input-field {
  margin-bottom: 10px;
}
</style>
