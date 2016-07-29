---
layout: post
title:  "First Post - Setting Up Jekyll"
date:   2016-07-28 23:28:04 -0700
categories: web
tags: jekyll
---
{% raw %} 
A few days ago, I decided to revamp my personal website (for those who are curious, still accessible [here][old]). I decided that this was an excellent opportunity to start a blog that outlines my journey in computer science as well as in startups! 

Forewarning: I haven't really thought through what I am planning to put on this blog, so I suppose it'll be a mix of my thoughts with some teaching components for those who are interested in learning more about what I'm playing with at the current time.


Here's a quick list of what I am using to make this site possible:

1. DNS: Google Domains
  * This is what I used to purchase my current website domain. I've had an excellent experience using Namecheap in the past (and currently as well), but I decided to try out Google's DNS. 
2. Hosting: Github Pages 
  * Very easy to set-up alongside Jekyll, more below. FREE!
3. Jekyll
  * Jekyll basically takes your blog layout/styling and your posts and generates a static website out of it that can then be hosted on a server such as Github Pages.
  * Simple way to host blogs. Basically after using a theme or building one on your own, adding posts is extremely easy.
  * I have not personally used WordPress before, but from the research I gathered WordPress is more of a CMS rather than a blog style website nowadays. 
  * Free hosting with Github Pages.
4. Embeds: Google Forms/Google Drive
  * Through the use of embeds, it is possible to have features that are normally reserved to a dynamic website, such as a contact form or to super easily view PDFs, in this case for my resume.

# Setup
As I have Ruby (RVM) and RubyGems already, this process was extremely easy by running the command `gem install jekyll`. Check out [Jekyll's website][jekyll] for links to all the dependencies you'll need.

# Creating Your Website
Run the following commands to create your website!
```
jekyll new my-awesome-site
cd my-awesome-site
~/my-awesome-site 
jekyll serve
```
Now go on `localhost:4000` on your browser and your brand new website! 

Important Note: Moving forward, `jekyll serve` will be very important as it is the command that both parses your code and hosts it locally. Jekyll automatically checks for any changes and will regenerate your website with one major exception, your `_config.yml` file. Simply hit `Control+C` to quit Jekyll and run `jekyll serve` again after.

# File Structure
With so many generated folders and files it may seem like a lot, but not to worry it's actually pretty straight forward! I'll go through the major ones that are of note.

* `_config.yml` is where configuration data is stored, things such as the title of your website, description, and url to your website.
* `_layouts` folder is, as explained by the folder, the actual layout and structure of the pages that you'll be creating. 
  - In `default.html`, you'll notice:
    - ` {% include head.html %}`, which basically means that the HTML code of `head.html` is inserted here.
    - `{{ content }}` , which means that the markdown document that is linked to the file 
* `_includes` is the folder that stores all of these little HTML bits of code that are to be used.
* `_posts` is where once you've built set-up everything to your liking, you'll be spending most of your time. This where all your blog posts will be going. 
* `css` will contain the main SCSS document. To summarize SCSS, think of it as CSS but more powerful as you can do things such as variable declarations. I'm personally not that familiar with it myself and will be learning it as I go. 
* `_sass` is where the variables that you established in the `css` folder will be applied. 
  - `_base.scss` contains the general HTML tags styling.
  - `_layout.scss` contains the CSS for specific classes. You will most likely be modifying this file quite a bit if you want to tweak the appearence of your website.
* For more information check [Jekyll's directory structure document][structure]. 

# Liquid Template
You may have noticed text surrounded by `{}`s. This is known as Liquid templating language, which is used to process tempaltes.  In summary, as the user you can put in filters and outputs. The most important ones you should be aware of is `{{ content }}` and {% include head.html %}, which was explained above, as well as this:

``` HTML
{% for my_page in site.pages %}
  {% if my_page.title %}
    <a class="page-link" href="{{ my_page.url | prepend: site.baseurl }}">{{ my_page.title }}</a>
  {% endif %}
{% endfor %}
```
The way this code block works is that Jekyll, with the help of Liquid Templating's tags, knows to search for all the pages within the site, and if it has a title, creates a link to it. More detail about Jekyll's template system is explained [here][template].

# Markdown



[old]: old.patrickshao.com
[jekyll]: http://jekyllrb.com/docs/installation/
[structure]: https://jekyllrb.com/docs/structure/
[template]: https://jekyllrb.com/docs/templates/
[post-problems]: http://stackoverflow.com/questions/30625044/jekyll-post-not-generated
{% endraw %}