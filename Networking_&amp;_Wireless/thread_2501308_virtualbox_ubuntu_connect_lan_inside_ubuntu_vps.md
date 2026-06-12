---
title: "virtualbox ubuntu connect lan inside ubuntu vps"
date: 2024-10-01
forum: Networking &amp; Wireless
---

### Post by rastinrastini on 2024-10-01
have vps with ip 172.16.22.92 and vm inside this vps and want to have  ip 172.16.22.101. vm is virtualbox vm and os of both are ubuntu. why  can not see vm from lan or can not see gateway from vm? ping gateway  from vm get destination host unreachable. ping gateway from vps is  correct and get connect.
 ========================output of following command on vps. command is: vboxmanage showvminfo kmaster |grep "NIC"
```
  
NIC 1:                       MAC: 0800274602EE, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
NIC 1 Settings:  MTU: 0, Socket (send: 64, receive: 64), TCP Window (send:64, receive: 64)
NIC 1 Rule(0):   name = tcp22321, protocol = tcp, host ip = , host port = 22321, guest ip = , guest port = 22
NIC 2:                       MAC: 080027E52C22, Attachment: Bridged Interface 'ens160', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none

```


 ========================on vm inside vps:  command is: ip a


```
  

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000                                                                                      link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00                                                                                                                        inet 127.0.0.1/8 scope host lo                                                                                                                                                  valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:46:02:ee brd ff:ff:ff:ff:ff:ff
    altname enp0s3
    inet 10.0.2.15/24 metric 100 brd 10.0.2.255 scope global dynamic eth0
       valid_lft 70043sec preferred_lft 70043sec
    inet6 fe80::a00:27ff:fe46:2ee/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:e5:2c:22 brd ff:ff:ff:ff:ff:ff
    altname enp0s8
    inet 172.16.22.101/24 brd 172.16.22.255 scope global eth1
        valid_lft forever preferred_lft forever    inet6 fe80::a00:27ff:fee5:2c22/64 scope link
       valid_lft forever preferred_lft forever




```


 ========================output of following file on vm inside vps: file is: /etc/netplan/50-vagrant.yaml


 [HR][/HR] ```


---
network:
  version: 2
  renderer: networkd
  ethernets:
    eth1:
      addresses:
      - 172.16.22.101/24
      routes:
        - to: 0.0.0.0/0
          via: 172.16.22.1


```


 ========================: output of following command on vps command is: ip a

```


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:50:56:a3:1c:76 brd ff:ff:ff:ff:ff:ff
    altname enp3s0
    inet 172.16.22.92/24 metric 100 brd 172.16.22.255 scope global dynamic ens160
       valid_lft 1221031sec preferred_lft 1221031sec
    inet6 fe80::250:56ff:fea3:1c76/64 scope link
       valid_lft forever preferred_lft forever
3: vboxnet0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 172.42.42.1/24 brd 172.42.42.255 scope global vboxnet0
       valid_lft forever preferred_lft forever
    inet6 fe80::800:27ff:fe00:0/64 scope link
       valid_lft forever preferred_lft forever


```

---

### Post by TheFu on 2024-10-01
a) when posting terminal stuff, please, please, please, use forum code-tags.  That's in the "Advanced Editor" with the '#' button.  Too hard to read the wall of text you've posted.

b) Ensure you have set the VM settings to use a "bridged" network, not NAT, not host-only, not internal-only.  The virtujalbox manual can explain more.  [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by rastinrastini on 2024-10-01
Thanks. i corrected code tags. NIC 2 in first code tag show Bridged  Interface 'ens160'.
in last code tag, enp0s8 inet 172.16.22.101/24 brd show bridge inside vm.

what is wrong here?

---

### Post by TheFu on 2024-10-01
If the VM config is setup for bridged, then inside the OS, you just need to set the normal static IP and routing correctly.

docker is known to screw networking, so I'd remove everything docker did to get it working, then add it back, slowly, testing constantly to see where docker borked it.  I don't use docker, sorry.  I use lxc for my linux container needs.

---

### Post by rastinrastini on 2024-10-01
oh sorry. i told wrong. my problem is with virtualbox created with  vagrant. nic1 and nic2 are for vm created. last code tag is for vm ip a  command.

---

### Post by TheFu on 2024-10-01
Is the VPS running on dedicated equipment for your use?  Normally, a VPS from a cloud provider comes with 1 public IP, so you cannot just grab other IPs as you like.  OTOH, doing nested virtualization is something I've only played with over a decade ago, just to see it work when it was new.
Typically, I use KVM/QEMU with libvirt on the physical server, then create VMs and connect them to either a standard Linux bridge or use PCIe passthru for exclusive access of a NIC on the LAN.  If I need something like lxc I'll either run that on the physical system or inside a full VM with a few other, related, Linux Containers.  There would be only 1 bridged (available outside) IP address. All the others would be internal to that VM - like a DB container or some non-front-end services.

I've never used vagrant either.  I remember seeing it used, but for my needs it seemed overly complex for my snowflake systems. Sorry.

---

### Post by rastinrastini on 2024-10-01
vps is on our esxi cloud

---

