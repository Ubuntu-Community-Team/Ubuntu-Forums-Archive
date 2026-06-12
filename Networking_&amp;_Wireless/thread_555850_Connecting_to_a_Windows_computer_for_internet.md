---
title: "Connecting to a Windows computer for internet"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by TidusBlade on 2007-09-20
Im currently using Ubuntu Feisty, I'm pretty new to Linux so dunno much :S 
I dual boot Windows XP and Ubuntu and the internet works perfectly on Windows, but then when in Ubuntu it dosent seem to receive the internet from the windows computer. Im connecting to it through an Ethernet cable from the back of the PC to a HUB and then that hub connects to a computer running XP and it connects to the modem... Is there something I have to do for it to connect to the internet this way or it something wrong with the other computer ? 
Thanx in Advance ^_^

---

### Post by badseed on 2007-09-20
Hi,
What is the network card that you are using?

Do you use DHCP of static IP?


Let's start troubleshooting. :guitar:
João Mendes

---

### Post by KCPokes on 2007-09-20
If you are routing your internet connection through your XP machine, and not through a standard router, then you probably need to look into ICS as your XP machine is essentially acting as a gateway to the internet for your other machine. 

[http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02july01.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02july01.mspx)

Normal configuration would be multiple machines on a router with the cable modem plugged into the WAN port, creating a gateway between your private network and the internet.

---

### Post by TidusBlade on 2007-09-21
> **badseed said:**
> Hi,
What is the network card that you are using?

Do you use DHCP of static IP?


Let's start troubleshooting. :guitar:
João Mendes
Im using an Intel PRO/ 100VE Network connection and I use DHCP if that helps :D


> If you are routing your internet connection through your XP machine, and not through a standard router, then you probably need to look into ICS as your XP machine is essentially acting as a gateway to the internet for your other machine.

[http://www.microsoft.com/windowsxp/u..._02july01.mspx](http://www.microsoft.com/windowsxp/u..._02july01.mspx)

Normal configuration would be multiple machines on a router with the cable modem plugged into the WAN port, creating a gateway between your private network and the internet.
Ill try doing that =] And ill post back what happens, Thanx ^_^


EDIT: I forgot to mention it sometimes switches on and works perfectly and then when I reboot, the internet is back off, at the moment it's on and working well ^_^ But it will probably not work when I reboot again :S so Ill refer to this later today :D

---

### Post by walecowry on 2008-04-24
Hi, I am in a smiliar dilemma as I am new to Linux as well.

I have Ubuntu 7.10 running on my Windows XP machine. From the installation guide I have, it says Ubuntu should have access to the internet automatically but it does not.

Don't know if I have done anything wrong.

---

