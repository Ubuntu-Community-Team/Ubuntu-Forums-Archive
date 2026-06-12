---
title: "Intellinet USB Wireless adapter"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by mastahchanta on 2008-04-30
Just installed ubuntu 8.04 and internet doesnt works. I have a usb wireless adapter brand Intellinet.
What should i do to make it work? My family wont use ubuntu if theres no internet.

Thanks a lot.

---

### Post by garyedwardjohnston on 2008-04-30
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by mastahchanta on 2008-04-30
That's chinese... how the hell do you expect windows migration?

---

### Post by zvbxrpl on 2008-05-01
Wireless support in Ubuntu is actually much better than in Windows,  which almost always requires a driver CD to be loaded before you can use it.  What you need to know is that the make of your wireless device is unimportant: what matters is the chipset inside it.  To find out what the chipset is, go to a terminal and type:

lspci

Cut and paste the results here.

---

### Post by mastahchanta on 2008-05-01
says something like:
intel corporation usb 82801eb

---

### Post by zvbxrpl on 2008-05-01
That's the USB controller on your computer and not the wireless adapter.  Please can you paste the whole of the output of lspci?

---

### Post by mastahchanta on 2008-05-03
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600XT] (rev a1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by zvbxrpl on 2008-05-04
Thanks for sending that information.  By the looks of things, your machine is a desktop rather than a laptop, correct?

Assuming that your wireless USB adapter was plugged in when you ran the lspci command, there is no entry in the list you sent that corresponds to your wireless adapter.  The Realtek device is a wired network adapter (maybe built into your computer's motherboard).

Is this device the same as the wireless USB adapter that you have?

[http://www.intellinet-network.com/html/521499.htm](http://www.intellinet-network.com/html/521499.htm)

At the moment Ubuntu is not detecting your wireless adapter at all.    With Ubuntu running, unplug the adapter, type dmesg in the terminal, and make a mental note of the last couple of lines of text that command provides you with.  Then plug the adapter in, type dmesg again, and see if there are any new messages.  If you see any, please copy and paste them here.  If you don't see any, try plugging the wireless adapter into a different USB port and repeat the process.

---

### Post by mastahchanta on 2008-05-04
Thats the device
Heres dmesg after plugging the device:

[   89.316185] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   89.317020] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  111.042128] usb 5-3: USB disconnect, address 2
[  111.044350] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[  111.044365] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[  111.044371] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[  111.044376] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[  111.044382] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[  111.044388] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[  152.526747] usb 5-3: new high speed USB device using ehci_hcd and address 5
[  152.798768] usb 5-3: configuration #1 chosen from 1 choice
[  153.064445] phy1: Selected rate control algorithm 'simple'
[  153.177977] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  170.183965] usb 5-3: USB disconnect, address 5
[  170.184391] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[  170.184408] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[  170.184414] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[  170.184420] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[  170.184426] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[  170.184431] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[  170.562907] usb 5-3: new high speed USB device using ehci_hcd and address 6

---

### Post by zvbxrpl on 2008-05-04
Thanks for the additional information.  Your wireless device uses a Ralink chipset.  Unfortunately, Ralink chipsets are rather problematic in Ubuntu.  The best way to get it working is to use the Windows driver that came on the CD with the device, and a program called ndiswrapper which adapts the Windows drivers for Ubuntu.  With the wireless device plugged in, type lsmod | grep rt and make a note of the output.  (The '|' symbol is to the left of the letter z on a UK keyboard).  That will tell you which driver ubuntu is trying to use.

Then cut and paste the lines of code in this thread to remove Ubuntu's own driver, install ndiswapper and load the Windows drivers instead:

