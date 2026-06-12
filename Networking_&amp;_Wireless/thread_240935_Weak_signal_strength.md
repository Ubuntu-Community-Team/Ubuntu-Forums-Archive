---
title: "Weak signal strength"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by shannon.cummins on 2006-08-21
I have successfully installed the lated ndiswrappwer and network-manager, and my atheros based chip is using the net5211 driver.  I can connect to my network using WPA and it did it rather quickly.  My issue is that the signal strength is very weak.  The access point is about 20 inches away so I know that distance is not the reason.  When I ran windows in a dual boot mode I get 100% signal strenght.  In Ubuntu I am lucky to hit 75%.  When I leave the room the connectivity drops.  What gives??

---

### Post by jml on 2007-01-08
I have the same problem.  My laptop uses an Atheros based card (Cisco Aironet 802.11 a/b/g), and Network-manager-gnome.  Establishing connection takes a bit of time, but download speeds seem OK.  With my computer in the same room as the access point I get signal strength reading of 14-18%.  When the strength dips below 10% the connection often drops.  With Windows the signal strengh pegs at the top of the scale.  With an old version of Kanotix (the only other distro I can get WPA working,) using Kwifi manager I get a signal strength of between 50-75% with the laptop in the same room, using the same wireless card I use with Ubuntu.  Is this really a performance issue, or is the calibration for the signal strength meter off?  Any help would be appreciated.  Thanks.

Joe

---

### Post by cywhale on 2007-01-14
Same problem here using a atheros-based pcmcia-card, network-manager-gnome.

**Dapper**: signal strength ~**45-55%**, full available speed reached (DSL 16000)
**Edgy**: signal strength ~** 21-23%**, download speed ~ DSL6000 :(

Laptop using Dapper/Edgy has not been moved anyhow during the test, 2 walls, ~5m to access point.

Using a SMC2835W card (edgy) signal strength is ~50-60%, but no WPA, thats why I switched to atheros.

Has anybody found a solution ?

---

### Post by cywhale on 2007-01-15
Tried latest madwifi-version, did not help (~24%).

Solved this issue for me 

 - without using the restricted-modules (apt-get remove) and 
 - using ndiswrapper-1.34 (compiled) and the TP_Link .inf-Driver from CD. 

Now I'm getting ~45% signal strength and full speed again. Any idea if just blacklisting ath_ modules could work, too? Maybe there is no need to remove the full restricted-drivers-package?

---

### Post by jml on 2007-01-24
Its possible the Linux drivers just don't emulate the Windows counterpart well enough.  I've always had problems getting NDISWRAPPER to work for me, dispite the great help I have gotten here.  Luckily, I did make a hardware discovery.  My Belkin wireless base station put out a weaker signal than the Linksys product.  I switched to a Linksys and added a set of high gain antennas and now Ubuntu gives me a signal strength of 45-50%.  Not an elegant solution, but at least I can now use Ubuntu exclusively for my wireless needs.

Joe

---

### Post by kaede on 2007-02-21
> **cywhale said:**
> Same problem here using a atheros-based pcmcia-card, network-manager-gnome.

**Dapper**: signal strength ~**45-55%**, full available speed reached (DSL 16000)
**Edgy**: signal strength ~** 21-23%**, download speed ~ DSL6000 :(

Laptop using Dapper/Edgy has not been moved anyhow during the test, 2 walls, ~5m to access point.

Using a SMC2835W card (edgy) signal strength is ~50-60%, but no WPA, thats why I switched to atheros.

Has anybody found a solution ?
hi cywhale, how you manage your smc 2835w to works on ubuntu? what version are you using?

thanks

---

