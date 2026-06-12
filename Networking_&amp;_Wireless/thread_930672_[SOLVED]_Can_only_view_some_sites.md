---
title: "[SOLVED] Can only view some sites"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by blingo on 2008-09-26
Hello,
Using the Ubuntu 8.04.1-desktop-i386 Live,
I can only get Firefox to view some sites, for example Mozilla sites work (really work, not cache) , but Google doesn't.
When I enter the address of a site that I can't see,
It hangs on "waiting for site.com...".

I have an ECI modem/router connected to two computer,
mine is one of them.

I can ping my router,
I can ping every site, and get response, and also see it's ip number (so it's not DNS problem...)

I can not get inside the router vie Firefox,
but can vie telnet.

Having this problem for a long time,
what I've done before is to install old kernel (7.14 I think) than upgrade from there, but this is causing problems with my screen card, and I would like to use 3D on Ubuntu for a change.

Interesting to note, that I've tried several other Linux
Distributions, all had the same problem...
But having no problem with another operating system...

Thank you.

---

### Post by shanix on 2008-09-26
some restriction on the router side only allow IE? 

[http://johnbokma.com/mexit/2004/04/24/changinguseragent.html](http://johnbokma.com/mexit/2004/04/24/changinguseragent.html)
[http://www.mydigitallife.info/2007/07/13/changing-user-agent-for-firefox-web-browser/](http://www.mydigitallife.info/2007/07/13/changing-user-agent-for-firefox-web-browser/)

---

### Post by prshah on 2008-09-26
> **blingo said:**
> 
I can only get Firefox to view some sites, for example Mozilla sites work (really work, not cache) , but Google doesn't.
When I enter the address of a site that I can't see,
It hangs on "waiting for site.com...".

But having no problem with another operating system...


Take a look at this thread [[SOLVED] Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709") for a possible explanation and a fix. It's better you go through the entire thread. The fix is near the end.

---

### Post by lian1238 on 2008-09-26
You mean:
[http://ubuntuforums.org/showthread.php?t=718709](http://ubuntuforums.org/showthread.php?t=718709)

;)

---

### Post by superprash2003 on 2008-09-26
also try using opendns servers 208.67.222.222 and 208.67.220.220

---

### Post by prshah on 2008-09-26
> **lian1238 said:**
> You mean:
[http://ubuntuforums.org/showthread.php?t=718709](http://ubuntuforums.org/showthread.php?t=718709)
;)

Yes, indeedy. Corrected now. Thanks.

---

### Post by blingo on 2008-09-28
All Right guys!!!

It worked,
I did everything that was written on
[http://ubuntuforums.org/showthread.php?t=718709](http://ubuntuforums.org/showthread.php?t=718709)
from page 1 to the end, 
except that I've noticed that my router MTU can still be on 1500,
(turned it to 1492 on Ubuntu)
Also I'm using Roaming mode, so to the file
/etc/network/interfaces
only added 
pre-up /sbin/ifconfig $IFACE mtu 1492

  Interesting phenomenons before fixing
-----------------------------------------
* After using 8.04 live, the installed 7 something Ubuntu network
died.
* Ubuntu 6.061 live, surfing worked for some seconds and than died. (?!?)
* after that Internet didn't worked on the commercial operating system and
had to reboot the router.

---

### Post by blingo on 2008-09-28
To be more specific,
I've used [http://ubuntuforums.org/archive/index.php/t-619531.html](http://ubuntuforums.org/archive/index.php/t-619531.html)

---

