---
title: "Chrome magnet links"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by nito2721 on 2011-02-09
[SOLVED Post 3]

This is probably a simple question for some, but I'm new to linux/ubuntu. 

I accidentally chose do nothing when clicking magnet links inside chromium. Now I cant associate to transmission...  

Ideas? 

I googled for answers which has fixed most of my issues, but this is a rare problem I guess. 

Thanks in advance.

---

### Post by nito2721 on 2011-02-10
Either my question was so simple that no one bothered to answer, or so complex that no one has an answer. 

Thanks anyways. I guess I'll just live with it. 

"Desire is the root of all suffering" - Buddha

---

### Post by nito2721 on 2011-02-11
When I get 105 views, and no answers it must mean "Figure it out on your own!!!"

So... I did. 

Alt + F2

type gconf-editor

enter

desktop -> gnome -> url-handlers -> magnet

edit command string

/usr/bin/transmission-gtk %s

exit then test. Worked for me. 

Credit to [this post]("http://ubuntuforums.org/showthread.php?t=229924")

---

### Post by heepie on 2012-01-12
This doesn't work anymore with Ubuntu 11.10 which uses dconf instead of gconf.

Any ideas how to fix this...

---

### Post by the_master on 2012-01-21
this doesn't work in 11.10 either.  Its ridiculous that its this difficult.

---

### Post by TechZilla on 2012-02-08
.. Its so ridiculous, the web is filled with people mindlessly echoing the same old answers.

If the answer (practically plastered all over the web) worked nobody would go through the trouble of posting.  Dconf has replaced gconf for a good amount of time already, so all the old answers involving Gconf are not applicable.

I think we have to mess with xgd-open, at least in regards to chrome

---

