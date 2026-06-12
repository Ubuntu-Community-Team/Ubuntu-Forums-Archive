---
title: "Wi-Fi Authentication Repeat"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by justin_2 on 2014-04-03
Hi! New Linux user here, I am booting from a USB flash drive. I have yet to actually install Linux yet because it says to ensure that the computer should be connected to the internet, which I am having trouble doing. I'm guessing there isn't any problem with my wireless drivers, because my computer is able to detect the network and see the network name, but every time I try to connect to it, I input the network password (which I have quadruple checked to be correct), and then it tries to connect, but then the authentication popup just comes back, and it does this every single time I try to connect. 

I am on an HP Pavilion dm1 netbook. Please help if you can!

---

### Post by ajgreeny on 2014-04-03
It is not actually essential to be connected to the internet when installing, but many users like to accept the option to update and add the restricted format packages at the same time, which you obviously can't do without the connection.

As you can actually see the network you need, there is obviously no major hardware problem, so I would go ahead and install without the net connection and we can sort out the wireless afterwards.  If you have a wired connection available it will be a lot easier to fully update after installing and you may then find that wireless works straight away.

Once installed run the command **lspci** in terminal and come back here with the output of that.

---

### Post by justin_2 on 2014-04-03
Installed it 
Results of lspci:

justin@Justin-Netbook:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

### Post by ajgreeny on 2014-04-04
I hate to just link you to a search page but at the moment I do not have any time to do more, so here goes.

Have a good look at some of the posts at [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=RTL8111+driver&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=RTL8111+driver&as_qdr=all&sa=Google+Search&lang=en) which may help you to sort out a driver for your wireless adapter.

Good luck. I'll check back much later today to see if you've got anywhere.

---

### Post by justin_2 on 2014-04-04
Unfortunately, due to my living situation (basically a really strict landlord) I am unable to connect directly to the router with Ethernet. However, I have been able to connect to the internet by using my phone as a tether, and I updated to the most recent version of Lubuntu through that, but still am not able to connect to the internet

However, I was able to briefly connect to the internet using the internet at my school.

I'll try and download something with the driver, but if I'm able to detect the network on my computer, doesn't that mean that the adapter itself is working...? I just get to the point where it asks me for authentication, and I put in the correct password, but it just doesn't connect

Also the link you sent appears to be for the ethernet controller driver..? Should I be looking for drivers for the network controller?

---

### Post by ajgreeny on 2014-04-05
In view of your comment about a strict landlord, are you 100% certain that your password is absolutely correct, and that you are typing it correctly?  Did your landlord just tell you what it is or is it written down to make sure the case of letters etc etc is right?

---

### Post by justin_2 on 2014-04-05
It's written down, and I've connected to the network before with other computers

---

### Post by ajgreeny on 2014-04-06
Sorry, my link in post #4 may have confused you as it was for the ethernet, not wireless; my apologies, I answered too quickly without reading your previous post properly.

Have a look at the info at [http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx) which may help a lot better then the realtek answer I gave before.

---

