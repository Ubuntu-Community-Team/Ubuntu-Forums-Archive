---
title: "Can Only Connect To Internet For A Few Seconds"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by DrSunnysock on 2008-04-27
Then the internet stops working.

Then, I can reconnect, but it still works only for a few seconds.

I am running the latest version of Ubuntu installed by Wubi.

I am using a Wireless USB Adapter to connect to the internet.

Uhhh......Please help. Thank you.

:popcorn::popcorn::popcorn::popcorn:

---

### Post by DrSunnysock on 2008-04-29
Bring up my poooooooooooooost. :mad:

---

### Post by DrSunnysock on 2008-04-29
Anyone?

---

### Post by DrSunnysock on 2008-04-30
:(

---

### Post by superprash2003 on 2008-04-30
does it reconnect by itself?

---

### Post by Ayuthia on 2008-04-30
Please include the results of lsusb and the name of your wireless device.  It will help us be able to determine what you might need to do.  Also, when you lose your connection, does dmesg say anything?

---

### Post by DrSunnysock on 2008-04-30
> **Ayuthia said:**
> Please include the results of lsusb and the name of your wireless device.  It will help us be able to determine what you might need to do.  Also, when you lose your connection, does dmesg say anything?

My internet worked fine when I was using an older version of Ubuntu not too long ago....

lsusb? Excuse me? >_> Sorry!!!

No dmesg says nothing....

I'm using a netgear USB adaptor WG111v2 to connect to a netgear router.

---

### Post by Ayuthia on 2008-04-30
Sorry, lsusb is a command that you use in the Terminal.  It is like lspci -nn where it will list your devices (in this case your usb devices) and their id numbers.

By any chance, are there any other connections nearby that are are sharing the same channel.  You can see this by typing:
```
iwlist scan
``` in the terminal.  If there are, you might try changing the channel on your router.

---

### Post by DrSunnysock on 2008-04-30
I do believe that did that trick....


<3

---

