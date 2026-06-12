---
title: "I need help bad........"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by izdalion on 2011-03-02
Ok so I tried to install my RT2561/RT61 chip set and messed something up. Now my chip set is not working and/or not reading any wifi. I know this is a little vague but I can give more info upon request. P.S I am a dum Newbie!

---

### Post by izdalion on 2011-03-02
Also when I tried to install the chipset I lost wlan0.

---

### Post by jeremyjjbrown on 2011-03-02
Did you put the previous wifi card back to test?

You need to find out if you have a bad card or if you sparked the motherboard.

---

### Post by izdalion on 2011-03-02
How would I do that (test).

---

### Post by jeremyjjbrown on 2011-03-02
Ok lets get more info.

Were you installing a wifi card into you computer or just card driver software?

---

### Post by izdalion on 2011-03-02
I'm pretty sure both. I read some where that the RT61 chip sets have a lil' trouble in ubuntu. So I tried installing windows drivers while trying to get the system to go through the chip and not the linux wifi setup. In all honesty, being the idiot I am, I copied and pasted like crazy and most likely blacklisted something I wasn't supposed to.

---

### Post by jeremyjjbrown on 2011-03-02
Does wifi still work in windows?

did you install this card into the computer yourself or did it com in the machine?

---

### Post by izdalion on 2011-03-02
My father actually built this machine for me and it worked with the original setup. And I only have ubuntu 10.4 in this machine so I'm not sure if it would work in windows. I am currently using a belkin usb and that works for wifi but I would rather have the chip set working LOL

---

### Post by izdalion on 2011-03-02
Also when I disconnect the belkin usb and try to see if the chip set will pop on it says something about the interface.

---

### Post by jeremyjjbrown on 2011-03-02
OK that chipset should have worked natively in ubuntu 10.04

were you following instructions posted some were?

---

### Post by jeremyjjbrown on 2011-03-02
> **izdalion said:**
> Also when I disconnect the belkin usb and try to see if the chip set will pop on it says something about the interface.

If you want help with computer issues you have to be very specific. If you get an error cut and paste or type it exactly into your post.

---

### Post by izdalion on 2011-03-02
Yes it did work with it until I touched the settings :P And yes I used directions but  from a bunch of sources but I couldn't tell you exactly which ones. I actually think one was from this forum.

---

### Post by jeremyjjbrown on 2011-03-02
Your going to have to be smarter than this if you want to work with computers.

1. If it is not broken, don't fix it.

2. If you try to fix it. keep a log of exactly what you did and were you got the info from.

I would like to help you but you are not giving me any useful info.

If you used the terminal go back in the commands by using the up arrow an cut and paste set by step what you did into a text file so you can post the commands you entered. If you can do some of that maybe someone can help you.

---

### Post by izdalion on 2011-03-02
OK gotcha.... this is what it says when I try with RutilT WLAN Manager:
Critical error :
Can't find any wireless network interface.
Code : -3

---

### Post by izdalion on 2011-03-02
I fully understand what your saying. But I can't learn if I don't try things.

---

### Post by jeremyjjbrown on 2011-03-02
Have you tried restarting your computer without the usb network card inserted?

If not try it. Then try to connect to the wireless network you use and post the exact errors you get.

---

### Post by jeremyjjbrown on 2011-03-02
> **izdalion said:**
> I fully understand what your saying. But I can't learn if I don't try things.

Of course, but you also can't learn if you have no way to remember exactly what you've been doing.

---

### Post by izdalion on 2011-03-02
Here's some more info if it helps:

lspci:
izdalion@izdalion-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
izdalion@izdalion-desktop:~$

---

### Post by izdalion on 2011-03-02
Tu- Shea! I have restarted and the only message I get is the one I posted other then the Network connection Icon saying disconnected. 

iwconfig:
izdalion@izdalion-desktop:~$ sudo iwconfig
[sudo] password for izdalion: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"linksys71611"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:76:8E:F6   
          Bit Rate=1 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:507F-CE3D-0D
          Power Management:on
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Note Wlan1 is from Belkin USB

---

### Post by jeremyjjbrown on 2011-03-02
> **izdalion said:**
> Here's some more info if it helps:

lspci:...


OK much better. Now

1. Restart your machine with out the usb card in it. Try to get to the wireless network and log the exact errors in a text file. 
2. Run lspci without th usb card inserted, log that to.
3. put the usb back connect and start a new thread with a VERY specific title. Paste your lspci (sans usb card) and exactly what errors you are getting and from what exactly source they are coming from.

You should attract the attention of a few people who have seen the error before. That's the best way to get things done here. If you are giving vague info most people will assume they can't help you. You have to be specific about every reply until the problem is fixed.

Good Luck!

---

