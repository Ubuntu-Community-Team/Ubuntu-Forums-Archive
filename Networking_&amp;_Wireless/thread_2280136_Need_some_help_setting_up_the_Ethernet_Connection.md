---
title: "Need some help setting up the Ethernet Connection"
date: 2015-05-28
forum: Networking &amp; Wireless
---

### Post by Steve_Cline on 2015-05-28
[SIZE=2][FONT=arial]I just installed 14.04 and have no Ethernet connection

result from:  [/FONT][/SIZE][SIZE=2][FONT=arial]sudo lshw* &#8236;-C network

*  &#8236;*-network*               
       description:* &#8236;Ethernet interface
*       &#8236;product:* &#8236;NetLink BCM5784M Gigabit Ethernet PCIe
*       &#8236;vendor:* &#8236;Broadcom Corporation
*       &#8236;physical id:* &#8236;0
*       &#8236;bus info:* &#8236;pci*@&#8236;0000:02:00.0
*       &#8236;logical name:* &#8236;eth0
*       &#8236;version:* &#8236;10
*       &#8236;serial:* &#8236;00:23:ae:a7:0b:37
*       &#8236;size:* &#8236;100Mbit/s
*       &#8236;capacity:* &#8236;1Gbit/s
*       &#8236;width:* &#8236;64* &#8236;bits
*       &#8236;clock:* &#8236;33MHz
*       &#8236;capabilities:* &#8236;pm vpd msi pciexpress bus_master cap_list ethernet physical tp* &#8236;10bt* &#8236;10bt-fd* &#8236;100bt* &#8236;100bt-fd* &#8236;1000bt* &#8236;1000bt-fd autonegotiation
*       &#8236;configuration:* &#8236;autonegotiation=on broadcast=yes driver=tg3* &#8236;driverversion*=&#8236;3.134* &#8236;duplex=full firmware=sb v2.19* &#8236;latency*=&#8236;0* &#8236;link=yes multicast=yes port=twisted pair speed*=&#8236;100Mbit/s
*       &#8236;resources:* &#8236;irq:44* &#8236;memory:dfbf0000-dfbfffff

result from: ifconfig

eth0*    &#8236;Link encap:Ethernet*  &#8236;HWaddr* &#8236;00:23:ae:a7:0b:37*  
          inet6* &#8236;addr:* &#8236;fe80::223:aeff:fea7:b37/64* &#8236;Scope:Link
