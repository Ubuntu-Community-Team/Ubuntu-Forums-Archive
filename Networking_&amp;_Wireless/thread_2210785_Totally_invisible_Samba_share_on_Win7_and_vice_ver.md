---
title: "Totally invisible Samba share on Win7 and vice versa"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by Steffen_G._Sveegaa on 2014-03-12
Hi there

I'm new to Linux, as I recently just decided to rebuild an old laptop to a NAS-server - why not learn it?
Anyway, I've come across a severe problem: My Ubuntu 12.04 laptop is completely invisible to my Win7 Ultimate machine using wireless connection on the Ubuntu machine. If the Ubuntu machine is wired, I do see the computer, but I get a really non-informative error (0x80070045 network path not found) when trying to access it.

I have followed every single instruction and manual on Win/Samba without any luck.
I can access the share without any trouble on a Vista machine and on my Android phone - when my Ubuntu machine is wired.

Any ideas? I've tried to describe my problem as accurately as possible, but do ask me if you need any extra info. I've spent too much time to troubleshoot this!

---

### Post by Vladlenin5000 on 2014-03-13
Hi, welcome.

The code error you mentioned has many results in a Google serach, among them: [http://www.sevenforums.com/network-sharing/226619-win7-sharing-problem-windows-services-issue.html](http://www.sevenforums.com/network-sharing/226619-win7-sharing-problem-windows-services-issue.html)

---

### Post by Steffen_G._Sveegaa on 2014-03-13
Hi, thanks

I followed your link, but that did not really help me out. I'm beginning to think there is a problem with my wireless on Ubuntu, because EyeFiServer (just installed it yesterday) runs smoothly via eth0. No such luck over wireless.

---

### Post by Steffen_G._Sveegaa on 2014-03-13
Ok, I might have narrowed some of the trouble down. Using wifi, I can't ping my router (destination host unreachable), but works perfectly when wired (but oddly, google.com pings fine on both). That may be the cause of the wireless problem itself.
I have a BCM4318 wifi card installed using firmware-b43-installer. Any ideas?

---

### Post by Vladlenin5000 on 2014-03-13
There are A LOT of threads here about BCN43xx. Definitely problematic.

---

### Post by Steffen_G._Sveegaa on 2014-03-23
Ok, now I've solved some more of it. Decided to install xubuntu instead and some other wifi drivers (they made ubuntu crash!) - and now I can nicely ping my xubuntu-machine form Win7. However, I'm still in trouble seeing the shares. Now I get an error 58: "the server cannot perform the requested operation".
I can see and access the shares via my smartphone without hassles.

I desperately need some help - this is just plain silly.

---

