---
title: "Broken Network in VMWare"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by brodie_sewak on 2007-09-06
Hi,

I'm pretty new to Linux so don't kill me if I ask something stupid...:)

I'm runnung WinXP on my laptop and in VMWare an Ubuntu Feisty server. Everything was working fine until I had to reinstall the XP on the machine. Since then I don't have any network connection in the VMWare server. The VMWare itself is fine, I tested that with a second VMWare Ubuntu server instance which had the same problem. There I reinstalled the system, but the other one I definitly want to keep because the configuration of some stuff took weeks to figure out.

So what I was looking for was basicly something like the automatic network configuration during the setup cause that went smooth or somebody who could tell me what to do. Strange thing is that I didn't change the network card in the laptop or so. No idea why it doesn't work anymore...

Maybe it has to do something with the bridges VMWare uses. Maybe it is not really the network card but some bridge???

```

/etc/init.d/networking restart
* Reconfiguring network interfaces...
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0

```

---

