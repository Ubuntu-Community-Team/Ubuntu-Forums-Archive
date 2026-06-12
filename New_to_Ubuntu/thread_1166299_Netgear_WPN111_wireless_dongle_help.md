---
title: "Netgear WPN111 wireless dongle help"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by loketar on 2009-05-21
as name suggets I am looking for help to getting my Netgear WPN111 wireless dongle to work on my system, I don't have the install CD just an .exe setup file i downloaded which I am told won't work with linux.
 
Do any of you know how to get this card to work? any help at all is gratefully appreciated.
 
thank you in advance.

---

### Post by lindsay7 on 2009-05-21
I gave up on trying to get mine to work. I bought a Edimax EW-7318USG from Newegg for around $25. It works out of the box and it has an external antenna that gives it good range.  Sorry to break the news to you. Maybe things have changed and there is a new wrapper or way to get your adapter to work.

---

### Post by loketar on 2009-05-21
thanks for the reply, sadly can't afford anything else for about month-month and a half (grr recession and OTT prices for download UK festival : /)
I think I MAY have some ethernet cables knocking around at my mates flat possibly try and pinch that until i can get another dongle.

---

### Post by loketar on 2009-05-21
just a stab in the dark here, but if i install my netgear drivers onto an XP system would there be files created i could use to transfer to my linux system to get it working?

---

### Post by lindsay7 on 2009-05-21
Ok< I look at your post again and I have mislead you. I could never get my [COLOR="Red"]Netgear WG111[/COLOR] which is a usb wireless adaptor to work.  You have something else.
There is a listing of wireless adapter and the chip sets that work in the forum on networking and wireless.  Sorry about the confusion.

---

### Post by Temposs on 2009-05-21
Windows drivers don't work on Linux. 

In some cases people make wrappers for windows drivers in order to make a go-between and thus have them work on linux. It seems people have had luck in the past getting this wireless card to work with ndiswrapper.

In Add/Remove, search for ndiswrapper, and install the "Windows Wireless Drivers" program that comes up. It will hopefully allow you to use the Windows drivers for your wireless card. I have never needed to use this program, so I personally don't know how to use it exactly. I know lots of people have found it useful, though.

---

### Post by lindsay7 on 2009-05-21
This might help.

[http://ubuntuforums.org/showthread.php?t=414023&page=3](http://ubuntuforums.org/showthread.php?t=414023&page=3)

---

