<template>
  <div class="aui-group">
    <div class="aui-item"><h3>Toggle button</h3>
      <va-tabs>
        <va-tab name="Example">
          <p>
            <va-toggle v-model="toggle1"></va-toggle>
            <span>{{toggle1}}</span>
          </p>
          <p>
            <va-toggle v-model="toggle2" label="Switch me" tooltip-on="On"
                               tooltip-off="Off">
            </va-toggle>
          </p>
          <p>
            <va-toggle v-model="toggle2" disabled></va-toggle>
          </p>
          <h5>Busy</h5>
          <p>
            <va-toggle v-model="toggle3" :busy="busy"></va-toggle>
          </p>
        </va-tab>
        <va-tab name="Code">
          <pre v-highlightjs><code class="xml" v-text='code'></code></pre>
        </va-tab>
      </va-tabs>
    </div>

    <div class="aui-item">
      <api-table name="va-toggle" :props="[
        {name: 'busy', type: 'Boolean', default: 'false', description: 'Shows the spinner over the button.'},
        {name: 'disabled', type: 'Boolean', default: 'false', description: 'Disable interactions.'},
        {name: 'value', type: 'Boolean', default: 'false', description: 'Represents current button status, on or off.'},
        {name: 'id', type: 'String', default: 'generated', description: 'Used to match label to the toggle button.'},
        {name: 'label', type: 'String', description: 'Adds aui-label with given text.'},
        {name: 'tooltip-off', type: 'String', default: 'right middle', description: 'Sets the tooltip text when the toggle is set to the \'off\' state.'},
        {name: 'tooltip-on', type: 'String', default: 'right middle', description: 'Sets the tooltip text when the toggle is set to the \'on\' state.'},
      ]" :events="[
        {name:'input', description: 'Emitted when toggle status is changed.'},
      ]">
      </api-table>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        toggle1: true,
        toggle2: false,
        toggle3: true,
        busy: true,
        code: `<p>
  <va-toggle v-model="toggle1"></va-toggle>
  <span>{{toggle1}}</span>
</p>
<p>
  <va-toggle
      v-model="toggle2"
      label="Switch me"
      tooltip-on="On"
      tooltip-off="Off"></va-toggle>
</p>
<p>
  <va-toggle v-model="toggle2" disabled></va-toggle>
</p>

<h5>Busy</h5>
<p>
  <va-toggle v-model="toggle3" :busy="busy"></va-toggle>
</p>
`
      }
    },

    mounted() {
      setTimeout(() => this.busy = false, 1000)
    },

    watch: {
      toggle3() {
        this.busy = true;
        setTimeout(() => this.busy = false, 500)
      }
    }
  }
</script>
