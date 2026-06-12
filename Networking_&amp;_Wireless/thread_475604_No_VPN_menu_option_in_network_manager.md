---
title: "No VPN menu option in network manager"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by rmcd on 2007-06-16
I have a new 7.04 install. I'm new to Ubuntu. My problem is that I can't see how to configure a VPN connection.

When I click on Network Manager I see "manual configuration". When I click on that and provide a password, I don't see any options related to VPN. I have installed the cisco vpn client (vpnc and network-manager-vpnc).

I noted in some other threads that selecting "enable roaming mode" affected available menu choices on network manager, but I have a fixed IP address.

Thanks in advance for any help or pointers.

---

### Post by hadiriazi on 2007-06-16
I have almost the same problem :(

---

### Post by rmcd on 2007-06-16
Okay, so unless I misunderstand, this behavior is a bug:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/87941](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/87941)

If you have a static network configuration (a fixed IP address would be one example of this) then Network Manager simply doesn't work properly. The /etc/network/interfaces file has to be empty (apart from pointing to localhost).

This post in the Ubuntu docs proved quite helpful:

[https://help.ubuntu.com/community/VPNClient?highlight=%28vpn%29](https://help.ubuntu.com/community/VPNClient?highlight=%28vpn%29)

This is a *really* bad bug IMHO.

---

### Post by sunken on 2007-07-15
ok, I did like this:
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

---

