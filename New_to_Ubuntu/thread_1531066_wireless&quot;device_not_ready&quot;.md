---
title: "wireless&quot;device not ready&quot;"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by sandeep79 on 2010-07-14
hello everyone,
      am new to linux and i installed  ubuntu 10.04 along with windows vista..ubuntu seems to hav some problem withe the wireless internet connection..when i check using iwconfig..the power management is showing in "OFF" status..can anyone tell me how to configure the wireless and how to activate the ethernet card status to "active"..

---

### Post by Excedio on 2010-07-14
Would be helpful to list the type of computer you have along with the type of network card. :-)

---

### Post by sandeep79 on 2010-07-14
am using dell inspiron 1525 and am not sure about the type of ethernet card....

---

### Post by Excedio on 2010-07-14
Does your laptop have a physical WiFi on/off button? Check the right side of the laptop below the expansion port.

---

### Post by sandeep79 on 2010-07-14
yesa i have tried even switching it OFF and turning it ON again..but no use it is showing "device no ready" for wireless....when i right click on the network tab the "enable" option is active for all the options.networking.. wireless...i guess my network card is realtek...how to make the ethernet card to "ON" or "active" statuss...??

---

### Post by Excedio on 2010-07-14
Go to:
 
System -> Administration -> Hardware Drivers
 
See is there are any drivers for your computer listed.

---

### Post by sandeep79 on 2010-07-14
ya i have logged into ubuntu and checked the hardware drivers...it says"please check your network status"...and its showing "no proprietary devices are in use on this system"..

---

### Post by anewguy on 2010-07-14
At the time you are trying this, you don't have a hard-wired connection to your router do you?  If so, the best that I have been able to tell, you need to physically disconnect that cable prior to attempting wireless.

You may want to try:

- open a terminal window (Applications/Accessories/Terminal)

- type:

lshw -C network <press enter>

In the output, locate your wireless - it may be wlan0 or some such thing. 

- type

sudo ifup xxxxx <press enter> Where you should substitute whatever you found is assigned to your wireless from above - example: sudo ifup wlan0

iwconfig has an option for power, which is used for power management.  I'm not sure if it would be of any use here or not.

For us to be of much more help, please do the following:

- in the same terminal window (or a new one if you closed the old one):

- type:

lshw -C network <press enter>

lspci <press enter>

lsusb <press enter>

Copy the outputs from the above and paste back in a reply here.  They will hopefully allow us to identify your wireless and help more.

Dave ;)

---

### Post by sandeep79 on 2010-07-14
ok i gave all the commands give by you..the output is below
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:d5:d7:f2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:9b:5a:60
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
root@sandy-laptop:/home/sandy# enable wlan0
bash: enable: wlan0: not a shell builtin
root@sandy-laptop:/home/sandy# ifup wlan0
Ignoring unknown interface wlan0=wlan0.
root@sandy-laptop:/home/sandy# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
root@sandy-laptop:/home/sandy# lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

_____________this is the output..hope u can give any help

---

### Post by sandeep79 on 2010-07-14
can anyone help me out through my previous message...

---

### Post by mrc4today on 2010-07-14
I'm getting the same thing on a Dell Latitude D531 with a Dell Wireless 1395 WLAN Mini-Card.  Running a dual-boot with Windows XP Pro as the primary and Ubuntu 10.04 as the choice boot.  Checked that the wireless card is on and I'm also getting DISABLED when I run *sudo lshw -C network* in the terminal.

---

### Post by anewguy on 2010-07-14
You have a Broadcom 4312 wireless adapter.  There are a couple of ways to get this work - let's start with the preferred way first.

**[FONT="Arial Black"][SIZE="3"]Preferred Way[/SIZE][/FONT]**

- Temporarily hard-wire your PC to your router.

- Open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press return>  Wait for this to finish.

- Go to System/Administration/Hardware Drivers.  If there is a driver listed there, enable it.

- Disconnect the hard-wire cable and wait a couple of minutes.

- Right-click on the network manager icon.  Be sure the "Enable Wireless" is checked.

- Click on the network manager icon and see if wireless networks show.


**[FONT="Arial Black"][SIZE="3"]Alternate Way[/SIZE][/FONT]**

- Locate the Windows XP driver files for your adapter (the .inf and .sys files - probably something like bcmlw5.inf and .sys).  Copy these files to your desktop.

