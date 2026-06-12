---
title: "I cannot connect to the internet!"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by Seldoms on 2006-08-17
I am using a DSL modem directly connected to my PC via an ethernet cord. I am a COMPLETE linux newbie.

When I click on my DSL CONNECTION thing in Windows I get the following stats:

Device Name: WAN Miniport (PPPoE)
Device Type: PPPoE
Server Type: PPP
Transports: TCP/IP
Authentication: PAP
Compression: (None)
PPP Multilink Framing: Off
Server IP Adress: 64.252.119.254
Client IP Adress: 64.252.114.212

In the Windows Command Prompt if I type IP Config i get the following info:

Windows IP Configuration 

Ethernet Adapter Local Area Connection

Connection Specific DNS Suffix  . :
Autoconfiguration IP Adress: 169.254.28.245
Subnet Mask: 255.255.0.0
Default Gateway: 

PPP Adapter DSL Connection

Connection Specific DNS Suffix . :
IP Adress: 64.252.114.212
Subnet Mask: 255.255.255.255
Default Gateway: 64.252.114.212

When I log onto Windows my internet is not automatically connected. I have to click on DSL CONNECTION and type in a username and password, and click Connect.

In Ubuntu, I got Problem Loading Page error on every online page.

I do not know whether to try and connect through eth0 or the pppo 
option. Or, if I need to manually make a new one. I am running DSL Elite Speed. It is not dial up, I can use the telephone will online.

Please help me get online in Ubuntu.

---

### Post by coffeecat on 2006-08-17
What make and model of modem is it? From the way you describe having to click on 'DSL connection' to connect in Windows it sounds as though you would have had to install a driver for it in Windows. And looking at your assigned IP address it doesn't sound like a modem/router. It may be some sort of Winmodem and if that is the case it won't work out of the box in Linux and you may or may not be able to get it working in Linux. I may be wrong but without details of the hardware I can't comment further.

Let's see what this modem is first, but here's a thought for you. If you had a dsl ethernet modem/router instead, you'de be able to configure it via a web-interface in either Windows or Linux and use it to connect to the internet without any extra drivers in the OS. Advantages would be a built-in firewall, NAT and the ability to connect more computers to it to share your dsl connection. If you don't want/need wireless, adsl modem/routers are not particularly expensive.

---

### Post by Seldoms on 2006-08-17
I have a Speedstream 5100 modem. It is connected to the pc via an ethernet cable. On the back of my modem it says 'Ethernet ADSL Modem'.

---

### Post by coffeecat on 2006-08-17
I have no experience of this modem, but I did a quick search on Google Linux and came up with one page which said,

> The SpeedStream 5100 DSL Modem works with any Ethernet equipped PC, regardless of operating system.

so it ought to work in Linux. Let's go back one step. Have you checked in System > Administration > Networking? What is that showing? Do you need to configure something there?

---

