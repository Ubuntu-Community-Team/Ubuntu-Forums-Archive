---
title: "Wireless Internet Setup...Firmware Missing..."
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Shtickboy on 2011-06-28
I need help setting up my wireless internet through Ubuntu 11.04, it says that the Firmware is missing...I don't know what to do...I am a Newbie to this forum and to Ubuntu, never used or touched it before, only heard about it...
 
If possible, make it step by step and very easy to understand, because I am lost and confused and it could very easy to make me even more confused and lost
 
I have tried all my other options and I cannot seem to get anybody else to help me or knows how to do it...This is my last option before I uninstall it and not use a Linux OS again...
 
Devon West :confused:

---

### Post by ratcheer on 2011-06-28
Please post the output of "sudo lspci -v".

Tim

---

### Post by Shtickboy on 2011-06-28
I am sorry, but where would I go to do that?? I don't understand command line very well...

---

### Post by Shtickboy on 2011-06-28
to understand better maybe, I installed with the run along with windows version...I am excellent with Windows OS but, I don't understand Linux at all...where or what do I do in order to put "sudo lspci -v"? If you could possibly give me directions (ratcheer)...Thanks

---

### Post by ratcheer on 2011-06-28
Start an application called Terminal. That will give you the "command line". Enter the command I gave without the quotation marks. You will then have to enter your password to be given root authority. Then copy the output (you only need the section for the wireless card) and paste it to a forum reply.

Tim

---

### Post by Shtickboy on 2011-06-28
ok, I found the Terminal App...I got the Sudo line in there and it asked for the password, it would not let me type or copy/paste...Now what do I do?? (ratcheer)

---

### Post by Rex Bouwense on 2011-06-28
Just type in your password.  It will look like nothing is happening but continue to put in your password and hit enter.  That will do it.

---

### Post by Shtickboy on 2011-06-28
Here is the output from [FONT=Times New Roman]sudo lspci -v
 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Subsystem: Dell Wireless 1397 WLAN Mini-Card
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at f69fc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Capabilities: [58] Vendor Specific Information: Len=78 <?>
Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
Capabilities: [d0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
Capabilities: [13c] Virtual Channel
Capabilities: [160] Device Serial Number ad-68-a1-ff-ff-34-70-f1
Capabilities: [16c] Power Budgeting <?>
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb
 
What Next??

---

### Post by Shtickboy on 2011-06-28
[FONT=Times New Roman][SIZE=3]Rex or ratcheer, I don't know what to do now, so if one of you could help me out, that would be great...I am signing off - so, I will catch your response on here ASAP...Thanks...[/SIZE][/FONT]

---

### Post by gandaran on 2011-06-28
> **Shtickboy said:**
> [FONT=Times New Roman][SIZE=3]Here is the output from [FONT=Times New Roman]sudo lspci -v[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][/FONT][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][FONT=Times New Roman]0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)[/FONT]
[FONT=Times New Roman]            Subsystem: Dell Wireless 1397 WLAN Mini-Card[/FONT]
[FONT=Times New Roman]            Flags: bus master, fast devsel, latency 0, IRQ 17[/FONT]
[FONT=Times New Roman]            Memory at f69fc000 (64-bit, non-prefetchable) [size=16K][/FONT]
[FONT=Times New Roman]            Capabilities: [40] Power Management version 3[/FONT]
[FONT=Times New Roman]            Capabilities: [58] Vendor Specific Information: Len=78 <?>[/FONT]
[FONT=Times New Roman]            Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+[/FONT]
[FONT=Times New Roman]            Capabilities: [d0] Express Endpoint, MSI 00[/FONT]
[FONT=Times New Roman]            Capabilities: [100] Advanced Error Reporting[/FONT]
[FONT=Times New Roman]            Capabilities: [13c] Virtual Channel[/FONT]
[FONT=Times New Roman]            Capabilities: [160] Device Serial Number ad-68-a1-ff-ff-34-70-f1[/FONT]
[FONT=Times New Roman]            Capabilities: [16c] Power Budgeting <?>[/FONT]
[FONT=Times New Roman]            Kernel driver in use: b43-pci-bridge[/FONT]
[FONT=Times New Roman]            Kernel modules: ssb[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]What Next??[/FONT][/FONT][/SIZE][/FONT]
try connecting to wired internet and update software package list
```
sudo apt-get update
```
then look in additional drivers for the broadcom wireless driver to activate it, this should get the wireless device working.
if you don't find any drivers in additional drivers after running the update or the driver didn't work follow this thread
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by ratcheer on 2011-06-28
You will probably need a lot of help to install and configure it, but here is the driver you should be using:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Tim

---

### Post by Zill on 2011-06-28
Shtickboy:  It looks like you have a Broadcom Corporation BCM4312 card.

