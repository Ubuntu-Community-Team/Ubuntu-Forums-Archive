---
title: "dual homed 17.10 Ubuntu Server static routes assistance"
date: 2018-04-24
forum: Networking &amp; Wireless
---

### Post by visonare2 on 2018-04-24
Hi, I'm looking for assistance in setting up persistent static routes.  I've been digging through help articles for the past several hours without much luck.  Syntax seems to change from version to version, with additions like netplan and network manager added for additional fun.  I've removed both Network Manager (couldn't get it to manage any wired connections, which kind of defeated the purpose) and NetPlan (including all the .yaml files).

That leaves me with /etc/network/interfaces.  I thought this would be fairly easy to configure but Ubuntu appears to be ignoring my new routes no matter what I try.  Current config is this:

#LAN Interface
allow-hotplug eth0
auto eth0
iface eth0 inet static
address 192.168.1.x
netmask 255.255.255.0
up ip route add 192.168.1.0/24 via 192.168.1.1 dev eth0
up ip route add 192.168.2.0/24 via 192.168.1.1 dev eth0
up ip route add -net 192.168.100.0/24 via 192.168.1.1 dev eth0
post-up route add -net 192.168.101.0 netmask 255.255.255.0 gw 192.168.1.1 dev eth0

#DMZ Interface
allow-hotplug eth1
auto eth1
iface eth1 inet static
address 69.40.211.x
netmask 255.255.255.x
gateway 69.40.211.x

So as you can see above I've been trying different syntax in the hopes that that was my issue.  None of those routes stick though.  I end up with a link-local for the 192.168.1.0/24 and a default for 69.40.211.x.  Missing are any of the additional routes that I'd like to go out via Eth0 and 192.168.1.1.

Can anyone assist me with what I'm missing here?  So far as I can tell I've eliminated anything that should be overriding the interfaces config and those were the various examples I found online.

Also worth noting, I can't restart the service without getting file exists/permission errors.  No clue what could be causing that, I've been testing by just rebooting the server.

Thanks,
Andrew

---

