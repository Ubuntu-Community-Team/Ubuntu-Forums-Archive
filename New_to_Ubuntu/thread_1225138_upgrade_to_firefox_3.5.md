---
title: "upgrade to firefox 3.5"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by wirate on 2009-07-28
Hi,
Using Synaptic package manager, I installed the package named firefox 3.5. I clicked mark all upgrades and installed all of them.
Earlier my firefox was showing version 3.0.8 and now it shows 3.0.12. :( why?

---

### Post by wojox on 2009-07-28
Are you clicking the icon on the panel?

Try Applications > Internet and look for another browser.

---

### Post by rannable on 2009-07-28
my ubuntu is showing the same version of firefox too, i heard firefox is slow to update on ubuntu. just be glad we arent using the cutting edge technology so its more stable :D

---

### Post by drs305 on 2009-07-28
You may have separate installations. The Firefox 3.5 standard icon (Shiretoko) is blue on my computer. In a terminal, try starting firefox 3.5 with"
```

firefox-3.5 &

```
If it starts 3.5, you may want to restart it with "firefox-3.5 -profilemanager" and point it to your current profile if it used a default profile on start (none of your bookmarks, homepage, etc).

---

### Post by viltsu on 2009-07-28
If you've installed the 3.5 and the 3.0 then it might be that the link in the menu is opening the older version. Try opening the terminal and try to start the firefox from there by typing "firefox-3.5". If that works then you could delete the symlink /usr/bin/firefox and relink it to the firefox-3.5 executable (probably in the same directory).

---

### Post by wirate on 2009-08-01
Installed Shiretoko and removed firefox :) (what kind of naming is that?)

---

### Post by arochester on 2009-08-01
You can get the "ordinary" Firefox 3.5.1 by using the script called Ubuntuzilla from
here: [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Page down to "Installation". I have a 32 bit machine so the operations are - download the .deb, right click it and install, then run the command (in a Terminal):
> ubuntuzilla.py -a install -p firefox
and answer the questions...

---

### Post by jacklinux on 2009-08-01
i had this problem so i installed 3.0 again and then tryed to upgrade. worked like a charm

---

### Post by Ratscallion on 2009-08-01
There is a video on YouTube for this: [http://www.youtube.com/watch?v=GW1MVXVReys](http://www.youtube.com/watch?v=GW1MVXVReys)

---

### Post by colau on 2009-08-15
> **waqar said:**
> Installed Shiretoko and removed firefox :) (what kind of naming is that?)
shiretoko is firefox-3.5

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by Ratscallion on 2009-08-16
> **colau said:**
> easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

+1

---

### Post by feb3 on 2009-08-16
Worked like a charm - much better than ending up with Shiretoko and two versions of FF on the computer. Thanks for link to video and website.
[[img]http://www.mysmiley.net/imgs/smile/happy/happy0062.gif[/img]](http://www.mysmiley.net/free-indifferent-smileys.php)

---

### Post by Dobbie03 on 2009-08-16
I have the proper Firefox installed none of this Shiretoko rubbish, this link here helped me with that:
[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)

---

