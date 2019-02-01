<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col">
        </div>
      </div>
      <div class="row justify-content-center">
        <div class="col col-6">
          <div class="card">
            <h4 class="card-header bg-dark text-white">
              Dynamic transitions
            </h4>
            <div class="card-body">
              <form>
                <div class="form-group">
                  <label for="chosenTransition">Select transition</label>
                  <select
                          id="chosenTransition"
                          v-model="chosenTransition"
                          class="form-control"
                  >
                    <option
                            v-for="transition in transitions"
                            :value="transition"
                    >
                      {{ transition | ucfirst }}
                    </option>
                  </select>
                </div>
              </form>
              <button
                      class="btn btn-primary"
                      @click="toggle"
              >
                Toggle transition
              </button>
              <hr />
              <transition :name="chosenTransition">
                <div
                        class="alert alert-success"
                        v-if="isActive"
                >
                  Alert!
                </div>
              </transition>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        /**
         * The name of the application.
         */
        name: 'my-app',

        /**
         * The data the Vue instance can use.
         *
         * @return {Object} The view model data.
         */
        data() {
            return {
                isActive: true,
                chosenTransition: 'bounce',
                transitions: [
                    'bounce',
                    'fade',
                    'flip-x',
                    'flip-y',
                    'light-speed',
                    'rotate',
                    'zoom',
                ],
            };
        },

      
        /**
         * The methods that are available on this Vue instance.
         */
        methods: {
            /**
             * Method used to toggle the isActive-property.
             */
            toggle() {
                this.isActive = !this.isActive;
            },
        },

        /**
         * The filters that are available on this Vue instance.
         */
        filters: {
            /**
             * Will uppercase the first character of the word.
             *
             * @param {string} value The value to be uppercased.
             *
             * @return {string} The uppercased value.
             */
            ucfirst(value) {
                if (!value) {
                    return '';
                }

                return value.charAt(0).toUpperCase() + value.slice(1);
            }
        }
    };
</script>
<style>
  .bounce-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: bounceIn;
  }

  @-webkit-keyframes bounceIn {
    0% {
      -webkit-transform: translateY(-500px);
      transform: translateY(-500px);
      -webkit-animation-timing-function: ease-in;
      animation-timing-function: ease-in;
      opacity: 0;
    }
    38% {
      -webkit-transform: translateY(0);
      transform: translateY(0);
      -webkit-animation-timing-function: ease-out;
      animation-timing-function: ease-out;
      opacity: 1;
    }
    55% {
      -webkit-transform: translateY(-65px);
      transform: translateY(-65px);
      -webkit-animation-timing-function: ease-in;
      animation-timing-function: ease-in;
    }
    72% {
      -webkit-transform: translateY(0);
      transform: translateY(0);
      -webkit-animation-timing-function: ease-out;
      animation-timing-function: ease-out;
    }
    81% {
      -webkit-transform: translateY(-28px);
      transform: translateY(-28px);
      -webkit-animation-timing-function: ease-in;
      animation-timing-function: ease-in;
    }
    90% {
      -webkit-transform: translateY(0);
      transform: translateY(0);
      -webkit-animation-timing-function: ease-out;
      animation-timing-function: ease-out;
    }
    95% {
      -webkit-transform: translateY(-8px);
      transform: translateY(-8px);
      -webkit-animation-timing-function: ease-in;
      animation-timing-function: ease-in;
    }
    100% {
      -webkit-transform: translateY(0);
      transform: translateY(0);
      -webkit-animation-timing-function: ease-out;
      animation-timing-function: ease-out;
    }
  }
  
  .bounce-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: bounceOut;
  }
  
  .fade-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: fadeIn;
  }
  
  .fade-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: fadeOut;
  }
  
  .flip-x-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: flipInX;
  }
  
  .flip-x-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: flipOutX;
  }
  
  .flip-y-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: flipInY;
  }
  
  .flip-y-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: flipOutY;
  }
  
  .light-speed-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: lightSpeedIn;
  }
  
  .light-speed-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: lightSpeedOut;
  }
  
  .rotate-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: rotateIn;
  }
  
  .rotate-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: rotateOut;
  }
  
  .zoom-enter-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: zoomIn;
  }
  
  .zoom-leave-active {
    animation-duration: .5s;
    animation-fill-mode: both;
    animation-name: zoomOut;
  }
</style>