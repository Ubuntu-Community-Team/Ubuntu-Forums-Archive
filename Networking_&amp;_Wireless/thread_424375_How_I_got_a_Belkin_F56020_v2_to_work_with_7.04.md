---
title: "How I got a Belkin F56020 v2 to work with 7.04"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by ianf43 on 2007-04-26
I am pretty new to Ubuntu but use Irix and Solaris regularly at work. I installed Ubuntu 7.04 on a Compaq Evo N1020V that doesn't have a wireless card pre-installed. I remembered that I had an old Belkin F56020 v2 PCMCIA card so I plugged it in and not much happened. ifconfig -a would show eth1 (the wireless card) but it was clear that it wasn't configured properly. I ran a tail -f /var/log/syslog when I plugged the card in and it looked fine. It produced this message (among others):

Apr 26 16:06:13 localhost kernel: [  956.632000] eth1: Atmel at76c50x. Version 0
.98. MAC 00:30:bd:d1:53:9b
Apr 26 16:06:13 localhost NetworkManager: <information>^Ieth1: Device is fully-s
upported using driver 'atmel_cs'. 

This at least narrowed down the driver I should be using- the internets gave me conflicting information on which driver to use; the atmel_cs is part of the kernal (I believe) so there is no need to download anything.

sudo pccardctl ident produced this:

Socket 0:
  product info: "Belkin", "11Mbps-Wireless-Notebook-Network-Adapter", "", ""
  manfid: 0x01bf, 0x3302
  function: 6 (network)

Which I used to add a few lines to /etc/pcmcia/config.opts. I added this:

# Belkin Wireless PCMCIA Card
card "Belkin 11Mbps Wireless Notebook Network Adapter"
  version "Belkin", "11Mbps Wireless Notebook Network Adapter"
  manfid 0x01bf, 0x3302
  bind "atmel_cs"
module "atmel_cs" opts "network_name=eth1"

Rebooted and it worked! Hope this helps!

---

