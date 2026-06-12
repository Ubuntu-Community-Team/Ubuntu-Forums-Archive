---
title: "wireless modem"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by bjhome on 2009-12-26
I have just bought a wireless modem and it is not connecting. can anybody tell me how to install it in ubuntu

---

### Post by Ben Wright on 2009-12-26
Could I please get some addition information about the wireless modem? Is it a usb wireless modem? You may also want to check out: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) . Thanks

---

### Post by bicyclerider on 2009-12-26
The setup should be as follows;
incoming internet- dsl,cable, satalite, etc
connected to modem using either coxial cable or dsl phone line.
from the modem it would travel out either through a ethernet cable and wireless combination ability.
The device you want to connect has to have a wireless card or built in wireless to setup a wep2 connection to the modem/router. If the modem doesn't have the wireless ability built in you will end up having to purchase a combination wired and wireless router.  What do you have there that your working with? name of the model of modem and part number?? Desktop or laptop? Have you searched the knowledge base for previously discussed articles relating to a similar situation?

---

### Post by bjhome on 2009-12-27
i have loaded wireless assistant what else do i have to do to get ubuntu to accept my wireless modem

---

### Post by 3rdalbum on 2009-12-27
> **bjhome said:**
> i have loaded wireless assistant what else do i have to do to get ubuntu to accept my wireless modem

What's this "wireless assistant"? I can't find it in Synaptic.

When you say "wireless modem", what exactly do you mean? Are you talking about a mobile broadband modem, where you get your internet connection from the mobile phone towers?

If this is what you mean, then go to the Network Manager applet on your top panel, right-click it, go to Edit Connections, click on the Mobile Broadband tab and click the Add button.

Or are you talking about a modem which plugs into your phone line for ADSL, so you can access your ADSL connection from anywhere in your house? If so, then left-click on the Network Manager applet and tell us what you see.

---

### Post by bjhome on 2009-12-27
it is the phone adsl connection where is the network applet that you want me to click on.

---

### Post by 3rdalbum on 2009-12-27
> **bjhome said:**
> it is the phone adsl connection where is the network applet that you want me to click on.

It's on the top panel, toward the right. The look of it will depend on what icon theme you have; it will probably look like two computers joined to eachother.

If this is a new modem that plugs into your phone line, then you'll need to connect it to your computer via an Ethernet cable to begin with, and set it up using the modem's web-based interface. The address to type into your web browser will be in the modem's manual; it's usually something like one of the following:

[http://192.168.0.1](http://192.168.0.1)
[http://192.168.1.1](http://192.168.1.1)
[http://192.168.0.254](http://192.168.0.254)
[http://192.168.1.254](http://192.168.1.254)

Once it's set up to create a wireless network, then left-click on the network manager applet and it will display a list of wireless networks in the area. Click on your network and Network Manager will connect, prompting you for a password if you have set up security on your modem (it's a VERY good idea to set your modem to use WPA2 security).

If Network Manager can't find any networks at all, then you may need to install a driver for your computer's wireless card. We can help - just post the output of the "lspci" and "lsusb" commands (note: these are lowercase Ls, not the number one).

---

### Post by bjhome on 2009-12-27
when i click on the network appelet i have a list which says  wired network and 802.1X Protected wired network and manual configuration.

---

### Post by bjhome on 2009-12-27
we have connected it using the http:/192.168.1.1 and it works fine on windows but i want it to work on linux

---

### Post by bjhome on 2009-12-27
where do i find the commands you are talking about

---

### Post by 3rdalbum on 2009-12-27
> **bjhome said:**
> where do i find the commands you are talking about

Okay it sounds like you might not have a driver for your wireless card.

Go to Applications > Accessories > Terminal and type (or copy and paste) those commands in, and then copy and paste the result into the forum.

---

### Post by spiky001 on 2009-12-27
open a terminal then type lspci then enter

---

### Post by bjhome on 2009-12-27
0:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
bev@bev-laptop:~$

---

### Post by bjhome on 2009-12-27
bev@bev-laptop:~$ "lsusb" 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
bev@bev-laptop:~$

---

### Post by 3rdalbum on 2009-12-27
Broadcom wireless.

Okay, we can deal with this. First, I'll get you to plug in your Ethernet, go to Synaptic Package Manager and hit the Reload button. When that's done, close Synaptic.

Then go to the Hardware Drivers program (System > Administration > Hardware Drivers) and see if it recognises a driver for you. If it does, then click the "Activate" button and the driver will download and install for you, then you can reboot.

If it doesn't find a driver, then you need Ndiswrapper - it's a piece of software that can use the .inf file from a Windows wireless driver. Use Synaptic Package Manager to install the "ndisgtk" and "ndiswrapper-common" packages. Then you can go to System > Administration > Windows Wireless Drivers program and specify the .inf file corresponding to the wireless driver from Windows. Reboot and you should be able to connect using Network Manager.

That's about as much as I can help you - I've never used Ndiswrapper, I've only ever bought wireless cards that work out-of-the-box on Linux. If you get stuck, you can try checking out Google for "ndiswrapper howto" and see if that helps.

---

### Post by bjhome on 2009-12-27
how do i know what the  corresponding.inf file is? where do i find this?

---

### Post by 3rdalbum on 2009-12-27
> **bjhome said:**
> how do i know what the  corresponding.inf file is? where do i find this?

It's inside the installer for the Windows drivers. But that's all I know. Can anyone else help?

---

### Post by bjhome on 2009-12-28
where do i find the .inf file? can anybody help me with this please.

---

