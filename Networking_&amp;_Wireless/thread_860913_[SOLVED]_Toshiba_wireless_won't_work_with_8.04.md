---
title: "[SOLVED] Toshiba wireless won't work with 8.04"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by cybrsaylr on 2008-07-16
Installed HH on my new couple month old Toshiba laptop as a dual boot system  with Vista a couple days ago. So far everything is running great except for the wireless, which I can't get to work. Been using Ubuntu about a year on my desktop as a dual boot with XP. I can't get the wireless to work with Ubuntu but it works fine with Vista. I have a Belkin wireless router that shows excellent signal but only works on Vista but can't get Ubuntu to recognize it so I have to stay hardwired to get on the net with the laptop. Tried some of the recommended fixes on this forum but so far nothing worked. Can anyone point me in the right direction to get it working?

---

### Post by thegodfaza on 2008-07-16
Post the output of lspci and are you running a 32 bit os or a 64 bit os?

---

### Post by cybrsaylr on 2008-07-16
I'm running 32 bit Vista and Ubuntu 8.04LTS as a dual boot.


tt@tt-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by thegodfaza on 2008-07-16
Your lspci perfectly matches mine so just follow these steps.
1) Download [ndiswrapper.]("http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&71847613")
2) Download your [cards drivers.]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1")
3) Extract both folders. Either tar zxvf or right click and select extract.
4) In terminal navigate to the folders directory.
5) Run ```
sudo apt-get install build-essential
```
6) cd into the ndiswrapper folder.
7) Run ```
make
sudo make install
ndiswrapper -i /directory/to/driver/netathw.inf
ndiswrapper -m
depmod -a
```
8) And just to make sure it starts up right.```
sudo nano /etc/modules
add ndiswrapper to the end of the file
```
9) Blacklist ath_pci
```
sudo nano /etc/modprobe.d/blacklist
```
Add this to the end
```
# replaced by ndiswrapper
blacklist ath_pci
```
10) Remove the default HAL. Go to System > Administration > Hardware Drivers. Uncheck Atheros Hardware Access Layer(HAL).
11) Reboot

And if you haven't used nano before, to save you press Ctrl + x, then y, then enter.

---

### Post by oneiromancer on 2008-07-16
I'm dealing with a similar problem (been avoiding dealing with it for about a month now actually, and hoped that 8.04.1 might fix it), and I checked my lspci against posted one, looked identical in all areas that mattered, so I tried the posted solution...  it all went fine, but wireless still doesn't work, or in any case, doesn't...  um...  that was weird...  I was about to say it still doesn't show up as an option under networking in top right corner, but as I went to verify it wasn't there, a "configure wireless networks" option was there for the first time...  I selected it, and no networks were listed, I exited out, and now the config. option is gone again...  spooky...

Anyway, I'm fairly puzzled, and by the way, in addition to Hardware Drivers saying Atheros HAL is "not in use" (after I unchecked enabled and restarted), it also said "not in use" for "Support for Atheros 802.11 wireless LAN cards", which I left checked, and was still checked, and had a previous status of "in use", even though it didn't seem to be working.

I'll appreciate any help!  I've had to use Winbloze almost exclusively on this laptop, as OS X won't run on it, and w/o wireless its not very portable.  Thanks!

My lspci in case it matters:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
17:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by thegodfaza on 2008-07-16
Make sure you uninstall all other wireless drivers and the only restricted driver you should get rid of is the HAL.

---

### Post by cybrsaylr on 2008-07-16
> **thegodfaza said:**
> Make sure you uninstall all other wireless drivers and the only restricted driver you should get rid of is the HAL.

Just got done attempting to do what you suggest in post #4 and still can't get wireless to connect. 

I'm not real familiar with terminal and such, so it is possible I messed up some trying to follow those directions. When I've used terminal in the past there were not that many steps to follow. 

I did try a couple times to follow those steps but in the end wireless still does not work with 8.04. This is more complicated than expected.

---

### Post by thegodfaza on 2008-07-17
There is usually a higher success rate with fresh installs. If you want I can write a script when I get a chance to do it automatically.

---

### Post by oneiromancer on 2008-07-17
By the way, I forgot to mention, I'm running 64bit, not 32, do you think that could make any difference?  Should it make your patch not work, and/or does it change your reccomended process?  I'm uninstalling Atheros drivers via Synaptic right now, we'll see if that helps any...

---

### Post by thegodfaza on 2008-07-17
64 bit doesn't work all that well.

---

### Post by cybrsaylr on 2008-07-17
I did a fresh install off the CD Ubuntu mails out.
That went through OK, then did the 233 updates that followed OK to.
Everthing is running OK except wireless on I believe my 32 bit dual boot setup with Vista. 

