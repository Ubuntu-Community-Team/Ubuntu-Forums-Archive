---
title: "Step by step help needed. US Robotics Ext"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by zapjb on 2007-05-17
OK hi all. I'm new, please be patient with me.

My current hardware config is:  

Processor  
1.85 gigahertz AMD Athlon XP
64 kilobyte primary memory cache
512 kilobyte secondary memory cache   

HDS722540VLAT20 [Hard drive] (41.17 GB) -- C

BENQ DVD DD DW1650 [CD-ROM drive] -- E
JLMS XJ-HD166S [CD-ROM drive] -- D
3.5" format removeable media [Floppy drive] -- A

Main Circuit Board
Board: ASUSTeK Computer INC. A7NVM400 Rev 2.xx
Bus Clock: 166 megahertz
BIOS: American Megatrends Inc. 1.00 11/25/2003

Memory Modules
992 Megabytes Installed Memory
Slot 'DIMM0' has 512 MB (serial number SerNum0)
Slot 'DIMM1' has 512 MB

I have 2 modems.
An internal Broadxent V.92 PCI DI3631-1 [Modem]. 
And a U.S. ROBOTICS COURIER EXTERNAL 56K V.EVERYTHING MODEM. It's a serial connection.




I searched here, there & the web. I can't find clear, concise & easy instructions on how to use my U.S. ROBOTICS COURIER EXTERNAL 56K V.EVERYTHING MODEM with ubuntu 7.04.

Everything is incomprehensible to this Linux n00b. I get the the same headache after a few seconds trying to follow any Linux instructions. That I did working on my 1st OS win98se. Please help me.

I need basic you click on this, enter that etc., etc. instructions.

Preferably with step by step pictures. This is ridiculous. I feel retarded with Linux.

I want to dump windows. But I can't. I'm very knowledgeable in xp. I have never been able to connect to the internet with Linux! I went so far as to try to configure my winmodem - IMPOSSIBLE. So I bought a very highly reguarded external US Robotics modem, known to work with Linux. Got it to work in xp. Had to search & found an install .inf for XP on a U.S. Robotics site for my modem. 

I currently have Ubuntu 7.04 installed on a spare HDD. And I have NO yes NO clue how to connect to my dialup ISP with my US Robotics external serial modem & Ubuntu 7.04.

Please help. And let me join the club. I will then help others. Thanks.

---

### Post by zapjb on 2007-05-17
Wheres the love?

---

### Post by jrlii on 2007-05-17
The Courier on a serial connection should just work: Go into System:Adminsitration:Networking and disable the wired connection and setup dialup networking. That'll be a lot like Windows.

I'd be more specific, but the Networking control panel is a bit different on Feisty than it was on Dapper.

---

### Post by zapjb on 2007-05-18
Well I called my ISP. They allow Linux connections. So got that out of the way.

Can't connect, 2-4 seconds. Then disconnect. Tried everything very frustrating.

So help still appreciated. Thanks.

---

### Post by NJC on 2007-05-18
I was able to get that modem working properly in Dapper FWIW. Have you checked out this:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6)

Establishing a dialup connection was a very messy and teeth-gnashing process ... it appears most of the dev work has gone into broadband installations (and fair enough). 

A few pts about the process I had:

- serial modem easily recognized. 
- needed to configure wvdial
- once wvdial working, installed Gnome-PPP (Great program, works well).

---

### Post by zapjb on 2007-05-18
My ppp logs (tail /var/log/messages) right after a disconnect:
I get 5 lines of code. 
MAY 18 05:34 ComputerName pppd[5376]:pppd 2.4.4 started by UserName, uid1000
MAY 18 05:34 ComputerName pppd[5376]:Using interface ppp0
MAY 18 05:34 ComputerName pppd[5376]:Connect:ppp0 < -- > /dev/tty50
MAY 18 05:34 ComputerName pppd[5376]:Connection terminated.
MAY 18 05:35 ComputerName pppd[5376]:Exit.

---

### Post by jrlii on 2007-05-20
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=391956](http://ubuntuforums.org/showthread.php?t=391956) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This turns out to be a persistent problem with Edgy and Feisty, and it hasn't made it very high up the developer's priority list yet. (Better Wi-Fi support seems to be their main priority.)

See the link below for details.

So, is there a way to re-install the Dapper Network Manager and freeze it, without going through the pain of re-installing Dapper?

---

### Post by zapjb on 2007-05-20
That Ubuntu forum discussion linked was revolting. Like M$ without the $$$.

:(

---

### Post by Bartender on 2007-05-20
zap -
Do some checking on KPPP.  You may find it easiest to install  a KDE-based distro, like PCLOS or MEPIS.  I got my old USR external working quite easily with PCLOS and Copper.net
[http://www.pclinuxos.com/index.php?option=com_smf&Itemid=99999999&topic=22862.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=99999999&topic=22862.0)

Does your Courier have the little switches on the back?  I don't know if yours will be the same as mine, but switches #3, 5, & 8 are down on my old Sportster.

There are even decent KPPP guides on some of the ISP websites, like ISP.com.  Take a look - ISP.com has a "Linux guide"!
[http://www.isp.com/help.asp#](http://www.isp.com/help.asp#)

I've gotta go.  PM if you want to talk more.

---

