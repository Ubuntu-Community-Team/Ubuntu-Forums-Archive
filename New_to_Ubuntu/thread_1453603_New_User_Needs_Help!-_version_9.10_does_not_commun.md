---
title: "New User Needs Help!- version 9.10 does not communicate with laptop"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by oldtrailmaster on 2010-04-13
Hello folks,

Several days ago, I installed Ubuntu 9.10 onto my Acer Aspire 3100 laptop, running it alongside Widows Vista as a dual-bootable system. Creation of the Ubuntu boot CD went fine, and the installation onto my hard drive was flawless. Ubuntu opens and behaves as I would expect, except for one little problem.

:confused:
For reasons unknown to me, Ubuntu is not communicating with my laptop's networking hardware, and I have no internet connectivity, even when sitting directly under the wireless router at the local library (literally), which puts out a wickedly-fast signal that my Windows Vista OS auto-detects and immediately connects to.

Up in the right side of the Ubuntu desktop, I click on the network icon and it does not show a wireless connection at all, even though I am only a few feet from the router. At home, where I use a dialup modem, I also see no means of getting online. My modem is an HDAUDIO Soft Data Fax Modem with Smart CP,manufactured by CXT (Conexant Systems Inc., file version 4.0.13.0, and the driver version is 7.58.0.0). My network adapter is a Broadcom 802.11g.

I desparately wish to convert to Ubuntu. I used Mac for ten years, and then Windows for ten years. Now, after 20 years, I want to live out my days as an open-source Ubuntu fanatic. I am ready to give the old status quo the boot! 

I am an advanced computer user, but I am not a programmer. I seek a solution that is user-friendly for normal people, something equivalent to a driver that I can easily install or activate that will allow Ubuntu to see my hardware and get me connected. Can anyone help me over this hopefully-little glitch so that I can move on in total Ubuntu bliss?

My processor is a Mobile AMD Sempron Processor 3500+ at 1.80 GHz, 1.50 GB RAM, and a 32-bit Operating System. I am running Windows Vista Home Basic, Service Pack 2.

My current email is [EMAIL="wildernessrogue@gmail.com"]wildernessrogue@gmail.com[/EMAIL] if you have a workable solution that does not require programmer status to implement. Surely this must be a simple fix that I simply am overlooking, but being the new guy on the block, I have yet to be enlightened. Thanks for your help in coming up to speed!!

[COLOR=DarkRed]**_UPDATE_: I just downloaded Fedora 12, and it immediately locates the libary wireless signal. I am online within seconds, with no glitches. So, it appears that Fedora will be my entry point into the world of Linux. Thank you all for your Ubuntu assistance. Wish I had the time to dedicate to further Ubuntu study and setup, but since Fedore handles it all seemlessly, my path is now down that road.**[/COLOR]

Steve
Wanna' be Ubuntu Fanatic
"If you're not living on the edge, you're taking up too much space."

---

### Post by zvacet on 2010-04-14
For dial up read [this]("https://help.ubuntu.com/community/DialupModemHowto") and for wireless type in applications>accessories>terminal

```
lspci | grep net
```

and post output here.

---

### Post by oldtrailmaster on 2010-04-14
Hello ZVACET,

When I type "lspci | grep net" into the terminal, it returns the following output:

 [COLOR=black][FONT=&quot]06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/FONT][/COLOR]

Thanks for any help you can give. 
Steve

---

### Post by zvacet on 2010-04-14
You can establish wired connection,but you know that already,and you didn´t ask that.Did you read link I posted to you and are you able to detect your modem and driver for it following instructions from link?I´m not an expert,so do not expect much from me,but I will try to help as far as I can.

---

### Post by anewguy on 2010-04-14
Please post the complete output of both of these commands, as we need to find out what type of wireless adapter is installed in the laptop and the chipset it is using:

lspci

lsusb


Thanks
Dave ;)

---

### Post by oldtrailmaster on 2010-04-15
Hi Dave,
I have entered the two codes into the terminal as you instructed. The complete outputs follow, along with a third that I tried myself to see if it might help. I do know that I have a Broadcom 802.11g Network Adapter, for whatever that's worth. 
Thanks for your assistance!
- Steve

Here are the outputs:

   wildrogue@wildrogue:~$ lspci
  
  00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
  
  00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
  
  00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
  
  00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
  
  00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
  
  00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
  
  00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
  
  00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
  
  00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
  
  00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
  
  00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
  
  00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
  
  00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
  
  00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  
  00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
  
  00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
  
  

   
  wildrogue@wildrogue:~$ lsusb
  
  Bus 002 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
  
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 001 Device 003: ID 0ef2:0065 I/O Magic Corp. 
  
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
  wildrogue@wildrogue:~$ 
  
  
  

   
  wildrogue@wildrogue:~$ lspci | grep 802
  
  06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
  
  wildrogue@wildrogue:~$

---

### Post by oldtrailmaster on 2010-04-15
[COLOR=DarkRed][B]_UPDATE_: I just downloaded Fedora 12, and  it immediately locates the libary wireless signal. I am online within  seconds, with no glitches. So, it appears that Fedora will be my entry  point into the world of Linux. Thank you all for your Ubuntu assistance.  Wish I had the time to dedicate to further Ubuntu study and setup, but  since Fedore handles it all seemlessly, my path is now down that road.
- Steve
[/B][/COLOR]

---

### Post by albert s on 2010-04-15
for my tuppence worth, it seems to me at least that a wired connection is a must for a first time installation of ubuntu.
it didnt "see" my wireless in my wifes laptop, or on my workmates desktop until it had installed the required updates.
perhaps this will be fixed in the next release, (heres hoping for new users).
anyway, thats how I sorted it, oh, it did see an edimax usb wireless device first time off on the laptop, but not the inbuilt broadcom card.
hope this helps.

---

### Post by zvacet on 2010-04-15
@ **oldtrailmaster**

Enjoy in Linux world.I hope you will try Ubuntu again in future. ;)

---

### Post by anewguy on 2010-04-15
Glad you found something that works for you - that's name of the game, no matter what OS or release it is.

If you decide in the future to try ubuntu again, be assured we can get your wireless working, it just takes a few minutes once you actually know what you have to do.

Best of luck!  Hope you enjoy Linux!

Dave ;)

---

