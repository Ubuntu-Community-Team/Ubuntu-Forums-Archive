---
title: "Only sometimes network at boot"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by kingmob on 2007-05-29
Only on several occasions do i get a proper eth connection after boot when booting my HTPC. There is a S40Networking in rcS.d, my hosts file is correct and since it is a wired connection /etc/networks is nothing special. It does seem to not come up after a shutdown -h, but does come up after a reboot, but i'm not 100% sure about this. I also tried shutting down and taking off the power. In this one test i got network after boot.
A simple```
 ifdown eth0 && ifup eth0
``` is enough to bring up the network after boot.
I have seen similar problems here, but i haven't managed to find a solution for me, especially since most problems seem to happen with wireless, not wired.
Here is some output of messages and dmesg:
```

mythtv@HTPC:~$ cat /var/log/messages |tail -n 500 | grep -i eth
May 29 19:09:14 HTPC kernel: [   28.708340] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 18, 00:d0:09:e8:10:f3.
May 29 19:09:14 HTPC kernel: [   38.910184] eth0: Media Link On 100mbps full-duplex
May 29 19:35:17 HTPC kernel: [   28.375838] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 18, 00:d0:09:e8:10:f3.
May 29 19:35:17 HTPC kernel: [   38.621797] eth0: Media Link On 100mbps full-duplex
May 29 19:36:44 HTPC kernel: [  136.536338] eth0: Media Link On 100mbps full-duplex

mythtv@HTPC:~$ dmesg | grep -i eth
[   28.375838] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 18, 00:d0:09:e8:10:f3.
[   38.621797] eth0: Media Link On 100mbps full-duplex
[   77.249112] eth0: no IPv6 routers present
[  136.536338] eth0: Media Link On 100mbps full-duplex
[  144.577587] eth0: no IPv6 routers present


```
This looks pretty normal to me...

---

### Post by Npl on 2007-05-29
if you have a cable or dsl and dont have to log in, its likely that the DHCP server responds not fast enough (sometimes).
Im pretty sure theres a setting in the mess of linux` config-files somewhere, which defines how long your computer waits for a response - if you find it you can increase it.
The other option would be to disable DHCP and poke in your configuration in the Dialogs, that should also speed up boot a little btw.

---

### Post by kingmob on 2007-05-29
Thank you for your reply but i am afraid you will have to be more specific. I'm not enough of a guru i guess.
Turning dhcp off on the router is sadly not possible, other gadgets in the house will not work without it ;)

---

### Post by Npl on 2007-05-29
ahh, if your router is local, then that shouldnt be the problem.
I was thinking you are directly on a cable/dsl-modem and fetch DHCP from a distant server (thus getting timeouts occasionally). you could still try opening the network-preferences and change to static-IP and then fill in the stuff you normaly get through DHCP (IP,Subnetmask,gateway, dns-servers...) when it works. That would be one variable eliminated.

Dont think Im a guru, I just blindly limped through hell after changing GFX-Card today. ;)

---

