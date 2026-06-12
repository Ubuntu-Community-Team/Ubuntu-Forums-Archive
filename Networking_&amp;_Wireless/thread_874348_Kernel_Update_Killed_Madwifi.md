---
title: "Kernel Update Killed Madwifi"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by PoopLoops on 2008-07-29
I made a batch update last night that ended up updating my kernel from 2.6.24-16-generic to 2.6.24-19-generic.  At the time, my wireless worked fine.  It is an Atheros card that I got working with madwifi.  Today I came home from work and booted up my laptop to find that wifi is gone.  Not only that, but no mention of wireless at all in my network settings.  I went back and booted the older kernel.  Now I had a list of wireless networks as usual but couldn't connect to any of them (my own WPA2 protected and a neighbor's open one, both of which worked before).

After searching a bit I found that this is a common problem, but for people using ndswrapper (or whatever).  I still got the pre-released fix for it, but no go.  So I figured I'd reinstall madwifi.  Still nothing.

I removed all the old files via make install (it prompts you), then reinstalled.  Then I type "sudo modprobe ath_pci" to get the drivers working.

What should happen is that when I type iwconfig I get 3 outputs, but I only get 2 (i.e. as if I had never done anything) and nothing wireless works.

I have no idea where to proceed from here.

---

### Post by chili555 on 2008-07-30
> I removed all the old files via make installI'm not quite sure you took all the needed steps. Please do:```
cd madwifi-folder
make clean
make
sudo make install
sudo modprobe ath_pci
```Does your card come to life?

Substitute your *madwifi* install directory as needed.

---

