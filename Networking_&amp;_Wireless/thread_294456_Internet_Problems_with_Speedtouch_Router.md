---
title: "Internet Problems with Speedtouch Router"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by dbott67 on 2006-11-06
I received a PM from Sergey requesting some help with his Speedtouch modem/router.  Here's our conversation so far:

[QUOTE=sergeyVasilov]Can you help me please? Im new one in the Linux world and i just installed Kubuntu 6.06 and it cant connect to the internet. Actually i have asdl line(384 kbits) and a speedtouch router and when i boot the system with the default network setting this the last detects my hardware, which is eth0 and eth1 and there are unable,both. The problem is that i cant see an IP address when i go to the configuration network system so that means that the router cant send me an IP. I think the machine can not comunicate with the router (you think???). Anyway, this is the auto mode(dhcp). I did it with the manual mode and i cant give an IP that could be used by the system. By the way, at a moment my system connect me with internet but it was only one moment before and now i dont know how to do.
Can you help me? Please![/QUOTE]

[QUOTE=dbott67]

Can you send me the output of the following commands:
```
cat /etc/network/interfaces
```
```
cat /etc/resolv.conf
```
```
route -n
```

Thanks,
Dave[/QUOTE]

[QUOTE=sergeyVasilov]The output is:
```
 cat/etc/network/interfaces
-->auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider
```

for 
```
 cat etc/resolv.conf
```
there was no output

for 
```
 route -n
Kernel IP routing table
Destination  Gateway  Genmask  Flags Metric Ref UseIface
```[/QUOTE]

[QUOTE=dbott67]You can try the following commands to see if they help get you connected:
```
sudo ifup dsl-provider
```
followed by:
```
sudo dhclient dsl-provider
```

If this works, then you probably just need to add the following line to your /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**[COLOR="Red"]auto dsl-provider[/COLOR]**
iface dsl-provider inet ppp
provider dsl-provider
```

If it doens't work, Ill need more info.  What kind of setup do you have to connect to the internet?

1. Do you have a DSL/Cable Router (like a Linksys or D-link-type device) or is your DSL modem connected directly to your computer?

-Dave[/QUOTE]

[QUOTE=sergeyVasilov]Well i dont know exactly what is a dsl/cable but anyway i have my tel line and on it i have too adsl line, here in my house i have only a speedtouch router and then a cable connected to  
eth interface (eth0 or eth1). When i boot windowsxp i get connected automatically or i need to enable the interface witch i have connected to the router and everything is made auto. I have a new one pc (AMD athlon 64bit DualCore 3800+, nVidia 7300 256MB, 2x512DDRII RAM, motherboard MSI K9N SLI Platinum). I dont understand whats problem with that.[/QUOTE]

[QUOTE=dbott67]Hi Sergey,

I don't mind helping you at all, but I would recommend that you start a topic in the networking section.  Once you post there, send me a PM and we can continue the thread there.  This way, others will be able to offer help as well.

Now, to answer some of your questions:

The issue may be how your router is configured.  If the speedtouch router is only acting as a DSL modem, then your computer needs to run PPPoE software to connect to your ISP.  

If the speedtouch router is acting as a NAT router, then you need to enter your ISP settings into the router so that it can log on for you.

[LIST=1]
[*]What is the make & model of the speedtouch router?
[*]From Windows XP, can you post the output of **ipconfig -all**?
[/LIST]

Thanks,
Dave[/QUOTE]
[QUOTE=sergeyVasilov]```
 Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrator>ipconfig -all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : master-l
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : lan

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : lan
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-16-17-77-D4-E3
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.0.0.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.0.138
        DHCP Server . . . . . . . . . . . : 10.0.0.138
        DNS Servers . . . . . . . . . . . : 10.0.0.138
        Lease Obtained. . . . . . . . . . : &#916;&#949;&#965;&#964;&#941;&#961;&#945;, 6 &#925;&#959;&#949;&#956;&#946;&#961;&#943;&#959;&#965; 2006 10:46:11 &#956;
&#956;
        Lease Expires . . . . . . . . . . : &#932;&#961;&#943;&#964;&#951;, 7 &#925;&#959;&#949;&#956;&#946;&#961;&#943;&#959;&#965; 2006 12:46:11 &#960;&#956;

```
This is the output of ipconfig -all

Actually im not good at english and some word i dont understand so this why i cant be more clear. Thanks 
"My name is elvis and im from Albania"[/QUOTE]

Any help from forum members would be appreciated.

Thanks,
Dave

---

### Post by sergeyVasilov on 2006-11-07
What is my problem? any sugestion would be greatful

---

