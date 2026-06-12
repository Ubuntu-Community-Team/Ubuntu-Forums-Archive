---
title: "2 Wireless cards issue"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Alfredo1234 on 2011-05-17
Hello everyone, I installed ubuntu 11.04 32 bit on my laptop yesterday, and since it needed to download the proprietary drivers for the Broadcom card, I plugged in my usb alfa network wireless card, so then it installed the broadcom card, (it says the drivers are active), 

but every time i unplug the external card nothing seems to happen, i also turn the switch on and off for which is on the laptop. What i did notice was that if i have the usb card pluged in, and I turn the switch, it will disconnect/connect me from the router (using the alfa card)

I use the external usb card for my desktop

---

### Post by NormanFLinux on 2011-05-17
This sounds like an obvious question but have you checked your network connections panel to connect automatically to your network?

---

### Post by Alfredo1234 on 2011-05-17
Sorry if i made it confusing, but I can connect to the network using the external card. It just seems like I cannot enable my internal card (although it is installed), because if i move the switch on the computer it only enables disables the external card

---

### Post by wildmanne39 on 2011-05-17
> **Alfredo1234 said:**
> Hello everyone, I installed ubuntu 11.04 32 bit on my laptop yesterday, and since it needed to download the proprietary drivers for the Broadcom card, I plugged in my usb alfa network wireless card, so then it installed the broadcom card, (it says the drivers are active), 

but every time i unplug the external card nothing seems to happen, i also turn the switch on and off for which is on the laptop. What i did notice was that if i have the usb card pluged in, and I turn the switch, it will disconnect/connect me from the router (using the alfa card)

I use the external usb card for my desktop

Hi I am no expert, but it sounds like you might have created a problem by having two wireless cards on the same machine. With the usb disconnected can your card see your wireless network?

---

### Post by Alfredo1234 on 2011-05-17
If i disconnect the USB card, its as if my internal card does not exist, because it doesnt even show the "enable wireless"

---

### Post by josephmills on 2011-05-17
Hi there could you please open up your terminal (ctrl+alt+t)and type in ```
lspci -nn -k
``````
lsusb
``` ```
rfkill list all
```and a ```
iwlist scan
``` please take out any mac and ip address and paste here thanks

---

### Post by ClientAlive on 2011-05-18
I was just about to post *THE LINK* buddy. Maybe there's an easier way for him though. It's on my clipboard tho.

:D

---

### Post by Alfredo1234 on 2011-05-18
lspci -nn -k:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Dell Device [1028:01cc]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
	Subsystem: Dell Device [1028:01cc]
	Kernel modules: i2c-i801
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Device [1028:01cc]
	Kernel driver in use: tg3
	Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb

lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 003 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rfkill list all

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: <mac address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Router"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000004e7a59c
                    Extra: Last beacon: 28408ms ago
                    IE: Unknown: 00053630305252
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303336303831393037383936321021000B32576972652C20496E632E10230011333830304847562D42204761746577617910240011333830304847562D4220476174657761791042000C3336303831393037383936321054000800060050F20400011011000A686F6D65706F7274616C10080002008E

---

### Post by josephmills on 2011-05-18
ok so do you want to make it work with or with out the usb thingy or both:p

---

### Post by Alfredo1234 on 2011-05-18
I wanted it to work with both, but Its fine with only the internal one working.

and btw, thank you all for your help, now i see one of the differences between windows, and linux. In linux theres alot of people that do want to help.

---

### Post by ClientAlive on 2011-05-18
By the way - If you click the "Quote" button on post #8 it reads different than just reading the post. Maybe good to leave it though. Maybe this info helps someone. idk.

---

### Post by josephmills on 2011-05-18
ok so unplug you usb thingy and open your terminal and type in ```
lsmod | grep b43
``` and a ```
dmesg | grep b43 
``` If nothing happens just say so thanks

---

