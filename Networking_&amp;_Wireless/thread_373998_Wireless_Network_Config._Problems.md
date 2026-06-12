---
title: "Wireless Network Config. Problems"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by kurtkn on 2007-03-01
Hey I was wondering if anyone can help me out. I just installed Ubuntu Edgy Efft recently and I can't get my wireless card to connect. I'm running an HP laptop with a AMD Turion64 Mobile and Ati Xpress 200m. When I try to check my card type it says "Broadcom Dell Wireless" Why would my HP laptop have a Dell card? I'm not really sure where to go with this all i know is that when i run networkmanager i can't connect.

thanks for any help in advance

---

### Post by Floppyjoe on 2007-03-01
Are you familiar with the terminal?
To open a terminal click on Applications/Accessories/Terminal.
Could you post the output of the following commands when entered into the terminal?
If your wireless device is a USB device then:
```
lsusb
```
otherwise:
```
lspci
```
Posting the output of:
```
iwconfig
```
might also help.

---

### Post by kurtkn on 2007-03-02
okay, sorry for the late reply and thank you for your help here are my read-outs as you have requested...

For lspci:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation Dell Wireless 1470 DualBand WLAN (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

for iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Thanks for your help again!

---

### Post by jml on 2007-03-02
Did you buy the laptop new from a store or from the manufacturer?  If yes, then I would first contact them and ask for an explanation.  If you bought the laptop used then its quite possible that the person who owned the laptop before you, may have installed a Dell branded Broadcom wireless card.

The bad news is that getting a Broadcom 43xx card working in Ubuntu can be hit or miss.  If you search this sub-forum for the terms Broadcom and wireless, you will find several posts on the subject.  In general terms here is what you may have to do.  Blacklist the Broadcom driver installed by default, (again searching this forum for blacklisting will help.) It seems that the native driver does not work reliably.  You will then need to download and install an application called ndiswrapper.  You will then use this application to "wrap" around the Window's driver for the Broadcom card.  The Windows driver can be found on the driver CD that usually ships with the laptop.  Once you get the card recognized by your system, then download two applications, network-manager, and network-manager-gnome.  This application does a good job of managing your network options, including setting up WPA encryption if needed.

Joe

---

### Post by kurtkn on 2007-03-02
Thanks a lot Joe for the insight, I will give it a try as soon as I get some free time. 

I really appreciate the help.

---

### Post by kurtkn on 2007-03-03
Alright I'm getting an error at the step:

"sudo modprobendiswrapper" ... i get

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Any thoughts as to what is failing? Up until this point everything has been going smoothly

---

### Post by kurtkn on 2007-03-03
**correction** "sudo modprobe ndiswrapper"

---

### Post by Floppyjoe on 2007-03-03
What is the result of:
```
ndiswrapper -l
```?

---

### Post by kurtkn on 2007-03-03
ndiswrapper -l

Installed drivers:
bcmwl5           driver installed, hardware present


so that seems to be in place, yet the modprobe is still coming up in an error

---

### Post by kurtkn on 2007-03-03
Also I should tell you that when i click on the network manager icon in the top right corner of my desktop screen my wireless card is not listed there. Only my wired and modem connection. I don't know if that will help you in identifying the problem or not.

---

### Post by Tahir on 2007-03-03
did you remove and blacklist the bcm43xx modules?If you dont then it wont work.  Do this:  (if you have not already)

Open the blacklisting file:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add this line to it:
```
blacklist bcm43xx
```
After saving it, type at the terminal:
```
sudo rmmod bcm43xx
```

then:

```
sudo modprobe ndiswrapper
```

after that, perhaps reboot, then type the following:

```
sudo iwlist scan
```

And copy/paste the results here and then we will see...

MAKE SURE THAT YOUR ROUTER IS BROADCASTING THE SSID THOUGH!!!

---

### Post by kurtkn on 2007-03-03
Alright, i did the above commands before and i did them again to double check, and yes my router is broadcasting SSID the results

sudo rmmod bcm43xx:

ERROR: Module bcm43xx does not exist in /proc/modules

sudo modprobe ndiswrapper:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

sudo iwlist scan:

lo             Interface doesn't support scanning.
sit0          Interface doesn't support scanning
eth0         Interface doesn't support scanning.

I just tried to wire the connection up as well and it seems like now my wired internet isn't working as well since i tried configuring the wireless.

any thoughts?

---

### Post by lavinog on 2007-03-04
Are you using a 64 bit distro or 32. there is a different bcmwl5 driver for each. I have found that the driver that came preinstalled didn't work on either 32 or 64 I had to try different drivers that were posted throughout the forums until one worked.
Unfortunatly my wireless on my 64bit partition isn't working after I upgraded my kernel and restricted kernel modules from 2.6.17.10 to 2.6.17.11, I wonder if there is an issue with the kernel.

---

### Post by kurtkn on 2007-03-04
I am using 64bit... perhaps that is the where the problem is taking place?

---

### Post by Tahir on 2007-03-04
Hello kurt,

I am a newbie myself and perhaps I cant help you out but I searched on the internet for ndiswrapper problems and loading the module into the kernel and I found this:

Look at marty's comment
[http://forums.fedoraforum.org/archive/index.php/t-18715.html](http://forums.fedoraforum.org/archive/index.php/t-18715.html)

I dont know whether that will help you because in order to follow the guidance you need to know how to recompile your kernel and stuff like that (probly need to learn a few more commands).  Ask around and hopefully you will get answers.  I dont know how to do those things myself but sooner or later I might have to.   Considering you have the 64-bit kernel its going to cause compatibility issues.

---

### Post by lavinog on 2007-03-04
> **kurtkn said:**
> I am using 64bit... perhaps that is the where the problem is taking place?
i just finished fixing my 64bit wireless
i went ahead and compiled the latest version of ndiswrapper and that fixed the problem
that i was having
 you should post your **dmesg** output

mine was giving me an error at the ndiswrapper section with the 2.6-17-11 kernel:
```
[   30.111354] ndiswrapper (NdisWriteErrorLogEntry:241): log: 13D519B0, count: 1, return_address: ffffffff881de13e
[   30.132013] ndiswrapper (NdisWriteErrorLogEntry:244): code: 271
[   30.152399] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[   30.172813] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[   30.193700] ndiswrapper (miniport_halt:327): device ffff8100139b9500 is not initialized - not halting
[   30.215044] ndiswrapper: device eth%d removed
[   30.236013] unregister_netdevice: device eth%d/ffff8100139b9000 never was registered
[   30.236023] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[   30.256994] ndiswrapper: probe of 0000:06:02.0 failed with error -22

```

while the 2.6-17-10 kernel worked fine:
```
[   29.831185] ndiswrapper version 1.23 loaded (preempt=no,smp=yes)
[   29.962917] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[   29.983898] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   30.003677] GSI 20 sharing vector 0xE1 and IRQ 20
[   30.022904] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 225
[   30.051152] ndiswrapper: using irq 225
[   30.722683] wlan0: vendor: ''
[   30.742066] wlan0: ethernet device 00:14:a5:ee:bd:aa using NDIS driver bcmwl5, 14E4:4318:103C:1355.5.conf
[   30.762146] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.824721] ndiswrapper: changing interface name from 'wlan0' to 'eth0'

```

I compiled the latest version of ndiswrapper using this guide:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")
because my card was a bcm4318 and not a 4311 i just used the driver from my windows partion.

after all of that i was able to connect with iwconfig, but not wifi-radar
wifi-radar detected all (7) wireless networks in my area, but would not get an ip address from mine.
after running it in a terminal i got an error saying that "set frequency" is not valid. so i changed the channel from auto to a set number and everything worked.

---

