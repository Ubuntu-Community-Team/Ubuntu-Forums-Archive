---
title: "Cant connect my Ubuntu!!!!"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by ggonmar on 2006-08-28
hey there!
since I couldnt setup my Ubuntu for Wifi, I decided to connect it by simple Ethernet to my router.
Now it is online, and the pings anywhere DO work.
However, if I run mozilla and type [www.google.com](www.google.com), or ubuntuforums.org, it doesnt shows up the website!!!  dont really know what to do...

any help????

---

### Post by Cubiq on 2006-08-28
Have a look at /etc/resolv.conf. Are your [FONT="Lucida Console"]namesarver[/FONT]s set correctly? (probably you just need to add "nameserver ip.of.your.router", w/o quotes)

---

### Post by ggonmar on 2006-08-28
yeah, the nameserver part is fine...

its kinda weird, though, coz it pings everywhere, and some websites do work ([www.blogger.com](www.blogger.com) does work, for example...) but not google, nor hotmail, nor... almost none!!

any other ideas?

thanks!!!

---

### Post by Cubiq on 2006-08-29
mmh weird. Probably you can see some sites just because of some DNS caching... are your DNS servers set correctly on your router? What does happen if you set them to 208.67.222.222 and 208.67.220.220? ([www.opendns.com](www.opendns.com))

---

### Post by ggonmar on 2006-08-29
hey, thanks for the help...

now it works... it was a problem with the DNS indeed, but not on the router, but on Ubuntu...
I thought I had to set the DNS as 192.168.0.1 (my router IP), but instead I had to set the real DNS that gets the router also (dont understand why?) 

anyway, its workin now :)

thanks!

---

