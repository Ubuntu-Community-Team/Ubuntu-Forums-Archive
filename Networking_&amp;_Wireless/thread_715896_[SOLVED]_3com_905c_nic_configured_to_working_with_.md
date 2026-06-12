---
title: "[SOLVED] 3com 905c nic configured to working with DHCP in newly installed ubuntu 7.10"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by ryecomp on 2008-03-05
I am new to ubuntu, and recently installed ubuntu 7.10. All went well, sound card, dual core cpu, onboard graphic card except onboard nic. Because I heard that driver for onboard nic is frequently not provided in ubuntu, I turned off this in bios and plug in realtek 8139c compatible nic. But this also failed with same issue. But this time static ip started to work, but not with DHCP. Even with static ip configuration network was stucked in few hours. 

Because I believed 3com nic is widely used and cannot be a source of problem, I bought used one from auction in 5$ and plug in this as replacement for realtek nic. But same problem occurred.... 

I started to focus on system configuration rather than nic, because 3com 905 tx series working in windows 2000, could not be a problem. Testing this and that, I found DHCP client failed to receive ip from server, So, I focused on dhclient.  

`man dhclient` said that default port of 68. But in actual invocation of dhclient I saw an timeout error in 67 port. So using -p option I changed port from 65 ~ 69, but see no change. And then I started to look at /etc/dhcp3/dhclient.conf file.  

It contains some commented line. One of them looked like MAC configuration. So I uncomment this line to include my nic MAC. after which dhclient was successful in receiving IP from dhcp server!!! All network worked fine and ifconfig which showed eth0, eth0:aho, lo was displaying eth0 and lo only. 

This works well till one or two hours, where network was also stucked. There might be an lease timeout problem. So I am planning to fix this later.

SYSTEM CONFIGURATION

newly installed ubuntu 7.10 
3com 905c tx nic 
ecs 945gty-m
intel dual core e2160
ide hdd
sata dvd

PROBLEM : how to make nic(eth0) function in DHCP network.

1) sudo vi /etc/modprobe.d/aliases : alias net-pf-10 ipv6
   --> alias ipv6 off 
       alias net-pf-10 off

2) firefox : about:config
   --> ipv6 disable

3) system->administration->network
   --> disable roaming 
       set as DHCP for eth0

4) reboot 

 
5) ifconfig 
   --> displaying eth0, eth:avah, lo (eth:avah must not exist when network is ok)
       rx count increasing in every ifconfig execution.

6) sudo ethtool eth0 
   --> Link detected : yes (hardware is functioning but there is software problem)

7) sudo vi /etc/network/interfaces 
   --> delete lines relating to eth0 except "auto eth0" and " iface eth0 inet dhcp"

8) sudo dhclient eth0
   --> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval ... fails

8) sudo vi /etc/dhcp3/dhclient.conf 
   --> uncomment MAC line and replace with my MAC 
                         (1:aa:bb:cc:dd:ee:ff where aa:~:ff is MAC)

9) sudo dhclient eth0
   --> DHCPDISCOVER success!!

10) sudo /etc/init.d/networking restart : for IP lease timeout

---

