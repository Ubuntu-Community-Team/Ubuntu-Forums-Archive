---
title: "Static IP with DHCP on Alias - same interface"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by lipinski on 2008-09-12
I'm trying to configure an Alias interface on Ubuntu 8.04.  

I have a single physical interface on my system, recognized as eth0.  This interface has and needs a static IP Address.  

I would like to add a second IP Address to this interface by assigning an alias, i.e., eth0:0.  The problem that I'm running into is that I would like the IP Address assigned to that Alias to be dynamically assigned by my DHCP Server.

For some reason, this does not work.  I get the following errors when the alias interface is attempted to be brought up with DHCP:
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth0:0

sniffing on the interface with Wireshark, I notice that no DHCP requests are sent at all.

Any ideas?

---

### Post by cdtech on 2008-09-12
If your eth0 IP is say 192.168.1.20 and you would like to create an alias eth0:0 with IP 192.168.1.21. Use the following command:

**sudo ifconfig eth0:0 192.168.1.21 up**

To set DHCP, edit:
**sudo gedit /etc/network/interfaces**
and add:
[B]auto eth0:0
iface eth0:0 inet dhcp[/B]

---

### Post by lipinski on 2008-09-12
> **cdtech said:**
> If your eth0 IP is say 192.168.1.20 and you would like to create an alias eth0:0 with IP 192.168.1.21. Use the following command:

**sudo ifconfig eth0:0 192.168.1.21 up**
[COLOR="Blue"]This works perfectly.  Unfortunately, I don't want a static IP on the alias interface...[/COLOR]

To set DHCP, edit:
**sudo gedit /etc/network/interfaces**
and add:
[B]auto eth0:0
iface eth0:0 inet dhcp[/B]
[COLOR="Blue"]This does not work.  When I attempt to bring up the alias interface (via ifup eth0:0 or /etc/init.d/networking restart), I get the error:
```
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth0:0.
```[/COLOR]

So, the problem seems to be related to using DHCP on the alias interface.

---

### Post by cdtech on 2008-09-12
Did you verify that the alias is up and running? Use following commands:
ifconfig
ping 192.168.1.21

---

### Post by lipinski on 2008-09-12
> **cdtech said:**
> Did you verify that the alias is up and running? Use following commands:
ifconfig
ping 192.168.1.21

Yes - I checked.  The alias interface is brought up and the IP ping-able when assigned manually (static).
However, when attempting to use DHCP, the interface is not up, and cannot be ping-ed.

Also, I checked with Wireshark, and there is no DHCP broadcast sent when attempting to being up the alias interface with DHCP.

---

### Post by cdtech on 2008-09-12
Ok, that's about the most I can help with. Sorry......

---

### Post by caljohnsmith on 2008-09-12
I've never messed with setting up an aliased interface, so this is just an idea that will only take a few seconds to try:
```
sudo dhclient eth0:0
```

---

### Post by lipinski on 2008-09-12
> **caljohnsmith said:**
> I've never messed with setting up an aliased interface, so this is just an idea that will only take a few seconds to try:
```
sudo dhclient eth0:0
```

Same errors unfortunately.

After googling around, I found this thread:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773)

It seems that the 
```
SIOCSIFFLAGS: Cannot assign requested address
```
Errors may be related to some wireless tools and could possibly be unrelated.

Towards the end of the thread some users have been having the same problem.  I haven't attempted downgrading my packages yet, but that may be the next step.

---

### Post by tmetro on 2009-03-31
> **lipinski said:**
> 
After googling around, I found this thread:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773)


Although related, I believe that bug is for a separate issue, and I've created [Bug #351378]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/351378") for research and workarounds of the problem where DHCP can't be used with virtual interfaces.

 -Tom

---

