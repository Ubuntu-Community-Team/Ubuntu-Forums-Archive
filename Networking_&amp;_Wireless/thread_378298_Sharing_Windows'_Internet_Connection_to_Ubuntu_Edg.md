---
title: "Sharing Windows' Internet Connection to Ubuntu Edgy Server"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by bryo21 on 2007-03-07
Hi Guys,

Sorry I created another post regarding internet sharing. I can't find any threads similar to my situation right now. I know there are already threads but I can't find it. I will appreciate if someone could give the link of threads. Anyways, here's my problem.

As of now, I'm using Windows to connect to internet because my only resource to connect is by using a NOKIA N70 cellphone as a modem. If I will have a dsl/cable connection then that's the time I will set my ubuntu server to connect to the internet.

What I need now is to share my windows internet connection to my ubuntu server so that I can update my Ubuntu Server and install programs from the repositories. I can ping both machines(windows to ubuntu and vise versa). I am using Putty in Windows to access my ubuntu server remotely.
 
My Ubuntu is a fresh install following steps from this [link]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10"). Following this steps will not install LAMP due to the author want to install just the important ones.

Here's my /etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

Here's my /etc/hosts
```
127.0.0.1       localhost.localdomain    localhost
192.168.0.100   dclnx01.sample.com       dclnx01

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Please help me guys, thanks in advance.:) 

~Bryan

---

