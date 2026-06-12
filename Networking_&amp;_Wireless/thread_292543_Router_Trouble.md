---
title: "Router Trouble"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by StormGuy on 2006-11-04
I'm trying to get my router to allow both my laptop and my PC to connect to the internet.  I'm running Ubuntu on both, and for some reason, if I USB connect my Linksys router to my desktop, the ethernet cable from my router to my laptop won't work.  If I connect an ethernet cable to both and remove the USB plug from the modem, then the laptop connects but not the desktop.  It's as though the desktop won't route through the router.  I'm not even sure where to begin troubleshooting :(

Hase anyone else had a similar problem or have any insight into a possible cause for the problem?

---

### Post by amohanty on 2006-11-04
> if I USB connect my Linksys router to my desktop, 

I am a bit lost as to what you mean by that?

AM

---

### Post by StormGuy on 2006-11-04
Sorry, I meant from my modem to my desktop.  There are two options with the Linksys modem: either ethernet or USB.

---

### Post by amohanty on 2006-11-04
Ok lets say that your router is connected to your DSL/Cable model with an ethernet cable and you both your laptop and desktop are connected to the router via ethernet cables:

cable/del modem --ethernet-- router --ethernet-- desktop
                               |------ethernet-- laptop

Edit: crap the asci stuff didnt come out right.

Now power down everything. Start in the follwing order waiting 30s every step:
1. cable/dsl modem
2. router
3. desk/lap top

then hit your route rweb page - usually 192.168.0.1 (assuming your subnet is 192.168.0) If you are lost on that - do an **ifconfig** on the machine that appears to be connected and then use the first three parts of its ip address and then add 1 at the end.

Now on the router site, lookfor alist of dhcp clients (assuming you use dhcp)

Do you see both the boxes there?
Can you ping the router?

AM

---

### Post by StormGuy on 2006-11-04
Thanks, those three steps did it :)

I have two internets!

---

