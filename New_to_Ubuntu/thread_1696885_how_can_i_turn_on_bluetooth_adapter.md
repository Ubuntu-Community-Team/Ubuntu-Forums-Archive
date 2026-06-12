---
title: "how can i turn on bluetooth adapter???"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by birdy.f on 2011-02-28
hello..there is a messege coming that bluetooth has been disabled by  a switch on ur computer,,..i really dont know how to turn it on..it was working fine in windows..but i really dont want to use windows again..guys out there can anyone help me !!

---

### Post by birdy.f on 2011-02-28
I switched off my bluetooth in windows now how do i turn it in here?

---

### Post by zenwalker on 2011-02-28
You sure you dont have a manual switch provided to switch it on or off?
[http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth](http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth)

---

### Post by birdy.f on 2011-02-28
no i dont have a manual switch ...i read here on the forums abt this exact same problem with someone else..so i guess m not the only person in this war ..:)
[http://ubuntuforums.org/showthread.php?t=1681280](http://ubuntuforums.org/showthread.php?t=1681280)

---

### Post by birdy.f on 2011-02-28
there are errors also in firmware-b43-installer

---

### Post by vivek.pandey on 2011-02-28
i too had a similar issue but my lapi has a key(antenna made over it). pressing it enabled bluetooth. i guess you should check your keys again as it says it has been disabled by a switch

---

### Post by birdy.f on 2011-02-28
yes i found that switch...now it says that bluetooth is disabled.. when i press it again it says no bluetooth adapters found..

---

### Post by birdy.f on 2011-02-28
**[*i guess wat i need is Dell Wireless 365 bluetooth module driver..*]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBMQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Farchive%2Findex.php%2Ft-961651.html&rct=j&q=dell%20wireless%20365%20bluetooth%20module%20driver%20for%20ubuntu&ei=LGZrTcuTOIKO4gaxhqnfCQ&usg=AFQjCNFsm-pI6ORFNxTzmIaPf_24Ylm2IA&cad=rja")**

i downloaded it from dell official site with windows but i guess i must have switched it off or something..before installing ubuntu,,and now i cant download this driver with ubuntu,,what should i do??

---

### Post by birdy.f on 2011-02-28
running this command lsusb gives s me this..
Bus 002 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 031: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 030: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 029: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by vivek.pandey on 2011-02-28
k finally you got the key... go to filesystem->etc->bluetooth
open main.conf in a text editor
check this

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

---

### Post by birdy.f on 2011-02-28
in additional drivers when i try to install broadcom B43 wireless driver this error occurs..
SystemError: installArchives() failed

---

### Post by birdy.f on 2011-02-28
how do i activate it??

---

### Post by birdy.f on 2011-02-28
ok neo plz dont go anywhere till u help me solve this!!i wud really appreciate!

---

### Post by birdy.f on 2011-02-28
how can i go there??

---

### Post by vivek.pandey on 2011-02-28
did you see the configuration file i asked you to see?

---

### Post by birdy.f on 2011-02-28
how can i open this file??

---

### Post by vivek.pandey on 2011-02-28
places->filesystem->etc->bluetooth->main.conf

also you can install the driver through terminal code will be
sudo apt-get install b43-fwcutter

---

### Post by vivek.pandey on 2011-02-28
> **birdy.f said:**
> how can i open this file??

right click on the file open with text editor

---

### Post by birdy.f on 2011-02-28
i mean there are thousands of files n folders in filesystem..i cannot find this bluetooth file!

---

### Post by vivek.pandey on 2011-02-28
in file systems you will see a folder etc go inside it you will find bluetooth in alphabetical order or else you just type bluetooth you will see bluetooth folder highlighted

---

### Post by birdy.f on 2011-02-28
[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered.
Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
PairableTimeout = 0

# Use some other page timeout than the controller default one
# which is 16384 (10 seconds).
PageTimeout = 8192

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 0 to use controller scheduler.
DiscoverSchedulerInterval = 0

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

# Remember the previously stored Powered state when initializing adapters
RememberPowered = true

# Use vendor, product and version information for DID profile support.
# The values are separated by ":" and VID, PID and version.
#DeviceID = 1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to true.
ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
DebugKeys = false

# Enable Low Energy support if the dongle supports. Default is false.
# Enable/Disable interleave discovery and attribute server over LE.
EnableLE = false

# Enable the GATT Attribute Server. Default is false, because it is only
# useful for testing. Attribute server is not enabled over LE if EnableLE
# is false.
AttributeServer = false

---

### Post by birdy.f on 2011-02-28
found it!

---

### Post by birdy.f on 2011-02-28
hey listen..i have power shortage right now! third world country..anyway will be able to switch on after 2 hours,..

---

### Post by vivek.pandey on 2011-02-28
k fine when you switch it on just try installing broadcom from terminal using the command i gave

---

### Post by birdy.f on 2011-02-28
ok using the command i got this error..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by birdy.f on 2011-02-28
ok now i did it again activating broadcom wireless driver B43 from addition drivers then again using the command in terminal i got..

carpenoctem@carpenoctem-Inspiron-1564:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

---

### Post by birdy.f on 2011-02-28
ok when i click the receive files , it says that Plz verify that '' Personal file sharing'' is currently installed..

---

### Post by birdy.f on 2011-02-28
ok i installed it ..but still..my bluetooth wont turn on..i mean it says bluetoooth is disabled..

---

### Post by birdy.f on 2011-02-28
[ATTACH]184707[/ATTACH]

[ATTACH]184708[/ATTACH]

now when i open the preferences i get this when i should be getting things like show my device and all...

---

### Post by birdy.f on 2011-02-28
when i click on the turn on button..nothing happens!

---

### Post by vivek.pandey on 2011-02-28
> **birdy.f said:**
> when i click on the turn on button..nothing happens!

sorry had gone for dinner so couldnt reply... see what is supposed to happen when you click the bluetooth icon in the preferences you will  get a bluetooth screen which says bluetooth disabled by a switch...something like this.then just click the bluetooth key on your keypad.this will bring the bluetooth screen which says turn on bluetooth a screen whose pic you attached wait for a couple of seconds without pressing anything

---

### Post by birdy.f on 2011-02-28
when i click the turn on button whos pic iv attached...nothing happens! its lyk a min since m waiting..

---

### Post by vivek.pandey on 2011-02-28
even in the attachment you sent you can see bluetooth is on.. the bluetooth icon one..try turning it off from the icon and then on and see if you can connect to any device everything seems to be ok...dont know where the problem is

---

### Post by birdy.f on 2011-02-28
wen i go to system- preferences - bluetooth manager...an error occurs..it says connection failed to blueZ...maybe the prob lies there>>??

---

### Post by birdy.f on 2011-02-28
y cant i get this ?? send files on device etc??

---

### Post by gandaran on 2011-02-28
> **birdy.f said:**
> when i click on the turn on button..nothing happens!
thats the problem with gnome-bluetooth, most of the times it wont work, install blueman from package manager and use it to turn on bluetooth.

---

### Post by birdy.f on 2011-02-28
i have! and i did..nothing happened..
its the same..pitty.

---

### Post by gandaran on 2011-02-28
> **birdy.f said:**
> i have! and i did..nothing happened..
its the same..pitty.
can you post a screenshot of blueman?

---

### Post by gandaran on 2011-02-28
do you have the bluetooth icon on the panel?

---

### Post by birdy.f on 2011-02-28
yes i had..now its gone!

---

### Post by birdy.f on 2011-02-28
i even took its snap..u saw it!

---

### Post by gandaran on 2011-02-28
> **birdy.f said:**
> i even took its snap..u saw it!
that was the gnome-bluetooth manager!
go to system » preferences, theres two bluetooth launches, one of them is blueman the other is the default gnome-bluetooth.
to get the icon back tick the show icon in gnome-bluetooth window.
use the applications » accessories » capture screenshots utily to take screenshots and post them.
another question, did you get the broadcom wireless driver to work?
[read thi]("http://freedomandlinux.wordpress.com/2010/02/23/quick-fix-for-broadcom-sta-wifi-bluetooth-in-ubuntu-9-10/")s, maybe there is some conflict between wireless and bluetooth.

---

### Post by birdy.f on 2011-03-01
yes i have blueman n i got my bluetooth icon appearing again..bt still wen i turn it on nothing happens..

---

### Post by birdy.f on 2011-03-01
i hav broadcom B43 installed..

---

### Post by birdy.f on 2011-03-01
i hust have one bluetooth manager wen i go to sys-preferences-bluetooth manager...and wen i click it open error occurs saying Connection to BlueZ failed-Bluez daemon is not running, blueman-manager cannot continue.

---

### Post by birdy.f on 2011-03-01
i dont seem anything wrong with bluez..should i change the version or something.??

---

### Post by birdy.f on 2011-03-01
wen i try this command

sudo /etc/init.d/bluez-utils restart

i get this
sudo: /etc/init.d/bluez-utils: command not found

---

### Post by gandaran on 2011-03-01
> **birdy.f said:**
> i hav broadcom B43 installed..

and wireless is working well?

---

### Post by gandaran on 2011-03-01
also post the output of
```
lspci
```

---

### Post by birdy.f on 2011-03-01
in the panel,it shows that wireless is disconnected!
output of 
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by thaDM on 2011-03-13
I have exactly the same problem as birdy. Any help appreciated.

Dell Inspiron, 10.10.

---

### Post by friend4u on 2011-03-14
Hi Team,
   I also got the exactly same problem. Did anybody fixed it? Don't know where to go. I am using Ubuntu 10.10.
Here is my lscpi output:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Thanks

---

### Post by thaDM on 2011-03-14
After a *lot* of searching and reading, it looks like the only current way to fix this is by installing Windows, activate the drivers *then *install Ubuntu. This appears to be a terrible workaround. Surely the Ubuntuverse could come up with a better solution...? It's times like these that I wish I was a programmer and could actually understand the inner workings of the OS :(

---

### Post by friend4u on 2011-03-14
Hi,
  Thanks for you inputs. I did exactly same but still same issue. I down graded to 10.04.02 (from windows vista) and the results are same. When connected to vista bluetooth worked.

---

### Post by thaDM on 2011-03-15
> **friend4u said:**
> Hi,
  Thanks for you inputs. I did exactly same but still same issue. I down graded to 10.04.02 (from windows vista) and the results are same. When connected to vista bluetooth worked.

How on earth did you "downgrade" to 10.04 from Vista? They're different operating systems.

---

### Post by friend4u on 2011-03-15
> **thaDM said:**
> How on earth did you "downgrade" to 10.04 from Vista? They're different 
operating systems.

Sorry for confusion caused. First I installed 10.10. I observed the following problems with that.
1. Static noise caused when recording with Sound recorder. Audocity also caused the same problem but less static.
2. While watching youtube vidieos maximising screen is not streaming video but able to hear audio. I need to go back to non full screen mode.
3. Bluetooth issue.

So I searched forums for bluetooth problem and non worked. I installed vista again and bluetooth enabled. Connected to my headphone and also mobile phone. This time I installed 10.04.2 LTS version. I didn't observe first two problems. But problem 3 still exist.
Thanks

---

### Post by friend4u on 2011-03-15
Here is what system trying to do with that device. Not able to recognize this as buletooth dongle I guess.

usbcore: registered new interface driver hiddev
Mar 14 20:40:31 E1405 kernel: [    2.157443] ohci1394 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 14 20:40:31 E1405 kernel: [    2.169268] input: HID 413c:8105 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
Mar 14 20:40:31 E1405 kernel: [    2.169630] generic-usb 0003:413C:8105.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8105] on usb-0000:00:1d.1-1/input0
Mar 14 20:40:31 E1405 kernel: [    2.189171] input: HID 413c:8105 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input8
Mar 14 20:40:31 E1405 kernel: [    2.189679] generic-usb 0003:413C:8105.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8105] on usb-0000:00:1d.1-1/input1
Mar 14 20:40:31 E1405 kernel: [    2.189750] usbcore: registered new interface driver usbhid