See the Ubuntu Documentation entitled [WifiDocsDriverbcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") for full driver installation instructions.

---

### Post by Shtickboy on 2011-06-29
ok so after I do this: You will probably need a lot of help to install and configure it, but here is the driver you should be using: [[COLOR=#000000]http://www.broadcom.com/support/802.11/linux_sta.php[/COLOR]]("http://www.broadcom.com/support/802.11/linux_sta.php")  
     
  I went to: See the Ubuntu Documentation entitled [[COLOR=#000000]WifiDocsDriverbcm43xx[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") for full driver installation instructions.  
     
  I printed that off...Do I follow this part of the whole Manual - [COLOR=olive]**Installing STA drivers, **[COLOR=olive]STA - No Internet access, 

[COLOR=black]If you do not have any other means of Internet access on your computer, you will have to install the bcmwl-kernel-source package from the [/COLOR][[COLOR=black]restricted[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu")[COLOR=black] folder under **../pool/restricted/b/bcmwl** on the Ubuntu install media. [/COLOR]
[COLOR=black]**Note:** Systems installed from CDROM can simply add the install CD as a [/COLOR][[COLOR=black]package source[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu")[COLOR=black] and install bcmwl-kernel-source, automatically installing the required dependencies. [/COLOR]
[COLOR=black]**Note:** The following instructions are for a stock Ubuntu 10.04 LTS Edition via USB install. Netbook edition, other variations and matured systems may require more/less packages be installed to satisfy dependencies of bcmwl-kernel-source. [/COLOR]
[COLOR=black]**Note:** The GUI front end for dpkg will automatically display required packages that need to be installed to satisfy the bcmwl-kernel-source dependencies. To use the front end, navigate the file system using the file manager and double click on the packages to install/list required dependencies. [/COLOR]
[COLOR=black]**Step 1.** [/COLOR]
[COLOR=black]Navigate the install media and install the packages listed below by double clicking **or** navigate the install media and install these packages consecutively in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**): [/COLOR]
[COLOR=black]../pool/main/d/dkms [/COLOR][COLOR=black]:/dkms/$ sudo dpkg -i dkms*[/COLOR]
[COLOR=black]../pool/main/p/patch [/COLOR][COLOR=black]:/patch/$ sudo dpkg -i patch*[/COLOR]
[COLOR=black]../pool/main/f/fakeroot [/COLOR][COLOR=black]:/fakeroot/$ sudo dpkg -i fakeroot*[/COLOR]
[COLOR=black]../pool/restricted/b/bcmwl [/COLOR][COLOR=black]:/bcmwl/$ sudo dpkg -i bcmwl-kernel-source*[/COLOR]
[COLOR=black]**Step 2.** [/COLOR]
[COLOR=black]Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. [/COLOR][COLOR=black]**Note:** A computer restart may be required before using the wifi card.[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]or is there something else that I am suppose to follow??[/COLOR]

---

### Post by ratcheer on 2011-06-29
I am not sure. If I were doing it for myself, I would follow the instructions in the readme.txt file on the Broadcom website page referenced.

I had the same problem (wrong driver loaded by Ubuntu) with my Realtek NIC. I downloaded the correct driver from the Realtek website, followed their instructions for making the module, blacklisted the wrong module, and updated initramfs to make the system load my new module. After that, my NIC worked perfectly. But, it is all fairly complex.

Some people say that you can simply blacklist the "wrong" driver and reboot, but that did not work for me.

Tim

---

### Post by Rex Bouwense on 2011-06-29
Do you have a wired connection to the Internet?  If you said I missed it.  That would be a much easier way to get the Broadcom driver.  I had to do that for my old Dell 1350 wireless card.

---

### Post by Shtickboy on 2011-06-29
The Readme.txt File is not very easy for me to understand, and no matter what command I put in there it gives me an error...I will try the wired connection and see what happens...

---

### Post by spidertattoos on 2011-06-29
enter in terminal

**rfkill list**

if it says
wirless 
softblocked yes
hardblocked no

enter [B]
sudo rfkill unblock wifi

[/B]also if its a driver fault then you need the previous driver
easy enough to find and download.
make sure you have the b43 fwcutter & bcmwl kernel installed through synaptic

this problem is random though as sometimes it happens again so just repeat the above steps if it happens again. it took me weeks to figure out and hopefully there will be a more permanent fix sometime soon.:guitar:

---

### Post by Shtickboy on 2011-06-29
Rex, when you connected to the internet (wired), what did you do to get the driver (firmware)?? When I connected, it put 178 updates on there and I really don't know what to do after I am connected...I am more lost than I was to begin with now...

---

### Post by gandaran on 2011-06-29
installing the broadcom driver should be very easy if you have wired internet, did you check in additional drivers to activate the driver?
read my post #10 again.

---

### Post by Zill on 2011-06-29
> **Shtickboy said:**
> ...I will try the wired connection and see what happens...
It is *always* easiest to get wifi working while your PC is already connected to the internet via a wired connection.  Just use a standard Ethernet cable to connect your PC directly to your router.  If the router has been configured correctly (i.e. with ISP username/password details etc) then Ubuntu should automatically connect the PC to the internet.  If Google opens OK in your browser this will verify the connection is working.

At this stage, ensuring the wifi card is connected, check to see if the right drivers are already available, as detailed in the [document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") I referred to earlier:
> The proprietary drivers can be activated under the desktop menu System > Administration > Hardware/Additional Drivers using an existing Internet connection (Ethernet or USB) for best results.
If no wifi drivers are listed then please open a terminal and post the output of the following command:
```
lspci -vvnn | grep 14e4
```

---

### Post by Rex Bouwense on 2011-06-29
I am using Lucid Lynix (Ubuntu 10.04).  I am not sure where you will find it in the version you are using but these folks are trying to tell you to check under System->Administration->Hardware Drivers to see if there is an additional driver listed.  If there is, you need to activate or enable it.  Since you already have installed the updates that were available, that should be all that you have to do.

---

### Post by Shtickboy on 2011-06-29
I connected it back to the wired internet connection and after a little while it popped up saying that I could download and install the wifi driver...I was able to activate it and use the wireless internet...Thanks for your help everyone...I will be sure to get back on here if I have any other problems that arise...

---

### Post by Shtickboy on 2011-06-29
I do not need anymore help on this topic...It has been resolved...

---

### Post by Zill on 2011-06-29
> **Shtickboy said:**
> I do not need anymore help on this topic...It has been resolved...
Pleased you got things working OK. :-)

Would you now please go to the "Thread Tools" near the top of the page and mark the thread as "Solved" to assist users searching in future.  Only the original poster can do this for a thread.

---

### Post by bigrthau on 2011-07-13
I have the same problem, I am using a hp pavilion zd7000, computer says firmware is missing for wireless controller. I am well experienced in windows but very new to linux and how everything works. if anyone can help me. It will be greatly appreciated, i typed in "sudo lspci -v" into the terminal and this is what i got.
thank you.





00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, fast devsel, latency 0
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [e4] Vendor Specific Information: Len=06 <?>
    Capabilities: [a0] AGP version 3.0
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 96
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=80
    Memory behind bridge: d1000000-d1ffffff
    Prefetchable memory behind bridge: e0000000-efffffff
    Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff) (prog-if ff)
    !!! Unknown header type 7f

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1cc0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1ce0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 2000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d2000000-d23fffff
    Prefetchable memory behind bridge: 20000000-23ffffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 2040 [size=16]
    Memory at 24000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 006a
    Flags: medium devsel, IRQ 10
    I/O ports at 2020 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1400 [size=256]
    I/O ports at 1c80 [size=64]
    Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
    Memory at d0000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: medium devsel, IRQ 17
    I/O ports at 1800 [size=256]
    I/O ports at 1c00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 006a
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 3.0
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nouveau, nvidiafb

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at 3000 [size=256]
    Memory at d2007800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at d2006000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 28000000-2bfff000
    I/O window 0: 00003400-000034ff
    I/O window 1: 00003800-000038ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
    Subsystem: Hewlett-Packard Company NX9500
    Flags: medium devsel, IRQ 18
    I/O ports at 3c00 [size=128]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: cb710
    Kernel modules: cb710

02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company NX9500
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at d2007000 (32-bit, non-prefetchable) [size=2K]
    Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
    Subsystem: Compaq Computer Corporation Device 00e7
    Flags: bus master, fast devsel, latency 32, IRQ 21
    Memory at d2004000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

me@ubuntu:~$

---

### Post by Zill on 2011-07-13
bigrthau:  Have you tried to activate proprietary drivers as described in my post [#20]("http://ubuntuforums.org/showpost.php?p=10994462&postcount=20") and others in this thread?

---

### Post by wildmanne39 on 2011-07-13
Hi, here is a link for instructions on getting your card working it is the 4306. You will need to scroll down the page until you see the 4306.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by westie457 on 2011-07-13
bigrthau my suggestion to you is plug in an ethernet cable and open a terminal. 

Run ```
sudo apt-get update
```

Type your password when prompted. Nothing will show on the screen but it will register.

And ```
sudo apt-get install b43-fwcutter
```

and ```
sudo apt-get firmware-b43legacy-installer
```

If you have already enabled the STA Driver via Additional Drivers open the Additional Drivers program and de-activate it. After this you will have to reboot to complete the removal of the driver. All should now be okay.

---

