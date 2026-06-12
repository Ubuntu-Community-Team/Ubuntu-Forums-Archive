---
title: "systemd-network static ip assignment"
date: 2021-01-04
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2021-01-04
I am running Ubuntu 20.  I am running it inside a LXC container.  I set a static IP, and do a reboot, and I am back to dhcp again.  I look at the file, and all of my changes are lost.  I did notice that my interface name changes.  The format is: eth0@nnn.  I tried for the match section, eth0@*, but that did not work.  How do I make my changes persistent upon a reboot?

---

### Post by TheFu on 2021-01-04
Did you tell LXC to use a bridge network connection provided by the host?  This is really an LXC question.  May want to be more specific about which Linux Container technology you are using, since some have taken over network settings.

For example, I use LXD and did connect it to the bridge from the host and it does have a static IP, managed by netplan in the normal way inside the container. It is an lxd ubuntu 18.04 image being used.  How I convinced lxd to use that bridge is a bit of a mystery, so I wouldn't claim to explain to someone else a way that definitely works.  Also, the host machine doesn't use netplan, it is running 16.04 still, using the old-school /etc/network/interface file to setup the bridge.

---

### Post by sniper8752 on 2021-01-06
I am using LXC in proxmox.  I am not sure if that helps... Let me know.

---

### Post by TheFu on 2021-01-06
I know nothing about proxmox. sorry.

---

### Post by #&amp;thj^% on 2021-01-06
> **sniper8752 said:**
> I am using LXC in proxmox.  I am not sure if that helps... Let me know.

Sounds Fun ;) :[https://forum.proxmox.com/threads/routing-inside-lxc-container-ubuntu-18.54873/](https://forum.proxmox.com/threads/routing-inside-lxc-container-ubuntu-18.54873/)

---