### Post by wildmanne39 on 2011-05-18
Hi, I am glad he is getting more help, I was in other threads and just got back and I preferto leave it to the experts):P

---

### Post by Alfredo1234 on 2011-05-18
Yea, it seems like it did nothing

---

### Post by josephmills on 2011-05-18
cool try  ```
 sudo apt-get install b43fwcutter&&firmware-b43-installer &&bcmwl-kernel-source
``` then reboot you got wireless?

---

### Post by Alfredo1234 on 2011-05-18
before i reboot, i thought ill post this:

"alfredo@Laptopalfredo:~$ sudo apt-get install b43fwcutter&&firmware-b43-installer &&bcmwl-kernel-source
\[sudo] password for alfredo: 
Sorry, try again.
[sudo] password for alfredo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43fwcutter"

not sure if thats an error

*rebooting now*

---

### Post by Alfredo1234 on 2011-05-18
I rebooted, but it did not do anything, i think it is because of that error what was displayed on the terminal

---

### Post by josephmills on 2011-05-18
sorry typo ```
sudo apt-get install b43-fwcutter && firmware-b43-installer && bcmwl-kernel-source

``` sorry again

---

### Post by Alfredo1234 on 2011-05-18
It gave me an error at the end of the commands:
"alfredo@Laptopalfredo:~$ sudo apt-get install b43-fwcutter && firmware-b43-installer && bcmwl-kernel-source
[sudo] password for alfredo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debhelper module-assistant quilt po-debconf libmail-sendmail-perl html2text
  libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 31 not upgraded.
Need to get 0 B/14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Selecting previously deselected package b43-fwcutter.
(Reading database ... 131420 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
firmware-b43-installer: command not found"

---

### Post by josephmills on 2011-05-18
arghh try post number 44 installing with out wireless connection [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by Alfredo1234 on 2011-05-18
I tried it, but it did not work, but then i tried the first section with the package manager, and after having reinstalled the 3 packages, my internal card did work, but after i rebooted, it stoped working

edit: and after i reinstalled the packages, the wifi light on my laptop turned on, and after rebooting it wasn't on anymore

---

### Post by Alfredo1234 on 2011-05-18
I might have to uninstall the other card.

---

### Post by wildmanne39 on 2011-05-18
> **Alfredo1234 said:**
> I might have to uninstall the other card.

Hi, that is possible,they may not play well together.

---

### Post by ClientAlive on 2011-05-18
> **Alfredo1234 said:**
> I tried it, but it did not work, but then i tried the first section with the package manager, and after having reinstalled the 3 packages, my internal card did work, but after i rebooted, it stoped working

edit: and after i reinstalled the packages, the wifi light on my laptop turned on, and after rebooting it wasn't on anymore


Sound's familiar. I have the broadcom card. Mine is the 4318 Air Force One.

Here's a link that shows how we dealt with it. It's a little technical and involved but if you are very careful and do everything exactly as it talks about I would think it will work for you. josephmills is great. He's the one that helped me and wrote the post there. (He's gonna kill me for saying that too). :P

[http://ubuntuforums.org/showthread.php?t=1731838&page=3](http://ubuntuforums.org/showthread.php?t=1731838&page=3)  (see post # twenty eight)

---

### Post by Alfredo1234 on 2011-05-18
I tried doing that, but it didn't seem to work, i also tried the sudo apt get commands, but those didnt work.

---

### Post by josephmills on 2011-05-18
> **Alfredo1234 said:**
> I tried doing that, but it didn't seem to work, i also tried the sudo apt get commands, but those didnt work.
sorry about that I hade to get some zzzz    :) tel me if you got it or not we will try to walk you though the whole thing. 
joseph

---

### Post by Alfredo1234 on 2011-05-18
Hi again, in the morning before going to school i reinstalled ubuntu 11.04, and this time i used the cat5 cable and it updated and all and it still did not work, so now im thinking its a conflicting with 11.04 and the Latitude D820 laptop.

Right now i just opened up the laptop took out the wifi card, then started up ubuntu checked the "additional drivers" and it wasnt on the list as expected, then i put back the card, but its still the same.

---

### Post by josephmills on 2011-05-18
so a fresh start sounds good lets try to re-install some things please go to synaptic package manager type in bcm remove anything that is on the list then **shut down** the computer then start it up again then make sure that your cat5 cable is plunged in and 
press (ctrl+alt+t ) then type in ```
sudo apt-get install b43-fwcutter
``` then ```
sudo apt-get install firmware-b43-installer 
``` then ```
sudo apt-get install bcmwl-kernel-source
``` then post ```
lsmod | grep b43 
``` here and also ```
dmesg | grep b43 
``` thanks

---

### Post by Alfredo1234 on 2011-05-18
lsmod | grep b43:

alfredo@alfredolaptop:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43

dmesg | grep b43

alfredo@alfredolaptop:~$ dmesg | grep b43
[    1.382237] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.382245] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    9.461383] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    9.640646] Registered led device: b43-phy0::tx
[    9.640734] Registered led device: b43-phy0::rx
[    9.640812] Registered led device: b43-phy0::radio
[    9.790657] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    9.790661] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    9.790664] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  227.164054] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

