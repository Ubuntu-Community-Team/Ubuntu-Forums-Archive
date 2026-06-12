---
title: "Trouble inserting a network bridge"
date: 2023-05-16
forum: Networking &amp; Wireless
---

### Post by jusp on 2023-05-16
I would appreciate some help or tips creating a bridge device on a machine that I am using. Here is the situation. 

The contents of /etc/netplan/99-netcfg-vmware.yaml are encountered as follows:

network:
  version: 2
  renderer: networkd
  ethernets:
    ens192:
      dhcp4: no
      dhcp6: no
      addresses:
        - 10.184.88.63/23
      gateway4: 10.184.88.1
      nameservers:
        search:
          - company.com
        addresses:
          - 10.10.10.53
          - 10.10.10.54

Resulting in 

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens192: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:50:56:be:79:52 brd ff:ff:ff:ff:ff:ff
    altname enp11s0
    inet 10.184.88.63/23 brd 10.184.89.255 scope global ens192
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:febe:7952/64 scope link 
       valid_lft forever preferred_lft forever



I modified this as follows:

network:
  version: 2
  renderer: networkd
  ethernets:
    ens192: [I][B]{}
  bridges:
    br0:[/B][/I]
      dhcp4: no
      dhcp6: no
      addresses:
        - 10.184.88.63/23
      gateway4: 10.184.88.1
      nameservers:
        search:
          - company.com
        addresses:
          - 10.10.10.53
          - 10.10.10.54
[I][B]      interfaces:
      - ens192
[/B][/I]
Which gives me after reboot:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens192: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:50:56:be:79:52 brd ff:ff:ff:ff:ff:ff
    altname enp11s0
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether fe:84:2b:31:34:06 brd ff:ff:ff:ff:ff:ff
    inet 10.184.88.63/23 brd 10.184.89.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::fc84:2bff:fe31:3406/64 scope link 
       valid_lft forever preferred_lft forever

$ ip route show dev br0
default via 10.184.88.1 proto static 
10.184.88.0/23 proto kernel scope link src 10.184.88.63 

$ ip route get 10.0.0.3
10.0.0.3 via 10.184.88.1 dev br0 src 10.184.88.63 uid 0 
    cache 

$ bridge link
2: ens192: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 master br0 state forwarding priority 32 cost 2 


This output looks to be what I wanted, except that the machine loses its network connection, and I am no longer able to log in to it.
This machine is a VM to which I only have ssh access, and I went into some trouble creating a cron job that restores the original 99-netcfg-vmware.yam, 
then executes the above commands while saving their output, then reboots.
I am in no way a networking expert. What could I be doing wrong here?

---

### Post by aljames2 on 2023-05-16
Code tags on your yaml file will help with reading it, plus these files can be tricky & not work without proper spacing.

mine looks something like this:
```

[COLOR=#000000]network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [eno1]
      addresses: [192.168.10.247/24]
      # gateway4 is deprecated, use routes instead
      routes:
      - to: default
        via: 192.168.10.1
        metric: 100
        on-link: true
      mtu: 1500
      nameservers:
        addresses: [192.168.10.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no[/COLOR]
```[COLOR=#000000]

I use KVM as my hypervisor not vmware, so not sure if the problem may be on the hypervisor end.  However, if your YAML file is configured correctly, everything should just work.

It may be worth asking, are you running Ubuntu Server or Desktop?  If desktop, then what have you done about Network Manager running in the background?[/COLOR]

---

### Post by jusp on 2023-05-16
Not sure, and not sure how to tell but it probably is a server. But since all I did was splitting the ethernet definition, any problem related to Network Manager should already have been there, right?
The indentation was lost when copy/pasting the text into this thread; however, the yaml files seem to be properly indented.

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy

---

### Post by aljames2 on 2023-05-16
It appears your bridge is there.  When you installed your VM did you select the bridge (br0) as the network interface for the VM?

Ubuntu Server does not boot up to a desktop environment by default.  Only if you later installed a DE on top of your Server installtion would you ever see a desktop environment.  Ubuntu Server uses netplan (YAML files for configuration), and Ubuntu Desktop uses NetworkManager by default.  NM can be used to customize your networking either via the Desktop GUI, or by using nmcli at the command line.  You do not use both networkd & NetworkManager.

what do you get when you run:
```
ls /etc/netplan/ -l
```

How about when you run:
```
nmcli d
```

Note: when posting results of your commands, please use code tags so the output is formatting is preserved like it would appear in your command line.

---

### Post by jusp on 2023-05-17
I had to install package netmanager for command nmcli. Before that, 99-netcfg-vmware.yaml was the only file in /etc/netplan. After installation of netmanager, a new 00-default-nm-renderer.yaml showed up with no effective contents:

> DEVICE  TYPE      STATE      CONNECTION 
ens192  ethernet  unmanaged  --         
lo      loopback  unmanaged  --         
$ ls /etc/netplan/ -l
total 8
-rw-r--r-- 1 root root  36 May 17 04:07 00-default-nm-renderer.yaml
-rw-r--r-- 1 root root 432 May 16 22:20 99-netcfg-vmware.yaml
$ cat /etc/netplan/00-default-nm-renderer.yaml
network:
  renderer: NetworkManager


---

### Post by aljames2 on 2023-05-17
I should have been clearer.  I wasn’t trying to get you to install network-manager, but instead to determine if you were running network manager or not.  nmcli commands do not exist on Ubuntu Server unless you install network-manager, which is not recommended on Ubuntu Server.

When a bridge is set up correctly, you should be able to assign the (br0) interface to the VM.  This allows you to ssh into the vm and makes the vm visible on the network. Perhaps the bridge setup is not your problem since you indicate you are able to access at times before it drops.  Others may be able to offer you some further help.

---

