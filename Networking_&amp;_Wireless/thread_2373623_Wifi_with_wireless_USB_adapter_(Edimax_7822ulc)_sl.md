---
title: "Wifi with wireless USB adapter (Edimax 7822ulc) slow or not working at all"
date: 2017-10-08
forum: Networking &amp; Wireless
---

### Post by mdm2814 on 2017-10-08
I've installed the Edimax 7822ulc on my desktop machine following the instructions given here:
[https://edimax.freshdesk.com/support/solutions/articles/14000065859-how-to-install-ew-7822ulc-adapter-in-linux-running-kernel-higher-than-v4-4](https://edimax.freshdesk.com/support/solutions/articles/14000065859-how-to-install-ew-7822ulc-adapter-in-linux-running-kernel-higher-than-v4-4)

The installation seems to have worked as my wifi adapter sees the network which my cell phone and tablets have no problem connecting to

Unfortunately my desktop seems to be in an endless loop trying to connect to the wireless network. if it does manage to connect, the speeds are unacceptably slow, like 1mbps

---

### Post by berghy on 2017-10-23
Hello mdm,

Have you tried with the manufacturer's drivers: [http://www.edimax.com/edimax/mw/cufiles/files/download/Driver_Utility/EW-7822ULC_Linux_Driver_1.0.0.9.zip](http://www.edimax.com/edimax/mw/cufiles/files/download/Driver_Utility/EW-7822ULC_Linux_Driver_1.0.0.9.zip)

I have curerntly installed it on my RPI3.

I'm interested in the output of the "# iw list" command of such a device. If you have the dongle working, could you please show me the output ?

ty,

F.

---

### Post by praseodym on 2017-10-23
Its a rtl8822bu chipset, installation instruction here:

[https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

---