- Put the LiveCD in your CD drive (don't boot it, just put it in the drive while Ubuntu is already running).  If a message comes up about a CD with software packages being found, just cancel it.

- Now you need to start using the file browser - click on "Places".

- Go to the /pool/main/n folder on the CD.  You should see 2 folders: 1 for ndisgtk (a GUI'd front end to ndiswrapper) and 1 for ndiswrapper.  

- Click on the ndiswrapper folder.  You should see 2 files: 1 for ndiswrapper common and 1 for ndiswrapper utilities.

- Click on the ndiswrapper common file to start its' installation.  Wait for it to finish.

- Click on the ndiswrapper utilities file to start its' installation.  Wait for it to finish.

- Go up 1 folder to the /pool/main/n folder.

- Click on the ndisgtk folder.  You should see 1 file for ndisgtk.

- Click on the ndisgtk file to start its' installation.  Wait for it to finish.

- Right-click on the network manager icon and be sure the "Enable Wireless" is checked.

- Click on the network manager icon and see if you can see wireless networks now.

Post back with any problems, etc.

Dave ;)

---

### Post by cope cola on 2010-07-22
Hey Dave, what if you have no CD, but a USB installer instead? Does it work samewise?

---

### Post by lkraemer on 2010-07-22
You have one more option, The B43 default 10.04 Drivers, that can be added to Dave's methods.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom)

lk

---

### Post by anewguy on 2010-07-22
> **cope cola said:**
> Hey Dave, what if you have no CD, but a USB installer instead? Does it work samewise?
Sorry I didn't see this earlier.  Yes, it should work the same with the USB installer flash drive.  The file system should be layed out the same there.

Dave ;)

---

### Post by cope cola on 2010-07-23
> **anewguy said:**
> Sorry I didn't see this earlier.  Yes, it should work the same with the USB installer flash drive.  The file system should be layed out the same there.

Dave ;)

Allrighty, thanks. What if I can't  hard-wire my PC to my router, because the router is somewhere else in the building? I have another working pc, though.

---

### Post by anewguy on 2010-07-23
> **cope cola said:**
> Allrighty, thanks. What if I can't  hard-wire my PC to my router, because the router is somewhere else in the building? I have another working pc, though.

If you can't hardwire, then you can use the alternate method using ndiswrapper.  Let me know if you need some help getting through it.

Dave ;)

---

### Post by cope cola on 2010-07-23
Ok then, let's start from scratch.


- Locate the Windows XP driver files for your adapter (the .inf and .sys files - probably something like bcmlw5.inf and .sys).  Copy these files to your desktop.


Do you mean locate in the internet, or somewhere in the hard-drive? How can Windows files be retained upon installation of ubuntu?

---

### Post by anewguy on 2010-07-23
If you have Windows installed on the same PC and dual-boot Windows or Ubuntu, then the driver files should be in your c:\windows\system32\drivers for the .sys file - it is really the driver itself, but the .inf file is a requisite to installing it as it "describes" the driver to the installer.  If your partition/drive that Windows is on is accessable while Ubuntu is running, I would open "places" then open the Windows drive.  Then do a search, including all subfolders, for bcm*.* and see what it returns.  If you can't find the files, let us know and we can probably dig some up for you.

Dave ;)

---

### Post by sandyd on 2010-07-24
> **anewguy said:**
> If you have Windows installed on the same PC and dual-boot Windows or Ubuntu, then the driver files should be in your c:\windows\system32\drivers for the .sys file - it is really the driver itself, but the .inf file is a requisite to installing it as it "describes" the driver to the installer.  If your partition/drive that Windows is on is accessable while Ubuntu is running, I would open "places" then open the Windows drive.  Then do a search, including all subfolders, for bcm*.* and see what it returns.  If you can't find the files, let us know and we can probably dig some up for you.

Dave ;)

you can only use the windows driver if it is windows xp. however, dell has a list of drivers on their site for your computer. go take alook.

---

### Post by sandyd on 2010-07-24
another way would be to grab the bcm-wl drivers directly from the broadcom site, stick them on usb, and compile them. once he gets his internet, he can just install the one from hardware drivers over it. however, I cant list the steps atm cause im on my phone... Ubuntu really needs to strike a deal with broadcom and some of the other companies so that the drivers are redistributable...

---

### Post by anewguy on 2010-07-24
> **carlee said:**
> another way would be to grab the bcm-wl drivers directly from the broadcom site, stick them on usb, and compile them. once he gets his internet, he can just install the one from hardware drivers over it. however, I cant list the steps atm cause im on my phone... Ubuntu really needs to strike a deal with broadcom and some of the other companies so that the drivers are redistributable...

+1  -  I just don't see what the big deal is with some of these companies and having open source drivers that are easily included with a distro.

---

### Post by anewguy on 2010-07-24
> **carlee said:**
> you can only use the windows driver if it is windows xp. however, dell has a list of drivers on their site for your computer. go take alook.

I forgot to mention XP - glad you caught that!  I forgot that on another thread a month or two ago and had some poor OP working for several days until I found out he didn't have XP drivers.

Dave ;)

---

### Post by cope cola on 2010-07-25
> **carlee said:**
> you can only use the windows driver if it is windows xp. however, dell has a list of drivers on their site for your computer. go take alook.

Thanks guys, but I do not have a partition. i formatted when I installed ubuntu. But good news, I found the router somewhere in my building, hard-wired the laptop and followed the preferred way. It works now! Many thanks

---

### Post by soldoutnradical on 2010-09-07
Thanks Dave ([anewguy]("http://ubuntuforums.org/member.php?u=331304")).

I was have the wireless issues all weekend after I installed Ubuntu for the first time.  I was getting frustrated with the terminal commands and could not figure it out.

I tried your 'preferred way' and it worked.

Many thanks.
Kevin

---

