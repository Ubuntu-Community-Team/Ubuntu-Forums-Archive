---
title: "D-Link DWA-542 + ndiswrapper freeze system when modprobe"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by Xares on 2007-02-20
cpu: AMD athlon 64
linux version: 2.6.17-10-generic (ubuntu edgy)
card: D-Link DWA 542
driver: net5416 (windows driver from accompanying CD)
ndiswrapper version: 1.37

After a fresh install of ubuntu, finally I managed to get ndiswrapper working.
The problem is, if the system attempts to load it while booting (sudo ndiswrapper -m),it leads to a soft lock on CPU.
Manually loading it (sudo modprobe ndiswrapper) freezes the computer,where a hard reboot is needed. Even the mouse stop moving!
However, everything seems to work smoothly if I do this:
```

sudo depmod -a
sudo modprobe ndiswrapper

```

As a linux newbie, I'm really curious what's the difference with and without depmod.
Man depmod, unfortunately, is too difficult for me to comprehand... :-| 
Any explanation is appreciated :-)

---

### Post by Avantasia on 2007-08-29
Harro!! 

I also have the [COLOR="Blue"]DWA-542[/COLOR], I got [COLOR="Red"]Ndiswrapper[/COLOR] working after 3 days of mad troubleshooting.
But it was still unstable and I had to connect manually after every boot...moreover Ndiswrapper CRASHES alot!!!

To make my story short, I got my internet working but I managed destroying my graphics while trouble shooting my video drivers...oops.
sooo... I re-installed Ubuntu 7.04 (Feisty), and decided to go with [COLOR="SeaGreen"]madwifi[/COLOR].. however that took a bit of playing around but was still 5X easier than [COLOR="Red"]Ndiswrapper[/COLOR].

[COLOR="DarkOrange"]ramdom tip[/COLOR] : I kept unpluging my networkcard after shutdown and kept trying to connect through the manual configuration. Also make sure that your ESSID is set to your network name.
[COLOR="Blue"]
NEED HELP!!!! STILL having a minor problem[/COLOR]
I am dual booting Linux&Windows and I notice a problem.
I can stay on one OS and wireless automatically connects fine; however if i switch from one to another  I need to unplug my network card manually.
If I don't, I am unable to connect to my network. This is a temporary fix that I found.

This is a direct DL of madwifi  ***[COLOR="Blue"] read the install and readme[/COLOR]***

[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233)

---

### Post by CleverCognomen on 2007-10-07
cpu: Intel Pentium 4
linux version: 2.6.20-15-generic (ubuntu feisty 7.04)
card: D-Link DWA 542
driver: net5416 1.02 (downloaded from d-link site)
ndiswrapper version: 1.48


I'm having very similar problems here. I have a system dual-booted with Ubuntu 7.04 and Windows XP. I compiled and installed ndiswrapper 1.48 (after having some difficulty with missing headers). The drivers install fine. 

However, I get a CPU software lock while booting the system. If I try to load it manually, the wireless connection doesn't even show up in System --> Network.

I'm a new Linux user, and I've now spent the better part of 3 days trying to get Ubuntu running. It's been nothing but constant frustration. To me, the two biggest problems are the ultra-steep learning curve due to the necessary use of the terminal and the almost complete lack of hardware support.

---

