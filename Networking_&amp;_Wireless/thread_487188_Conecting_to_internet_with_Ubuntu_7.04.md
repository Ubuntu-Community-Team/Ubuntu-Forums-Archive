---
title: "Conecting to internet with Ubuntu 7.04"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by edward233 on 2007-06-28
Hi 
Im new to Ubuntu I just installed Ubuntu 7.04 every thing install fine except I cant connect to the internet
My network adapter is a
Intel(R) Pro/100 VE Network Connextion and I have a D-Link ASDL Ethernet Modem
Ubuntu say that I have a wired connection but I cant get on  the internt

PS I do have Highspeed and run a dule operating system Ubuntu and Windos Vist Home Primiume.

HEEEEElp I want to get rid of windows.

Ed :(

---

### Post by GeeZor on 2007-06-29
Well, to start off you are on the right track.. 
get rid of windows.

next,

open a console and get your ip-information ```
 ifconfig -all 
```

Try pinging your own ip,
try pining your default gateway
try pinging you DNS servers
check how your DSL modem has been set up.
maybe you need to add your ISP's DNS servers locally on you machine. If you Modem has these servers as DNS servers, try setting you modem as an DNS server (so put the default gateway as your first DNS server.) 
If your done editing you networkcard configuration be sure to do a 
```
ifdown eth0
ifup eth0
```
to restart your network. (assuming your networkcard in question is the eth0 card.) you can find this out using ```
dmesg |grep eth
```

Please post the results of you pinging actions and (if possible) you LAN configuration and WAN configuration of you modem. Please be sure NOT to post you public IP adres for security reasons. We dont need that to solve this issue.

---

### Post by edward233 on 2007-06-30
> **GeeZor said:**
> Well, to start off you are on the right track.. 
get rid of windows.

next,

open a console and get your ip-information ```
 ifconfig -all 
```

Try pinging your own ip,
try pining your default gateway
try pinging you DNS servers
check how your DSL modem has been set up.
maybe you need to add your ISP's DNS servers locally on you machine. If you Modem has these servers as DNS servers, try setting you modem as an DNS server (so put the default gateway as your first DNS server.) 
If your done editing you networkcard configuration be sure to do a 
```
ifdown eth0
ifup eth0
```
to restart your network. (assuming your networkcard in question is the eth0 card.) you can find this out using ```
dmesg |grep eth
```

Please post the results of you pinging actions and (if possible) you LAN configuration and WAN configuration of you modem. Please be sure NOT to post you public IP adres for security reasons. We dont need that to solve this issue.
Hi I think this is what your looking for
like i said im new to ubuntu.

eth0      Link encap:Ethernet  HWaddr 00:16:76:0B:56:50  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1380812 (1.3 MiB)  TX bytes:37897 (37.0 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:16:76:0B:56:50  
          inet addr:             Bcast:169.254.255.255                         Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:            Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:157290 (153.6 KiB)  TX bytes:157290 (153.6 KiB)


Ed

---

### Post by GeeZor on 2007-06-30
Dear ED,

as you can see you indeed have a wired connection but no valid IP adres:
> 
eth0:avah Link encap:Ethernet HWaddr 00:16:76:0B:56:50
inet addr: Bcast:***169.254.255.255*** Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1


To fix this (And eventually get rid of that nasty evil windows!!!) we are gonna set you up..

We need to know wheter you can use DHCP to obtain an IP automatically or if we need to set it up by hand.. (which is okay, but we need to know your specific settings. )

Since you can still use windows i suggest booting into windows and open an DOS box. In the DOS box type ```
 ipconfig/all
```
write down the **bold** items:
(mine looks like this in dutch)
Windows IP-configuratie

Ethernet-adapter LAN-verbinding 5:
        Verbindingsspec. DNS-achtervoegsel:
        Beschrijving . . . . . . . . . . .:
          Realtek RTL8139 Family PCI Fast Ethernet NIC #2
        Fysiek adres. . . . . . . . . . . : 00-08-A1-83-6F-A8
  **      DHCP ingeschakeld:. . . . . . . . : nee**
**        IP-adres. . . . . . . . . . . . . : 192.168.2.201**
 **       Subnetmasker. . . . . . . . . . . : 255.255.255.0**
**        Standaardgateway. . . . . . . . . : 192.168.2.200**
**        DNS-servers . . . . . . . . . . . : 212.142.28.68**
**                                             62.179.104.196**
        NetBIOS over TCPIP. . . . . . . . : uitgeschakeld


Assuming your windows can get to the internet the settings you find there should work. 
On Ubuntu go to System, Administration, Network and add the settings you found on Windows. That should be enough to get you online...
(and read this forum from you Linux powered system :)  )
Let me know how things work out!

---

### Post by edward233 on 2007-07-01
Hi
I tried what You sujested but sill no luck.  I seem to remember that The last release or maybe the one before that that ubuntu dind not support my modem or lan card????

any way here is what i get when i do a ipconfig/all

C:\Users\Edward>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Upstares-Pc
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

PPP adapter Nrtco:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Nrtco
   Physical Address. . . . . . . . . :
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 66.79.231.173(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 216.168.96.10
                                       216.168.96.13
   NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
   Physical Address. . . . . . . . . : 00-16-76-0B-56-50
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::291c:8d3c:9192:8453%8(Preferred)
   Autoconfiguration IPv4 Address. . : 169.254.132.83(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 201332342
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled


Thanks for your help
Ed

---

### Post by splintercellguy on 2007-07-01
Looks like you have a static IP address. Enter that information and disable DHCP.

---

### Post by GeeZor on 2007-07-01
listen to splintercellguy. He is right...
all that is left is to determine what your DNS servers should be.. 

do an nslookup on you Windows and one of the addresses should be listed there...

oh, and you want to disable Ip.v6 also.. just in case...

---

### Post by envis on 2008-06-08
i have the exact same problem than this guy.. its strange i installed ubuntu 7.04 a few days ago on a adm64 and my internet was automatically working.. but then i had a problem while trying to upgrade to ubuntu 8 because of my KVM switch (sometimes freezes computers...) and then i reinstalled ubuntu 7.04 from scratch cos it was not booting anymore (reformatted and all..)

but this time, the internet wont work.. though its the same computer, same install CD...

what is strange is that i have that avahi eth which i never noticed before and my eth0 only has ipv6 address, instead its that avahi that has the ipv4 address and its 169.x.x.x. i cant seem to edit the setting of that eth0:Avahi cos it tells me it doesnt exist when i click edit!

i tried writing sudo ifconfig eth0 192.168.0.103 and
sudo ifconfig eth0 192.168.0.199 (just to try a new lease)
and when i do that, the avahi eth disapears and the eth0 starts showing ipv4 set to the proper ip (in ifconfig) but still i cant get my routers page at 192.168.0.1 or i cant get any website either... so since i cant get my router, i dont think my problem is DNS...

i really cant figure it out.... also roaming is not activated on my eth0

should i just try re-installing again and cross my fingers that the internet works on that install?

i cant figure out why it doesnt work now and it was working fine at my first install... it was only like 5 days ago.. i was using a different ISP (on same DSL modem) actually but i dont see how that could change anything the computer is behind a switch connected on a router...

anyways... just asking that cos it seems im not the first one to get that problem...

in the past i remember ubuntu 6.04 on my adm64 required me to pull out the power AC plug for 30 seconds after installation to make ETH work.. i tried that though this time and it changed nothing...

actually you know what... i just tried pulling out the AC plug again but for longer this time... plus i turned on and off the I/O switch a few times... then booted again and now it works!!...

so i guess that was just that for me...

id dont know if you have tried that edward233

if your computer is a amd64 and your ETH is onboard ETH on a NVIDIA motherboard like me. its possible that all you need to do is disconnect the computer from the electricity for lets say, 60 seconds.. then reboot and your internet will work!... well it did it for me and my problem was looking exactly like yours...

---

