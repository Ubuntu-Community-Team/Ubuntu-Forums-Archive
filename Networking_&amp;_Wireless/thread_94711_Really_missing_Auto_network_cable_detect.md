---
title: "Really missing: Auto network cable detect"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by fourhead on 2005-11-24
One thing I loved in Windows/MacOS and which I'm REALLY missing in Linux is the automatic detction of a network cable. During bootup, Kubuntu synchronizes the clock via the Internet, but on my laptop, when I turn it on and I don't have a network available, the boot hangs at "Synchronizing clock..." for a few minutes, and this is so annoying. Isn't it possible to detect if the network is actually available before trying to sync the clock?

Another issue: Is there an easy way in KDE to switch between network profiles? At home, I use static IPs, but when I'm at university, I'd like to switch the laptop to DHCP mode easily.


Tom

---

### Post by john280z on 2005-11-25
You may want to check out "ifplugd", available thorugh Synaptic.

johnm

---

### Post by Manuel Siggen on 2005-11-25
[QUOTE=fourhead]One thing I loved in Windows/MacOS and which I'm REALLY missing in Linux is the automatic detction of a network cable. During bootup, Kubuntu synchronizes the clock via the Internet, but on my laptop, when I turn it on and I don't have a network available, the boot hangs at "Synchronizing clock..." for a few minutes, and this is so annoying. Isn't it possible to detect if the network is actually available before trying to sync the clock?[/QUOTE]

I had the same problem until I found Network Manager (sudo apt-get -i network-manager). Network manager automagically detects and uses the best connection available (network cable or wifi, basically) much like Windows does.

Hope it'll help...

Manuel

---

