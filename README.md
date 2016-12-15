# marionete-mnx
Marionette Declarative Templating

Brainstorming

Will probably support template literal tag and a renderer function as well... or something..

Goal API:
```js
const View = Mn.View.extend({
  triggers: {
    'click @ui.button': 'click'
  },
  onClick() {
    this.showChildView('content', new MyContentView(this.model)); // replaceElement: true by default
    this.showChildView('other', new MyOtherView(this.model)); // replaceElement: false by default
    console.log(this.getRegion('content').$el.selector); // '[data-mnr-1234]'
    console.log(this.ui.button.$el); // '[data-mnui-74893];
  },
  onMouseover() {
    console.log('"on-" prefixes will add a trigger');
  },
  onMouse
  template() {
    return mnx`
      <div>
        ${ '<strong>Will not be bolded and html encoded</strong>' }
        ${ { string: '<strong>Will not be bolded and html encoded</strong>' } }
        ${ { html: '<strong>Will be bolded</strong>' } }
        <button ui="button" on-mouseover="mouseover">Click Me</button>
        <region name="content"></region>
        <div region="other"></div>
      </div>
    `;
  }
});
```
