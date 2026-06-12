---
title: "Ubuntu 10.04 Gateway Computer WiFi Problem"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by McTwitch on 2011-02-14
So, I installed Ubuntu 10.04 onto a friend's Gateway laptop. So far, everything is working fine, except that it won't connect to the Internet, via Wifi. My first ideas are that the password or the connection are wrong, etc.

So, how would I find out if her wireless card is compatible with Ubuntu, and if it's not, how do I remedy the situation?

---

### Post by Habeouscorpus on 2011-02-14
Wireless in Ubuntu is a crapshoot. Go to System>Administration>Additional Drivers. If there are drivers needed for your wireless, they'll be there. If you have a Broadcom chipset, enable the Broadcom-STA driver. That one worked for me.

To find out what chipset you have, type "lspci" in a terminal, and search for the "Network Controller" Line. That's your wireless chipset.

---

### Post by dFlyer on 2011-02-14
My wife has a gateway running 10.10, wireless and all out of the box, no problems.

---

### Post by McTwitch on 2011-02-14
Well, glad your wife likes it. If she can tell me how to make it work, I'd be much appreciated.

There isn't an additional drivers option, there is, however a "hardware drivers" but that only has the driver for the ATI graphics thing. Is there something else that I could do that would make it work, or give you a better idea of what's going on?

---

### Post by Habeouscorpus on 2011-02-14
Go ahead and post the output of lspci in [CODE] tags.

---

### Post by McTwitch on 2011-02-14
I don't have it, I'm trying to help the friend over the phone. I'll be able to get it to you tomorrow, though.

---

### Post by fallenstar on 2011-02-15
> **dFlyer said:**
> My wife has a gateway running 10.10, wireless and all out of the box, no problems.

My broadcom card ran fine on 10.10 using the STA driver, I've downgraded for other reasons to 10.04 and I CANNOT get it to work. 

Fed up and re-upgrading.

):P

---

### Post by McTwitch on 2011-02-15
```
   	 	 	 	p { margin-bottom: 0.08in; }  00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge  
 00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)  
 00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)  
 00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)  
 00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)  
 00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]  
 00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller  
 00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller  
 00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)  
 00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)  
 00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control 
 01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]  
 01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller  
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)  
 03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)  
 06:09.0 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)  
 06:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)  
 
```

There's the result from "sudo lspci" Hope it's helpful.

---

### Post by Habeouscorpus on 2011-02-18
(About the PM: Thanks for understanding! Sorry about that.)

Okay, so I started Googling. You have a Marvel and an Atheros...

I found a link that might promise results: [http://ubuntuforums.org/showthread.php?t=1368259](http://ubuntuforums.org/showthread.php?t=1368259)

Also, look into Ndiswrapper: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by ubun2geek on 2011-02-18
just uninstall 10.04 and install 10.10 - that fixed it for me!

---

### Post by McTwitch on 2011-02-18
Well, I'll look into the links, and into installing 10.10. I've looked further into the problem, and, to be quite honest, I believe the problem might just be that she has the wrong password. I'm leaning towards that at the moment, but if that turns out to be fruitless, I'll know where to turn. Thank!

---

### Post by Habeouscorpus on 2011-02-19
> **OpenOffice.org said:**
> just uninstall 10.04 and install 10.10 - that fixed it for me!

Or you could just upgrade. Go to the update manager and click the UPGRADE button next to where it says that there's a new version available at the top.

---

### Post by fallenstar on 2011-02-21
after upgrading i went into synaptic, installed anything to do with sta, activated it in additional drivers, restarted and voila wifi!

---

