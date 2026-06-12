---
title: "Still totally stumped"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by jmitche1 on 2008-11-22
I have been trying for about a month now to set up my wireless on my hp dv2000 laptop. I have the broadcom and have gone through most (if not all) of the options on this forums and have been trying because I know how much of a pain it is to have repeats on a forum. I also have added wifi radar on my ubuntu (sorry as Im new to linux im not sure of the exact version, but it is the newest available) I really enjoy ubuntu and all the features it has but hate having to switch over to vista to use my wireless in classes. Anyone have any idea of what I am doing wrong?

1. I have set up my ip address and all the information on my modem, all passwords (though i must be doing this wrong?) and my wireless even shows up on "wifi radar"

2. I have qwest wireless

3. I'm probably not remembering everything you need to know to help me but anything would be great. 

I'm really trying not to give up but its getting quite frustrating. I want to be totally over to ubuntu by christmas but dont know if I will at all.

You guys are awesome by the way. Thanks for the help and even if you have any ideas of places I can take my lappy to set up the wireless please let me know. Thanks again!

---

### Post by prshah on 2008-11-22
> **jmitche1 said:**
> 
my hp dv2000 laptop. I have the broadcom 
 but hate having to switch over to vista to use my wireless in classes. Anyone have any idea of what I am doing wrong?


It's nice to see a post one-in-a-while that asks something nicely and intelligently. There are too many whiners about. It's also rare to see someone take the blame themselves rather than make Ubuntu / Linux the scapegoat.

Can you summarize what you have done till now?

Also please open a terminal (Applications-Accessories-Terminal) and post back the outputs from the following commands [indent]a) Is your wireless recognised? ```
iwconfig
```
b) Can you see your wireless router / modem?```
sudo iwlist `iwconfig 2> /dev/zero | grep ESSID | cut -f 1 -d " "` scan
``` (Note: if your iwconfig cannot find a card, then this command will fail with an error; you can safely ignore this command instead.)
c) Are you using fw-cutter, ndiswrapper or "dont-know"?
d) After connecting in Vista, can you open the "Command Prompt" and post back information related to your network```
ipconfig /all
```
e) Finally, can you post information about your network card```
lspci -v | grep -i -A 6 -B 2 "wireless\|broadcom"
```
[/indent]

Best of luck, I'm sure everyone here will help to get this working.

---

### Post by jmitche1 on 2008-11-22
Thank you so much for your response....
I havent had the best of luck with forums posting in the past but thanks again for all your help. I'm starting to get excited to get this working.

These are my results thus far:


a) Is your wireless recognised? 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

b) Can you see your wireless router / modem?

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:21:1E:54:06:A0
                    ESSID:"epicfail"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-23 dBm  Noise level:-24 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:18:3F:A0:DC:51
                    ESSID:"2WIRE600"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-16 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 2A:E9:F5:2A:1E:C2
                    ESSID:"Free Public WiFi"
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-13 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 04 - Address: 00:14:6C:98:01:92
                    ESSID:"BRUCH"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-56 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

c) Are you using fw-cutter, ndiswrapper or "dont-know"?
Sorry again I don't know. I am trying to read up on ubuntu because I love what I have so far and have a book that got excelent reviews on Amazon.com coming. As you can tell I'm motivated to move myself from vista.

(d) I will post this information when in another reply when I switch back to vista (unless I don't know how, I have to log off ubuntu)
	
e) Finally, can you post information about your network card

!!! Unknown header type 7f

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by Olivier2371 on 2008-11-22
I think you might find the following link of interest.

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Let me know if it helped.

---

### Post by jmitche1 on 2008-11-23
As nice as it is for you to provide me that link... Im still rather embarrassed that I'm not quite sure what to do. I'll look at it a little more put appreciate the help!

---

