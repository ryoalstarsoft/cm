
# Front End Refactoring Challenge

In TodoForm component, I converted jquery to ref.

From
```
<input
    type="text"
    id="itemName"
    className="form-control"
    placeholder="add a new todo..."
/>
```
To
```
<input
    type="text"
    ref={e => this.itemNameRef = e}
    id="itemName"
    className="form-control"
    placeholder="add a new todo..." />
```

From
```
componentDidMount() {
    $("#itemName").focus();
}
onSubmit(event) {
    event.preventDefault();
    var newItemValue = $("#itemName").val();

    if (newItemValue) {
      this.props.addItem({ newItemValue });
      $('#todoForm').trigger("reset");
    }
}
```
To
```
componentDidMount() {
    this.itemNameRef.focus();
}
onSubmit(event) {
    event.preventDefault();
    let newItemValue = this.itemNameRef.value;

    if (newItemValue) {
      this.props.addItem({ newItemValue });
      this.refs.form.reset();
    }
}
```

In Timer Component,

From
```
updateTimer = () => {
    this.setState({
      count: this.state.count += 1
    });
}
```
To
```
updateTimer = () => {
    this.setState({
      count: this.state.count + 1
    });
}
```

Removed in App.js
```
const $ = window.$ = window.jQuery = jquery;
```