---
title: "Intel i225-v networking woes with 10900k and ROG Strix Z490-F Gaming Motherboard"
date: 2020-05-27
forum: Networking &amp; Wireless
---

### Post by scum2k on 2020-05-27
Hi folks,

My first post here, a new linux user who took the plunge and went full Ubuntu 20.04 last week.

I've cobbled together a PC using ROG Strix Z490-F Gaming Motherboard a 10900k and a 6 year old air cooler, an 8 year old case and a brand new PSU.

Ubuntu installed no problem at all, networking worked from the outset. But after the first reset the network adapter was stuck with a status of Unplugged, I restarted a LOT, restarting the PC tended to have a 20% success rate, sometimes it would initialise, sometimes it wouldn't.

I wanted to eliminate a hardware problem so I installed Windows which worked no problem with the motherboard drivers out of the box.

So I reinstalled Ubuntu (dual boot) and again, after the first boot, the problem persevered. So I've started learning a little about Linux networking. I managed to install ifdown to see if I could manually start or disable the adaptor (which I couldn't) and started tinkering with the settings inside /etc/network

I've run journalctl -u NetworkManager to see if any errors exist.

The main error when it fails to work is **failed to open /run/network/ifstate**


I tried editing /etc/network/interfaces with a number of configurations

dynamic, dhcp and static with appropriate ip/gateway/dns etc (which worked occasionally if I rebooted enough).

The DHCP setting would always end up pausing start and shutdown with 
A stop job is running for raise network interfaces


Looking at the back of the PC I can see that the network adaptor initialises fine when turning on the PC (both lights come on) but as Ubuntu boots (and when the network fails) the lights switch off completely.

As the issue is intermittent I can only imagine this is a driver issue, but hasn't this particular network adaptor been around for a while?

There is definitely something I am not taking into account. Here's hoping there is light at the end of the tunnel and appreciate any help and advice!

Cheers!

---

### Post by slickymaster on 2020-05-27
Thread moved to **Networking & Wireless** for a better fit

---

### Post by scum2k on 2020-05-27
Thanks Slicky!

---

