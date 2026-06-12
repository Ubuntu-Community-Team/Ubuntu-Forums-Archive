---
title: "How can I view/control/communicate with other PCs on my LAN"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by carvacrol on 2009-11-19
How can I view/control/communicate with other PCs on my LAN, using Remote Desktop Viewer? I have 2 PCs: one Ubuntu, the other Windows 7. I want to access the Windows PC from my Ubuntu PC.


The other PC(the one I want to access remotely) is running Windows 7, the PC I am currently using is running Ubuntu. Every time I try to connect(while using Ubuntu) when using the Window that says "which machine do you want to connect to?" after typing the host name of the other Windows PC and clicking "connect" it says "connection to host "hostname" was closed.". How can I access my other PC through Ubuntu using Remote Desktop Viewer or some other Ubuntu program? Thanks.

Edit: The 2 PCs are connected to each other and to the Internet through a Linksys router(not wireless).

---

### Post by undecim on 2009-11-20
You need to set up windows to allow remote desktop connections.

---

### Post by carvacrol on 2009-11-20
> **undecim said:**
> You need to set up windows to allow remote desktop connections.

I've already done this. It seems I can't even get my two PCs to recognize or communicate with each other, even though they are connected through a router.

---

### Post by bodhi.zazen on 2009-11-20
The general method is via VNC, although there are other options from ssh to ftp to samba ...

What have you done ?

Do you have a firewall on either computer ?

How are you trying to connect ?

---

### Post by carvacrol on 2009-11-21
> **bodhi.zazen said:**
> The general method is via VNC, although there are other options from ssh to ftp to samba ...

What have you done ?

Do you have a firewall on either computer ?

How are you trying to connect ?

I've tried using Remote Desktop Viewer on my Ubuntu PC to view my Windows 7 PC(both are hooked up through a router and can access the Internet with no problem). At the connect screen where it says to enter "host", I enter the name of my Windows PC. I've also used Terminal Server Client but get no response. I can't even "see" the other PC from the other. I've even tried to ping my windows PC from my Ubuntu PC command prompt(and vice versa) to see if I can get a response. Nothing, and I admit I am confused over what the unique IP addresses of my individual PCs are. 

I'm not all that new to computers or the Internet, but I am very new to setting up LANs since I've never had more than one PC.

The Windows PC does have a Firewall, but I've shut it down when I've tried to connect to it from my other computer. I've enabled "remote access" in the network settings for my Windows PC(the Ubuntu is running Firestarter). As a novice, I need to look up a lot of things, but now I understand what IP addresses are. I've tried using Samba to connect, but I'm not sure what the "authentication mode" is, or what the "workgroup" name is or the description. Maybe I should connect through my Windows PC? On my Windows PC I have "Internet Information Services" enabled, along with FTP Server, Web Management Tools, WWW Services in the "turn windows features on or off" in the Control Panel.

Like I said, I am very new to this. I need a step by step process to help me get these two PCs to recognize each other, then communicate with each other or do remote viewing and FTP file-sharing. If they were both Windows PCs I assume it would be easier, but I like the challenge. Thanks in advance, I've found Ubuntu users to be very helpful so far.

---

### Post by Zzl1xndd on 2009-11-21
I would suggest VNC as the way to go. You just need a VNC server installed on your Windows Box.

[http://www.realvnc.com/products/free/4.1/winvnc.html](http://www.realvnc.com/products/free/4.1/winvnc.html)

Then use the Remote Desktop viewer in Ubuntu.

---

