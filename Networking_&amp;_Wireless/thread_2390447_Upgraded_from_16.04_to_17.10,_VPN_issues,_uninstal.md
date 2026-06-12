---
title: "Upgraded from 16.04 to 17.10, VPN issues, uninstalled, internet stopped working"
date: 2018-04-28
forum: Networking &amp; Wireless
---

### Post by francis-degagne on 2018-04-28
Hi, I was having difficulty with my VPN (PIA) after upgrading to ver 17.10. It would work once and a while but would often shutdown without notification (and no ability to check status etc).

I debated reverting back to 16.04 because I had no issues there, but it seemed too complex.

I uninstalled the VPN software, and my internet went dead. Nothing seemed out of the ordinary, not sure what to adjust.

So I went to re-install the VPN, since I had the tar.gz file, but nearing completion it tried to access the internet and could not, so it stopped the installation.

At a loss. I have started a ticket with PIA but so far no instructions (other than to re-install)

---

### Post by francis-degagne on 2018-04-29
To be clear, PIA is not running, it is uninstalled.

I have tried deleting my wired connection and creating a new one - no difference.

---

### Post by francis-degagne on 2018-04-29
Fixed it! ):P

Found some good instructions on [https://askubuntu.com/questions/835195/how-do-i-reset-my-network-settings-to-default/1029877#1029877](https://askubuntu.com/questions/835195/how-do-i-reset-my-network-settings-to-default/1029877#1029877)

Run this:

sudo nano /etc/network/interfaces
[COLOR=#111111][FONT=Ubuntu]and you should get something inside....delete everything and paste this (but change the network adapter name where enp0s3 is):[/FONT][/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet dhcp
[COLOR=#111111][FONT=Ubuntu]save the document and reboot...[/FONT][/COLOR]

---

