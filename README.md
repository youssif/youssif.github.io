# Personal Site Template

This is a template for your own personal site including a portfolio, blog, and résumé. It is based on the fantastic [middleman-zurb-template](https://github.com/mattolson/middleman-zurb-template) project.

## Installation

**NOTE:** The following instructions assume that you'll be using GitHub Pages personal sites as your host. You'll want to go ahead and clone down your personal site repo first, and then delete it from GitHub. Now go ahead and create a new one (username.github.io).

Go ahead and grab a copy of the code for the site and install the bundle:

```console
git clone https://github.com/makersquare/personal-site-template.git username.github.io
cd username.github.io
bundle install
```

If you haven't already, create your personal site repo on GitHub (be sure it has the name username.github.io, where username is your GitHub username. Now run the following setup rake task:

```console
bundle exec rake setup_github_pages
```

It will ask you to paste in the git URL for your personal site repo. Personal sites use the master branch, so this rake task will rename your master branch to source. Go ahead and push up the code for your site:

```console
git push origin source
```

Now generate and deploy the site:

```console
bundle exec middleman build
bundle exec middleman deploy
```

After a few minutes, your site should be live.

## Configuration

Most of the site can be configured via altering values in the `config.rb` file.

### Résumé

Drop a PDF of your résumé in the source directory. Now set `resume` to the name of the file. A link will appear in the top navigation bar.

### Social Networking Links

Under the "Social Network link settings" section of `config.rb`, reset the values to point at your social networking accounts, or set them to nil to leave them out of the navigation.

### Projects

You can highlight your projects with the portfolio section of the site. Use the `data/projects.yaml` file as a template for listing a description of each of your projects. They will automatically 

#### Taking Screenshots

Use Safari to view a live version of your project. Press command-shift-4-space, then click on the Safari window to save a screenshot to the Desktop. Now open the screenshot in Preview, and resize the image to 50% of its original size. Now drop the image file into `source/images`.


### Disqus integration (for blog)

Create a Disqus account for your blog, and set the `disqus_shortname` variable in `config.rb` to the shortname for your blog.

### Google Analytics integration

Create a Google Analytics account, and set the `google_analytics_tracking_id` appropriately.

## Blogging

Refer to [the middleman-blog docs](http://middlemanapp.com/blogging/) for information on using the blog.

### Removing blog functionality

This template is still a good starting point for sites that don't require blogging functions. To remove blog-specific stuff:

1. `git rm source/blog/*`
2. `git rm source/layouts/article.erb`
3. Remove middleman-blog from Gemfile.
4. Remove blog-related styles from source/stylesheets/base.css.scss. They are all at the bottom of the file grouped together under the header "Blog Articles".
5. Remove blog-related settings from config.rb. They are all grouped at the top under the header "Blog Settings".
6. Remove the link to the blog in the markup for the navbar (in `layouts/layout.erb`).
7. Remove the `section.latest-from-blog` element from the markup in `index.html.erb`, and remove the following code from `landing-page.css.scss`:

```scss
section.latest-from-blog, section.featured-project {
  @include grid-column(6);
}
```

## Deploying

To deploy, just run the following again:

```console
bundle exec middleman build
bundle exec middleman deploy
```

