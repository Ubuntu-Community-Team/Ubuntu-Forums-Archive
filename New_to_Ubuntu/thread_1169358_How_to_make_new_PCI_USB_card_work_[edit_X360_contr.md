---
title: "How to make new PCI USB card work? [edit: X360 controller and BT dongle, not USB]"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by juzza on 2009-05-25
Hi everyone,

Just back to Ubuntu, hopefully this time I'll give up Windows for good. In the mail today I got a PCI USB 2 card (cheapo, NEC based apparently) I ordered off eBay. I plugged it in but to my disappointment devices I plug in won't show up (bluetooth dongle and XBOX 360 controller). I don't think Linux sees the card, or is using it. Is there a way to make the card work? I would have assumed it would detect and work at start up? I'm running Ubuntu x86 9.04 final.

Any ideas, tips and advice are greatly appreciated


This is the output of a command I tried:
```

justin@melchior:~$ lspci | grep USB
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
06:01.0 USB Controller: NEC Corporation USB (rev 43)
06:01.1 USB Controller: NEC Corporation USB (rev 43)
06:01.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
justin@melchior:~$ 

```


EDIT:
I plugged the mouse in and it works, I guess the USB card is working but the BT dongle and X360 controller aren't, any ideas on how to get them to work? Thanks

---

### Post by juzza on 2009-05-25
Whoa I just plugged my mouse in and it works... I guess the problem is getting the bluetooth dongle and XBOX 360 controller to work... original post edited

---

### Post by juzza on 2009-05-25
OK although not getting any notification to the fact, I fired up ZSNES and the X360 controller is working now... odd!

Now to figure out the bluetooth dongle... getting there ^_^

---

### Post by juzza on 2009-05-25
Nevermind, put the dongle in two other PC's - it's dead :D

Thanks anyway...

---

