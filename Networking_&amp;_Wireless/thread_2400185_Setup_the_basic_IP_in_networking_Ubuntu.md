---
title: "Setup the basic IP in networking Ubuntu"
date: 2018-09-03
forum: Networking &amp; Wireless
---

### Post by sed_faster on 2018-09-03
hello folks,

I am trying do a basic configuration on Ubuntu but I can't get this done. My system is:
```

$ uname -a
Linux qw 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

```

I configure this file just like this (I think it is this file to configure):
```

$ cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp0s25

iface lo inet static
address 192.168.1.52
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8

```

But after reboot entire system, because this commands don't works:
```

$ /etc/init.d/networking restart
-bash: /etc/init.d/networking: No such file or directory
qw@qw:~$ sudo service networking restart
Failed to restart networking.service: Unit networking.service not found.

```

After reboot I can't connection from this machine and I have this output through command "ifconfig":
```

$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 196  bytes 14539 (14.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 196  bytes 14539 (14.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

I need disable all configuration which I put on file interfaces and reboot entire system to get this IP:
```

$ ifconfig
enp0s25: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.104  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6795:8c49:1091:4b04  prefixlen 64  scopeid 0x20<link>
        ether f4:ce:46:12:f0:f7  txqueuelen 1000  (Ethernet)
        RX packets 1505  bytes 777732 (777.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1015  bytes 116170 (116.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  memory 0xf0500000-f0520000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 196  bytes 14539 (14.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 196  bytes 14539 (14.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

What am I doing wrong?
Thanks

---

### Post by wildmanne39 on 2018-09-03
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by steeldriver on 2018-09-03
EDIT:

Oops I just noticed your version information (18.04) - AFAIK that uses netplan rather than /etc/network/interfaces

---

### Post by sed_faster on 2018-09-03
I should put 
```

iface enp0s25 inet static

```
I was do this and the problems it is the same!

---

### Post by TheFu on 2018-09-03
/etc/network/interfaces isn't used anymore.  You have to use netplan, as steeldriver said above.
There are examples: [https://netplan.io/examples](https://netplan.io/examples)

Start and stop of all services changed to systemd (systemctl) a few years ago.  init.d/ is deprecated, so don't expect that to work correctly.  Running commands from 10.04 and expecting them to work on 18.04 won't get results.  There are lots of guides for systemd [https://www.tecmint.com/manage-services-using-systemd-and-systemctl-in-linux/](https://www.tecmint.com/manage-services-using-systemd-and-systemctl-in-linux/) is one.  I find some things easier with systemd controls and others harder.  The error reporting kinda sucks,  but seeing startup errors/warnings using journalctl **is** one of the easier things that systemd brought.

---

### Post by chili555 on 2018-09-03
I advise against using netplan in a desktop environment. By default, it points to Network Manager. You can set a static IP in NM easily, so why reinvent the wheel. Could we unravel NM and revise netplan and change 3-4 other files? Probably, but why? It is dead simple in NM.

[http://3.bp.blogspot.com/-zXKEt3vxNg4/T58h-Cm1HJI/AAAAAAAAAjs/uOC0tCLcS4w/s1600/ScreenHunter_02%2BApr.%2B30%2B16.37.gif](http://3.bp.blogspot.com/-zXKEt3vxNg4/T58h-Cm1HJI/AAAAAAAAAjs/uOC0tCLcS4w/s1600/ScreenHunter_02%2BApr.%2B30%2B16.37.gif)

Please revert your flawed entries in /etc/network/interfaces to the default:```
auto lo
iface lo inet loopback
```

---

### Post by sed_faster on 2018-09-03
Hello,

I intend learn configure this through terminal because I need learn how do this.
I revert /etc/network/interfaces to the default and execute this commands:
```

sudo nano /etc/netplan/01-network-manager-all.yaml

On the file I put this commands/configurations:
network:
version: 2
renderer: networkd
ethernets:
enp0s25:
dhcp4: no
dhcp6: no
addresses: [192.168.1.41/24]
gateway4: 192.168.1.1
nameservers:
addresses: [8.8.8.8,8.8.4.4]


```
But when I try put this sh*** peace of code to run I received the error message:
```

$ sudo netplan apply
Error in network definition //etc/netplan/01-network-manager-all.yaml line 1 column 8: expected mapping

$ sudo netplan --debug generate
DEBUG:command generate: running ['/lib/netplan/generate']
** (generate:1637): DEBUG: 01:43:45.579: Processing input file //etc/netplan/01-network-manager-all.yaml..
** (generate:1637): DEBUG: 01:43:45.579: starting new processing pass
Error in network definition //etc/netplan/01-network-manager-all.yaml line 1 column 8: expected mapping

```

I can't put the exactly tabs on commands and when I tried I receive many message error.
Now I lost "board" network, because when I did sudo ifconfig I receive this:
```

$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 129  bytes 8997 (8.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 129  bytes 8997 (8.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
I haven't networking on this machine.

What I am doing wrong?
Thanks

[UPDATE1]
If I do "sudo ifconfig -a" I got this:
```

$ ifconfig
enp0s25: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.104  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6795:8c49:1091:4b04  prefixlen 64  scopeid 0x20<link>
        ether f4:ce:46:12:f0:f7  txqueuelen 1000  (Ethernet)
        RX packets 2824  bytes 241767 (241.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2152  bytes 295936 (295.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  memory 0xf0500000-f0520000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 129  bytes 8997 (8.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 129  bytes 8997 (8.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
But I haven't communication through network card with outside networking...

---

### Post by chili555 on 2018-09-04
> I can't put the exactly tabs on commands They are specifically not tabs; they are spaces. Netplan is very strict about spacing and indentation. Like most of Linux, if it isn't exact, it won't work at all.

Please try:```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      addresses: [192.168.1.41/24]
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8,8.8.4.4]
```Followed by:```
sudo netplan generate
sudo netplan apply
```

---

### Post by sed_faster on 2018-09-04
> **chili555 said:**
> They are specifically not tabs; they are spaces. Netplan is very strict about spacing and indentation. Like most of Linux, if it isn't exact, it won't work at all.

Please try:```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      addresses: [192.168.1.41/24]
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8,8.8.4.4]
```Followed by:```
sudo netplan generate
sudo netplan apply
```

This means which I should use space to indentation all parameters? For exempl, this is correct:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s25:
      addresses: [192.168.1.41/24]
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8,8.8.4.4]

```
but this it is wrong? (I missed a space before parameter name network card enp0s25:
```

network:
  version: 2
  renderer: networkd
  ethernets:
   enp0s25:
      addresses: [192.168.1.41/24]
      gateway4: 192.168.1.1
      nameservers:
          addresses: [8.8.8.8,8.8.4.4]

```

Thanks

---

### Post by sed_faster on 2018-09-04
I rewrite the file about netplan and I can configure the network on my computer.
Later I will try miss up all file *.yaml to see which modification and spacing I can put on this file.

Thanks

---

### Post by TheFu on 2018-09-04
There is a specification for all yaml files.  They are like human-readable XML.
Perhaps nano isn't the best editor choice if you are trying to learn to manage servers with a shell. I've never seen nano on any router, for example.  vi/vim are always there.

---

### Post by sed_faster on 2018-09-04
Thumb up TheFu. I will chance the editor text, but first I need learn more about Vi or Vim.
Thanks to advice

---

