---
title: "[SOLVED] Wireless Network Not Working"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by mclimber43 on 2007-12-11
I just installed a new wireless adapter - a Trendnet TEW-423PI.  I cant access any wireless networks, though I know that many are available around me.  I have checked the driver, hardware, et cetera.  No wireless networks show up when I look for them.  Not sure where to go from here.  I am running Ubuntu 7.10 (gutsy gibbon).  I just built this computer today, so I want to make sure that there is not a hardware problem before I can exchange parts.

---

### Post by tagskill on 2007-12-11
ive experienced this too I have a xps 410 with a new wireless adapter

---

### Post by NullHead on 2007-12-11
> **mclimber43 said:**
> I just installed a new wireless adapter - a Trendnet TEW-423PI.  I cant access any wireless networks, though I know that many are available around me.  I have checked the driver, hardware, et cetera.  No wireless networks show up when I look for them.  Not sure where to go from here.  I am running Ubuntu 7.10 (gutsy gibbon)

Hello check[ hear]("http://www.trendnet.com/downloads/info/TEW-423PI.htm") for drivers from trendnet. Also please open a terminal ( for ubuntu it's under applications>accessories>terminal) and type ```
lspci
```and copy out what text was displayed.

---

### Post by mclimber43 on 2007-12-11
terminal > lspci 

gives



aaron@aaron-toshiba:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
01:0b.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
01:0b.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by mclimber43 on 2007-12-11
Also, terminal > iwconfig

gives

Power Management: off

Is this the root of the problem?  If so, how do I turn it on?

---

### Post by heindsight on 2007-12-11
Hi mclimber,

I don't know anything about Trendnet wireless cards, but the only wireless device I see in your lspci output is an Intel Pro/Wireless 2200bg (perhaps the Trendnet card uses the intel
chipset?):
> **mclimber43 said:**
> 
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


I have an IPW2200BG card in my laptop and it works perfectly. My iwconfig also outputs Power Management: off, this doesn't seem to affect the working of the card, so I doubt that's your problem.  Could you perhaps post the entire output from iwconfig?

The IPW2200 cards do have a "Radio Frequency Kill Switch", If this switch is On, your wireless won't work. If the kill switch is on, the first line of iwconfig output for your card will say "radio off". If this is indeed your problem, you'll have to find a way to turn the rf kill switch off: have a look at the documentation for your card, perhaps it's mentioned somewhere in there. My laptop has a hardware switch on the side to switch the radio on/off, there are also software utilities available (do a search for rfkill).

If that's not the problem, you might want to check your lsmod output to make sure that the ipw2200 driver is loaded, and have a look in /var/log/messages for anything related to the
ipw2200 driver.

---

### Post by mclimber43 on 2007-12-11
Here is the printout for terminal > lspci and terminal > iwconfig.  Ignore the above lspci, I am not sure what happened there.


aaron@aaron-desktop:~$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2) 
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3) 
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3) 
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a3) 
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) 
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) 
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) 
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) 
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) 
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) 
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) 
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2) 
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3) 
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20) 
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1) 


aaron@aaron-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     802.11b/g  Mode:Managed  Frequency=2.432 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry: on   Fragment thr: off 
          Power Management: off 
          Link Quality: 0  Signal level: 0  Noise level: 0 
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0 
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon :0

---

### Post by mclimber43 on 2007-12-13
I got the wireless card to to work. First, I had to log in as root.  I went to Sysem > Administrator > Login Window, went to the security tab, and clicked th box to allow a local administrator to log in.  I then changed the password for the root user under system > Administrator > Users and Groups.  I logged out and back in as root. Then, I

1  Got the .inf file for the windows driver for my wireless adapter.
2  installed ndiswrapper
3  In the terminal, got to the folder where the .inf driver was located (wherever I wanted to put it really).
4  Typed ndiswrapper -i net5211.inf  (where my driver was named net5211.inf)
5  Typed ndiswrapper -l to se if it worked.  I found that there was an alternate driver listed, so I had to blacklist it.
6  Blacklisted the other driver by typing echo 'blacklist atp' | sudo tee -a /etc/modprobe.d/blacklist  (where atp was the name of my alternate driver WITHOUT .inf)
7  To get ndiswrapper (and hence my driver) to boot, I typed sudo gedit /etc/modules
8  I added ndiswrapper to the end of the list in the file that opened

I hope that this helps others in my situation!

---

### Post by NullHead on 2007-12-13
please use the thread tools tab and mark this thread as [SOLVED]

---

