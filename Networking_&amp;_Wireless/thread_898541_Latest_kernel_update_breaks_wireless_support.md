---
title: "Latest kernel update breaks wireless support"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by joeinnes on 2008-08-23
I think that 2.6.24-21-generic breaks wireless support on ipw2200 on a Sony Vaio PCG-TR2MP (sorry, I'm not sure of the exact hardware). Wanted to check that the problem was occuring across the board before filing a bug report.

---

### Post by lgp171188 on 2008-08-23
It happened for me also ipw3945 on HP dv9704tx :(

---

### Post by ravenon on 2008-08-23
I can confirm on an intel pro wireless ipw2200. Fortunately I have the previous kernel. Actually, I don't think its the kernel update but the update I got this morning linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.30) to 2.6.24-21.31

EDIT: I just uninstalled linux-ubuntu-modules-2.6.24-21.31 and installed the same .30 (still located in /var). Wireless is now back.

---

### Post by AgenticState on 2008-08-23
Same problem here. Toshiba Tecra laptop with Intel 2200 Pro Wireless.

As with ravenon, downgrading to linux-ubuntu-modules-2.6.24-21-generic version 2.6.24-21.30 brings back the wireless for me.

---

### Post by tuwxyz on 2008-08-23
Same problem here.

ThinkPad T42
Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

I've installed the previous version - WiFi works.
@ravenon - Thx for hint.

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/260664](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/260664)

---

### Post by brienc on 2008-08-24
Same problem here (Acer TravelMate 290 ipw2200), reverting to the old version did the trick.

For my fellow noobs, I used aptitude to remove linux-ubuntu-modules and then used dpkg --install on the older (.30) version which was located in /var/cache

---

### Post by AlexenderReez on 2008-08-24
heh~~
i just feel like i'm using unstable version because of this problem...
-sigh-
is there any software or way to check my last installing activities so that i can solve this kind of problem for next time?

---

### Post by foe83 on 2008-08-25
> **brienc said:**
> Same problem here (Acer TravelMate 290 ipw2200), reverting to the old version did the trick.

For my fellow noobs, I used aptitude to remove linux-ubuntu-modules and then used dpkg --install on the older (.30) version which was located in /var/cache

Yup, that worked for me, even easier, i typed in command line:

```
sudo dpkg --force-downgrade -i /var/cache/apt/archives/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.30_i386.deb 

```

You may have the ending in "x64.deb" instead of "i386.deb" if your machine is 64bits, otherwise, that's all folks! :KS

---

### Post by coffeecat on 2008-08-25
> **AlexenderReez said:**
> heh~~
i just feel like i'm using unstable version because of this problem...
-sigh-

If you've installed the -21 kernel, you **are** running an unstable version. The only way you can get the -21 kernel is by enabling the proposed updates repository. [See what it says here]("https://help.ubuntu.com/community/UbuntuUpdates").

> **AlexenderReez said:**
> is there any software or way to check my last installing activities so that i can solve this kind of problem for next time?

Yes. Disable the proposed repository, unless you want to help with testing or you like breaking your system.

---

### Post by ravenon on 2008-08-25
The problem has be fixed in the latest updates. From proposed updates the kernel image was again updated to linux-image-2.6.24-21-generic (2.6.24-21.40) to 2.6.24-21.42 and linux-ubuntu-modules to
linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.30) to 2.6.24-21.32

---

