---
title: "Networking help."
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Squeak2 on 2007-04-14
Ok, I am brand new to this whole scene so bear with me please. I am on 6.10 and I got to the Networking window.... I've been reading tutorials but they are really technical for me. so if I'm on a WMP54GS how would I find the info to fill in the stuff under eth1(my wireless connection.) Also do I need to fill in the DNS and Host stuff? If I do, how do I find that stuff?! XD Sorry for being a pain, but we all got to start somewhere right?! Thanks.

---

### Post by RaZer0r on 2007-04-14
the WMP54GS should have an automatic dhcp and dns server, so it should give you the right ip adresses rightaway...
if not, try the standard configurations..
dns gateway 192.168.01.1

the wireless key might be in hexadecimal system (it should be al 10 letter based key ( FA105TC5GA) of something else, dependant on your way to secure your router.
if you used wpa or wpa2 on a windows system i migth suggest you try to lower those settings to WEP (i know it's less secure, but for home use it is enough).
do you have a windows computer running at the same network? if so, you can find the manual input when you open comand prompt and enter ipconfig/all (you can allways copy paste the info here so i can help you out setting up your wireless

---

### Post by octoberdan on 2007-04-14
> **Squeak2 said:**
> Ok, I am brand new to this whole scene so bear with me please. I am on 6.10 and I got to the Networking window.... I've been reading tutorials but they are really technical for me. so if I'm on a WMP54GS how would I find the info to fill in the stuff under eth1(my wireless connection.) Also do I need to fill in the DNS and Host stuff? If I do, how do I find that stuff?! XD Sorry for being a pain, but we all got to start somewhere right?! Thanks.
Do you or have you had other computers on the network? How did you set them up? More information will help us help you. And if you have any questions along the way, don't hesitate to ask.

---

### Post by Squeak2 on 2007-04-14
Yes, I do have other comps in the network as well. I set them up by putting in the install disk and then putting in the card... ubuntu doesn't read my disks right which I know is normal for linux to do. but ya... so I'm pretty lost.

Someone needed the ipconfig /all? Here it is.
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : jared
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : VIA Compatable Fast Ethernet Adapter

        Physical Address. . . . . . . . . : 00-11-2F-D0-7F-AE

Ethernet adapter Linksys 1:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Linksys Wireless-G PCI Network Adapt
er with SpeedBooster
        Physical Address. . . . . . . . . : 00-16-B6-99-9F-83
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 207.69.188.185
                                            207.69.188.186
                                            207.69.188.187
        Lease Obtained. . . . . . . . . . : Saturday, April 14, 2007 3:59:07 PM
        Lease Expires . . . . . . . . . . : Sunday, April 15, 2007 3:59:07 PM

---

