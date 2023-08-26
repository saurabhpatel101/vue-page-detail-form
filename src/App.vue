<template>
  <div>
    <h1>Basic Detail </h1>
    <form @submit.prevent="submitForm">
      <div>
        <label for="firstName">First Name:</label>
        <input v-model="firstName" id="firstName" type="text" />
        <span v-if="!validateFirstName">First name should not contain numbers</span>
      </div>
      <div>
        <label for="lastName">Last Name:</label>
        <input v-model="lastName" id="lastName" type="text" />
        <span v-if="!validateLastName">Last name should not contain numbers</span>
      </div>
      <div>
        <label for="joiningDate">Joining Date:</label>
        <input v-model="joiningDate" id="joiningDate" type="date" />
      </div>
      <div>
        <label for="address">Address:</label>
        <input v-model="address" id="address" type="text" />
        <span v-if="!validateZipCode">Invalid zip code</span>
      </div>
      <div>
        <label for="phoneNumber">Phone Number:</label>
        <input v-model="phoneNumber" id="phoneNumber" type="text" />
        <span v-if="!validatePhoneNumber">Invalid phone number</span>
      </div>
      <div>
        <label for="email">Email Address:</label>
        <input v-model="email" id="email" type="email" />
        <span v-if="!validateEmail">Invalid email address</span>
      </div>
      <div>
        <label for="dob">Date of Birth:</label>
        <input v-model="dob" id="dob" type="date" />
      </div>
      <div>
        <label for="password">Password:</label>
        <input v-model="password" id="password" type="password" />
        <span v-if="!validatePassword">Invalid password format</span>
      </div>
      <button @click="displayDetails" type="submit">Submit Button</button>
      <div v-if="displayed">
        <h2>User Details</h2>
        <p><strong>FirstName:</strong>{{firstName}}</p>
        <p><strong>LastName:</strong>{{lastName}}</p>
        <p><strong>JoiningDate:</strong>{{joiningDate}}</p>
        <p><strong>Address:</strong>{{address}}</p>
        <p><strong>PhoneNumber:</strong>{{phoneNumber}}</p>
        <p><strong>Email Address:</strong>{{email}}</p>
        <p><strong>Date of Birth:</strong>{{dob}}</p>
        <p><strong>Password:</strong>{{password}}</p>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      joiningDate: "",
      address: "",
      phoneNumber: "",
      email: "",
      dob: "",
      password: "",
      displayed:false,
    };
  },
  computed: {
    validateFirstName() {
      return /^[A-Za-z]+$/.test(this.firstName);
    },
    validateLastName() {
      return /^[A-Za-z]+$/.test(this.lastName);
    },
    validateZipCode() {
      return /^[0-9]{5}$/.test(this.address);
    },
    validatePhoneNumber() {
      return /^[0-9]{10}$/.test(this.phoneNumber);
    },
    validateEmail() {
      return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.email);
    },
    validatePassword() {
      return /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/.test(this.password);
    },
  },
  methods: {
    submitForm() {
      if (
        this.validateFirstName &&
        this.validateLastName &&
        this.validateZipCode &&
        this.validatePhoneNumber &&
        this.validateEmail &&
        this.validatePassword
      ) {
        // Perform form submission logic here
        console.log("Form submitted successfully");
      } else {
        console.log("Form validation failed");
      }
    },
    displayDetails(){
      this.displayed = true;
    },
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.underline{
  text-decoration: underline;
}
.promoted{
  font-style: italic;
}
.new{
  color: olivedrab;
}
.sold-out{
  color: red;
}
</style>
