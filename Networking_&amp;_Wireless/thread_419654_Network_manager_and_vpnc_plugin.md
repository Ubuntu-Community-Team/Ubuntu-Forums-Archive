---
title: "Network manager and vpnc plugin"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Gujs on 2007-04-23
Hello,

I have a problem with vpnc plugin for network manager. It is his strange behaviour, that sometimes i have options on the network icon for vpn connections and sometiomes don't.

I use location configurations for home and work. I tried to delete them both and have just one setup without location and still doesn't work. It strange that previous boot i had is but then vpn connections didn't work. It disconencted it in 30 minutes.

I rebooted again and now I don't have options for vpn on network icon any more.

Please help!

---

### Post by Gujs on 2007-04-23
I found out that network manager is working great if I have dhcp enabled on eth0 and file /etc/network/interfaces looks like this:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
auto eth1

iface eth2 inet dhcp
auto eth2

iface ath0 inet dhcp
auto ath0

iface wlan0 inet dhcp
auto elan0

```

But even now my vpnc connection get disconnected apter 30-60 seconds. The good thing is that I can select connection thought network manager.

But when I click Manual configuration on network manager and configure static ip, I lose all options but Manual configuration. Network manager doesn't detect wired network, I can't select any vpn connections and can't see Connection information (it is grey - disabled ).

---

### Post by codedmin on 2007-05-03
> **Gujs said:**
> I

But even now my vpnc connection get disconnected apter 30-60 seconds. I Can fix the problem
> 

I've solved it by rebuilding without the patch:

cd /usr/src
sudo apt-get source vpnc
cd vpnc-0.4.0/debian/patches

sudo gedit 00list

remove the line 06_stolen_from_head

cd ../..
sudo debian/rules binary

cd ..

sudo apt-get remove vpnc
sudo dpkg -i vpnc_0.4.0-2ubuntu1_i386.deb

if you had installed network-manager-vpnc you'll have to reinstall it

be careful when upgrading the system, don't update vpnc or you will get the patched version


Solution from artt  in [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413](https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413) comment [26]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413/comments/26")

Hope could help you

---

### Post by orn on 2007-09-11
Hi, additional information that I didn't find and needed to figure out at least:

To be able to build the package I had to install the following packages via apt:
dpatch
dpkg-dev
debhelper
libcrypt-dev
libgcrypt11-dev

I also installed build-essential, but I'm not sure if that's required.

So,
```
sudo apt-get install dpatch dpkg-dev debhelper libcrypt-dev libgcrypt11-dev build-essential
```

---

### Post by Gujs on 2007-09-11
If you need to install dependencies for network manager just run

```

sudo apt-get build-dep network-manager

```

---