[http://ph.ubuntuforums.com/showthread.php?t=564419](http://ph.ubuntuforums.com/showthread.php?t=564419)

You will need to have your computer connected via the wired ethernet to install ndiswrapper.  When you reach the blacklisting step, blacklist the drivers you noted when you ran the lsmod command.

If you don't have any luck, you might like to consider replacing your wireless USB adapter with a wireless bridge.  I noticed that your adapter only supports WEP encryption and not the more secure WPA.  WEP isn't much good these days - it's easily cracked using widely available tools.  You might want to take a look at:

[http://www.buffalo-technology.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-ethernet-converter/](http://www.buffalo-technology.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-ethernet-converter/)

What this device does is to convert your wired ethernet connection into a wireless one.  It's configured via a web interface, so it doesn't matter what computer you use.  I own one of these and they're great - you can plug up to 4 computers into them.  The signal is much more powerful as well.

---

### Post by mastahchanta on 2008-05-07
if i cant connect a ethernet cable im screwed?

---

### Post by zvbxrpl on 2008-05-07
Is there any particular reason why you can't use a wired connection?  By the look of your lspci output, your ethernet card (Realtek) is being detected just fine.

If you decide to go for a wireless bridge, you will of course need to use your wired ethernet port to connect to it.  If you want to try configuring your existing wireless USB device using ndiswrapper and the Windows driver, I think there is a copy of ndiswrapper on the Ubuntu CD, meaning you don't have to go online to download it.  Put the CD in the drive before installing ndiswapper ('sudo apt-get install ndiswrapper', at the terminal, see the instructions I linked to above) and the installer should search the CD drive for the program.

---

### Post by mastahchanta on 2008-05-07
I only have access to wireless network, cant connect a cable to the router.

---

### Post by zvbxrpl on 2008-05-08
OK, I'm going to try and talk you through uninstalling the Ubuntu driver and installing ndiswrapper from CD.  You will need your Ubuntu CD, and the driver CD that came with your wireless USB adapter.  The following is a slightly customised version of this page:

[http://ph.ubuntuforums.com/showthread.php?t=564419](http://ph.ubuntuforums.com/showthread.php?t=564419)

First, plug in the wireless adapter and insert your Ubuntu CD.  Open a terminal and type

lsmod | grep rt

The output should contain at least one of the following lines:

rt2500usb
rt2500pci
rt2500
rt2570
rt73usb
rt73pci
rt73
rt61usb
rt61pci
rt61
rt2x00usb
rt2x00lib

Make a mental note of which drivers listed above are shown (it's probably rt2x00usb and maybe rt2x00lib as well).  You'll see other, unrelated items - only note down drivers that are listed above.  Now install ndiswrapper:

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

Now load the ndiswapper module into the kernel:

sudo depmod -a
sudo modprobe ndiswrapper

and create an alias for it:

sudo ndiswrapper -m

Now blacklist the driver(s) that you noted when you ran lsmod, above.  Replace <your_ralink_driver> with the name of the driver, and repeat if necessary until all the drivers from the list above that appeared when you ran lsmod are blacklisted:

echo 'blacklist <your_ralink_driver>' | sudo tee -a /etc/modprobe.d/blacklist

Now remove the Ubuntu CD and insert the CD that came with your wireless USB adapter.  What you need to do now is to look at the contents of the CD.  Sometimes the CD consists of all the driver files in folders - in which case you need to find a folder that contains files ending in .inf, .cat and .sys.  Alternatively, the drivers may be zipped up in a self-extracting .exe. file.  If it's the latter case, skip down now to where I've typed ******.  

If there are drivers for several versions of Windows on the CD, use the most recent version.  Drag and drop the contents of the folder - let's call it 'DriverXP' into your home directory in Ubuntu.  Returning to the terminal, you should already be in your home directory, so navigate to the folder you just copied over by typing

cd DriverXP

or whatever the name of the folder was.  Now load the driver into ndiswrapper:

sudo ndiswrapper -i <your_ralink_driver>.inf

where <your_ralink_driver> is the name of the .inf file in the folder you just copied over.

Check the driver has installed correctly:

ndiswrapper -l

you should see something like this:

rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)

Now edit the network configuration file by typing:

sudo gedit /etc/network/interfaces

and check that these two lines are present:

auto wlan0
iface wlan0 inet dhcp

If they're not, add them, then save and close the file.  Reboot the computer, and you should hopefully now be able to see your wireless network in Network Manager on the desktop (top right hand corner of the screen).

**********

If the drivers on the CD are zipped up in a self-extracting .exe file, you will have to extract them first.  Create a new folder in your home folder (let's call it 'wireless') then drag and drop the .exe file  from the CD into it.

Returning to the terminal, navigate to the folder you just created by typing:

cd wireless

or whatever the folder name was, then type:

unzip <driver_archive>.exe

where <driver_archive> is the name of the file you copied over.  This should create new folder(s), one of which should contain the driver files - take a look in the file browser to check which one contains the .inf, .sys and .cat files.  Now go back up the page and read on from the *****.

Good luck!

Edmund.

---

