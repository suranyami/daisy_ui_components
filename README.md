# DaisyUI Components

<img src="daisyui-logomark-1024-1024.png" alt="Daisy UI Logo" width="150">

[![CI](https://github.com/phcurado/daisy_ui_components/actions/workflows/ci.yml/badge.svg)](https://github.com/phcurado/daisy_ui_components/actions/workflows/ci.yml)
[![Coverage Status](https://coveralls.io/repos/github/phcurado/daisy_ui_components/badge.svg?branch=main)](https://coveralls.io/github/phcurado/daisy_ui_components?branch=main)
[![Hex.pm](https://img.shields.io/hexpm/v/daisy_ui_components)](https://hex.pm/packages/daisy_ui_components)
[![HexDocs.pm](https://img.shields.io/badge/Docs-HexDocs-blue)](https://hexdocs.pm/daisy_ui_components)
[![License](https://img.shields.io/hexpm/l/daisy_ui_components.svg)](https://hex.pm/packages/daisy_ui_components)

This project brings [Daisy UI](https://daisyui.com/) components into your Phoenix LiveView project.

This project is still experimental, expect breaking changes in future.

## Installation

<!-- MDOC -->

Reference this repository on your `mix.exs` file to start using.

```elixir
def deps do
  [
    {:daisy_ui_components, "~> 0.3"}
  ]
end
```

Add through `npm` the daisy UI package inside your phoenix application:

```
cd assets
npm i -D daisyui@latest
```

On `tailwind.config.js` include Live DaisyUI Components under the content list and reference under plugins

```javascript
module.exports = {
  content: [
    //...
    "../deps/daisy_ui_components/**/*.*ex" // <- reference DaisyUIComponents as content path
  ],
  //...
  plugins: [
    //...
    // comment the tailwind form to not conflict with DaisyUI
    // require("@tailwindcss/forms"),
    require("daisyui")  <- // add daisyUI plugin
    //...
  ]
}
```

Add error translation function to your app's config.exs file. This function is used to translate ecto changeset errors

```elixir
config :daisy_ui_components, translate_function: &MyAppWeb.CoreComponents.translate_error/1
```

And now this library is ready. To have the components available under liveview, import the components on the web folder

```elixir
defp html_helpers do
  quote do
    # Translation
    use Gettext, backend: MyAppWeb.Gettext

    # Import DaisyUI components into your project
    use DaisyUIComponents
    # HTML escaping functionality
    import Phoenix.HTML
    # Phoenix CoreComponents replacement
    import DaisyUIComponents.CoreComponents

    # import YourProjectWeb.CoreComponents
    # Importing CoreComponents from your project is no longer necessary since
    # DaisyUIComponents.CoreComponents offers a drop in replacement
    # If you still want to use your own core components, remember to delete the default components generated from phoenix in this file
    # ...
  end
end
```

In order to not conflict with some of the DaisyUI default styles, remove the `bg-white` class in your `root.html.heex` file.

```heex
# Change from this
<body class="bg-white">
# to this
<body>
```

This library includes its own [Core Components](./lib/daisy_ui_components/core_components.ex) styled with DaisyUI. It is designed to replace your existing CoreComponents, ensuring that Phoenix generators continue to work seamlessly in your project.

If you encounter any compatibility issues, feel free to open an `issue` or submit a `pull request`, and I'll take a look.

## Liveview 1.0

This project is fully compatible with the Liveview 1.0 🔥. If you are using a previous Liveview version, check the [migration guide](https://github.com/phoenixframework/phoenix_live_view/blob/main/CHANGELOG.md#backwards-incompatible-changes-for-10).

## Components

List of available components.

- [Alert](https://daisyui.com/components/alert) ✅
- [Artboard](https://daisyui.com/components/artboard) ❌
- [Avatar](https://daisyui.com/components/avatar) ✅
- [Badge](https://daisyui.com/components/badge) ✅
- [Bottom navigation](https://daisyui.com/components/botton-navigation) ❌
- [Breadcrumbs](https://daisyui.com/components/breadcrumbs) ✅
- [Button group](https://daisyui.com/components/button-group) ✅
- [Button](https://daisyui.com/components/button) ✅
- [Card](https://daisyui.com/components/card) ✅
- [Carousel](https://daisyui.com/components/carousel) ❌
- [Chat bubble](https://daisyui.com/components/chat) ❌
- [Checkbox](https://daisyui.com/components/checkbox) ✅
- [Collapse](https://daisyui.com/components/collapse) ❌
- [Countdown](https://daisyui.com/components/countdown) ❌
- [Divider](https://daisyui.com/components/divider) ❌
- [Drawer](https://daisyui.com/components/drawer) ❌
- [Dropdown](https://daisyui.com/components/dropdown) ❌
- [File input](https://daisyui.com/components/file-input) ❌
- [Footer](https://daisyui.com/components/footer) ❌
- [Join](https://daisyui.com/components/join) ✅
- [Hero](https://daisyui.com/components/hero) ❌
- [Indicator](https://daisyui.com/components/indicator) ❌
- [Input group](https://daisyui.com/components/input-group) ❌
- [Text Input](https://daisyui.com/components/input) ✅
- [Kbd](https://daisyui.com/components/kbd) ❌
- [Link](https://daisyui.com/components/link) ❌
- [Loading](https://daisyui.com/components/loading/) ✅
- [Mask](https://daisyui.com/components/mask) ❌
- [Menu](https://daisyui.com/components/menu) ❌
- [Code mockup](https://daisyui.com/components/mockup-code) ❌
- [Phone mockup](https://daisyui.com/components/mockup-phone) ❌
- [Window mockup](https://daisyui.com/components/mockup-window) ❌
- [Modal](https://daisyui.com/components/modal) ✅
- [Navbar](https://daisyui.com/components/navbar) ✅
- [Pagination](https://daisyui.com/components/pagination) ✅
- [Progress](https://daisyui.com/components/progress) ❌
- [Radial progress](https://daisyui.com/components/radial-progress) ❌
- [Radio](https://daisyui.com/components/radio) ❌
- [Range slider](https://daisyui.com/components/range) ✅
- [Rating](https://daisyui.com/components/rating) ❌
- [Select](https://daisyui.com/components/select) ✅
- [Stack](https://daisyui.com/components/stack) ❌
- [Stat](https://daisyui.com/components/stat) ✅
- [Steps](https://daisyui.com/components/steps) ❌
- [Swap](https://daisyui.com/components/swap) ✅
- [Tabs](https://daisyui.com/components/tab) ❌
- [Table](https://daisyui.com/components/table) ✅
- [Textarea](https://daisyui.com/components/textarea) ✅
- [Toast](https://daisyui.com/components/toast) ❌
- [Toggle](https://daisyui.com/components/toggle) ✅
- [Tooltip](https://daisyui.com/components/tooltip) ✅

✅: Implemented
❌: To be implemented
