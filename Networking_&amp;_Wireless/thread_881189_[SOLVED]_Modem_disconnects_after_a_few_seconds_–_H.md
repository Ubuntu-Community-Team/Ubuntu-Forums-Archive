---
title: "[SOLVED] Modem disconnects after a few seconds – How to fix?"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by mal_conductor on 2008-08-05
Hello,

I installed my HSF modem.
I am running Ubuntu Kernel 2.6.24-19 generic with the linuxant driver hsfmodem-7.68.00.12full_k2.6.24_19_generic_ubuntu_i386.deb.  Free version so only running at 14.4 kbs.

I am using the Gnome PPP to connect.  The modem dials out and connects, but the connection drops after a few seconds.

The phone line and modem work well on Windows XP (dual boot, so same phone same computer).

I have tried unchecking the “check carrier line” option and Ignore terminal strings.

Please suggest possible ways to trouble shoot.

Regards,

---

### Post by ModelM on 2008-08-05
I think you might get some help from this thread...

[http://ubuntuforums.org/showthread.php?t=877706](http://ubuntuforums.org/showthread.php?t=877706)

At least until you get your modem working I'd suggest using wvdial instead of GnomePPP. wvdial allows you to see every command sent to your modem & every response from the modem. This information is invaluable in setting up/diagnosing dialup modems.

GnomePPP and other such dialers hide this information from you microsoft-style in an attempt to make things "easier". Having information hidden makes nothing easier & it is impossible to know if a modem is misbehaving if you don't know exactly what instructions the modem has been given.

The information in the above thread should be enough to get you started with wvdial. Give it a try & let's see how it works.

---

