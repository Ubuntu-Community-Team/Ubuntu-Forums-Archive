---
title: "Dual NIC caused internet loss!"
date: 2017-12-05
forum: Networking &amp; Wireless
---

### Post by tjscool914 on 2017-12-05
Hey Everyone,

I'm new to linux, but enjoying the learning experience. I'll try to list as much information as I can to give you insight as to the problem. I have a Dell Optiplex 790 with an onboard NIC and a secondary PCIe NIC (single port).
[B]
lspci -vv | grep Ethernet:

00:19.0  Ethernet  controller:  Intel Corporation 82579LM Gigabit Network Connection (rev 04)
02:00.0  Ethernet  controller:  Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
              Subsystem:  Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express[/B]

[B]cat /etc/network/interfaces:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback[/B]

Until today, I've always used the onboard Ethernet port (eth1) for internet connectivity on my linux PC (Optiplex 790). I just installed a secondary NIC in my Windows PC with intentions of creating a local network to run synergy between the two PCs (can't use synergy over work network). 

I connected the two PCs together and used gnome-nettool to configure a static (manual) address for the linux PC secondary NIC (eth0). From my linux PC, I can ping my Windows PC through my work network (cant ping Windows PC secondary NIC, but I believe that is a Windows firewall issue). I can also ping my ubuntu secondary NIC static IP address from my Windows PC. What is most troublesome is I've now lost internet connectivity on my linux PC. 

Any help in restoring my linux pc internet connectivity and keeping my dual NIC setup is greatly appreciated!!!

---

### Post by powersj on 2017-12-05
> **tjscool914 said:**
> I can also ping my ubuntu secondary NIC static IP address from my Windows PC. What is most troublesome is I've now lost internet connectivity on my linux PC.

Hi! Sounds like you configured th enetwork address correctly, but something in your routing is incorrect. Can you run the wireless-info script from the sticked post to get some info on your configuration? See: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

