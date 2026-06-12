---
title: "Intel Pro 2200BG - Firmware Error Message"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by MrWES on 2009-08-26
On or around August 22, I started having issues with my Intel Pro 2200BG card dropping connections and reconnecting. I checked dmesg and I'm getting the following error message many many times per minute:
```
Aug 22 18:54:14 bill-laptop kernel: [   21.519058] ipw2200: Firmware error detected.  Restarting.

```

Up to this point it has been a flawless card. I believe it started when the last kernel update came out, but I'm not absolutely sure:
```
Linux bill-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

```

I changed the card out for a BCM4309 and the card worked without dropped connections, but that card is notoriously slow, so I ordered another Intel 2200BG and installed it today. So far my connection is not dropping out, but I'm still getting the error in my system log. Any thoughts or area I should be investigating to solve this? 

Bill

---

### Post by lswb on 2009-08-26
Do you still have the previous kernel 2.6.28-14 on your system? It should be on your grub boot menu? Try it and see if it works OK, then at least you'll know it is a problem with the last update.

---

### Post by MrWES on 2009-08-27
> **lswb said:**
> Do you still have the previous kernel 2.6.28-14 on your system? It should be on your grub boot menu? Try it and see if it works OK, then at least you'll know it is a problem with the last update.

I booted into the previous kernel, 2.6.28-14-generic and I'm still seeing the error message in the system log, but I'm not getting the dropped connections as before. I wonder if there was a change to the ipw2200 firmware in the restricted-modules. 

I originally wondered if I had an issue with my router, but after seeing this continuous error message and the fact that my widnows laptop is not having any issues with dropped connections -- I figured something has changed, but I can't put my finger on it.

Also, since I put the new card in, the keyring manager is prompting me for the default password when the network manager is accessed....sigh.

Bill

Looks like this is the same bug, but I'm baffled on why it's happening now. I've used that card for over two years without issues.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352150]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352150")

---

### Post by MrWES on 2009-08-28
I ended up installing Wicd and seems to have solved my issues....shrug.

Bill

---

