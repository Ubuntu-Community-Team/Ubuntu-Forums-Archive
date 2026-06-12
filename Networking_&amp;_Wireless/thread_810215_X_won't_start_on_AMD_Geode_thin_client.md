---
title: "X won't start on AMD Geode thin client"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by joehill on 2008-05-28
I'm trying to get a thin client with an AMD Geode (LX 800) chipset to boot over the network (PXE boot). (This unit is essentially the same as a Koolu thin client, except I bought it directly from the vendor in Taiwan.)  It starts to boot and gives me all the progress bars, but when it comes time to start LDM, I get a black screen with a blinking cursor on the upper-left corner.  I've tried changing the xserver in ldm.conf (auto, geode, amd, vesa), which doesn't change anything.

Any ideas on how to get this working?  I know Koolu has been using similar thin clients for a long time with Feisty and Gutsy, so it should work.

Joe

---

### Post by npinhao on 2008-06-05
I'm having the same problem, this time with a Kubuntu server and a Thincan thin client (using a Geode LX700).
I see the progress bar starting and then it is at ~1/6, the screen goes black and nothing else happens :(

---

### Post by Jarlathg on 2008-09-02
I'm having the same issue with thincan's, blank screen with blinking cursor, anyone out there have any idea's, I've just bought 3 of them. They should be plug and play. :confused:

---

### Post by Jarlathg on 2008-09-22
HOWTO make Geode thin clients work on Ubuntu/Hardy LTSP

Funkyware has an answer, sorted the thincan DBE61.
Nice one.

[http://q-funk.blogspot.com/2008/06/howto-make-geode-thin-clients-work-on.html](http://q-funk.blogspot.com/2008/06/howto-make-geode-thin-clients-work-on.html)

---

### Post by mtl3414 on 2008-10-20
I've been able to start the thin client with the vesa driver but only in 640x480 with LTSP 5 and with a usb key I've been able to start it with the old Xvesa at 1280x1024x24.

Anyone knows how to use Xvesa in LTSP 5?

Thanks

---