I uninstalled the Atheros drivers as suggested but it had no effect.

---

### Post by thegodfaza on 2008-07-17
You also have to work through my guide and install ndiswrapper and all that jazz. Did you set it so ndiswrapper starts when you boot up. Did you blacklist ath_pci? Did you only disable Atheros HAL and not the other Atheros Driver?

---

### Post by lisati on 2008-07-17
Please forgive me if this is obvious, but is the wireless switch on your laptop in the "on" position? On my Toshiba laptop (one of the A100 range) it doesn't seem to affect the output of lspci, but will make a difference when you try to connect.

---

### Post by cybrsaylr on 2008-07-17
> **lisati said:**
> Please forgive me if this is obvious, but is the wireless switch on your laptop in the "on" position? On my Toshiba laptop (one of the A100 range) it doesn't seem to affect the output of lspci, but will make a difference when you try to connect.

Yes it's on, the orange light is on.

[QUOTE=thegodfaza]You also have to work through my guide and install  and all that jazz. Did you set it so ndiswrapper starts when you boot up. Did you blacklist ath_pci? Did you only disable Atheros HAL and not the other Atheros Driver?[/QUOTE]

Installed ndiswrapper OK but had a problem extracting the drivers downloaded. As I said I'm not real familiar with terminal and added those lines of code one at a time to terminal. Some went right through, others gave a 'wierd' terminal screen as I went along. I did  blacklist ath_pci and did only disable Atheros HAL and not the other Atheros Driver.

---

### Post by lordhedgehog on 2008-07-18
I´m having the same problem with a fresh install on a Toshiba Satellite L355D-S7809.  I used the drivers from Toshiba´s website, following your directions, and while lspci shows the card, eth0 and lo are my only network interfaces.

I installed 64bit Ubuntu, and used the Vista 64bit drivers -- do I need to reinstall 32bit Ubuntu to get wireless to work?

```

lordhedgehog@ubuntu:~$ ndiswrapper -l
netathrx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

lordhedgehog@ubuntu:~$ ifconfig -a -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0      2364      0 19480591962 0          2211      0      0      0 BMRU
lo        16436 0       160      0      0 0           160      0      0      0 LRU

```

---

### Post by Tigin on 2008-07-18
Oneiromancer , i am kinda noob but i have a solution worked for me well several times.

Try this IF YOUR WIRELESS CARD IS ATHEROS AR5007EG (AR242x 802.11abg same)  for 64bit :


"" sudo apt-get install build-essential ""

get this file :[http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2](http://primepage.de/downloads/stuff/misc/madwifi_patch.tar.bz2)

run ""install sh"" ( double click on it and hit "run in terminal" again or drag it to terminal then hit "enter" )

then uncheck "atheros Hardware Access Layer (HAL)" and "support for atheros 802.11 wireless lan cards" in "SYSTEM>ADMINISTRATION>HARDWARE DRIVERS" menu , then restart.

cheers

---

### Post by lordhedgehog on 2008-07-18
Tigin,

Worked like a charm with my Toshiba and 64bit.  It prompted me to uninstall ndiswrapper, which I did, then it worked flawlessly on reboot, WPA2 and all.

---

### Post by Tigin on 2008-07-18
Heh heh glad to hear it worked :D 

Just in case keep the   "tar.bz2" file you downloaded via link , once i had to  

download it again after a kernel update .

/cheers

---

### Post by cybrsaylr on 2008-07-19
SUCCESS! 
Problem solved!

I now have wireless!
I was going through this forum and came across this thread that gave me the solution:

[http://ubuntuforums.org/showthread.php?t=863777](http://ubuntuforums.org/showthread.php?t=863777)

I followed the directions joelbrochill posted and now have a wireless network installed that works!

Thanks for all those that helped me out on this...):P

---

### Post by thegodfaza on 2008-07-19
I must warn you I did not suggest madwifi because even though it works some people have problems when trying to sleep or hibernate.

---

### Post by cybrsaylr on 2008-07-19
> **thegodfaza said:**
> I must warn you I did not suggest madwifi because even though it works some people have problems when trying to sleep or hibernate.

Thanks for the warning. 
What should I watch out for?

I do notice that the wireless connection is not as fast as when I was hardwired. With wireless there is more of a lag for pages to load that wasn't as noticable when hardwired. Other than that all seems well so far.

My desktop that had Gutzy used to have problems with when it would sleep or hibernate. I couldn'get get get out of hibernation, so I set it not hibernate. When I upgraded to Hardy of the desktop I didn't test it out on this yet.

---

### Post by Tigin on 2008-07-19
> **thegodfaza said:**
> I must warn you I did not suggest madwifi because even though it works some people have problems when trying to sleep or hibernate.









weird , i had no problem since i set them on this laptop .

---

