---
title: "prolonged boot problem and  no sound"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by SandyM on 2010-09-28
I usually download a lot of software and also do some tweaking. But one day I noticed that my ubuntu took nearly 7 to 8 minute to boot after slecting the right grub menu entry.

Then when it finally booted, I noticed that my sound and volume icon was not there in the panel, later when I played some music sound was not there.

Now I am consistently facing this problem and have to reboot again and again till I am fortunate enough to get back my sound. However the icon is still absent.

I believe the prolong boot can directly be attributed to the sound problem but does not know how to tackle it.

---

### Post by andrewthomas on 2010-09-28
What do the logs look like?

/var/log/messages

---

### Post by johnjb on 2010-09-28
First off right click on your panel then click add to panel look for Notification Area select then add should clear your missing icons.
I would suggest upgrading Alsa sound drivers as this is how I cured mine the ling I used was  
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Hope this Helps

---

### Post by SandyM on 2010-09-30
> **johnjb said:**
> First off right click on your panel then click add to panel look for Notification Area select then add should clear your missing icons.
I would suggest upgrading Alsa sound drivers as this is how I cured mine the ling I used was  
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Hope this Helps

> **andrewthomas said:**
> What do the logs look like?

/var/log/messages




Sir I don't know how to interpret this log. What do you want me to do with it?

---

### Post by SandyM on 2010-09-30
> **johnjb said:**
> First off right click on your panel then click add to panel look for Notification Area select then add should clear your missing icons.
I would suggest upgrading Alsa sound drivers as this is how I cured mine the ling I used was  
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
Hope this Helps

I did as you asked. I added notification area but nothing happened my sound icon was still not there.

I also compiled the latest alsa as recommended by you through the link you posted but nothing helped. 

I am still facing prolonged boot and absence of sound when I finally log on.

---

