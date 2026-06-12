---
title: "I can't seem to get a static IP setup."
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by grs on 2008-09-12
I can't seem to get Ubuntu to use a static IP. Currecntly /etc/network/interfaces looks like this, getting an Ip address from the DHCP (A Linksys router)

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# DHCP IP
 auto eth1
 iface eth1 inet dhcp


```

I have looked a few guides and they all tell me to try this to get a static IP:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Static IP
 iface eth1 inet static
 address 192.168.1.110
 network 255.255.255.0
 gateway 192.168.1.1
 nameserver 62.231.32.10
 nameserver 62.231.32.11
 nameserver 89.124.172.10


```

When the server starts up with the static code I tried I can see it says Fail whenn trying to startup interfaces.

---

### Post by Mr_Whippy on 2008-09-12
From reading your post you have two network cards installed, 

are you sure you are plugged into the right one, as i understand it, if you only have one network card you should be using eth0 not eth1.

may be worth confirmation on this though.

---

### Post by grs on 2008-09-12
I probable should say I'm using Ubuntu Server. I have two networks. One on the motherboard which Ubuntu doesn't seem to want use and one in a PCI slot which it can see and use.
I would have liked it to use the one on the motherboard as its a faster card.

---

### Post by caljohnsmith on 2008-09-12
I'm not sure, but I don't think you can set up your DNS nameserver in /etc/network/interfaces; the DNS nameserver info is usually stored in /etc/resolv.conf. Try this in your /etc/network/interfaces:
```
iface eth1 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
```
Notice also the "netmask" instead of "network".

---

### Post by grs on 2008-09-13
I didn't get anything with that.

Whats the nmap command for listing all the IP's connected to a network?

---

### Post by grs on 2008-09-16
???

---

### Post by Iowan on 2008-09-16
Is the **nmap** advice in [this]("http://ubuntuforums.org/showthread.php?p=5794650#post5794650")  thread what you need?

---

### Post by grs on 2008-09-17
Yes, I got nmap listing what I wanted.
I still can not get Ubuntu Server to create a static IP, can anyone help?

---

### Post by Iowan on 2008-09-17
Post current details: **ifconfig** and contents of **/etc/network/interfaces**.

---

### Post by grs on 2008-09-18
Below is the interfaces file:-

```


# The loopback network interface
auto lo
iface lo inet loopback

# DHCP on eth1 (PCI card)
 auto eth1
 iface eth1 inet dhcp


```

Below is the ifconfig read out:-

```

eth1      Link encap:Ethernet  HWaddr 00:c0:df:05:07:72
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:dfff:fe05:772/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17457 (17.0 KB)  TX bytes:47332 (46.2 KB)
          Interrupt:20 Base address:0xbc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)


```

---

### Post by grs on 2008-09-20
Are those readouts an help?
What do you get from ifconfig and the contents of /etc/network/interfaces?

---

### Post by Iowan on 2008-09-20
My results are similar... but this workstation is fine on DHCP.  My server (a Breezy machine) has following information.```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.9
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
~

```My Hardy LAMP server also gets address via DHCP - I'll change that... eventually (maybe to a static lease - just to see if it works).

---

### Post by anubhavrocks on 2008-09-20
Try using the gui
```
sudo network-admin
```

---

### Post by grs on 2008-09-20
When typed in

sudo network-admin

I got command not found, I guess the gui is not setup my system, how do I do that?

---

### Post by anubhavrocks on 2008-09-21
Oh i see,you have a server installation ;)

Please read this howto
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

---

### Post by grs on 2008-09-21
Yes, does that make a difference?

---

