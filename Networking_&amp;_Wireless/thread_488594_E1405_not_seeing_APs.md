---
title: "E1405 not seeing APs"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by MisterMehoff on 2007-06-30
Hi, 

I own the Dell E1405 and installed Ubuntu Ultimate 1.3 last night on a new 80GB hd and the Intel Pro 3945 recognized the wifi access points initially.  Now, access points don't appear in the list in the networking icon on the top menu bar and the wifi led indicator is continuously doing the rapid blinking.  I read up on the Intel website about the 3945 about the drivers and not sure if that applies to me.  

Can someone help me out please?

---

### Post by MrFSL on 2007-06-30
I have ran across countless wireless issues with Linux over the years. There is so much information that you can get from the CLI and so many useful tools out there... HOWEVER, 90% of all my wireless headaches have been instantly solved by installing and using wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Of course you will have to remove network manager if you have it installed. Plus, wicd is not 100% bug-free (what is bug free in Linux?).

If you are interested and think this might help I would download the deb file.
Open a terminal and then:

$ sudo killall nm-applet
$ sudo apt-get --purge -y remove network-manager
$ sudo dpkg -i wicd*.deb

Hope this solves your issues. If not we can dig deeper.

Cheers!
MrFSL

---