*          &#8236;UP BROADCAST RUNNING MULTICAST*  &#8236;MTU:1500*  &#8236;Metric:1
*          &#8236;RX packets:670529* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;frame:2
*          &#8236;TX packets:25139* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;carrier:0
*          &#8236;collisions:0* &#8236;txqueuelen:1000* 
          RX bytes:45408377* (&#8236;45.4* &#8236;MB*)  &#8236;TX bytes:4895284* (&#8236;4.8* &#8236;MB*)
          Interrupt:16* 

lo*        &#8236;Link encap:Local Loopback*  
          inet addr:127.0.0.1*  &#8236;Mask:255.0.0.0
*          &#8236;inet6* &#8236;addr:* &#8236;::1/128* &#8236;Scope:Host
*          &#8236;UP LOOPBACK RUNNING*  &#8236;MTU:65536*  &#8236;Metric:1
*          &#8236;RX packets:62413* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;frame:0
*          &#8236;TX packets:62413* &#8236;errors:0* &#8236;dropped:0* &#8236;overruns:0* &#8236;carrier:0
*          &#8236;collisions:0* &#8236;txqueuelen:0* 
          RX bytes:5160183* (&#8236;5.1* &#8236;MB*)  &#8236;TX bytes:5160183* (&#8236;5.1* &#8236;MB*)

[/FONT][/SIZE][SIZE=2][FONT=arial]I am not sure how to proceed from this.  Any guidance is greatly appreciated.
[/FONT][/SIZE]

---

### Post by oldfred on 2015-05-28
What are you connecting to?

Normally if a router with DHCP, it just connects automatically.

Screen shot is from my old router, but typical. Routers usually are 192.168.0.1 or similar or 10.0.0.1 or similar. 

And what does Network Connections show?

---

### Post by Steve_Cline on 2015-05-28
I am not sure where to look to answer that question.  I have a cable modem.  From that I have a switch splitting to a netgear router (which is working fine) and the computer running Ubuntu.

---

### Post by oldfred on 2015-05-28
Is switch a newer one and addressable or just a old switch.
And can you ping modem, is modem issuing DHCP addresses?

When you installed was it on line?
Or did live installer work with Ethernet automatically?

What does this show? Maybe nothing if not connected? But if live installer connects run it again.
route -n

And this:
lspci

---

### Post by Steve_Cline on 2015-05-28
Not sure if the it is addressable or not.  It is about a year old - Linksys ES1500

[COLOR=#000000]And can you ping modem, is modem issuing DHCP addresses?[/COLOR]
Not sure how to do that.

route -n results
Kernal IP routing table
Destination   Gateway     Genmask     Flags Metric Ref     Use Iface

lspci results
00:00.0* &#8236;Host bridge:* &#8236;Intel Corporation* &#8236;82G33/G31/P35/P31* &#8236;Express DRAM Controller* (&#8236;rev* &#8236;0a*)
00:01.0* &#8236;PCI bridge:* &#8236;Intel Corporation* &#8236;82G33/G31/P35/P31* &#8236;Express PCI Express Root Port* (&#8236;rev* &#8236;0a*)
00:02.0* &#8236;VGA compatible controller:* &#8236;Intel Corporation* &#8236;82G33/G31* &#8236;Express Integrated Graphics Controller* (&#8236;rev* &#8236;0a*)
00:02.1* &#8236;Display controller:* &#8236;Intel Corporation* &#8236;82G33/G31* &#8236;Express Integrated Graphics Controller* (&#8236;rev* &#8236;0a*)
00:1b.0* &#8236;Audio device:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family High Definition Audio Controller* (&#8236;rev* &#8236;01*)
00:1c.0* &#8236;PCI bridge:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family PCI Express Port* &#8236;1* (&#8236;rev* &#8236;01*)
00:1d.0* &#8236;USB controller:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family USB UHCI Controller* &#8236;#1* (&#8236;rev* &#8236;01*)
00:1d.1* &#8236;USB controller:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family USB UHCI Controller* &#8236;#2* (&#8236;rev* &#8236;01*)
00:1d.2* &#8236;USB controller:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family USB UHCI Controller* &#8236;#3* (&#8236;rev* &#8236;01*)
00:1d.3* &#8236;USB controller:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family USB UHCI Controller* &#8236;#4* (&#8236;rev* &#8236;01*)
00:1d.7* &#8236;USB controller:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family USB2* &#8236;EHCI Controller* (&#8236;rev* &#8236;01*)
00:1e.0* &#8236;PCI bridge:* &#8236;Intel Corporation* &#8236;82801* &#8236;PCI Bridge* (&#8236;rev e1*)
00:1f.0* &#8236;ISA bridge:* &#8236;Intel Corporation* &#8236;82801GB/GR* (&#8236;ICH7* &#8236;Family*) &#8236;LPC Interface Bridge* (&#8236;rev* &#8236;01*)
00:1f.1* &#8236;IDE interface:* &#8236;Intel Corporation* &#8236;82801G* (&#8236;ICH7* &#8236;Family*) &#8236;IDE Controller* (&#8236;rev* &#8236;01*)
00:1f.2* &#8236;IDE interface:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family SATA Controller* [&#8236;IDE mode*] (&#8236;rev* &#8236;01*)
00:1f.3* &#8236;SMBus:* &#8236;Intel Corporation NM10/ICH7* &#8236;Family SMBus Controller* (&#8236;rev* &#8236;01*)
02:00.0* &#8236;Ethernet controller:* &#8236;Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe* (&#8236;rev* &#8236;10*)


[COLOR=#000000]

[/COLOR]

---

### Post by Steve_Cline on 2015-05-28
Also, it was not online when I installed the OS.  It was plugged in but had not internet access.

---

### Post by oldfred on 2015-05-28
Does live installer work with Internet?

Now older, so I would think it works, but not familar with all the various chips. 
Someone that knows more details will have to chime in.

[http://askubuntu.com/questions/189223/wireless-disabled-even-though-the-direct-connectin-thru-modem-is-working-fine](http://askubuntu.com/questions/189223/wireless-disabled-even-though-the-direct-connectin-thru-modem-is-working-fine)

---

### Post by Steve_Cline on 2015-05-28
That link appears to be in reference to a wireless connection issue which I do not have.

---

### Post by Steve_Cline on 2015-05-28
Maybe this will help out as well.  I have another computer running Ubuntu in the house (actually Xubuntu) so I turned off the wifi and tried to plug it in to the same network connection as the one in this post.  It did not work either.  As mentioned earlier, I have a switch that splits my connection from the modem to the computer in question and a Netgear router.  I plugged the Xubuntu laptop into the router and the wired connection worked.  I cannot physically move the other computer to the router but I am thinking I have an issue with the specific connection from the switch.  I happened to have an Airport Express, which I have not really used much but I plugged it in to the modem and then to the computer.  It now has an ethernet connection but I cannot access the internet.  

Does this help?

---

### Post by Steve_Cline on 2015-05-28
bump

---

### Post by oldfred on 2015-05-29
If you are connecting directly to the switch and modem is not serving addresses, but router is giving the DHCP addresses, then you cannot connect directly to switch. 
You may be able to disconnect router and use the one address the modem has to connect directly to Internet.

Before I had a router that was both wi-fi & 4 ports, I had to connect directly to Internet provider. And when switching computers they knew it was a different computer and it took 20 minutes to connect. But once I got router, that one address was always the same, so it connected and served internal addresses to all my other devices.

I would think you need modem, router, switch as the order of connections.

---

