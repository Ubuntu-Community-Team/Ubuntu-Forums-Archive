---
title: "wireless actually works, but I need 3 essids automatically..."
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by docsmooth on 2007-05-10
I've been a Kubunutu user for about 6 months now, Debian for 6 months prior to that.  I currently run a Dell D520 (ipw3945 wireless and b44 wired) Feisty system.  I'm having issues getting the system to roam properly as follows:

1) I don't use NetworkManager or knetworkManager - I log into tty1 quite often, and need network access there.
2) ifplugd fixed.
3) I have 3 essids (none broadcast, 2 of them shared on about 25 APs) that I need to be able to automatically connect to, and I"d like to also be able to pick up unsecured networks (like at Cosi) automatically.
4) if I set /etc/network/interfaces with the appropriate info for a single essid, and it'll come up automatically, but I have to change it to roam.  That's obviously no fun.
5) I also have scripts in ~/bin/ to modify iwconfig and re-trigger dhclient to more easily pick up each WAP, but it still requires manual intervention.

It appears that waproamd and ifplugd will do what I want, but I can't get them to work right.  **If I'm wrong and should be using something else, please tell me.**

1) ifplugd fixed.  I removed "-f" from the options list.
2) waproamd picks up essids from "iwlist eth1 scanning", but it's acting up, setting the AP statically, and setting the ESSID with only the last 3-5 letters of the chosen AP.  If my home network is called "WPA2ATHOME", then my ESSID in iwconfig becomes "OME".  If the ESSID is hidden, then my essid in iwconfig becomes "dden>".
3) waproamd isn't connecting to any unsecured APs ever.
4) I have tried waproamd with both keyfiles alone and scripts alone.  unfortunately, it's not very well documented, and I can't find many people using it, cause they're mostly using wpa_supplicant, but we can't support WPA at work yet, and I don't bother with it at home.

Config files (stripped of identifying marks) are attached below.  I've tried it with the firewall set to ACCEPT all (no rules, policy ACCEPT), with no affect.

Thanks!

Doc SmooTH
Ubuntu for 6 months, Windows for years.

---

### Post by docsmooth on 2007-05-17
Ifplugd actually isn't working - I still have to ifdown eth0 to get my cisco VPN started.

No thoughts from anyone?

Thanks in advance.

---

