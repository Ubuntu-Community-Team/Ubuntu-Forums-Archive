---
title: "Update broke wireless"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by dalziel_86 on 2007-04-12
I have my desktop running Edgy, and bridging an Atheros wireless card to my wired LAN, so I can connect via wireless from my MacBook. The wireless card is set up to run as an access point, with WPA and everything. This has all worked fine for almost two weeks since I got it set up (took me a lot of fiddling).

However, this afternoon, I installed a couple of updates that the update notifier told me I needed, then rebooted when it told me to do that.

And now my wireless card is gone. It still shows up with lspci, but neither ifconfig nor iwconfig show it at all. When I try to do 'sudo modprobe ath_pci' I get:

```
FATAL: Error inserting ath_pci (/lib/modules/2.6.17-11-386/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I found someone with a similar problem that was fixed by installing updated linux-restricted-modules, so I tried that, to no effect.

I don't understand why a prescribed update should break this sort of thing. And I really want to get this fixed. Any suggestions?

---

### Post by Gavigan280 on 2007-04-14
I know someone having a similar problem on Feisty.  Her wireless worked fine until she downloaded a few updates the other day and then it just died.  

The lshw shows ```
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 4
       bus info: pci@08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
       resources: iomemory:d0200000-d020ffff irq:11

```

And sudo modprobe ath_pci yields ```
FATAL: Module ath_pci not found.
```

Been looking around the forums for a solution and have yet to find one.

---

### Post by dalziel_86 on 2007-04-15
I managed to fix my problem by recompiling and reinstalling the madwifi drivers. Should have posted my solution, but I forgot about it.

However your problem looks a bit different to mine. Still, it couldn't hurt to try re-installing the drivers.

---

### Post by cookfromfrozen on 2007-04-15
I had the same problem after installing recent kernel updates for 2.6.17-11 (symbol errors.  The restricted-modules are already up-to-date.  I  did not try a reinstall of  restricted-modules because I'm not using 2.6.17-11 but  2.6.19.2 with the latest MadWifi.

It does seem like this update broke atheros for some people though.

---

### Post by jimbob on 2007-04-17
Same thing happened to me yesterday.  Fixed it by booting the old kernel 2.6.17-10-generic in place of the newly updated one 2.6.17-11-generic.  lsmod shows all of atheros modules are missing.

 IMHO this needs a bug report if there isn't one already.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by theDaveTheRave on 2007-04-17
Same thing happened to me last week with a dapper auto update, luckily I keep a laptop to hand that hasn't been updated so i could still access the net to check the forums and attempt to resolve....

I also lost all the routing table information! however evertything suggested that the driver was installed and the device found and should have been functioning, The really strange thing is that in the networking tool I no longer have the option of adding a device (ie a wlan0), and hence I couldn't set up the device this way?

I was unable to find the tools for setting the wlan0 interface up from the command line, I am assuming that there is one!

In the end all I could do was uninstall the ndiswrapper and re-install everthing, I am getting quite good at this now, and I'm wondering if I can write a script to do the whole thing for next time :confused: 

Anyway all is back working again.... glad I kept a note of the install procedure on my pc!

isn't it strange what we get up to a 5am in the morning!

Oh well, all the joy of Tux I presume, I guess if it had been a windows poblem then everything would have broken and i wouldn't have been able to re-install the device or anything... a problem that I had on another system!

good luck getting back online.

Dave

---

### Post by dstubb on 2007-04-24
> **dalziel_86 said:**
> I managed to fix my problem by recompiling and reinstalling the madwifi drivers. Should have posted my solution, but I forgot about it.

However your problem looks a bit different to mine. Still, it couldn't hurt to try re-installing the drivers.

Forgive the noob question, but how do I recompile and reinstall the madwifi drivers as you did?

---

### Post by dalziel_86 on 2007-04-24
(double post: couldn't figure out how to delete)

---

### Post by dalziel_86 on 2007-04-24
> **dstubb said:**
> Forgive the noob question, but how do I recompile and reinstall the madwifi drivers as you did?

Just follow the directions in [this guide]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo"). Download the latest version of the drivers, remove the old ones, make, then make install the new ones. You'll need to make sure you have build-essential installed, since despite being 'essential', it doesn't come with Ubuntu. And you'll need to make sure the version of gcc you have is the same version used to compile your current kernel.

This is usually the best solution to problems caused by kernel updates, but it won't fix every problem.

---

