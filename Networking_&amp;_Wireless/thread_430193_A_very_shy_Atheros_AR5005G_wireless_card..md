---
title: "A very shy Atheros AR5005G wireless card."
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by xaval on 2007-05-01
Hello,

One Atheros AR5005G wireless card is living inside my laptop, but she and Feisty Fawn (7.04) seem to be shy and never meet, never speak, never nothing.

When I type "lspci" I get: 08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01).

It is the only clue I have that one wireless card stowaway is in my boat.

My Ubuntu distro has the "linux-restricted-modules-2.6.20-15-generic" and the "madwifi-tools" packages installed, but I don't know how to make the wireless card to work.

In System > Administration > Networks is not listed any wireless connection.

I tried to install the Windows .inf driver through the Windows Wireless Drivers utility, but this utility is laughing at me. My actions have no effects on it. I hate this behavior!

I've been browsing these forums, but at the end I get frustration and headache. I try to be patient and browse again the next day, but... nothing.

Can some good heart help me or link me to a helpful thread?

Lots of thanks in advance.

---

### Post by jml on 2007-05-01
If you have not already done so install network-manager and network-manager-gnome.  After its installed, there will be a new network aplet icon in the top right of your screen.  It will look like a small monitor.  You access it by either left clicking or right clicking on it.  You should be able to set up your card that way.  Good Luck.

Joe

---

### Post by Hallvor on 2007-05-02
> **xaval said:**
> Hello,

One Atheros AR5005G wireless card is living inside my laptop, but she and Feisty Fawn (7.04) seem to be shy and never meet, never speak, never nothing.

When I type "lspci" I get: 08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01).

It is the only clue I have that one wireless card stowaway is in my boat.

My Ubuntu distro has the "linux-restricted-modules-2.6.20-15-generic" and the "madwifi-tools" packages installed, but I don't know how to make the wireless card to work.

In System > Administration > Networks is not listed any wireless connection.

I tried to install the Windows .inf driver through the Windows Wireless Drivers utility, but this utility is laughing at me. My actions have no effects on it. I hate this behavior!

I've been browsing these forums, but at the end I get frustration and headache. I try to be patient and browse again the next day, but... nothing.

Can some good heart help me or link me to a helpful thread?

Lots of thanks in advance.


I have a problem with the same type of card. Seems to me the driver is buggy.

---

### Post by khaosangel on 2007-07-04
Bump, 

I didn't want to post the same question, but now that madwifi 0.9.3 is out, has anyone been able to defeat this odd problem.

---

### Post by khaosangel on 2007-07-04
In case you might still read this, I figured out my answer was that I couldn't tell that I had disabled the wifi card with the little button on the bottom of my laptop, check that. Such a stupid answer yet idiot simple answer.

---

