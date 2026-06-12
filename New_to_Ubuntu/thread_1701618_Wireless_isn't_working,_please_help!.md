---
title: "Wireless isn't working, please help!"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by B10hazard on 2011-03-06
Hi, I'm at a friends and his computer keeps blue-screening, so I installed Ubuntu (10.10, desktop, basic) on it and it's working perfectly except for 1 not-so-small problem: the wireless card doesn't seem to register. 
When I type in "lspci" I get this:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9803
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)

```
 
any help would be appreciated, and the faster the better! (I have to leave soon, and my friends computer clueless...)
 
thanks

---

### Post by grahammechanical on 2011-03-06
Go to system>Administration>Additional Drivers. Is there an option to activate a driver. You will need to be connected by cable to the modem for this work.

Do you see the network icon? Is there a red exclamation mark against it?

Right click the network icon and make sure that there is a tick mark against the lines Enable Networking and Enable wireless.

Left click the network icon. Do you see any available wireless networks.

If the machine is a laptop make sure that the wireless adapter is activated by the keyboard.

If you switch the modem off and then back on it will broadcast a signal that the laptop should detect.

Please do two more things. 1) Provide information and the machine and the messages that Ubuntu gives you. 2) Teach your friend to access these forums and to read the advice given to others on this problem and other problems. Do not leave him forum clueless.

Regards.

---

### Post by maqtanim on 2011-03-06
Welcome to UF... :D

Check at **System > Administration > Hardware Drivers**, whether it says to install new driver for the wireless. If it says, then install the driver from there.

Also check whether the wireless mode of laptop is on or off. From the right side of the top panel, right click on the network icon, and look there if there is a tick mark in both **Enable Networking** and **Enable Wireless.**

---

### Post by wep940 on 2011-03-06
I did some searching on the net for you and found some answers.  The drivers you can download from Realtek apparently don't work in 10.10.  Some have been using a different method, though it is not supported by Canonical.  If you follow this method, you will need to rerun it each time a new kernel is delivered.
 
One such thread with this information can be found at:
 
[http://en.community.dell.com/support-forums/software-os/f/3525/t/19352306.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19352306.aspx)
 
The end of the thread is what you are interested in:
 

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
 
I think most have rebooted at this stage as well.
 
 
While the thread may be for a different PC, and the driver appears wrong (rtl8192ce), this is the common steps used everywhere I have found so far for people to get your wireless adapter rtl8176 working.
 
This obviously does require internet access, so if at all possible hard-wire your PC to the router to do the above steps.  Afterwards, just disconnect the hard-wire before trying your wireless.
 
I have never used this as I haven't had that adapter, but I would be happy to try to work with you if needed.  I'm sure there are others out there who are probably more familiar with this and your adapter that can hopefully help as well.

---

