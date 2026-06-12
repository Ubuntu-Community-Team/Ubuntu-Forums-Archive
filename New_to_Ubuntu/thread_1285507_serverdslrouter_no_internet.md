---
title: "server/dsl/router: no internet"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by VaMark on 2009-10-07
Hi,  I am beginner to Ubuntu and server machines. I hope for some help ( I'll do a full intro on my profile soon).
Here is the situation: I was given an HP DL360 server and I know it was doing an ethernet connection at work as simple as connect cat 5 to router and bingo I was on.
I brought the server home where I have Verizon DSL moder and Netgear router (both functional) but I can NOT get internet connectivity here. Is it some setup with Mac addressing which both the DSL modem and Wireless router have; I am just trying to do a direct ethernet connection to back of router (not wireless) but I get nothing. I have 9.04 for desktop. What could be the solution ( please.......)
Regards,
Mark

---

### Post by ermeyers on 2009-10-07
It is an unfortunate fact in this world that ISP's like Verizon/Comcast/Etc. will not support Linux users.  You need to have established the initial DSL service install with Windows and Verizon's Windows SW, then you can glean the network configuration information off of the Windows machine, using Run ipconfig /all.  I have Verizon DSL and a 9.04 Desktop.  I have two Dell dual-boot computers that work whatever the OS XP/Ubuntu is on each.

My DSL link is DHCP, so whatever your eth? is, set it up for DHCP.  You also have the GNOME Network Manager program involved, because you installed the Desktop version of Ubuntu.  To bypass the Network Manager, you can edit /etc/network/interfaces directly, otherwise Network Manager will control Auto eth? for your desktop session.

On my main computer connected to the DSL, eth0 is my LAN and eth1_rename is my WAN/Internet connection:

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 192.168.0.1
   netmask 255.255.255.0
   network 192.168.0.0
   broadcast 192.168.0.255

auto eth1_rename
iface eth1_rename inet dhcp

```

Verizon's gateway and DNS server is 192.168.1.1.  Modem brand is Westell.

/etc/resolv.conf:
```

domain westell.com
search westell.com
nameserver 192.168.1.1

```

---

### Post by VaMark on 2009-10-08
Thanks for the advice! I will try that out over the weekend when I get some free time.
~Mark~

---

