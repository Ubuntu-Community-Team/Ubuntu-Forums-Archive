---
title: "Network fails to recover after waking from hibernate, Ubuntu 20.04.4 LTS/5.4.0-104-LL"
date: 2022-03-14
forum: Networking &amp; Wireless
---

### Post by robertwk on 2022-03-14
I'm having a problem where my network adapters do not function after waking from hibernation. It takes a reboot and doing [FONT=courier new]netplan -d apply[/FONT] and [FONT=courier new]systemctl disable NetworkManger.service [FONT=arial]in order to get things working again. This is really starting to get irritating and I need to solve the problem.

I'm running Ubuntu 20.04.4 LTS with Kernel 5.4.0-104-lowlatency following the security update for the dirty pipe vulnerability.

Unfortunately my system has the realtek ethernet driver, and I'm using r8168 and r8125 (r8169 had problems and wouldn't work correctly).

[/FONT][/FONT]  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
  *-network
       description: Ethernet interface
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.

In addition, my netplan configuration has the two ethernet ports working in a bonded connection, which I was finally able to get working correctly.

After waking from hibernate, the network connection still has an IP address but can't really ping any of my local network devices.

So far the issue has been reproducible, and there are various fixes out there but I would like to be sure that whatever it is will fix the problem indefinitely.

Update: 

For some reason, doing 

sudo modprobe -r r8168
sudo modprobe -i r8168

seems to fix it, but I thought this was fixed?

---

