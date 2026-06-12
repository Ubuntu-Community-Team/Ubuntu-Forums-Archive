---
title: "Explanation of Startup Services"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by TheEvilOne6620 on 2009-08-04
I was wondering if anyone can explain to me the following startup services and whether or not their safe to disable.  I have Googled them but cannot find any good information on them.

AT SPI Registry Wrapper
Gnome Settings Daemon and Gnome Settings Daemon Helper
Seahorse Daemon

---

### Post by jerrrys on 2009-08-05
found the first one. is it safe to disable? you be the judge...

[http://ubuntuforums.org/archive/index.php/t-971848.html](http://ubuntuforums.org/archive/index.php/t-971848.html)

[http://www.google.com/search?q=at+spi+registry+wrapper+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=at+spi+registry+wrapper+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

seahorse?  how bout the browser seamonkey....

---

### Post by wojox on 2009-08-05
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by Shig on 2009-08-05
Hi

AT SPI helper daemon is used as part of the assistive technologies tools in Ubuntu to collect usage feedback for the Ubuntu developers. It seems to only do anything if you are using assistive technologies (text-to-speech, screen magnifiers, etc) designed to help people with various impairments to use Ubuntu. It's harmless and will most likely not use many system resources to run, you can try disabling it if it bothers you, but be aware that it is tied into gnome-session, which handles your logon to Ubuntu.

Gnome settings daemons are important, these act almost like the registry in Windows and store gnome related settings in xml databases. Best to leave these running.

Seahorse is an encryption suite tied into Nautilus and other Gnome tools to let you encrypt and decrypt various things, good explanation is [here]("http://live.gnome.org/Seahorse")

Hope this answers your questions!

---

