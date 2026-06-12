---
title: "Where is Network Manager?"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by SusieK on 2007-06-30
Hello

I'm trying to set up a wireless connection from my laptop. I have a Netgear router, and I know nothing about how any of it works. It just does, in Windows XP.

I can connect to the Internet via a cable from the laptop to the router, but if I remove the cable, the connection disappears.

I have read several threads, but they all refer to Network Manager, and I can't find the thing anywhere. I've looked under System, Administration, and there is Network, and Network Tools, but no Network Manager.

Please, how do you find it?

---

### Post by weblordpepe on 2007-06-30
If you're in Feisty, then it should automatically appear in the list of available networks along with the wired network connection.
If not, then the drivers aren't loaded for your wifi device. What you'll need to do is figure out what chipset your wifi is.

If its not working, then theres a good chance you are using a Broadcom chipset wifi. In which case you're in the same boat as me. A tiny, overcrowdy, smelly boat full of refugees from Redmond floating towards the island of Ubuntu.

---

### Post by lisati on 2007-06-30
> **SusieK said:**
> Hello


I have read several threads, but they all refer to Network Manager, and I can't find the thing anywhere. I've looked under System, Administration, and there is Network, and Network Tools, but no Network Manager.

Please, how do you find it?

Check out the System->Administartion->Network - you might be able to do the necessary tinkering with your settings, including enabling your Wifi, from there.

---

### Post by savantelite on 2007-07-20
Right click on the panel and select add to panel. In the Utilities section select notification area. Network manager won't be there yet as you must log out and log back in.

---

### Post by SusieK on 2007-07-24
Tthank you Saventelite

I tried that. I clicked on the panel, then went to the Utilities section and selected notification area. However, although I clicked on it, and clicked on "add", and also tried dragging to the panel, nothing happened. I never did find anything that said Network Manager. :-(

---

### Post by weblordpepe on 2007-07-26
hit alt-f2 and type:
 **nm-applet --sm-disable**

---

### Post by SusieK on 2007-07-26
Where do I need to be to do that? Sorry, I'm an absolute newbie.

---

### Post by weblordpepe on 2007-07-26
Thats  okay.
Hitting alt-f2 in Ubuntu is like opening the 'Run' dialogue in Windows. So you just need to be at the desktop.

The program you need to run is **nm-applet --sm-disable**
Hit Alt-F2, and put that into the box. Hit 'Run'
A Wifi signal strength icon should appear in the notification area of the toolbar. Either in the top-right or bottom right whever your toolbar is.

[LIST]
[*]If nothing happens, you may not have Wifi or a network driver enabled. In other words, the driver for your Wifi  or network card might not be loaded or working.
What you can do to get more details is run that program from the command prompt. Well its actually called the Terminal, but who cares.
Hit Alt-F3, and a command prompt/terminal appears. Type in **nm-applet --sm-disable** and hit enter. If any error messages will appear, they will appear here in the terminal.
[/LIST]
You can left-click and right-click the icon in the toolbar to either switch networks or just view information. Unfortunately in feisty I don't know of a way to specify a static IP address without using a the **network-admin** tool. Its just called **Network** and under the **System** and then **Administration** menu. 
[LIST]
[*]If it isn't there, you can run it with Alt-F2 or in the terminal. You MUST run this program as the **root** user instead of your own login. Its easy to do, just put **gksu** infront of the program name. So that makes it **gksu network-admin**. When you hit Run or the enter key, Ubuntu will just ask you for the root password.
[/LIST]If you're wondering about the odd shortcut keys - it actually makes sense. Alt-F1 is the menu, Alt-F2 is the Run dialogue, and Alf-F3 opens a command prompt.

---

### Post by SusieK on 2007-08-02
Thank you for the explanation, and please excuse the delay in replying, as my work has prevented me spending any time on Ubuntu until today.

I hit Alt-f2 and typed in "nm-applet --sm-disable" and then hit Run.

A message appeared: "Could not open file: //nm-applet --sm-disable. The location or file could not be found."

Then I tried using Alt-f3, but nothing at all happened.:confused::(

---

### Post by kevdog on 2007-08-02
I see you are having problems getting your wireless going.  At the command line I want you to type the following:

(To open up terminal Applications->Accessories->Terminal)

lspci -nn
lshw -C network

You can cut and paste the output of these commands to a post in this forum.  This will tell us the chipset in your wireless card.

---

### Post by SusieK on 2007-08-02
I went back into Ubuntu (I'm running it on the same machine as Windows XP, so have to keep restarting to move between one and the other). When I hit Alt f2 this time, the screen filled with  a strange symbol I haven't seen before. It just kept putting in line after line of these things. When I eventually got in to the terminal and typed in the letters you gave me, a great mass of stuff appeared. I cut it, created a new text file on my D: drive in Windows, pasted it in, saved it, restarted Windows, but the file is not there. 

Tomorrow I will try again, connecting with a cable so that I can access the forum direct from Ubuntu.

---

### Post by SusieK on 2007-08-29
Once again, sorry for the delay, I was held up by a work overload.

Below is the result. I hope it will help in getting my wireless network sorted out.

susie@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:09.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
susie@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@06:05.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:2f:74:1a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b0100000-b0101fff irq:17
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e5:46:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.5 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:3000-30ff iomemory:b0102000-b01020ff irq:23
susie@ubuntu:~$ 

Thank you for your help.

---

