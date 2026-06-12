---
title: "Second network interface is preventing first from operating correctly 18.04"
date: 2020-10-24
forum: Networking &amp; Wireless
---

### Post by raptorlinux on 2020-10-24
Running Ubuntu 18.04.5 server on Virtualbox 6.1.14
Problem persists regardless of if I'm using netplan or interfaces

On boot: 
- Second interface works fine
- First interface can only be pinged over it's leased address
- ```
ifdown enp0s8;ifdown enp0s3
``` followed by ```
ifup enp0s3
``` brings up my internet but if I ```
ifup enp0s8
``` after bringing up enp0s3 it breaks enp0s3 and enp0s8 can't be brought up and down anymore without generating _*RTNETLINK answers: file exists*_


```
# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug enp0s3
iface enp0s3 inet dhcp

# The internal network interface
allow-hotplug enp0s8
iface enp0s8 inet static
        address 192.168.56.105
        netmask 255.255.255.0
        gateway 192.168.56.1

```

I generally use *auto device* but I was playing with different settings. 

This problem doesn't exist on Debian 10.6.0. I was able to get my two network interfaces working perfectly with no issues using these interface settings so this brings me to my last question; _*Is there a way to modify Ubuntu 18.04.5 or the newest to switch back to the* _**_*network package & configurations of it's Debian parent?*_** 

Suggestion: Option for using the default package(s)/configuration of the Debian distro 18.04.5 and 20.04 are based off of.

---

### Post by TheFu on 2020-10-25
Wasn't ifupdown deprecated in 17.10 and later?  Use netplan. Post your netplan file please.

---

### Post by raptorlinux on 2020-10-26
disabled. Tried netplan and it has same problem. Debian was working. booted it again after post and it stopped working. I was running my servers with zero issues on Ubuntu so the problem is Windows. Also did you read what I wrote? Is it not obvious that i disabled netplan to use interfaces? just because its deprecated doesn't mean I'm suddenly not allowed to use it.

---

