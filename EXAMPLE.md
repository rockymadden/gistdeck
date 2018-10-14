name: inverse
layout: true
class: center, middle, inverse
---
#[Gist => Deck](https://github.com/gistdeck/gistdeck.github.com)
.footnote[powered by [remark.js](https://github.com/gnab/remark)]
---
## What is it and why should I be using it?
---
layout: false
.left-column[
## What is remark?
]
.right-column[
A simple, in-browser, Markdown-driven slideshow tool
- Markdown formatting, with smart extensions
- Presenter mode, with cloned slideshow view
- Syntax highlighting, supporting a range of languages
- Slide scaling, thus similar appearance on all devices / resolutions .red[*]
- Touch support for smart phones and pads, i.e. swipe to navigate slides
.footnote[.red[*] At least browsers try their best]
]
---
.left-column[
## What is remark?
## What is gistdeck?
]
.right-column[
gistdeck let you host your remark source code in gist, and instantantly render in to remark slide, which means:
- you don't have to find place to host your slides
- you got version control of your slide source
- you can even analytics your slide by using [ga-beacon](https://github.com/igrigorik/ga-beacon)
]
---
.left-column[
## What is remark?
## What is gistdeck?
## Why use it?
]
.right-column[
If your ideal slideshow creation workflow contains any of the following steps:
- Just write what's on your mind
- Do some basic styling
- Easily collaborate with others
- Share with and show to everyone
Then remark might be perfect for your next.red[*] slideshow!
.footnote[.red[*] You probably want to convert existing slideshows as well]
]
---
template: inverse
## How does it work, then?
---
name: how
.left-column[
## How does it work?
### - Markdown
]
.right-column[
A Markdown-formatted chunk of text is transformed into individual slides by JavaScript running in the browser:
```remark
# Slide 1
This is slide 1
---
# Slide 2
This is slide 2
```
.slides[
.first[
### Slide 1
This is slide 1
]
.second[
### Slide 2
This is slide 2
]
]
Regular Markdown rules apply with only a single exception:
- A line containing three dashes constitutes a new slide
(not a horizontal rule, `&lt;hr /&gt;`)
Have a look at the [Markdown website](http://daringfireball.net/projects/markdown/) if you're not familiar with Markdown formatting.
]
---
.left-column[
## How does it work?
### - Markdown
### - Inside HTML
]
.right-column[
A simple HTML document is needed for hosting the styles, Markdown and the generated slides themselves:
```xml
<!DOCTYPE html>
<html>
<head>
<style type="text/css">
/* Slideshow styles */
</style>
</head>
<body>
* <textarea id="source">
<!-- Slideshow Markdown -->
&lt;/textarea&gt;
* <script type="text/javascript" src="remark.js">
</script>
<script type="text/javascript">
* var slideshow = remark.create();
</script>
</body>
</html>
```
You may download remark to have your slideshow not depend on any online resources, or reference the [latest version](https://remarkjs.com/downloads/remark-latest.min.js) online directly.
]
---
template: inverse
## Of course, Markdown can only go so far.
---
.left-column[
## Markdown extensions
]
.right-column[
To help out with slide layout and formatting, a few Markdown extensions have been included:
- Slide properties, for naming, styling and templating slides
- Content classes, for styling specific content
- Syntax highlighting, supporting a range of languages
]
---
.left-column[
## Markdown extensions
### - Slide properties
]
.right-column[
Initial lines containing key-value pairs are extracted as slide properties:
```remark
name: agenda
class: middle, center
# Agenda
The name of this slide is {{ name }}.
```
Slide properties serve multiple purposes:
* Naming and styling slides using properties `name` and `class`
* Using slides as templates using properties `template` and `layout`
* Expansion of `{{ property }}` expressions to property values
See the [complete list](https://github.com/gnab/remark/wiki/Markdown#slide-properties) of slide properties.
]
---
.left-column[
## Markdown extensions
### - Slide properties
### - Content classes
]
.right-column[
Any occurences of one or more dotted CSS class names followed by square brackets are replaced with the contents of the brackets with the specified classes applied:
```remark
.footnote[.red.bold[*] Important footnote]
```
Resulting HTML extract:
```xml
<span class="footnote">
<span class="red bold">*</span> Important footnote
</span>
```
]
---
.left-column[
## Markdown extensions
### - Slide properties
### - Content classes
### - Syntax Highlighting
]
.right-column[
Code blocks can be syntax highlighted by specifying a language from the set of [supported languages](https://github.com/gnab/remark/wiki/Configuration#highlighting).
Using [GFM](http://github.github.com/github-flavored-markdown/) fenced code blocks you can easily specify highlighting language

A number of highlighting [styles](https://github.com/gnab/remark/wiki/Configuration#highlighting) are available, including several well-known themes from different editors and IDEs.
.pull-left[
<pre><code>```javascript
function add(a, b){
return a + b
}
```</code></pre>
]
.pull-right[
<pre><code>``````ruby
def add(a, b)
a + b
end
```</code></pre>
]
]
---
.left-column[
## Markdown extensions
### - Slide properties
### - Content classes
### - Syntax Highlighting
### - MathJax
]
.right-column[
`$$\int_\Omega \nabla v \cdot \nabla u - \lambda v u ~dV = \int_\Omega v f ~dV$$`
]
---
.left-column[
## Presenter mode
]
.right-column[
To help out with giving presentations, a presenter mode comprising the
following features is provided:
- Display of slide notes for the current slide, to help you remember
key points
- Display of upcoming slide, to let you know what's coming
- Cloning of slideshow for viewing on extended display
]
---
.left-column[
## Presenter mode
### - Inline notes
]
.right-column[
Just like three dashes separate slides,
three question marks separate slide content from slide notes:
```markdown
Slide 1 content
*???
Slide 1 notes
---
Slide 2 content
*???
Slide 2 notes
```
Slide notes are also treated as Markdown, and will be converted in the
same manner slide content is.
Pressing __P__ will toggle presenter mode.
]
???
Congratulations, you just toggled presenter mode!
Now press __P__ to toggle it back off.
---
.left-column[
## Presenter mode
### - Inline notes
### - Cloned view
]
.right-column[
Presenter mode of course makes no sense to the audience.
Creating a cloned view of your slideshow lets you:
- Move the cloned view to the extended display visible to the audience
- Put the original slideshow in presenter mode
- Navigate as usual, and the cloned view will automatically keep up with the original
Pressing __C__ will open a cloned view of the current slideshow in a new
browser window.
]
---
template: inverse
## It's time to get started!
---
.left-column[
## Getting started
]
.right-column[
Getting up and running is done in only a few steps:
1. Go to your gist and write some markdown.
2. put a "deck" right after "gist" in url like this:
```
              deck
                v
https://gist.github.com/jcouyang/8acfc555a718d62b77b2
                |
                V
https://gistdeck.github.com/jcouyang/8acfc555a718d62b77b2
```
3. enjoy the slide remark generated.
For more information on using remark, please check out the [wiki](https://github.com/gnab/remark/wiki) pages.
]
---
name: last-page
template: inverse
## That's all folks (for now)!
Slideshow created using [remark](http://github.com/gnab/remark) and host on [gistdeck](https://gistdeck.github.com).
