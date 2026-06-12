---
title: "Problems with Broadcom wireless card"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by arnarg on 2008-08-13
I Have an Asus X50r and I recently installed Ubuntu 8.04 and everything worked "including" the wireless internet (after I installed the Broadcom B43 driver). But now it's so random if it will let me online, sometimes it will, sometimes it won't. The Wireless card I have is Broadcom BCM4311. I don't know how to explain it better, and I'm such a beginner on linux so thorough help would be good. If you need more info, just ask :P

*EDIT*
If it helps my router is ZyXEL 660HW

---

### Post by Ayuthia on 2008-08-13
I know that this happens occasionally with some people.  You can try using ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

or if you don't mind using a pre-release kernel, you can try this:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

You can also try changing the channel on your router.  Sometimes there is some interference in the air that is making the b43 driver not work so well with your router.

---

### Post by arnarg on 2008-08-13
Thanks, I changed the channel to 6 the other day so I wouldn't get mixed (?) with my neighbours internet. (sorry for not so good english :P)

---

### Post by Ayuthia on 2008-08-13
> **arnarg said:**
> Thanks, I changed the channel to 6 the other day so I wouldn't get mixed (?) with my neighbours internet. (sorry for not so good english :P)

Your english was fine!  That is how I would have said it.  Did that fix the problem?

---

### Post by arnarg on 2008-08-14
Well I made these changes before I even installed Ubuntu so...

---

