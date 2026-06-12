---
title: "Broke Entire Networking on Wireguard Uninstall"
date: 2020-06-12
forum: Networking &amp; Wireless
---

### Post by databoy2k on 2020-06-12
--I have completely revised this question; I am at least up and running but am not sure how to fix the issue itself--

I was running a Wireguard server; however, in the update on June 11 it broke and I was never able to get it back up and running. I uninstalled it and rebooted my server (Ubuntu 18.04). When I rebooted, I saw "Raise Network Interfaces" fail on boot and had no network connectivity. ifup -v enp4s0 reported "cannot find device enp4s0". The /etc/network/interfaces file referred to both lo and enp4s0.

The kernel version is 5.3.0-1026.28~18.04.1

lshw -C network output included "Network: UNCLAIMED". Lspci reports ethernet controller as Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06).

I have since been able to get running again by reverting to kernel 4.15.0-106-generic using an old GRUB entry, but I would like to know how to fix 5.3.0 as well (both get connectivity up and get wireguard working).

What troubleshooting steps do I need to go through? I have no way of getting network while on 5.3.0 right now, but I can download as long as I'm on 4.15.0.

---

