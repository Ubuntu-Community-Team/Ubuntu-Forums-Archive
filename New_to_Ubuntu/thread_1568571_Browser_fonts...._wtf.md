---
title: "Browser fonts.... wtf"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-09-05
(this is my first post from ubuntu yay)
i just got on the web and noticed the text in firefox looks different here than on windows... then i started going to some sites and the text gets jumbled up..
i attatched a file of a screenshot of a site that jumbles up

---

### Post by sandyd on 2010-09-05
> **Proto_Blaze said:**
> (this is my first post from ubuntu yay)
i just got on the web and noticed the text in firefox looks different here than on windows... then i started going to some sites and the text gets jumbled up..
i attatched a file of a screenshot of a site that jumbles up
what video drivers are you using?
there was an issue with them earlier in the release.
post the output of
```

lspci
``````

cat /etc/X11/xorg.conf
```(just ignore if it says file missing, this is perfrectly ok)

and have you installed the ubuntu-restricted extras package as well?
the fonts on the page may very well be microsoft fonts, which are included in the package. Which would also explain why the corruption is occuring.

If you havent installed it, install ubuntu-restricted-extras

---

### Post by Proto_Blaze on 2010-09-05
> **carlee said:**
> what video drivers are you using?
there was an issue with them earlier in the release.
post the output of
```

lspci
``````

cat /etc/X11/xorg.conf
```(just ignore if it says file missing, this is perfrectly ok)

and have you installed the ubuntu-restricted extras package as well?
the fonts on the page may very well be microsoft fonts, which are included in the package. Which would also explain why the corruption is occuring.

If you havent installed it, install ubuntu-restricted-extras

ive installed the ubuntu extras and did the codes you gave me (which didnt change anything)
as for video drivers.. i used the ones that the ubuntu pop up thing wanted to install

---

### Post by Rubi1200 on 2010-09-05
Maybe take a look here:
[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

There is a section near the end about font issues (not exactly the same but it may lead you in the right direction I hope)

(courtesy of forum member lovinglinux)

You might also want to take a look at the default font in Firefox and change it to something else (Edit > Preferences > Content)

---

### Post by Proto_Blaze on 2010-09-05
would a different browser fix this?

---

### Post by Rubi1200 on 2010-09-05
Not sure; you may have a corrupted Firefox profile:
[http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

See #4 on the list

---

### Post by Proto_Blaze on 2010-09-05
switching profiles didnt help... and now i cant switch to my old profile.. with my settings and all that. :-(

---

### Post by Proto_Blaze on 2010-09-05
just so you know.. that site is the only site that jumbles the text.. every other site ive been on works perfect... and looks perfect

---

