---
title: "Total Beginner Having NIC/Web Trouble"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by emilyrides on 2007-03-05
Hello Ubuntinites...I had to bother you with a question, but I'm really stuck, and I've spent two entire days trying to solve my problems through the online faqs, documentation and searching posts here, all to no avail. Here's the basic outline of my problem...

A few day ago I decided to jump into Linux whole hog, and I downloaded Ubuntu version 6.10 and installed it on my desktop machine (I formatted the whole drive, there is no 'Other' operating system). Everything went perfectly during the installation, except when I opened Firefox, I realized that I have no internet connection at all.  After doing some searching, I think the problem is related to the fact that I am using an an AMD/Nvidia Motherboard that has a built in NIC. I'll give a list of all the relevant info I know with the hopes someone can help me along:

Nforce2 Ethernet Controller (built in to Motherboard) Device Type:80203
AMD Athlon XP @ 2.16ghz Chipset: NVIDIA nForce2 IGP
Linksys WRT54GS Wireless Router
RCA DCM315 Digital Cable Modem

I'm certain that the modem and router are functioning correctly because I am able to connect via wireless with my Macbook.

I have tried connecting my Ubuntu box to the router via the port on the back of the router to the NIC on the box. Under System/Admin/Networking - I see the card as Wired Connection (eth0), and under properties I have 'Enable This Connection' checked and under Configuration:Automatic Configuration DHCP.  With these setting I still am not able to get any web signal at all.
I also tried switching the 'Configuration' to manual and plugging in my IP address and Subnet mask, but still no luck.

Next, I tried to connect the modem to my computer directly via USB, and the modem shows up in System/Admin/Newtworking as ETH1, but there is no signal.

The NIC shows up in the Device Manager as 'nForce 2 Ethernet Card', and when the modem is connected via USB is appears in the Device Manager as DCM245 Cable Modem.

That's basically all the info I have, and all the things I've tried to get it to work. I'd be very happy to use either the modem via usb or the router via an ethernet cable, whichever I can get to work.  

Thanks in advance for your help, I'm really stuck and I'm dying try out Ubuntu, it seems great from the little I've seen so far. Cheers!

---

### Post by Floppyjoe on 2007-03-05
When connected to the router via ethernet cable did you try to enter this command into the terminal?
```
sudo dhclient eth0
```
To open a terminal click on Applications/Accessories/Terminal

---

### Post by emilyrides on 2007-03-06
Thanks for the reply, I just tried that, and I get:

Listening on LPF/eth0/00:48:ca:6d:9b:a1
Sending on LPF/eth0/00:48:ca:6d:9b:a1
Sending On Socket/Fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

NO DHCPOFFERS received
No Working leases in persistent database - sleeping


Then I tried to see if there was any connection, but still nothing!
I'm really hoping to get this working, I've heard too many good things about Ubuntu to not get this going.  Anything else I should try, or methods to explore?  I really appreciate any help, Thanks in advance.

---

