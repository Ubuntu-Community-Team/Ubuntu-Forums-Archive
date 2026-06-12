---
title: "VPN broke my internet connection?"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by johnnyy14114 on 2017-02-01
Today after starting my computer I was unable to access the Internet. When trying to access any website in Firefox, it returned the typical 'website not found' method immediately. I tried to access any website using command line, which also didn't work. Connecting to other WiFi networks, rebooting my computer and resetting iptables didn't solve the problem. 

It happened to me a week ago and then I reinstalled the system because I didn't want to mess with it but now it happened the second time and I'm asking for help because I'm tired of setting up my OS over again.

I think I should mention that I use a commercial VPN provider Mullvad to browse the Internet. Its client is based on openvpn. I also use the client's killswitch feature which blocks the internet in case the connection disconnects. I thought it may be the issue but resetting iptables didn't solve the problem. Furthermore, the Internet broke after booting my system today in the morning and not when the vpn client was running, so it's another argument why the VPN is not responsible for the issue. I just mention this in case it turns out to be important in solving the problem.

Really looking forward to your ideas on how to solve the problem. **Ideally I think it would be the best if there was a way to reset all my internet settings and configuration to its default (just like it was fresh after the installation**). Thanks :)

---

### Post by #&amp;thj^% on 2017-02-01
Run

```
ifconfig
```

and see the name of your network adapter. Mine is: **enp0s3**

now run this command

```
sudo nano /etc/network/interfaces

```
and you should get something inside....delete everything and paste this (but change the network adapter name where **enp0s3 is**):

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet dhcp
```

save the document and reboot...

---

