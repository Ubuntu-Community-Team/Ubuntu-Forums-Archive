---
title: "Toshiba Tecra A4 WiFi works with PClinuxOS but Not Ubuntu"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by pstephens on 2006-08-20
I am new to Linux, but over the last couple of weeks have Tried several Distros on the Toshiba Tecra A4  Laptop.

PCLinuxOS finds the WiFi and works with EZlink 409 Ethernet Driver (Module PCNET_CS). It only detects the WiFi hardware if the PC is booted with the WiFi hardware switch in the OFF position, then the switch must be moved to the ON position for WiFi to work. But nothing else works well so I tried Kubuntu.

KuBuntu finds the WiFi gear if the switch is OFF, and once the switch is move to ON, detects my network, but does not seem to connect.

Ubuntu Finds the WiFi as PRO/Wireless 2915ABG MiniPC Adapter and says the card is working, but no connection. I have installed WiFi Radar, and it says it is connecting to the wireless network, and getting an IP address, but does not connect. 

The Windows XP dual boot works fine.

Some things I have discovered.
1) The WiFi switch MUST be off at boot time for the hardware to be detected.
2) The WiFi switch MUST be on for networking to operate.
3) The Wifi hardware will not be detected if warm booting from Windows, the Laptop MUST be switched off, and pere removed before booting into Linux.
4) Sometimes the WiFi connection must be de-activated and re-activated to work.
5) In PCLinuxOS the Ethernet port must be disabled before the WiFi will work.

What do I have to do to tell Ubuntu to used the EZLink 409 Ethernet Driver?

Thanks for being patient, I have tried so many distros that I am getting confused, but the PCLinuxOS is the only system that will talk to the WiFi. Unfortunately it misses a lot of the other hardware and will not use my printers. I LIKE Ubuntu, the ONLY isse is the WiFi card. Any help would be appreciated.

---

### Post by pstephens on 2006-08-23
Thanks all - I have not been able to resolve the WiFi problem, so I have moved to PCLinuxOS on the Toshiba. 
I would prefer Ubuntu, but no wireless is a deal breaker. I am still using Ubuntu on my desktop, and will hope for a resolution with the next release of Ubuntu.
In the interim, I have managed to get everything working on PCLinuxOS except the Brother printer. I have a driver, but have not had time to get it going, but am otherwise very pleased.

Phil Stephens

---

### Post by Gtaylor on 2006-12-20
The Tecra A4 wireless will work if you disable encryption on your network, but even then it will restart with firmware errors periodically. This obviously isn't ideal on many different levels.

But yes, it's a long-standing issue that I've been trying to nudge the developers on for a while, please add to this stuff to the [bugpost]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55532").

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55532](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55532)

---

