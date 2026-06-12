---
title: "Belkin F5D6020 on Fiesty issues"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by russnash37 on 2007-09-19
I just installed 7.04 on my trusty old Thinkpad T21, the only issue I am left with has me baffled, despite lots of googling of similar issues:

I'm aiming to use wireless networking with a Belkin F5D6020 pcmcia card, it's FCC ID is K7SF5D6020 which should (I believe) place it in the hands of the orinoco driver, which is what 7.04 is using for it by default.

I've configured the card as follows:

iface eth1 inet static
address 10.0.0.15
netmask 255.255.255.0
gateway 10.0.0.11
wireless-essid dylan
wireless-mode managed

There is no WEP key enabled on the AP (A linksys befw11s4) and MAC filtering is disabled.

The card appears fine, ifconfig shows it configured correctly and the interface is up, iwconfing eth1 reports the correct essid and that it sees the AP.  Link quality, signal level & noise level all report seemingly 'real' values indicating a connection.

However, whenever I try to ping the AP or any other device on the network I get 'Destination Host Unreachable'.

I've tried disabling acpi by adding 'acpi=off pci=noacpi' to my boot line, yet still no joy.

I know I've used this very same card before sucessfully in the very same laptop with Linux, however, that was almost 4 years ago under Gentoo.  Since then, it's been running fine under win2k.

Can anyone help?  I'm fresh out of ideas.

Thanks in advance!

Russ.

---

