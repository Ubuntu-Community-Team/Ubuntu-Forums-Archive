---
title: "installed Intrepid 8.10, now Firefox hangs on random sites"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by evouga on 2009-01-23
I just installed Intrepid today, and launched Firefox. Some websites (such as this one) work fine, but others (such as Gmail and a few others) cause firefox to hang. The cursor becomes stuck as either a hand or the spinning ball thing, and Firefox no longer repaints if I drag a different window over it. If I click the "X" I get the option to force quit. Restarting Firefox and visiting the same site predictable  hangs Firefox again.

So far I've tried the following:
 - Rebooting the machine
 - sudo apt-get purge firefox-3.0 followed by sudo apt-get install firefox-3.0.

Please let me know if you have any advice...

EDIT: I've installed Konquerer and and can use it to access the web, however this is a very sub-optimal long-term solution. Should I report this as a Firefox bug? I have Firefox 3.0 installed on my Windows machine and do not experience this problem, so I'm wondering if Firefox is reacting badly to Ubuntu or some shared library.

---

### Post by Melk79 on 2009-01-23
I've changed my link to this [https://mail.google.com/mail/#inbox](https://mail.google.com/mail/#inbox) and gone into about:config, search on IPv6 and disable (change to True).  Seems to speed things up on more than Gmail, can't remember where I read it originally.

---

### Post by evouga on 2009-01-26
In case anyone has similar problems and finds this thread: the problem was that Adobe's flash player is buggy. Disabling the plugin fixed all the issues I was having.

---

### Post by HittingSmoke on 2009-01-26
> **evouga said:**
> In case anyone has similar problems and finds this thread: the problem was that Adobe's flash player is buggy. Disabling the plugin fixed all the issues I was having.

Install NoScript for firefox and any time you visit a new site with Flash or Java content just temporarily enable the site once to see how it works. If it crashes just force quit and it wont load Flash next time you load the site.

---

### Post by TheLions on 2009-01-26
> **evouga said:**
> In case anyone has similar problems and finds this thread: the problem was that Adobe's flash player is buggy. Disabling the plugin fixed all the issues I was having.

download flash again:

for 32bit Ubuntu:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)

and for 64bit:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)
and extract it to /home/username/.mozilla/plugins/ 
you'll probably need to enable hidden files which can be done by pressing Ctrl+H to see .mozilla

---

