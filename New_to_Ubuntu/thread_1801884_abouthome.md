---
title: "about:home"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by Old-un on 2011-07-11
Decided i didn't want to see Google and its toolbars everytime i opened Firefox so i set the page to about:home but now the search tool in the middle of the page don't work?

---

### Post by nomko on 2011-07-11
Normally i set it to blank page. But did you entered a home page?

---

### Post by Old-un on 2011-07-11
Yes i set it to about:home

---

### Post by Frogs Hair on 2011-07-11
Try about:startpage in preferences and it should bring up the Ubuntu start page if you have Ubuntu Firefox modifications enabled .

I have a Nightly build , so if I use about:home it brings up the Nightly start page . The development builds have different start pages.

---

### Post by dcsoldschool53 on 2011-07-11
I would like to have more details please. I want to know step by step, of exactly, what you did. I know that Ubuntu's starterpage is ```
about:startpage
```and about:home had worked for me. On the other hand, it did not have the look and feel of Google's search engine. ```
about:home
``` is Mozilla's version of a startpage. I would say, change it to something else to see if it works there.
As for the toolbar, you can removed it through managed add-on, in Firefox's preferences. The toolbar maybe what is causing the problem, try removing it.

---

### Post by Old-un on 2011-07-11
Have started using the about:startpage. Still don't like Google's black toolbar but better than before. Thanks for all the help and advice everyone.

---

### Post by grahammechanical on 2011-07-11
If you have about:startpage open, then try a right click and select View Page Source. You will see that the images on that page are download from web sites. Scroll down until you see this:

> <h1 class="logo"><a href="[http://www.google.com]("http://ubuntuforums.org/view-source:http://www.google.com/")">&nbsp;</a></h1>That is where the word/image Google comes from. In fact it is a button linking to the Google home page.

It is possible to copy and paste this source code into a web page editor such as Bluefish and replace what is between <h1 class="logo"> and </h1> with something else, such as Unity Will Conquer! and then save the page as a HTML file with its own name and make it your home page. You will then remove the Google branding but still keep the link to the Google search engine.

Regards.

---

