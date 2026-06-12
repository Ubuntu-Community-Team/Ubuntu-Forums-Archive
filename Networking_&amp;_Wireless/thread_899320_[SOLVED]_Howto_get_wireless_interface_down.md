---
title: "[SOLVED] Howto get wireless interface down?"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by psie on 2008-08-24
Hey guys,
the question sounds so easy and tough is very challanging!

I used... ```
sudo ifconfig wlan0 down
```
... to get my wireless interface down, this works for a short term, but after a few minutes the interface is up again!
I already uninstalled network-manager so this doesn't influence the situation...
May be I can modify my /etc/network/interfaces to make it work the way I want it to, this it how it lookes like [http://pastebin.ubuntu.com/40158/](http://pastebin.ubuntu.com/40158/)

Thanks for help

---

### Post by SpaceMaster on 2008-08-24
```
sudo ifdown ath0 (or wlan0, or wifi0, depending on the wireless card)
```

That's what I always use, but I guess it's about the same.
Also, deactivating it in the GUI works, too.

right click the network icon -> deselect "Enable Wireless"

---

### Post by Hazer on 2008-08-24
Hi, you need to reinstall network manager und uninstall any other connection manager replacements, then right click on network manager icon and untick "enable wireless"

---

### Post by psie on 2008-08-24
Thanks guys! Spacemaster your solution worked great for me!
If I use... ```
ifconfig <interface> down
```
... then the interface comes up after a while by itself, but if I use...```
ifdown <interface>
```
... it sytays down as long as I type...```
ifup <interface>
```

---

