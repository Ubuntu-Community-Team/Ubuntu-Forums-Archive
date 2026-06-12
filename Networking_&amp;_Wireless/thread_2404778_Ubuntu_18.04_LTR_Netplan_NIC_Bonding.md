---
title: "Ubuntu 18.04 LTR Netplan NIC Bonding"
date: 2018-10-28
forum: Networking &amp; Wireless
---

### Post by cmp828 on 2018-10-28
Hello,

I am not new to Linux or Ubuntu, and just loaded clean Ubuntu onto a HP DL360 G7 server to make a new DVR Camera server using I.P. Cameras. I went from 16.04 to 18.04 and from what it looks like, in Ubuntu 17.x they changed things and now Ubuntu uses NetPlan for network configuring. At first I was editing the etc\network\interfaces file and appeared to get the bond set but not able to access the network. Researching / Googling more I see reference to NetPlan.  For now I just want to set up bonding with DHCP and once that is working I can later go back and static it. When I tried an example with my bonding configs I was able to get a local loopback on the  169.254.10.162. I have 5 network ports, 4 on the motherboard and one card in a slot, and right now I have the single card / port working as just a single port on DHCP so I can work with the machine and access it via ssh.

As I read, looks like Ubuntu 17.x and forward Netplan is what is running the show as a front end. I assume you can still manually edit the netplan files, which is what I am doing, or trying to do.

So as I research since I loaded the Desktop  version of Ubuntu 18.04LTS and it is patched to most current updates, I see the netplan file I need to make or add entries into is  /etc/netplan/01-network-manager-all.yaml  I read that server and clould are different named files one would need to edit. 



network:
  version: 2
  renderer: NetworkManager

 bonds:
       bond0:
               dhcp4: yes
               interfaces:
                       - enp3s0f0
                       - enp3s0f1
                       - enp4s0f0
                       - enp4s0f1
               parameters:
                       mode: balance-xor
                       primary: enp3s0


sudo netplan apply
Invalid YAML at //etc/netplan/01-network-manager-all.yaml line 1 column 0: found character that cannot start any token
chad@DVR-ProLiant-DL360-G7:~$ 





chad@DVR-ProLiant-DL360-G7:~$ ip add
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 3c:d9:2b:fb:42:d8 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::3ed9:2bff:fefb:42d8/64 scope link 
       valid_lft forever preferred_lft forever
3: enp3s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 3c:d9:2b:fb:42:da brd ff:ff:ff:ff:ff:ff
    inet6 fe80::3ed9:2bff:fefb:42da/64 scope link 
       valid_lft forever preferred_lft forever
4: enp4s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 3c:d9:2b:fb:42:d4 brd ff:ff:ff:ff:ff:ff
5: enp4s0f1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 3c:d9:2b:fb:42:d6 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::3ed9:2bff:fefb:42d6/64 scope link 
       valid_lft forever preferred_lft forever
6: enp7s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:21:5a:d3:31:6c brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.193/24 brd 192.168.2.255 scope global enp7s0
       valid_lft forever preferred_lft forever
    inet6 fe80::221:5aff:fed3:316c/64 scope link 
       valid_lft forever preferred_lft forever
7: bond0: <NO-CARRIER,BROADCAST,MULTICAST,MASTER,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 2a:9d:e4:51:c4:a5 brd ff:ff:ff:ff:ff:ff
    inet 169.254.10.162/16 brd 169.254.255.255 scope link bond0:avahi
       valid_lft forever preferred_lft forever
chad@DVR-ProLiant-DL360-G7:~$ sudo ifconfig sudo netplan apply
netplan: Unknown host
ifconfig: `--help' gives usage information.
chad@DVR-ProLiant-DL360-G7:~$ sudo netplan apply     
Invalid YAML at //etc/netplan/01-network-manager-all.yaml line 1 column 0: found character that cannot start any token
chad@DVR-ProLiant-DL360-G7:~$ 


this is all I have in the etc/network/interfaces

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



So if I whould start over from scratch, what should be in the etc/network/interfaces file if anything?

Next what should be in the /etc/netplan/01-network-manager-all.yaml and is this the correct location / file to be adding my configurations?

mode: balance-xor is the type of bond I will use.

I assume I am close but what else am I missing?  I have spend a week Googling and reading posts and info on Netplan and Bonding but just can't seem to get the right combination. 


Are there any good Forum posting anyone has found on other sites that tell step by step how to do what I want to do? I will be happy to wipe out and reload server with Ubuntu if needed to have a default configuration and start over clean.

Chad

---

