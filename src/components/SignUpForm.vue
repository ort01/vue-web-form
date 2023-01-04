<template>
  <form>
    <!-- input email binding -->
    <label>Email:</label>
    <input type="email" required v-model="email" />

    <label>Password:</label>
    <input type="password" required v-model="password" />

    <!-- select form field binding -->
    <label>Role:</label>
    <select v-model="role">
      <option value="Developer">Web Developer</option>
      <option value="Designer">Web Designer</option>
      <option value="Manager">Project Manager</option>
    </select>

    <!-- single checkbox binding (true/false) -->
    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>Accept terms and conditions</label>
    </div>

    <!-- binding value of checkboxes with array (values => array) -->
    <div class="names">
      <div>
        <input type="checkbox" value="Shaun" v-model="names" />
        <label>Shaun</label>
      </div>
      <div>
        <input type="checkbox" value="Jacob" v-model="names" />
        <label>Jacob</label>
      </div>
      <div>
        <input type="checkbox" value="Arthur" v-model="names" />
        <label>Arthur</label>
      </div>
    </div>

    <!-- Keyboard events & modifiers -->
    <div class="skills">
      <input type="text" v-model="temporarySkill" @keyup="addSkill" />
      <div v-for="skill in arrayOfSkills" :key="skill" class="skill">
        {{ skill }}
      </div>
    </div>
  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>{{ terms }}</p>
  <p>{{ names }}</p>
</template>

<script>
export default {
  name: "SignUpForm",
  props: [""],
  data: () => {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      names: [],
      temporarySkill: "",
      arrayOfSkills: [],
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "Enter" && this.temporarySkill) {
        if (!this.arrayOfSkills.includes(this.temporarySkill)) {
          this.arrayOfSkills.push(this.temporarySkill);
        }
        this.temporarySkill = "";
      }
    },
  },
};
</script>


<style scoped>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 25px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
  cursor: pointer;
}
input:focus,
select:focus {
  outline: none;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.skill {
  color: rgb(119, 119, 119);
  display: block;
  margin: 15px 0;
  font-size: 0.8em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
</style>
