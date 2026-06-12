---
title: "ThinkPad R60 Wireless not working"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by superbenny on 2007-10-06
Hey-

I just upgraded from 7.04 to 7.10 (Kubuntu)
My Intel wireless card worked fine in 7.04, but now its not working.
When i first restarted after the upgrade, it said something about the restricted driver, but it was enabled so i didnt worry about it. knetwork manager says that theres no device, but iwconfig finds my network, and lshw finds my card. i went into System Settings>Network Settings>Net. Connections and configured my card, but it doesnt connect, and now knetwork manager is convinced its connected to a wired network that is not there. when i plug my eth cable in, it works, but i dont want to be anchored to my router. thoughts?
intel chipset
btw, wireless worked out of the box when i installed 7.04

---

### Post by Lambert on 2007-10-07
> **superbenny said:**
> Hey-

I just upgraded from 7.04 to 7.10 (Kubuntu)
My Intel wireless card worked fine in 7.04, but now its not working.
When i first restarted after the upgrade, it said something about the restricted driver, but it was enabled so i didnt worry about it. knetwork manager says that theres no device, but iwconfig finds my network, and lshw finds my card. i went into System Settings>Network Settings>Net. Connections and configured my card, but it doesnt connect, and now knetwork manager is convinced its connected to a wired network that is not there. when i plug my eth cable in, it works, but i dont want to be anchored to my router. thoughts?
intel chipset
btw, wireless worked out of the box when i installed 7.04

post the output of the following terminal command.

```

dmesg | grep ipw

```

You also upgraded to an incomplete OS. I don't think it's even reached beta stage so problems like this are expected. Bug reports shows a few problems surrounding firmware with intel wireless devices.

Since you upgraded, you might have to use wired connection for a little while and upgrade daily and keep testing to see if the updates correct the problem you're having.

---

### Post by superbenny on 2007-10-10
nevermind, its a problem with knetworkmanager. i am able to connect with other clients, even thru the network settings in system settings. so do not mind me, ill just keep my eye out for knetworkmanager updates

thanks anyways!

---

