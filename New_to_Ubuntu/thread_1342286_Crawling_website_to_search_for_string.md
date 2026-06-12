---
title: "Crawling website to search for string"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by jsfour on 2009-11-30
Hey Guys,

I am looking for a more efficient way to crawl through a website [www.[xyzdomain].com](www.[xyzdomain].com) and search all of the documents for a specific string.

Right now, I am using wget to grab the site recursively and running grep on the output. This works, but it seems a little redundant because I just end up deleting the files afterwards.

Anyone have any ideas?

---

### Post by 0cton on 2009-11-30
you could do a script in python.

---

### Post by Zill on 2009-11-30
jsfour:  There are various search add-ons for Firefox that may help with this problem.
eg. [Search Everywhere]("https://addons.mozilla.org/en-US/firefox/addon/5054")

Caveat: I haven't actually tried this one so I can't personally vouch for it ;-)

---

### Post by jsfour on 2009-11-30
> **0cton said:**
> you could do a script in python.

How would I go about starting this? I have a few years (3+ years of c++,c,.asp,php) programming in college under my belt so i understand how coding works. 

Does python execute *nix commands?

---

### Post by nazgulord on 2009-11-30
why not use ```
wget -O - your_website| grep your_string
```?

Using the -O - option makes wget output to stdout, so no files are created.

---

### Post by jsfour on 2009-11-30
> **nazgulord said:**
> why not use ```
wget -O - your_website| grep your_string
```?

Using the -O - option makes wget output to stdout, so no files are created.


I think this may do it, can I set wget to only search in text documents (html, php, etc)? 

Would that be the -A switch? 

```
wget -r -A.html -O - mysite.html | grep the_string?
```

?

---

### Post by nazgulord on 2009-12-01
Yep, just looked at wget's help and that seems right :).

---