There it is, and my wifi light came on, and i can see the networks, but i fear if i restart it will break. It seemed to start working once it started installing the last package (the source)

---

### Post by josephmills on 2011-05-18
> **Alfredo1234 said:**
> lsmod | grep b43:

alfredo@alfredolaptop:~$ lsmod | grep b43
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
ssb                    45942  1 b43

dmesg | grep b43

alfredo@alfredolaptop:~$ dmesg | grep b43
[    1.382237] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.382245] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    9.461383] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    9.640646] Registered led device: b43-phy0::tx
[    9.640734] Registered led device: b43-phy0::rx
[    9.640812] Registered led device: b43-phy0::radio
[b][    9.790657] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    9.790661] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    9.790664] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[/b][  227.164054] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

There it is, and my wifi light came on, and i can see the networks, but i fear if i restart it will break. It seemed to start working once it started installing the last package (the source)

Please do not restart as the firmware will not alow you to get wireless when rebooting just wanted to get that out to you fast will post next steps soon

---

### Post by josephmills on 2011-05-18
please do a ```
sudo apt-get remove firmware-b43-installer 
``` then do a ```
sudo apt-get install firmware-b43-installer 
``` then show me a ```
dmesg | grep b43 
``` Do not restart until we get rid of those errors.

---

### Post by Alfredo1234 on 2011-05-18
[    1.382237] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.382245] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    9.461383] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    9.640646] Registered led device: b43-phy0::tx
[    9.640734] Registered led device: b43-phy0::rx
[    9.640812] Registered led device: b43-phy0::radio
[    9.790657] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[    9.790661] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    9.790664] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  227.164054] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)


edit: oh, and yea i did not reboot

---

### Post by josephmills on 2011-05-18
Make sure you do this right,```
sudo su
echo b43 >> /etc/modules
exit
``` now reboot with out the cat 5 cable in

---

### Post by Alfredo1234 on 2011-05-18
*rebooting*

---

### Post by Alfredo1234 on 2011-05-18
It Worked!! :D

I don't know how to thank you, but its running!

---

### Post by josephmills on 2011-05-18
now the usb stick ?

---

### Post by ClientAlive on 2011-05-18
> **alfredo1234 said:**
> it worked!! :d

i don't know how to thank you, but its running!:


     popcorn:

---

### Post by Alfredo1234 on 2011-05-18
both Work :D thank you!! :D

---

### Post by josephmills on 2011-05-18
> **Alfredo1234 said:**
> both Work :D thank you!! :D

please mark as solved thank and once again welcome to ubuntuforums and happy wireless :D

---

