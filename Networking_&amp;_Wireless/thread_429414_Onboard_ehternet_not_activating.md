---
title: "Onboard ehternet not activating"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by War1910 on 2007-05-01
I am using Ubuntu 7.04 and have installed from the DVD (amd64).  The first time I installed the network and everything else worked fine - it updated and I found it to be really cool being able to just 'get' things (first time linux user - can't you tell)

The problem is, after the second or third reboot, the network no longer activates - the network card is found (it is listed under hardware) and I have set the IP address and everything same as under Windows XP (DNS, Subnet and so on), but this isn't helping when the light on the hub showing a link doesn't light..

anything that I can do? I've been trying to get this to work for 2 days.... (if you can keep them n00bish, I'm still learning here)

Thanks

---

### Post by chili555 on 2007-05-01
Let's take a look at:```
cat /etc/network/interfaces
```Let's see if we can tweak it a bit.

---

### Post by War1910 on 2007-05-01
the interfaces file has:

```
auto lo
iface lo inet loopback

iface eth0 inet static

^G ^w
address 192.168.1.248
netmask 255.255.255.0
gateway 192.168.1.254
```

---

### Post by netztier on 2007-05-01
> **War1910 said:**
> I am using Ubuntu 7.04 and have installed from the DVD (amd64).  The first time I installed the network and everything else worked fine - it updated and I found it to be really cool being able to just 'get' things (first time linux user - can't you tell)

The problem is, after the second or third reboot, the network no longer activates - the network card is found (it is listed under hardware) and I have set the IP address and everything same as under Windows XP (DNS, Subnet and so on), but this isn't helping when the light on the hub showing a link doesn't light..

anything that I can do? I've been trying to get this to work for 2 days.... (if you can keep them n00bish, I'm still learning here)

Thanks

What kind of hardware do you have? What brand is the mainboard (or the computer), which chipset does it have (if you know, then let us know), which Ethernet Chip is being used?

Some of these answers can be found with the outputs of **lspci**, **lsmod** and **dmesg | grep eth**.

best regards

Marc


PS: I'm aiming at the "noapic" option needed for the kernel... my Shuttle Barebone with it's nVdia nForce3 chipset and the Marvell Yukon Gigabit Chip (running with the *skge* module) still needs it. Without it, everything seems fine, all modules loaded etc - but not a single bit will go out to the wire :-(. Ever since 5.10 it was like this, up to and including 7.04.

---

### Post by chili555 on 2007-05-01
```
auto lo
iface lo inet loopback

iface eth0 inet static

^G ^w
address 192.168.1.248
netmask 255.255.255.0
gateway 192.168.1.254
```I have no idea what  '^G ^w' is; is it a typo?

If you want your ethernet to start automatically, I'd *sudo gedit /etc/network/interfaces* to this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.248
netmask 255.255.255.0
gateway 192.168.1.254
```Reboot and let us know.

---

### Post by thorby on 2007-05-01
> The problem is, after the second or third reboot, the network no longer activates Is there a small "network" icon at the top of the screen? (two overlapped monitors) Click it and select Wired Network from the dropdown menu. This is the "Network Manager applet" and it seems to have a hard time remembering to open a wired connection as expressed in several other threads here.

If no icon, try the command **sudo dhclient** which also works to open the wired network for some.

---

### Post by War1910 on 2007-05-02
I changed the interfaces file to:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.248
netmask 255.255.255.0
gateway 192.168.1.254
```

still no good - I don't get a link light on the switch.

> Is there a small "network" icon at the top of the screen? (two overlapped monitors) Click it and select Wired Network from the dropdown menu. This is the "Network Manager applet" and it seems to have a hard time remembering to open a wired connection as expressed in several other threads here.

i have the icon on the top right.  left clicking and selecting manual selection shows me the wired connection (that's how I set up the IP  etc)

deselected, and waited for a minute then selected it again.

Still no go.

I have a ABIT 939SLI-eSATA2 motherboard with an onboard realtek gigabit network card (realtek RTL8168 )

I dual boot Windows XP professional and ubuntu.

Like I said - when i first installed it about 3 days ago the network was running fine - i was able to install the video card using the ubuntu wiki and was looking forward to playing around.  it just stopped later in the same day and hasn't come back...

I have rei-installed (and discovered that ubuntu remembers the settings you had) formatted and reinstalled - which is where I'm up to now.  

> sudo dhclient

did that - the result is:

```
Internet Systems Consortium DHCP Client v3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:8f:9f:26:f4
Sending on LPF/eth0/00:13:8f:9f:26:f4
Sending on socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by netztier on 2007-05-03
> **netztier said:**
> PS: I'm aiming at the "noapic" option needed for the kernel... my Shuttle Barebone with it's nVdia nForce3 chipset and the Marvell Yukon Gigabit Chip (running with the *skge* module) still needs it. Without it, everything seems fine, all modules loaded etc - but not a single bit will go out to the wire :-(. Ever since 5.10 it was like this, up to and including 7.04.

It turned out that the noapic kernel option is no longer needed if I set the APIC function from "Auto" to "Disable" in the BIOS.

Have you checked if the BIOS of your computer has such a configuration option?

best regards

Marc

---

### Post by chili555 on 2007-05-03
War1910-

Could we see the result of```
route -n
```Thanks.

---

### Post by War1910 on 2007-05-04
> **chili555 said:**
> War1910-

Could we see the result of```
route -n
```Thanks.

```
root@warlock-desktop:/home/warlock# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

---

