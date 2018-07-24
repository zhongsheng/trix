# Trix for Ruby on Rails

[![Build Status](https://api.travis-ci.org/kylefox/trix.svg)](https://travis-ci.org/kylefox/trix)

Want to include Basecamp's awesome [Trix WYSIWYG
editor](http://trix-editor.org) in your Ruby on Rails application?
You've come to the right place!

Compatible with Rails 4.2 and up.

# Installation

Add `trix-rails` to your `Gemfile`:

```ruby
gem 'trix-rails', require: 'trix'
```

Run `bundle install` and restart your server to make the files available through the pipeline.

Import Trix styles in `app/assets/stylesheets/application.css`:

```css
*= require trix
```

Require Trix Javascript magic in `app/assets/javascripts/application.js`:

```js
//= require trix
```

# Usage

You can use `trix-rails` as a standalone tag, in a form builder, or with popular form libraries.

## Standalone Tag

Create a simple `<trix-editor>` tag:

```ruby
trix_editor_tag(name, value = nil, options = {})
```

For example:

```erb
<%= trix_editor_tag :post, :body, required: true %>
```

## Form builder

Create a Trix editor for a `form_for` or `form_with` attribute:

```ruby
trix_editor(method, options = {})
```

For example:

```erb
<%= post_form.trix_editor :body, required: true, autofocus: true %>
```

## Formtastic and Simple Form

If you're using [Formtastic](https://github.com/justinfrench/formtastic) or [Simple Form](https://github.com/plataformatec/simple_form), you can do this:

```ruby
f.input :body, as: :trix_editor
```

## Options

Any `options` provided will be passed along to the [`content_tag`](https://api.rubyonrails.org/classes/ActionView/Helpers/TagHelper.html#method-i-content_tag) call that outputs the `<trix-editor>` tag.

For example:

```erb
<%= post_form.trix_editor :body, autofocus: true, data: { coffee: :delicious } %>
```

will render:

```html
<trix-editor autofocus="true" data-coffee="delicious">
```

# Contributing

Bug reports and feature requests are welcome. They're _much_ more likely to be addressed if they are accompanied by a pull request 😘

* [Report a bug](https://github.com/kylefox/trix/issues/new?template=bug_report.md)
* [Request a feature](https://github.com/kylefox/trix/issues/new?template=feature_request.md)

## Testing

All pull requests should include tests, where applicable. Pull requests without tests may be rejected.

`trix-rails` uses [Appraisal](https://github.com/thoughtbot/appraisal) to test against supported versions of Rails. You can run the specs against all supported versions with:

```shell
bundle exec appraisal rake spec
```

## Upgrading Trix

To upgrade Trix, simply copy the _compiled_ styles from [`trix/dist`](https://github.com/basecamp/trix/tree/master/dist) into this repository:

- Copy [`trix.js`](https://raw.githubusercontent.com/basecamp/trix/master/dist/trix.js) to `vendor/assets/javascripts/trix.js`
- Copy [`trix.css`](https://raw.githubusercontent.com/basecamp/trix/master/dist/trix.css) to `vendor/assets/stylesheets/trix.css`

# License (MIT)

`trix-rails` is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
