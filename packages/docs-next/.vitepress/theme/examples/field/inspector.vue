<template>
  <doc-wrapper :inspect-class="inspectClass">
    <template #default="s">
      <o-field v-bind="s" label="Field">
        <o-input v-model="name" name="name" placeholder="Name" expanded></o-input>
        <o-input name="email" type="email" placeholder="nobody@nowhere.com" expanded></o-input>
      </o-field>
    </template>
  </doc-wrapper>
  <inspector :inspectData="inspectData" @inspect-class="inspectClass = $event"></inspector>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      inspectClass: {},
      inspectData: [
        {
          class: "rootClass",
          description: "Class of the root element"
        },
        {
          class: "mobileClass",
          description: "Class of file component when on mobile",
          warning: "Switch to mobile view to see it in action!",
        },
        {
          class: "horizontalClass",
          description: "Class to align label and control in horizontal forms",
          properties: ['horizontal'],
          specificity: "when <b>mobileClass</b> is applied",
          action: (cmp) => {
            cmp.data.horizontal = true;
          }
        },
        {
          class: "groupedClass",
          description: "Class when fields are grouped together",
          properties: ['grouped'],
          action: (cmp) => {
            cmp.data.grouped = true;
          }
        },
        {
          class: "groupMultilineClass",
          description: "Class when fields fill up multiple lines",
          properties: ['groupMultiline'],
          action: (cmp) => {
            cmp.data.groupMultiline = true;
          }
        },
        {
          class: "labelClass",
          description: "Class for field label"
        },
        {
          class: "labelSizeClass",
          description: "Class for field label size",
          properties: ['labelSize'],
          suffixes: ['small', 'medium', 'large'],
          action: (cmp) => {
            cmp.data.labelSize = "large";
          }
        },
        {
          class: "labelHorizontalClass",
          description: "Class for field label when horizontal",
          properties: ['horizontal'],
          specificity: "when <b>mobileClass</b> is applied",
          action: (cmp) => {
            cmp.data.horizontal = true;
          }
        },
        {
          class: "fieldInputWrapperClass",
          description: "Class for wrapper that contains input and message",
        },
        {
          class: "bodyClass",
          description: "Class for field body"
        },
        {
          class: "bodyHorizontalClass",
          description: "Class for field body when horizontal",
          specificity: "when <b>mobileClass</b> is applied",
          properties: ['horizontal'],
          action: (cmp) => {
            cmp.data.horizontal = true;
          }
        },
        {
          class: "addonsClass",
          description: "Class for components automatically attached together when inside a field",
          warning: "Use the <code>expanded</code> prop on the control to fill up the remaining space",
          action: (cmp) => {
            cmp.data.expanded = true;
          }
        },
        {
          class: "messageClass",
          description: "Class for the field message",
          properties: ["message"],
          action: (cmp) => {
            cmp.data.message = 'This is a message for the field';
          }
        },
        {
          class: "variantMessageClass",
          description: "Class of the message field variant",
          properties: ["variant"],
          suffixes: ['primary', 'info', 'warning', 'danger'],
          action: (cmp) => {
            cmp.data.variant = "info";
            cmp.data.message = 'This is a message for the field';
          }
        },
        {
          class: "variantLabelClass",
          description: "Class of the label field variant",
          properties: ["variant"],
          suffixes: ['primary', 'info', 'warning', 'danger'],
          action: (cmp) => {
            cmp.data.variant = "info";
          }
        },
        {
          class: "focusedClass",
          description: "Class for the focused field",
          warning: "focus event emitted by form elements",
          action: (cmp) => {
            cmp.$el.focus()
          }
        },
        {
          class: "filledClass",
          description: "Class for the filled field",
          warning: "when it contains a input",
          action: () => {
            this.name = 'Oruga'
          }
        },
      ],
    };
  },
};
</script>
