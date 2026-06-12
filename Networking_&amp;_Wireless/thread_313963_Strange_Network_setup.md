---
title: "Strange Network setup"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by racertj5 on 2006-12-06
Ok, so I am a new Ubuntu user with network problems. I just took an old Compaq and upgraded some of the parts. I set it up in my room and installed Ubuntu on it. I now want to add it to my network. Here is my setup. In my Living room there is a linksys wireless router with a few computers hardwired into it that are in various rooms of my house. In my room I have a Desktop computer running windows XP with a linksys wireless card in it. I am on the network and share the internet and shared files with all the other computers in my house. I just put this ubuntu computer in. I added a netgear network card to both the old compaq and the regular windows xp computer in my room. I have a netgear fast ethernet switch. Is there a way to connect theese 2 computers with the switch and still allow both to be on the network and use the internet nor do I have to go out and purchase a crossover cable. If there is a way to make this work please tell me how.

---

### Post by dbott67 on 2006-12-06
You'll need to enable ICS ([Internet Connection Sharing]("http://support.microsoft.com/kb/306126")) in XP.

The wireless interface will be your "internet connection" (WAN side) and your wired card will be the LAN side.

Connect the both computers to the switch, and then in the configure the Ubuntu computer to be on the same subnet as your XP ICS lan.

WARNING: Be sure to use a different private subnet for your Ubuntu and XP connection sharing.  If you don't know what this means, please post the current IP address of your Windows XP computer (or the internal IP of your wireless access point).

---

### Post by racertj5 on 2006-12-06
In Windows Xp I went into wireless network connection status.
IP Adress 192.168.1.106

---

### Post by racertj5 on 2006-12-06
I also need to know how to configure ubuntu correctly please sorry to be a pain.

---

### Post by racertj5 on 2006-12-07
come on please I got it connected and everything works on xp computer I just cant get ubuntu to connect

---

### Post by dbott67 on 2006-12-07
In Windows XP, can you please post the output of **ipconfig /all**?
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\WINDOWS>**ipconfig /all**

Windows IP Configuration

        Host Name . . . . . . . . . . . . : omega-xp
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-15-C5-0C-AD-ZZ

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-16-CE-31-88-ZZ
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.105
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Saturday, December 02, 2006 3:25:06
PM
        Lease Expires . . . . . . . . . . : Saturday, December 09, 2006 3:25:06
PM

C:\WINDOWS>
```

This should show both network interfaces: your wireless (which is 192.168.1.106) and the wired (which is what I need to know).

Ubuntu will need to be configured with a static IP address on the same subnet as the wired interface (192.168.0.1 possibly --- the MS KB article indicates that this is the default address).

If this is the case, you'll need to configure Ubuntu with the following settings:

IP Address: 192.168.0.2
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1 <-- this is the IP of the Windows XP computer running ICS

You can set the IP by clicking SYSTEM > ADMINISTRATION > NETWORKING (see attached screenshots).

-Dave

---

### Post by dbott67 on 2006-12-07
After configuring Ubuntu, please print the output of **cat /etc/network/interfaces**.  The output should like like this, assuming the IP addresses given in my example are the same:
```
dbott@edgy:~$ **cat /etc/network/interfaces**
auto lo
iface lo inet loopback

[COLOR="Red"]auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1[/COLOR]

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by racertj5 on 2006-12-07
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Tim>ipconfig/all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : tims-computer
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : Yes
        DNS Suffix Search List. . . . . . : hsd1.nj.comcast.net.

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NETGEAR FA311 Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-A0-CC-79-30-76
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Wireless Network Connection 2:

        Connection-specific DNS Suffix  . : hsd1.nj.comcast.net.
        Description . . . . . . . . . . . : Linksys Wireless-G PCI Network Adapt
er with SpeedBooster
        Physical Address. . . . . . . . . : 00-12-17-65-94-F4
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.106
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 68.87.64.146
                                            68.87.75.194
        Lease Obtained. . . . . . . . . . : Thursday, December 07, 2006 6:26:01
AM
        Lease Expires . . . . . . . . . . : Friday, December 08, 2006 6:26:01 AM


C:\Documents and Settings\Tim>

---

### Post by racertj5 on 2006-12-07
Thats the log now what do i do?

---

### Post by dbott67 on 2006-12-07
Did you set the IP on the Ubuntu computer like I described in post 6:
> IP Address: 192.168.0.2
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1 <-- this is the IP of the Windows XP computer running ICS

You can set the IP by clicking SYSTEM > ADMINISTRATION > NETWORKING (see attached screenshots).



If so, try pinging the XP computer from Ubuntu:
```
ping 192.168.0.1
```
Let me know if you get a response.

-Dave

---

### Post by racertj5 on 2006-12-07
I pinged from ubuntu packets sent 12 packets recieved 0 packet loss 100%.   Is there somthing I am overlooking?

---

### Post by racertj5 on 2006-12-07
ok I am fed upwith this so I am going to try an experiment. I will run xp on the other computer and see if it connects this way I will know whether its ubuntu or my setup itself

---

### Post by dbott67 on 2006-12-07
> **racertj5 said:**
> ok I am fed upwith this so I am going to try an experiment. I will run xp on the other computer and see if it connects this way I will know whether its ubuntu or my setup itself

This is a good idea.. it helps isolate the trouble.

A few things:

1. Have you set a static IP in Ubuntu to 192.168.0.2?
2. Can you post the output of **cat /etc/network/interfaces**.
3. Can you post the output of **route -n**

-Dave

---

### Post by racertj5 on 2006-12-07
Turns out it's not ubuntu.  I cant get it to connect n windows either.  Sorry for wasting your time I guess I will just have to get a crossover cable.

---

