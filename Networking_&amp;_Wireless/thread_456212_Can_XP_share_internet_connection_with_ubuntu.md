---
title: "Can XP share internet connection with ubuntu?"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by Radium on 2007-05-27
Hello, I must say that I'm new to Linux.

I have two computers, one has XP OS, and in the other I just installed Ubuntu 7.04.
My question is like this: can I share my internet connection in XP, with Ubuntu on the second computer, both are wired.
I have already succeeded sharing files, but not internet connection.

Can anybody please guide me (if it is possible) how to share my internet connection.

Thank you.

---

### Post by chrisLACHCIK5084 on 2007-05-27
On my connection, I have my mom who has XP and my brother who has XP (they hate Ubuntu) and we all connect perfectly. so i hope that helps. if you were asking help to set it up, let me know.

---

### Post by Radium on 2007-05-27
Thank you for your answer :D

Yes, I need help.
How can I set it up?

---

### Post by merlinus on 2007-05-27
How are you conecting to the Internet?  And how are the two computers connected?

-merlin

---

### Post by Radium on 2007-05-27
My XP OS is connected to the internet with ADSL modem (USB).
and the ubuntu is connected to the computer (XP) with a cable, LAN.

and now, for unkown reason my LAN connection has been lost.. :/ I have no idea how to bring it back.. 
This operating system is very interesting, but hard to controll..

---

### Post by phillipchandler1 on 2007-05-29
Im thinking you need to get a router (IE Netgear), have the modem go into the router and then connect all the PC's (XP & Ubuntu) to the router. Rather than Modem>XP>Ubuntu

---

### Post by merlinus on 2007-05-29
A router is defrinitely the way to go, and not only to make Internet access and sharing easy.

I have a Linksys with built-in firewall, and do not have the usual array of zombie-making garbage attacking my windows boxes or partitions.

Very easy to set up for multiple machines.

Good luck!

-merlin

---

### Post by Synflux on 2007-05-29
Hi,

I'm new to Ubuntu but I'm going to say that it is possible. I did something very similar the other night with my friends playstation 3. ADSL->USB modem->XP PC->Play station. A router would be easier but it would probably mean dumping your usb modem unless it also has an ethernet connection.

You have to enable 'internet connection sharing' on your xp pc:
1. Control Panel
2. Switch to Classic View (in top left corner). If it says switch to category view it can be left alone.
3. Double click on Network Connections
4. Right click on your internet connection and click Properties
5. Click the advanced tab.
6. Tick the 'allow other users to connect...' box and choose 'Local area connection' in the home networking drop down box.
7. Click OK.

It should now change your local area connection's ip address to 192.168.0.1 (default, you can change if you want).

Now all you need to do is manually configure Ubuntu's ip address to use 192.168.0.1 as the default gateway and DNS servers, the xp box will forward on dns requests and you should find it works.

Have to say I haven't tried this and it may be complete rubbish but I hope it helps :)

---

### Post by elicoten on 2007-05-29
I can confirm that Synflux's answer does work. I have used it myself, and its certainly not complete rubbish :) .

XP's internet connection sharing can be a real pain some times but once you have it working, if a Windows client can connect to it then so can a Linux/Ubuntu client. It makes things easier if you use DHCP for addressing, as the Windows Internet Connection Sharing provides a DHCP server which will configure IP Addresses, DNS servers and default gateway settings automatically.

Its actually quite easy to setup assuming you do it correctly and don't have any other conflicting DHCP servers or manual IP addresses with the wrong settings. By default Ubuntu is set to use DHCP anyway so you shouldn't have a problem.

---

### Post by danilo.correa on 2007-05-31
Hi

I'd like to know if the opposite can be done... I have a Ubuntu connected to the internet and want to share it with other computer with WinXP, but I don't know how. They are connected by direct cable, and I have a ADSL USB modem connected to my computer.

Thank you

---

### Post by jml on 2007-05-31
danilo, I'm affraid I do not know the answer to your question, but I would like also suggest that you obtain a simple router and connect your modem to it and then connect your two computers to the router.  It really makes networking and sharing internet connections much simpler.  A router also eliminates the need to keep the gateway computer, (the one connected to the modem,) on all the time.  Plus the router does a decent job of acting as a hardware firewall.  Just my two cents worth.

Joe

---

### Post by danilo.correa on 2007-05-31
Joe

I just thought that if i configure my Ubuntu as a DHCP server it would work, but it didn't work either. XP can't get a IP from Ubuntu, even if i install DHCP server on it. :( Thank you for the tip, anyway.

---

### Post by jim87410 on 2007-06-01
If your XP box is having problems pulling a IP address,  assign a static address to it and use the IP addr of the ubuntu box as the default gateway.  I have dialup with a edgy box acting as gateway for a W2K laptop, a W2K server and fiesty box.  It can be painfully slow, but it works.

I have to say though that a router offers the best solution... as long as the modem has an ethernet port.

good luck,
jim

---

### Post by Genecks on 2007-06-01
I'm very interested in figuring out how to do this with XP and Ubuntu. At the moment, I'm using wireless to obtain a connect. So far, I've followed [these directions]("http://ubuntuforums.org/showpost.php?p=2744539&postcount=8"). I want Windows XP to be the host and Ubuntu to be the client.

So, what's next? What do I do to Ubuntu after messing with Windows?

---

### Post by viciouslime on 2007-06-01
> **danilo.correa said:**
> Hi

I'd like to know if the opposite can be done... I have a Ubuntu connected to the internet and want to share it with other computer with WinXP, but I don't know how. They are connected by direct cable, and I have a ADSL USB modem connected to my computer.

Thank you

This is definitely possible as I have done it myself. I followed a guide on the ubuntu wiki can't remember what it was called now, i will see if i can find it and will post a link.

---

### Post by viciouslime on 2007-06-01
Found it, I think:[https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")

---

### Post by Docter on 2007-06-01
To share a connection from ubuntu you need to set up packet  forwarding and IP masquerading. The easiest way to do that is through the Firestarter wizard. Windows should do a decent job of detecting the network settings. I think you need to avoid DHCP if going this route too.

---

