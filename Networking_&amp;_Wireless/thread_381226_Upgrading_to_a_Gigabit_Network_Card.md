---
title: "Upgrading to a Gigabit Network Card"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by n8oay on 2007-03-10
Having already screwed up a video card upgrade I think I should ask some questions before the doing the next hardware upgrade... I am planing to install a Netgear GA311 10/100/1000 network card, which has a Realtek 8169s-32 chip. The computer currently is using the integrated VIA VT6103L 10/100 NIC on the Biostar P4M80-M4 motherboard. What do I need to do to make this upgrade hassle-free? I have edited several lines in the xorg.conf file for other things, but I do not see anything in it for the network card. I have red through some of the posts on this Networking forum, but did not find anything that made sense to me for planning ahead for the upgrade.

---

### Post by chili555 on 2007-03-10
Step away from the keyboard, please. xorg is mostly for display and has nothing to do with networking.

I think all you will have to do is physically install the card, restart your computer and go into the BIOS and disable the onboard VIA nic. Save, exit and boot into Ubuntu. Open a terminal and issue a command ifconfig. I think you will see eth0 all happy with an IP address.

You can adjust settings as necessary with a command ethtool. You can learn more about ethtool by the command man ethtool.

Good luck and post back if you get stuck.

---

### Post by Mr. C. on 2007-03-10
n8oay,

Are the other our networking components also Gigabit Ethernet ?  Some are under the illusion that they will get better performance by simply replacing 100Mbit with 1000Mbit.  No need to reply if this is obvious already.

MrC

---

