---
layout: post
title: "Jekyll Learning #01 - Add Google Analytics"
subtitle: 'How to add Google Analytics to your Jekyll website?'
date: 2024-02-18 11:00:00
author: "WENEW"
copyright-statement: 
hidden: false
header-img: "img/post/post-bg-google-analysis.jpg"
excerpt: And thus know more about your visitors.
catalog: true
tags:
  - Jekyll
  - Google Analytics
---

Adding Google Analytics to your Jekyll website enables you to know more about your visitors, including the number of visitors, the time they visit, their locations and more. Sounds interesting right?


Well, nothing comes without a price. From then on, Google has an eye on your website :-)

But let's get started and go through the steps.

### Create a Google Analytics account

First, go to [Google Analytics](https://analytics.google.com/analytics/web/) and create an account.

Then, create a property for your website. During the process, remember to open **Show advanced options** and turn on the switch for **Create a Universal Analytics property**. Input the URL of your website and choose **Create a Universal Analytics property only**.

Finish the property creation steps and you should see your "UA-" tracking ID and a code snippet similar to the following (my tracking ID is replaced with "X"s btw so make sure to use your own ID).

```
<!-- Global site tag (gtag.js) - Google Analytics -->
<script
  async
  src="https://www.googletagmanager.com/gtag/js?id=UA-XXXXXXXXX-X"
></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
  gtag("js", new Date());

  gtag("config", "UA-XXXXXXXXX-X");
</script>
```

### Configure Jekyll settings

Use the previous code snippet to create a new file called `google_analytics.html` and put it inside the folder `_includes` of your Jekyll project. Create the `_includes` folder as well if you don't have one.

<div class="codeblock-label">_includes/google_analytics.html</div>

```
{% raw %}<!-- Global site tag (gtag.js) - Google Analytics -->
<script
  async
  src="https://www.googletagmanager.com/gtag/js?id=UA-XXXXXXXXX-X"
></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
  gtag("js", new Date());

  gtag("config", "UA-XXXXXXXXX-X");
</script>{% endraw %}
```

Then, include the `google_analytics.html` inside the layout file we want to have the tracking functionality. For me it is the `default.html` inside the `_layouts` folder.

<div class="codeblock-label">_layouts/default.html</div>

```
{% raw %}{% include google_analytics.html %}{% endraw %}
```

The last step is to put your tracking ID inside the `_config.yml` of your Jekyll website.

<div class="codeblock-label">_config.yml</div>

```
{% raw %}google-analytics: UA-XXXXXXXXX-X{% endraw %}
```

That's it!

Now you may access [Google Analytics](https://analytics.google.com/analytics/web/), clicking the left sidebar and go to `REPORTS/Realtime/Overview`.

You will see that your website has one visitor, which is yourself!

What a success!

### References

- [How to add Google Analytics to a blog hosted on Github pages](https://morotsman.github.io/blog,/google/analytics,/jekyll,/github/pages/2020/07/07/add-google-analytics.html)
