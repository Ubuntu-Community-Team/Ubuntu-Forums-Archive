---
title: "[SOLVED] Start network connection automatically"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by rac56 on 2007-09-17
I have Feisty  installed on a Dell desktop using a wired network connection.  When I start the PC, I would like it to connect to the wired network automatically.  As it is, I have to click the Network Manager icon and select "Wired Network" whenever I start the PC.  I tried working with the "Manual Configuration" option and it does not seem to make a difference.  Thanks!

---

### Post by noob12 on 2007-09-17
If you configure by DHCP and you want the interface to be brought up automatically at boot, you need an entry like the following in the file  **/etc/network/interfaces**.  This assumes the interface is called **eth0**, so replace that if appropriate.

```

auto eth0
iface eth0 inet dhcp

```

---

### Post by rac56 on 2007-09-17
Thanks for the suggestion Noob12.  My /etc/network/interfaces looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

...and it still does not work.  I tried disabling Network Manager also.  When I do that, I have to go into System > Network Settings and uncheck and check the box for the network to get it to start.  I verified that my network connection is eth0.

Anything else to try?

---

### Post by noob12 on 2007-09-17
Can you post the output of these
```

sudo lshw -C network

ifconfig -a

dmesg

```

---

### Post by rac56 on 2007-09-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/83143](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/83143) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well, I did some research today and found a reference to a bug in Network Manager that is very close to the symptom I am experiencing.  See the link above.

To fix the issue, I unchecked Network Manager under System > Preferences > Sessions and disabled it using the instructions found here:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5")

This did the trick for me.  When I start the PC, the network is up as it should be.  This fix is good for me because the machine in question is a desktop with only one network interface.  No wireless complications to deal with, so Network Manager does not seem to be needed.  Noob12, thanks for your help!

---

