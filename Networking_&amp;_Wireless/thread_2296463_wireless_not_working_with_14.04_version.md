---
title: "wireless not working with 14.04 version"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by sivakrishna2 on 2015-09-26
Hi,

am new to Ubuntu and i have an issues with wifi connectivity in my laptop. I am unable to see wireless SSID's which are enabled. i am using my laptop at home and i have router in my home which is working fine with mobiles and other laptops.

My laptop model: dell insp n4010
i am getting notification : attached screenshot

Thanks,
-Siva

---

### Post by grahammechanical on 2015-09-26
The network discovery service is there to identify another computers on the network. Those other computers would include the servers of our Internet Service Provider. I see that message when Network manager connects to the router before the router has established conncetion to the ISP. It does not stop me from accessing the Internet once the router has established the connection.

Of more concern is your statement that you are unbled to see wireless SSID's. That could indicate that the wireless adapter is

1) switched off in hardware
2) not enabled in software
3) does not have a driver installed.

Is this a new installation? Is networking enabled? Is WiFi enabled? Is there another OS on the computer and is WiFi disabled in that OS to save battery power? If you have Windows on that machine and you switch off WiFi to save battery power, then when you load Ubuntu the WiFi adpater will still be switched off. There should also be a key sequence  to switch the WiFi adapter On & Off. Make sure that it is set to On.

Regards.

---

### Post by sivakrishna2 on 2015-09-26
[ 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"): Thanks for the reply. its a new installation.. i don't have dual boot on it... i am using only Ubuntu 14.04..I am not sure wifi enabled or not..due to am not new to ubuntu i am not sure wifi enabled or not.. but i have gone through some threads in ubuntu and verified most of the possible debugging steps but still i am failed to see wifi network along with my ethernet network.

I went to system settings -> software updates -> Additional Drivers -> I have noticed that "No Drivers are available" information displayed to me.

Please guide me further steps to fix my issue.

Thanks,
-Shivv

---

### Post by sivakrishna2 on 2015-09-26
I tried this :

command: sudo lshw -C network

Response:
*-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:6f:5e:66
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.145 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f0400000-f043ffff ioport:2000(size=128)
siva@siva-Inspiron-N4010:~$ ^C

---

