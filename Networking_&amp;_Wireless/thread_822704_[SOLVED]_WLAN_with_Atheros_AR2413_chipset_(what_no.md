---
title: "[SOLVED] WLAN with Atheros AR2413 chipset (what now?)"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by causeitsme on 2008-06-08
I posted earlier about my problems with getting my wireless to work. 
Although that thread is probably irrelevant now it is [HERE]("http://ubuntuforums.org/showthread.php?t=773163") .  

I am now at this point......

I have installed the madwifi-ng-r2756+ar5007 - this didn't help anything

I then did a ndiswrapper and didn't have any luck there either

I then downloaded madwifi-0.9.4 and following the INSTALL readme text instructions I did a 'make clean' then a 'make' then a 'sudo make install' and finally a '# modprobe ath_pci'.

When I go to System>Administration>Network I get this box. I unticked 'Enable Roaming' as my router requires a password and I wasn't being asked for one. So once 'Enable Roaming' was unticked I entered the data you see here...[[IMG]http://img141.imageshack.us/img141/6416/1001177modifiedkf5.th.jpg[/IMG]](http://img141.imageshack.us/my.php?image=1001177modifiedkf5.jpg)

When I right click on the network icon and select 'Edit Wireless Networks...' and I get this box...[[IMG]http://img141.imageshack.us/img141/5240/screenshotwirelessnetwoln7.th.png[/IMG]](http://img141.imageshack.us/my.php?image=screenshotwirelessnetwoln7.png)
Which as you can see has no data entered in any of the boxes.
Should there be data there?
 
Below I have listed some data that may or may not be relevant.

Section 1 
--------------------------------------------------------------------

PCI buses and devices

bobby@bobby-laptop:~$ lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
bobby@bobby-laptop:~$ 




Section 2
------------------------------------------------------------
Blacklist
I put this command in at Terminal:

bobby@bobby-laptop:~$ gksudo gedit /etc/modprobe.d/blacklist

Below is a copy of the text file that was generated:
 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

I show you the blacklist now as prior I had entered a blacklist for ath-pci as referenced on another tutorial I was following that didn't work. I have since removed that blacklist entry and now this is what is left.

So, what now? Do I need to enter other data somewhere? How is it that belkin54g automatically popped up and it didn't ask me for my WPA password. Why does it show belkin54g with 95%? What does that 95% mean? Is that the percentage of signal I'm receiving?

Any help getting this resolved would be greatly appreciated and I hope I didn't make this to long to get help.

Bobby

---

### Post by confuded92 on 2008-06-08
Why don't you use synaptic to install madwifi? Try this. It might be the drivers compiled incorectly or something, leaving you with no passkey detection... (WPA or WEP). It's just a theory, but is worth trying... 

Does the card scan and detect the AP (Acces point) at all?

~confuded

---

### Post by causeitsme on 2008-06-09
> **confuded92 said:**
> Why don't you use synaptic to install madwifi? Try this. It might be the drivers compiled incorectly or something, leaving you with no passkey detection... (WPA or WEP). It's just a theory, but is worth trying... 

Does the card scan and detect the AP (Acces point) at all?

~confuded

Hi confuded,

I tried synaptic to install madwifi, but, the only thing listed there was:

madwifi-tools

Which is described as:

tools for the Multiband Atheros Driver for WiFi
This package provides userspace tools for the madwifi driver. The tools are
required to use and manipulate the madwifi interfaces present in a system.

I installed this.

Is this an interface that I can use? I can't seem to find it anywhere under Applications or System.

Re your question "Does the card scan and detect the AP (Acces point) at all?" 

I don't really know, nothing has ever popped up saying that there was a network discovered. The only thing that indicates to me that it has found the network is the fact that it shows up in the Network Name (ESSID) dropdown box when you go to System>Administration>Network and select wireless network properties and untick 'Enable Roaming'. (As referenced by the first thumbnail shown above in my first post in this thread)

---

### Post by causeitsme on 2008-06-09
By the way, I did a iwconfig and below is the result, does that mean anything to anyone?

-------------------------------------------------------------------------------------------
This is with 'Enable Roaming' unticked.

bobby@bobby-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:23830  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bobby@bobby-laptop:~$

------------------------------------------------------------------------------
This is with 'Enable Roaming' ticked.

bobby@bobby-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"belkin54g"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:01:4E:1A   
          Bit Rate:54 Mb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-29 dBm  Noise level=-94 dBm
          Rx invalid nwid:26075  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bobby@bobby-laptop:~$

---

### Post by causeitsme on 2008-06-09
It's FIXED !!!

I followed the instructions on this site: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Everything worked great as soon as I rebooted. 

Mark this one as solved.

---

