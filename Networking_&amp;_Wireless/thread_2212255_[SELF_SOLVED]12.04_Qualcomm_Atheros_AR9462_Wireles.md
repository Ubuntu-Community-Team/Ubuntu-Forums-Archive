---
title: "[SELF SOLVED]12.04 Qualcomm Atheros AR9462 Wireless connection issue"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by elpiel93 on 2014-03-20
**EDIT: My Wireless now works properly for no reason? If someone wants to help me to find what make it work, for the next Ubuntu install or next person with the same problem, write here =)**

Hello,

Whole day I'm trying to run my Wifi, looking at the forum, trying at freshly installed Ubuntu 12.04.4 kernel release: 3.11.0-18-generic. Acer Aspire v3-772G

The problem is: It can't connect to wifi, if it does, connection is 1 mbps.

I've tried:
```
sudo gedit /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
```

Tried:
```
sudo gedit /etc/modules
acer_wmi
```

Also after removing it:
```
sudo gedit /etc/modprobe.d/blacklist.conf
blacklist acer_wmi

```

Also:

rfkill list all:

```
Soft blocked: no
Hard blocked: no
```

I tried aslo other stuff like Compiling blackports-3.11-rc3-1.tar.bz2 without any changes from this post - [http://ubuntuforums.org/showthread.php?t=2173686&p=12785322#post12785322](http://ubuntuforums.org/showthread.php?t=2173686&p=12785322#post12785322)
I also opened the file /net/wireless/ath/ath9k/pci.c (looking at other post from the same user [[COLOR=#000000]chili555[/COLOR]]("http://ubuntuforums.org/member.php?u=35909"))
found that my AR9462 isn't listed in the:

Static DEFINE_PCI_DEVICE TABLE

If someone have Idea it's welcome to answer :) I've tried a lot of posts, so I might have done some of the ideas

Regards,
Lachezar Lechev

---

### Post by Steven Bell on 2014-03-21
I had this issue only in Trusty beta1

I also had the mystery solve, and was wondering what solved it, I had thought it was something to do with Network Manager settings and kwallet?

But now it's slower than before, now 48Mb/s and not 54-300Mb/s

---

### Post by varunendra on 2014-03-21
> **elpiel93 said:**
> Tried:
```
sudo gedit /etc/modules
acer_wmi
```

Also after removing it:
```
sudo gedit /etc/modprobe.d/blacklist.conf
blacklist acer_wmi

```

Those two attempts do exactly the opposite things - The /etc/modules file 'Forces' a driver to load, while the blacklist file tries to prevent it from loading. If you have kept both the settings, be aware that both are conflicting settings and the "/etc/modules" will win (which means the same thing happening if you remove the entries from both files).

Regarding your Edit in the first post, **IF** the problem returns, you may try a newer driver as suggested in this post : [http://ubuntuforums.org/showthread.php?t=2211168&p=12963298#post12963298](http://ubuntuforums.org/showthread.php?t=2211168&p=12963298#post12963298)

**@Steven Bell,**
Same suggestion for you too, if the problem persists or returns.

---