---

### Post by friend4u on 2011-03-15
I guess this should work: but need to try: (Thanks to Topogigi)
So, here comes the workaround:

1) Boot into Vista and download from the Dell support site the last BT 350 driver for Windows XP and unzip it in a folder
2) Find a directory in that folder called "DFU"
3) Find the file called "DFU.exe", right click it and choose "Run as administrator"
4) Wait until the firmware downgrade has finished, then reboot into  Vista and you will find that the bluetooth chip is now not recognized.  Go to Device manager and manually reinstall the Vista BT driver (don't  use the setup.exe provided by the driver pack, simply install it using  the "have disk" way and load the .inf file directly from the Vista  driver directory).
5) Reboot into Linux. Voilà

---

### Post by friend4u on 2011-03-15
> **friend4u said:**
> I guess this should work: but need to try: (Thanks to Topogigi)
So, here comes the workaround:

1) Boot into Vista and download from the Dell support site the last BT 350 driver for Windows XP and unzip it in a folder
2) Find a directory in that folder called "DFU"
3) Find the file called "DFU.exe", right click it and choose "Run as administrator"
4) Wait until the firmware downgrade has finished, then reboot into  Vista and you will find that the bluetooth chip is now not recognized.  Go to Device manager and manually reinstall the Vista BT driver (don't  use the setup.exe provided by the driver pack, simply install it using  the "have disk" way and load the .inf file directly from the Vista  driver directory).
5) Reboot into Linux. Voilà

Thank you guys. My bluetooth working like charm. Here is what I did.
1. boot to windows vista. 
2. Remove bluetooth windows profiler.
3. Falsh xp version of drivers using DFUinstaller.exe (found on dell website)
4. Install Ubuntu.

---

