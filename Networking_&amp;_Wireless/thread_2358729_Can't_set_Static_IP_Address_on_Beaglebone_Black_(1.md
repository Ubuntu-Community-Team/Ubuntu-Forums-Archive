---
title: "Can't set Static IP Address on Beaglebone Black (16.04.2)"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by dwfunk4475 on 2017-04-16
This old thread did not resolve my issue:  [https://ubuntuforums.org/showthread.php?t=2288300&highlight=beaglebone+black](https://ubuntuforums.org/showthread.php?t=2288300&highlight=beaglebone+black)
Bug fix did not resolve my issue:  [http://bugs.elinux.org/issues/91](http://bugs.elinux.org/issues/91)

Ubuntu 16.04.2 LTS installed, used BBB-eMMC-flasher-ubuntu-16.04.2-console-armhf-2017-04-07-2gb.img to flash my emmc.

Can not set a static IP.  Keeps getting a dhcp IP from somewhere. WHERE???

/etc/network/interfaces has:

iface eth0 inet static
address 192.168.0.41
netmask 255.255.255.0
gateway 192.168.0.1

all usb0 lines have been commented out.

What am I missing?


-david

---

### Post by chili555 on 2017-04-16
> What am I missing?At least two things and maybe three!

First, verify that your interface is actually eth0:```
ifconfig
```Next, you haven't any 'auto' declaration. That means that you will start the interface from the command line if and when it's needed. Did you?

Next, you need DNS.

Did you verify that 192.168.0.41 is outside the range used in the router for DHCP?

I recommend that you amend the file to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.41
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
```Reboot.

---

### Post by dwfunk4475 on 2017-04-23
> **chili555 said:**
> At least two things and maybe three!

First, verify that your interface is actually eth0:```
ifconfig
```Next, you haven't any 'auto' declaration. That means that you will start the interface from the command line if and when it's needed. Did you?

Next, you need DNS.

Did you verify that 192.168.0.41 is outside the range used in the router for DHCP?

I recommend that you amend the file to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.41
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
```Reboot.


file does have the auto declaration, didn't post entire contents, but here's what's in there:

```
ubuntu@node1:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.41
    netmask 255.255.255.0
    gateway 192.168.0.1
    dns-search google.com
    dns-nameservers 8.8.8.8 8.8.4.4


# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE

ubuntu@node1:~$


```


The static IP assigned is not used by the DHCP server and is not used anywhere on the network.  

The BBB gets an IP from the DHCP server of 192.168.0.16. But where is there a DHCP declaration in this image?

I even tried commenting out everything:

 ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet static
#    address 192.168.0.41
#    netmask 255.255.255.0
#    gateway 192.168.0.1
#    dns-search google.com
#    dns-nameservers 8.8.8.8 8.8.4.4

# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE


```
should have come up with NO IP address of any kind, but again it got a DHCP IP of 192.168.0.16.

In addition, without any declaration, usb1 is present:

```
ubuntu@node1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d0:39:72:37:b9:be
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2601:2c3:8400:76c0:d239:72ff:fe37:b9be/64 Scope:Global
          inet6 addr: fe80::d239:72ff:fe37:b9be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST DYNAMIC  MTU:1500  Metric:1
          RX packets:1547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:184234 (184.2 KB)  TX bytes:91472 (91.4 KB)
          Interrupt:181

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)

usb1      Link encap:Ethernet  HWaddr d0:39:72:37:b9:c3
          inet addr:192.168.6.2  Bcast:192.168.6.3  Mask:255.255.255.252
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@node1:~$
```


Somethings broke? My interface file works as expected in 12.04 . . .


Any thoughts, ideas??


-david


Ubuntu 16.04.2 LTS (GNU/Linux 4.4.59-ti-r96 armv7l)

---

### Post by chili555 on 2017-04-23
> file does have the auto declaration, didn't post entire contentsHow can we possibly help you when you give us some but not all of the information?> Keeps getting a dhcp IP from somewhere. WHERE???
Either Network Manager or Wicd. Are either running? If so, you are far better off to set your static IP address there.

---

### Post by dwfunk4475 on 2017-04-24
> Either Network Manager or Wicd. Are either running? If so, you are far better off to set your static IP address there.

Neither one is installed:

```
ubuntu@node1:~$ apt-cache policy wicd
wicd:
  Installed: (none)
  Candidate: 1.7.4+tb2-1
  Version table:
     1.7.4+tb2-1 500
        500 http://ports.ubuntu.com/ubuntu-ports xenial/universe armhf Packages
ubuntu@node1:~$

ubuntu@node1:~$ apt-cache policy network-manager
network-manager:
  Installed: (none)
  Candidate: 1.2.6-0ubuntu0.16.04.1
  Version table:
     1.2.6-0ubuntu0.16.04.1 500
        500 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main armhf Packages
     1.1.93-0ubuntu4 500
        500 http://ports.ubuntu.com/ubuntu-ports xenial/main armhf Packages
ubuntu@node1:~$


```



-david

---