### Post by jmitche1 on 2008-11-23
In response to letter D) above:


Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\John Mitchell>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : JohnMitchell-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : 00-1D-72-40-CA-9D
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::1d96:ceb6:1264:6491%9(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.68(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, November 22, 2008 8:51:20 PM
   Lease Expires . . . . . . . . . . : Sunday, November 23, 2008 8:51:20 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 285220210
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadcom 802.11b/g WLAN
   Physical Address. . . . . . . . . : 00-1A-73-D6-65-FB
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d887:eab6:66ef:1f0b%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.67(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, November 22, 2008 8:51:22 PM
   Lease Expires . . . . . . . . . . : Sunday, November 23, 2008 8:51:22 PM
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 201333363
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:1c30:13aa:b455:a80c(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::1c30:13aa:b455:a80c%18(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{D332706D-537F-4F99-946F-848F5DB4F
117}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.0.68%15(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{51481980-D702-4438-96E0-DE5476F99
EEA}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.0.67%17(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Users\John Mitchell>

---

### Post by Olivier2371 on 2008-11-23
Where are you know?

---

### Post by jmitche1 on 2008-11-23
I'm still looking at the page you provided...
every time I try to run the commands in my terminal I get negative messages.
Any ideas?

---

### Post by Olivier2371 on 2008-11-23
Could you please give the detail on how you install ubuntu, as well as the version you are using.

---

### Post by jmitche1 on 2008-11-23
I am running Ubuntu 8.04 the hardy heron, I installed it in vista from the internet and have it dual booted with vista. Could this be my problem?

---

### Post by Olivier2371 on 2008-11-23
Do you mean that you have installed ubuntu like a software in vista, or do you have a different partition for ubuntu.

Also did you download the ISO file from internet then burnt it on a CD-Rom.

---

### Post by Ayuthia on 2008-11-23
It looks like you have a Broadcom 4312 rev 01 which most likely means that you have the 14e4:4315 chipset.  The range that shows in your scan reflects the wl (Broadcom STA) driver is beig used (The wl driver tends to show on a scale from 0 to 5 where the b43 shows from 0 to 100).  This module tends to have some problems with WEP for this chipset if I recall.  Is it possible to switch to WPA2 on your router?  If not, you might try ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If you go that route, feel free to post here again if you have problems.

If you are able to turn off the WEP encryption on your router, you can test and see if you connect.  This will help us see if the driver is having problems with WEP or if the driver is just having problems connecting.

---

### Post by Olivier2371 on 2008-11-23
Have you tried to use Broadcom B43 wireless driver instead of the STA driver.

And if you can use WPA/personal TKIP. Just make sure you apply the same encryption method on your router setup.

Normally ndiswrapper should be use as the last option. 
Further more the Broadcom 4312 doesn't need ndiswrapper.

What ever change you make be sure to reboot the machine.

---

### Post by Ayuthia on 2008-11-23
> **Olivier2371 said:**
> Have you tried to use Broadcom B43 wireless driver instead of the STA driver.

And if you can use WPA/personal TKIP. Just make sure you apply the same encryption method on your router setup.

Normally ndiswrapper should be use as the last option. 
Further more the Broadcom 4312 doesn't need ndiswrapper.

What ever change you make be sure to reboot the machine.

If this is the 4312 card with the 14e4:4315 chipset, the b43 driver does not support it.

---

### Post by Olivier2371 on 2008-11-23
Ayuthia,

Please read this page.

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

### Post by Ayuthia on 2008-11-23
> **Olivier2371 said:**
> Ayuthia,

Please read this page.

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

The 4312 rev 01 card was known under 8.04 as the Broadcom 4310.  However, the 4310 name was a USB device and the wireless card is not a USB device.  In 8.04.1, the card was updated to be listed as a 4312 card.  The easiest way to recognize this card is to see the chipset.  If you check lspci -nn, you will see the chipset.  If you see 14e4:4315 this is the card that can only use the wl driver or ndiswrapper.  The b43 driver does not support it because it as an LP PHY.  The developers have been working on reverse engineering the device and last I read, they were about to start on the specifications so the can do the programming for it.

---

### Post by Olivier2371 on 2008-11-23
Ayuthia,

Sorry about that you are correct, and thanks for the reminder.

---

