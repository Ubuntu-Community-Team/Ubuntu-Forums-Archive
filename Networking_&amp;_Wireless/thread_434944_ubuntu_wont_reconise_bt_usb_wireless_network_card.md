---
title: "ubuntu wont reconise bt usb wireless network card"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by hessiess on 2007-05-06
the card isant recognised and i know that it wont connect to the network without this adapter and bt's software, becose of previous attempts to get the built in card to work. is there any way around this? is it posable  port the drivers and software to ubuntu?

---

### Post by hessiess on 2007-05-06
bump!

---

### Post by hessiess on 2007-05-07
anouther bump

---

### Post by chili555 on 2007-05-07
"bt usb wireless" doesn't tell us much. Can you give us a model number or a link to where you bought it? Evidently you have tried to get it going before; please tell us what you tried and where you got stuck. Thanks.

---

### Post by hessiess on 2007-05-07
furstly, i didont buy it, dad did. secondly i hate wireless stuff becose it never works propaly, but im stuck with it at the moment :(.

this is what it ses on the usb adapter:

bt voyager 1010 usb adapter

how would i run the windows softwere in linux?

i didont get anywere, it just wouldent reconise it. how can i tell if it has reconised it?

---

### Post by chili555 on 2007-05-07
> i hate wireless stuff becose it never works propalyI quite disagree. Some works quite well, some OK and some poorly, just like any other consumer product you can buy. There are consumer products built to a low price point that may work sort of, for a few weeks. There are other consumer items that are better built and consequently more expensive that work quite well for many years. I would have no idea where the BT Voyager 1010 fits on the scale.

I am replying on one of my two laptops that use wireless, Both of them work flawlessly.

I believe your BT can work with the drivers native in Ubuntu with the addition of firmware. First, let's confirm the chipset details, if we can. Plug it in and then do:```
sudo lshw -C network
```and please post the result here.

---

### Post by hessiess on 2007-05-07
ok, haft to write it down.

---

### Post by hessiess on 2007-05-07
comand not reconised :(

---

### Post by rich.bradshaw on 2007-05-07
Hi again, I'll answer you here as someone else can help when I'm offline...

type 

lspci

to list the devices - it should say in their somewhere about your card.

The make isn't important - the chip inside is. This may be broadcom or ralink or some other chip.

Once you know that, search these forums for info on it. Almost all cards work pretty easily after you know what to do!

ndiswrapper will almost certainly be used - if you can get non-wireless internet then it will help you to get the software onto your computer.

---

### Post by hessiess on 2007-05-07
> **chili555 said:**
> I quite disagree. Some works quite well, some OK and some poorly, just like any other consumer product you can buy. There are consumer products built to a low price point that may work sort of, for a few weeks. There are other consumer items that are better built and consequently more expensive that work quite well for many years. I would have no idea where the BT Voyager 1010 fits on the scale.

I am replying on one of my two laptops that use wireless, Both of them work flawlessly.

I believe your BT can work with the drivers native in Ubuntu with the addition of firmware. First, let's confirm the chipset details, if we can. Plug it in and then do:```
sudo lshw -C network
```and please post the result here.

ok, i saved the webpage rebooted to linux pasted it and got this:.

```
  *-network                
       description: Network controller 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@05:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=ipw3945 latency=0 
       resources: iomemory:d6000000-d6000fff irq:19 
  *-network 
       description: Ethernet interface 
       product: PRO/100 VE Network Connection 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@08:08.0 
       logical name: eth0 
       version: 02 
       serial: 00:16:d3:08:df:be 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s 
       resources: iomemory:d6100000-d6100fff ioport:3000-303f irq:22 
```

i have no acsess to a non wireless internet conection

---

### Post by hessiess on 2007-05-07
lspci......

a@a-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1) 
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02) 
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01) 
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05) 
a@a-laptop:~$  

witch is the wireless adapter? the computer has a bult in one and the bt one, bult in one dosant work becose its a old house with extremly thick walls. usb one is on a masave usb extention cable to a bit of the house that actualy gets a signal!

---

### Post by hessiess on 2007-05-07
bump

---

### Post by hessiess on 2007-05-08
bump

---

### Post by hessiess on 2007-05-08
bump!

---

### Post by Bremenacht on 2007-05-08
Hi,

I've got the same problem and I'm new to linux & ubuntu, so I'm having fun with it. :)

I opened up the USB adapter to look at the chips and got the following model name:

ATMEL AT76C503A

This model is referred to on the [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") page but the instructions ("It just works!") haven't worked for me. I got the following info using command lsusb:

josh@josh-desktop:~$ **lsusb**
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 069a:0821 Askey Computer Corp. BT Voyager 1010 802.11b Adapter
Bus 001 Device 001: ID 0000:0000

I've also found some source material at [http://at76c503a.berlios.de/devices.html]("http://at76c503a.berlios.de/devices.html"), but I haven't read anything on, err, 'how to compile sourcecode on ubuntu when you've only just  worked out how to install it and you've not used linux before'... :D

There's loads more I've yet to read on configuring wireless on these forums, so I'll have another fartabout later in the week, if someone else doesn't come up with an answer first.

---

### Post by chili555 on 2007-05-08
Ah ha! Now we're getting somewhere! I was hoping I wouldn't have to buy one of these just to take it apart to see the chipset! Please open a terminal and type:```
sudo tail -f /var/log/messages
```This is so you can watch kernel messages as we try to load the driver for the wireless key. Leave it open and watch it.

Insert the BT and open another terminal and type:```
sudo modprobe at76c503
```If we are successful, the 'messages' terminal should indicate a device was registered; it may even say the interface, eth1 or wlan0, etc. Do:```
iwconfig
```Do you see your interface? If so, do:```
sudo iwconfig wlan0 essid <your_esid>
sudo dhclient wlan0
```Substitute the interface you found for wlan0 in my examples.

---

### Post by hessiess on 2007-05-09
thx, il try that now. its a pain to reboot all the time just for internet acsess!

---

### Post by Blacktalon on 2007-05-09
I am not even going to attempt to help here, just wanted to tell you hessiess, please learn to bloody well spell!

---

### Post by hessiess on 2007-05-09
you canot coment on my spelling.

DYSLEXIA IS A RECOGNISED DISOBILATY AND PEOPLE SHOULD MAKE RESNABLE ADJUSTMENTS !!!!!!!!!!! 

YOU SHOULD LEARN TO BLOODY WELL THINK BEFORE POSTING!!!!!!!!!!!!!!!!
___________________________________________________________________________

it didont work :(

```

a@a-laptop:~$ sudo modprobe at76c503 
FATAL: Module at76c503 not found. 
a@a-laptop:~$
```

what do i do now?

---

### Post by chili555 on 2007-05-09
Blacktalon-
How unbelievably rude and insensitive. Please do not intrude on my threads.

Hessiess-
Sorry he intruded. Let's proceed. Please try again with:```
sudo modprobe at76_usb
```Please let me know.

---

### Post by hessiess on 2007-05-10
it dosant do anything

output
```

a@a-laptop:~$ sudo modprobe at76_usb 
a@a-laptop:~$
```

?:confused:

---

### Post by hessiess on 2007-05-10
bump

---

### Post by chili555 on 2007-05-10
> it dosant do anythingExcellent! It doesn't kick out any errors and, presumably, it sticks. Now do:```
iwconfig
```Did your wireless interface appear?

---

### Post by hessiess on 2007-05-10
carnt, instaling a graphics card driver mucked up the user interface. how do i go back to the driver i was using? (the defolt one)

---

### Post by chili555 on 2007-05-10
You can usually uninstall it in Synaptic. It's a bit tricky, so please give us some more details. Nvidia? Manual install or through apt-get? Is there a backed-up copy of xorg.conf in /etc/X11?

---

### Post by hessiess on 2007-05-10
used metherd 2 of this guide, its a nividia go 7600

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

blender will only run 1000 polys without a graphics card driver!

i only have acsess to a comand line, witch i dont know how to use

---

### Post by fwheeler_1 on 2007-05-10
Hi guys-  I don't want to butt in to the hard work you are doing, but I was reading the thread and noticed something.  In post #10, a "sudo lshw -C network" was requested, and part of the output that was posted follows:

 ```
 *-network                
       description: Network controller 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@05:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=ipw3945 latency=0 
       resources: iomemory:d6000000-d6000fff irq:19 
```

If I interpret this correctly, it means that an Intel 3945 WiFi chip is onboard the computer.  Would it help to try to use that rather than an external card?  Continued good luck in trying to get things working.  --Fw

---

### Post by hessiess on 2007-05-10
i live in a 400 year old cottage with extremly thick walls. there is absolutly no signal in my room, so the usb adapter is on a huge usb extencion cable to a pece of the house witch gets a signal.

---

### Post by chili555 on 2007-05-10
The uninstall instructions are on the page you referred me to, about half-way down the page, titled: HOW TO UNINSTALL THE DRIVER (FROM METHOD 2).

The command line is no different than a terminal, just type in the text, double-check it and press 'Enter.' Let me know if you get stuck.

fwheeler_1-
The answer is a little further down.

---

### Post by fwheeler_1 on 2007-05-10
That makes sense, but it's too bad.  On the laptop I have, the antenna build into the LCD lid for the 3945 works a lot better than another computer I have with a USB adapter.

As far as USB adapters go, there is a limit to the length of extension wires that can be used.  So, keep that in mind if your able to get the adapter working but have trouble with dropout.  Keep pluggin' away.  --Fw

---

### Post by hessiess on 2007-05-10
i tryed

"sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf"

got 

file dos not exist

and "sudo dpkg -reconfigure -phigh xserver-xorg" dident healp eather

____________________________________________________________________

the extencion adapter works perfectualy in windows.

---

### Post by hessiess on 2007-05-11
bump

---

### Post by hessiess on 2007-05-11
bump

---

### Post by chili555 on 2007-05-11
> "sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf" got file dos not existIf you do:```
cd /etc/X11/
ls -l
```You can see if you have xorg.conf_back or xorg.conf.back or what you might have in there. If you find one, that's the one you want to copy over your current file.

> "sudo dpkg -reconfigure -phigh xserver-xorg" dident healp eatherUsually, if you simply select the 'nv' driver for your video card, you will at least get a working desktop. Remember, you need to restart GDM afterwards:```
sudo /etc/init.d/gdm start
```

---

### Post by hessiess on 2007-05-12
ive got it working agen :)

iwconfig:.


```
a@a-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11b  ESSID:off/any  Nickname:"" 
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated    
          Bit Rate:11 Mb/s   Tx-Power=15 dBm    
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
eth1      radio off  ESSID:off/any   
          Mode:Managed  Frequency:nan kHz  Access Point: Not-Associated    
          Bit Rate:0 kb/s   Tx-Power:off    
          Retry limit:15   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
a@a-laptop:~$  
```

what now?

---

### Post by chili555 on 2007-05-12
Excellent! Now let's do:```
sudo iwlist wlan0 scan
```It may take a few tries. We are looking for the exact ESSID. When you find it, then do:```
sudo iwconfig wlan0 essid <what_you_found>
sudo dhclient wlan0
```This assumes you have no encryption, WPA, WEP, etc. in place.

---

### Post by hessiess on 2007-05-12
there is incription, its a 128 bit wep. i canot disable it

---

### Post by chili555 on 2007-05-12
Let's try:```
sudo iwconfig wlan0 essid <what_you_found>
sudo iwconfig wlan0 key <your_key>
sudo dhclient wlan0
```If it's ASCII, instead of hex, prepend your key with s: like this:```
sudo iwconfig wlan0 key s:mylittlekey
```If it's hex, please use lower case for any letters.

---

### Post by hessiess on 2007-05-12
> sudo iwlist wlan0 scan

```
a@a-laptop:~$ sudo iwlist wlan0 scan 
wlan0     Interface doesn't support scanning. 
 
a@a-laptop:~$  

```

i carnt do any of the outher things becose i dident find anything

the network keys are genarated from a pascode by the bt voyager app wen you conect to the network. i dont know what the keys are, and dont know how to find out.

 in the help file it ses that the pascodes arnt computable with any other system and you haft to use keys.

what do i do now?

---

### Post by hessiess on 2007-05-12
bump

---

### Post by hessiess on 2007-05-13
bump

---

### Post by hessiess on 2007-05-13
bump

---

### Post by chili555 on 2007-05-13
> the network keys are genarated from a pascode by the bt voyager app wen you conect to the network. i dont know what the keys are, and dont know how to find out.

in the help file it ses that the pascodes arnt computable with any other system and you haft to use keys.

what do i do now?Can you tell what the ESSID is in Windows? Does the BT Voyager app run on your computer, or are you connecting to one of their servers, putting in a user-name or passcode, etc.?

---

### Post by hessiess on 2007-05-13
the bt voyager app runs on the computer, and it wont recognise the card without it installed. il check the manual to make shore

> Can you tell what the ESSID is in Windows?

how would i find this out?

the network is the only resen im booting windows more at the moment! i rilly want to get this thing working in ubuntu!

dono if this would healp?
the bilt in card will find the network in both windows and ubuntu, but ive never been able to conect using it. probaly becose of the pascode-key thing in the app.

---

### Post by chili555 on 2007-05-13
You might try getting the ESSID by detaching your USB device and walking the laptop over to the wireless access point, turning on the switch for the built-in ipw3945 and doing:```
sudo iwlist eth1 scan
```It might take a few tries. Then with the ESSID, we can see if we can connect to the access point.

Be careful, the ESSID needs to be exactly perfect. Voyager is not the same as voyager is not the same as VOYAGER. 

There are posts on the forum about setting up passwords, etc. to connect to your provider. Search for BT Voyager. I have never tried, so I can't tell you which posts are good or bad. This one looks hopeful: [http://ubuntuforums.org/showthread.php?t=140010&highlight=BT+Voyager](http://ubuntuforums.org/showthread.php?t=140010&highlight=BT+Voyager)

---

### Post by hessiess on 2007-05-13
thx, il try that.

this is what it ses in the manual:.

> The process of setting up WEP Keys involves entering long string of digits and can be quite cumbersome. For this reason, BT Voyager uses the concept of Passcode to set Keys automatically and effortlessly. When entering a Passcode, BT Voyager software uses a special algorithm to create WEP Keys automatically

Devices outside the BT Voyager product range are not compatible with BT Voyager Passcodes and you must instead enter the WEP keys associated with this Passcode:


on ubuntu it only has one key, but the pas code genarates 4 keys

---

### Post by chili555 on 2007-05-13
Does it generate a key with numbers and letters that you can see somewhere? A typical WEP key is something like:```
93c8530b2df51711bad5596f91
```If you can see that somewhere, perhaps in the administration page of your access point, we can probably just use it to connect.

For security reasons, please do not post it here. You can obscure it like this: 93c8xxxxxxxxxxxxxxx96f91> on ubuntu it only has one key, but the pas code genarates 4 keysMost routers generate 4 keys and, unless you specify otherwise, broadcast #1. Linux, generally, and Ubuntu, as well, assumes key #1, unless you specify otherwise.

---

### Post by hessiess on 2007-05-13
sudo iwlist eth1 scan, with bult in card, in a diffrent room with a signal

```
a@a-laptop:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:90:96:7F:60:FC
                    ESSID:"BTVOYAGER-FC"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=57/100  Signal level=-74 dBm  Noise level=-74 dBm
                    Extra: Last beacon: 72ms ago

a@a-laptop:~$ 

```

it wont conect using any of the keys. thay do look like the example

---

### Post by chili555 on 2007-05-13
Did you try:```
sudo iwconfig wlan0 essid BTVOYAGER-FC
sudo iwconfig wlan0 key <your_key_1> open
sudo dhclient wlan0
```You might also try with```
sudo iwconfig wlan0 key <your_key_1> restricted
```Follow with the dhclient command.

---

### Post by hessiess on 2007-05-13
it found the network on the network button on the bar at the top, i put the keys in there and nothing hapened.

il try with the comands

---

### Post by Bremenacht on 2007-05-17
Hi, following all useful advice, I've progressed a bit further but I'm now stuck again.

Following the suggestions, I found out that the device is recognised and a driver installed:
```
josh@josh-desktop:~$ **sudo lshw -C network**
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:a0:ec:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=0.90.0-44 wireless=IEEE 802.11b

josh@josh-desktop:~$ **lsusb**
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 069a:0821 Askey Computer Corp. BT Voyager 1010 802.11b Adapter
Bus 001 Device 001: ID 0000:0000
```

Watching for messages when plugging the device in...
```
May 17 20:13:48 josh-desktop kernel: [ 3464.509348] usb 1-2: new full speed USB device using uhci_hcd and address 5
May 17 20:13:48 josh-desktop kernel: [ 3464.663518] usb 1-2: configuration #1 chosen from 1 choice
May 17 20:13:51 josh-desktop kernel: [ 3467.100758] usb 1-2: reset full speed USB device using uhci_hcd and address 5
May 17 20:13:51 josh-desktop kernel: [ 3467.249069] usb 1-2: device firmware changed
May 17 20:13:51 josh-desktop kernel: [ 3467.249123] usb 1-2: USB disconnect, address 5
May 17 20:13:51 josh-desktop kernel: [ 3467.251145] ubuntu/wireless/at76/at76c503.c: wlan0 disconnecting
May 17 20:13:51 josh-desktop kernel: [ 3467.251166] ubuntu/wireless/at76/at76c503.c: at76_usb disconnected
May 17 20:13:51 josh-desktop kernel: [ 3467.360710] usb 1-2: new full speed USB device using uhci_hcd and address 6
May 17 20:13:51 josh-desktop kernel: [ 3467.514245] usb 1-2: configuration #1 chosen from 1 choice
May 17 20:13:51 josh-desktop kernel: [ 3467.823818] ubuntu/wireless/at76/at76c503.c: firmware version 0.90.0 #44 (fcs_len 4)
May 17 20:13:51 josh-desktop kernel: [ 3467.824830] ubuntu/wireless/at76/at76c503.c: device's MAC 00:90:96:a0:ec:c2, regulatory domain MKK1 (Japan) (id 65)
May 17 20:13:51 josh-desktop kernel: [ 3467.825098] ubuntu/wireless/at76/at76c503.c: registered wlan0
```

more info:
```
josh@josh-desktop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"hello"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

josh@josh-desktop:~$ **sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:96:a0:ec:c2
Sending on   LPF/wlan0/00:90:96:a0:ec:c2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Having read the manual for iwconfig (and therefore all the things that could go wrong), I've tried to make it as simple as possible by having no encryption on my access point, and setting iwconfig accordingly:

```
josh@josh-desktop:~$ **sudo iwconfig wlan0 enc open**
josh@josh-desktop:~$ **sudo iwconfig wlan0 key off**
```

No joy. I've also tried setting the channel to auto, but it won't accept that:

```
josh@josh-desktop:~$ **sudo iwconfig wlan0 channel auto**
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.
```

So, I set the AP & device channel to use the same channel.

I can use this device Ok in W2K. The router is Ok too, because I've been testing it's config using a Nintendo DS, which connects without problem whatever settings I use.

Appreciate your time.

---

### Post by chili555 on 2007-05-17
May we see ```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Bremenacht on 2007-05-17
```
wlan0           No scan results
```

---

### Post by hessiess on 2007-05-18
> **Bremenacht said:**
> Hi, following all useful advice, I've progressed a bit further but I'm now stuck again.

Following the suggestions, I found out that the device is recognised and a driver installed:
```
josh@josh-desktop:~$ **sudo lshw -C network**
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:a0:ec:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=0.90.0-44 wireless=IEEE 802.11b

josh@josh-desktop:~$ **lsusb**
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 069a:0821 Askey Computer Corp. BT Voyager 1010 802.11b Adapter
Bus 001 Device 001: ID 0000:0000
```

Watching for messages when plugging the device in...
```
May 17 20:13:48 josh-desktop kernel: [ 3464.509348] usb 1-2: new full speed USB device using uhci_hcd and address 5
May 17 20:13:48 josh-desktop kernel: [ 3464.663518] usb 1-2: configuration #1 chosen from 1 choice
May 17 20:13:51 josh-desktop kernel: [ 3467.100758] usb 1-2: reset full speed USB device using uhci_hcd and address 5
May 17 20:13:51 josh-desktop kernel: [ 3467.249069] usb 1-2: device firmware changed
May 17 20:13:51 josh-desktop kernel: [ 3467.249123] usb 1-2: USB disconnect, address 5
May 17 20:13:51 josh-desktop kernel: [ 3467.251145] ubuntu/wireless/at76/at76c503.c: wlan0 disconnecting
May 17 20:13:51 josh-desktop kernel: [ 3467.251166] ubuntu/wireless/at76/at76c503.c: at76_usb disconnected
May 17 20:13:51 josh-desktop kernel: [ 3467.360710] usb 1-2: new full speed USB device using uhci_hcd and address 6
May 17 20:13:51 josh-desktop kernel: [ 3467.514245] usb 1-2: configuration #1 chosen from 1 choice
May 17 20:13:51 josh-desktop kernel: [ 3467.823818] ubuntu/wireless/at76/at76c503.c: firmware version 0.90.0 #44 (fcs_len 4)
May 17 20:13:51 josh-desktop kernel: [ 3467.824830] ubuntu/wireless/at76/at76c503.c: device's MAC 00:90:96:a0:ec:c2, regulatory domain MKK1 (Japan) (id 65)
May 17 20:13:51 josh-desktop kernel: [ 3467.825098] ubuntu/wireless/at76/at76c503.c: registered wlan0
```

more info:
```
josh@josh-desktop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"hello"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

josh@josh-desktop:~$ **sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:96:a0:ec:c2
Sending on   LPF/wlan0/00:90:96:a0:ec:c2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Having read the manual for iwconfig (and therefore all the things that could go wrong), I've tried to make it as simple as possible by having no encryption on my access point, and setting iwconfig accordingly:

```
josh@josh-desktop:~$ **sudo iwconfig wlan0 enc open**
josh@josh-desktop:~$ **sudo iwconfig wlan0 key off**
```

No joy. I've also tried setting the channel to auto, but it won't accept that:

```
josh@josh-desktop:~$ **sudo iwconfig wlan0 channel auto**
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.
```

So, I set the AP & device channel to use the same channel.

I can use this device Ok in W2K. The router is Ok too, because I've been testing it's config using a Nintendo DS, which connects without problem whatever settings I use.

Appreciate your time.

how exactly did you get it to work? ive still had no luck! :( wont conect in windows or linux with the bult in card eather.

---

### Post by dannyboy79 on 2007-05-18
well I am guessing this is the same situation as the Belkin Usb wireless adapter.Ubuntu does have support built in but the driver's just don't work. AS you may be able to tell, chili555 has been helping you vigirously over the last couple weeks without success. so I am thinking that you need to compile your own driver from source. 

I found this on the internet under gogle. Apparently the same exact usb adpater is working in Suse 9.1 so we can obivously get it working on Ubuntu. Here is what the person wrote down for us and as you'll notice what I bolded, it's the same exact usb device id's. All we have to do is find the source that suse 9.1 used and we can compile it for ubuntu. I'll keep looking but this is at least some hope.

Hi everyone

I bougth this device months ago. This time I was
trying to setup the BT Voyager to work on linux. I
have had problems with the kernels 2.4.20 and 2.4.21.
Sometimes my computer hangs when the USB device driver
was loading, sometimes when the sound card driver was
loading and sometimes random. I was using the driver
included in suse  9.0.

Now I installed suse 9.1, add this line to the driver
included in the distribution located at
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503-rfmd.c

#define VENDOR_ID_BT_Askey   0x069a
#define PRODUCT_ID_BT_Askey  0x0821 /* BT Voyager 1010
*/

and other line to add this device to the dev_table,
downloaded the firmware, compiled, instaled and the
device now is working fine (the computer too!!, no
hangs).

This is more information about the USB device:

oscar:~ # usbmodules --device /proc/bus/usb/001/002
at76c503-rfmd

oscar:~ # hwinfo --usb
05: USB 00.0: 10a00 Hub                               
         
  [Created at usb.120]
  Unique ID: k4bc.6D_HQg8DEQ1
  SysFS ID:
/devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.4-52-default uhci_hcd UHCI Host
Controller"
  Hotplug: USB
  Vendor: "Linux 2.6.4-52-default uhci_hcd"
  Device: "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:07.2"
  Driver: "hub"
  Speed: 1.5 Mbps
  Config Status: cfg=new, avail=yes, need=no,
active=unknown
06: USB 00.0: 0000 Unclassified device
  [Created at usb.120]
  Unique ID: cLrx.V1ZhSVF3+oC
  Parent ID: k4bc.6D_HQg8DEQ1
  SysFS ID:
/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0
  SysFS BusID: 1-2:1.0
  Hardware Class: unknown
  Model: "Askey Unclassified device"
  Hotplug: USB
  Vendor: usb **0x069a** "Askey Computer Corp."
  Device: usb **0x0821** 
  Revision: "1.00"
  Driver: "at76c503-rfmd"
  Speed: 1.5 Mbps
  Config Status: cfg=new, avail=yes, need=no,
active=unknown
  Attached to: #5 (Hub)

oscar:~ # uname -a
Linux oscar 2.6.4-52-default #1 Wed Apr 7 02:08:30 UTC
2004 i686 i686 i386 GNU/Linux
oscar:~ # 

/var/log/messages:
May  4 11:30:00 oscar kernel: usb usb1: Product: UHCI
Host Controller
May  4 11:30:00 oscar kernel: usb usb1: Manufacturer:
Linux 2.6.4-52-default uhci_hcd
May  4 11:30:00 oscar kernel: usb usb1: SerialNumber:
0000:00:07.2
May  4 11:30:00 oscar kernel: hub 1-0:1.0: USB hub
found
May  4 11:30:00 oscar kernel: hub 1-0:1.0: 2 ports
detected
May  4 11:30:00 oscar kernel: usb 1-2: new full speed
USB device using address 2
May  4 11:30:00 oscar kernel: usbdfu: no version for
"struct_module" found: kernel tainted.
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/usbdfu.c:
USB Devi
ce Firmware Upgrade (DFU) handler v0.12beta9-fwdl
loading
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503.c:
Generi
c Atmel at76c503/at76c505 routines v0.12beta9-fwdl
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503-fw_skel.c
: Atmel at76c503 (RFMD) Wireless LAN Driver
v0.12beta9-fwdl loading
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503-fw_skel.c
: downloading firmware atmel_at76c503-rfmd.bin
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503-fw_skel.c
: got it.
May  4 11:30:00 oscar kernel: drivers/usb/core/usb.c:
registered new driver at76c503-rfmd
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503.c:
$Id: a
t76c503.c,v 1.48 2004/03/26 21:54:10 jal2 Exp $
compiled May  1 2004 03:45:55
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503.c:
firmwa
re version 1.101.2 #84 (fcs_len 4)
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503.c:
device
's MAC XX:XX:XX:XX:XX:XX, regulatory domain MKK1
(Japan) (id 65)
May  4 11:30:00 oscar kernel:
/usr/src/kernel-modules/at76c503-0.12beta9-fwdl/at76c503.c:
regist
ered wlan0

I think this device is ready to be added to the source
code, so everyone can use it in linux.

Regards
O Mejia

---

### Post by dannyboy79 on 2007-05-18
this is a little over my head now, but it appears that you can take the source, modify the code somehow and get the driver to work. at least that's what these people did with it because apparently linksys wusb11 and this BT voyager use the same chip. here's the link:

[http://www.unixadmintalk.com/f59/bt-voyager-1010-linksys-wusb11-110506/index2.html](http://www.unixadmintalk.com/f59/bt-voyager-1010-linksys-wusb11-110506/index2.html)

I do wish you get this working and it's to bad it's not working out of the box for ya. here's the website for the berlios source code for the driver and there's also instructions.

[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

---

### Post by hessiess on 2007-05-18
have i alredy instaled the kernal scorce when i did add cd? this is starting to confuse me abit, windows just dos everyting for you, ive never compiled anything before.

---

### Post by dannyboy79 on 2007-05-19
follow the instructions, you will need to downlaod the source for the driver within windows and save it a place that you have access to in ubuntu. you'll need to download anything that the guide stats, and just follow the instructions.

---

### Post by Bremenacht on 2007-05-20
> **hessiess said:**
> how exactly did you get it to work? ive still had no luck! :( wont conect in windows or linux with the bult in card eather.
Under W2K? The utility never seemed to work, so I looked at the device settings (control panel/system/device etc) and found that they were different from what the utility had set. I set them manually and it worked.

@dannyboy79: Thanks for the advice. Only just having got ubuntu installed (my first Linux install), jumping to driver compiling might be too much too soon, but I'll have a read anyway.

I've noticed in the messages log that it appears to describe a driver file when the device is plugged into the USB:

```
May 20 20:03:58 crap-desktop kernel: [ 5394.599682] ubuntu/wireless/at76/at76c503.c: firmware version 0.90.0 #44 (fcs_len 4)

```
Is it possible to force it to select a different driver? Or to pre-select one?

---

### Post by dannyboy79 on 2007-05-21
it choosing that driver because that's the drive it needs to use BUT as I stated the driver provided in the fiesty install doesn't work as you're finding out. As I stated, there is the same situation with the Belkin Usb wireless adapter. The RT73 or RT2xxx or RT71 drivers provided in the Fiesty Install DON'T work so the thread here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) specifically informs a person how to compile their own correct driver using the serialmonkey drivers aty which point your wireless would work then!

So, if you want wireless to work, then I don't see any other way then to compile this from source. I could maybe do it for you and provide the .deb on my ftp server. I am very busy however so if you'd like me to do it please let me know and I'll let you know when I could have it done.

---

### Post by hessiess on 2007-05-21
ok, i tryed to compile the driver but it chucked out tuns of errors

```

cd 
a@a-laptop:~$ cd at76c503-0.11 
a@a-laptop:~/at76c503-0.11$ make 
gcc -MD -O2 -Wall -Wstrict-prototypes -pipe -fno-strict-aliasing -fno-common -Wno-sign-compare -Wno-unused -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB -DDRIVER_VERSION=\"v0.11\" -I/lib/modules/2.6.20-15-generic/build/include -DMODVERSIONS -include /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h -c at76c503.c 
cc1: error: /lib/modules/2.6.20-15-generic/build/include/linux/modversions.h: No such file or directory 
at76c503.c:76:26: error: linux/config.h: No such file or directory 
In file included from /lib/modules/2.6.20-15-generic/build/include/asm/thread_info.h:16, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/thread_info.h:21, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/preempt.h:9, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/spinlock.h:49, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/capability.h:45, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/sched.h:46, 
                 from at76c503.c:79: 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:82: error: &#8216;CONFIG_X86_L1_CACHE_SHIFT&#8217; undeclared here (not in a function) 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:82: error: requested alignment is not a constant 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h: In function &#8216;cpuid_count&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of &#8216;native_cpuid&#8217; differ in signedness 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of &#8216;native_cpuid&#8217; differ in signedness 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of &#8216;native_cpuid&#8217; differ in signedness 
/lib/modules/2.6.20-15-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of &#8216;native_cpuid&#8217; differ in signedness 
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/sched.h:51, 
                 from at76c503.c:79: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:33:3: error: #error You lose. 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if 
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/sched.h:51, 
                 from at76c503.c:79: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_msecs&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:274: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:274: error: for each function it appears in.) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_usecs&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:285: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;msecs_to_jiffies&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:298: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;usecs_to_jiffies&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:311: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;timespec_to_jiffies&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:330: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:336: error: &#8216;SHIFT_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_timespec&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:349: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;timeval_to_jiffies&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:371: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:375: error: &#8216;SHIFT_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_timeval&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:387: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_to_clock_t&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:401: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;clock_t_to_jiffies&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:412: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h: In function &#8216;jiffies_64_to_clock_t&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/jiffies.h:432: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
In file included from at76c503.c:79: 
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h: In function &#8216;dequeue_signal_lock&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h:1309: warning: implicit declaration of function &#8216;local_irq_save&#8217; 
/lib/modules/2.6.20-15-generic/build/include/linux/sched.h:1311: warning: implicit declaration of function &#8216;local_irq_restore&#8217; 
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/module.h:21, 
                 from at76c503.c:86: 
/lib/modules/2.6.20-15-generic/build/include/asm/module.h:62:2: error: #error unknown processor family 
at76c503.c:90:35: error: linux/devfs_fs_kernel.h: No such file or directory 
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/irq.h:22, 
                 from /lib/modules/2.6.20-15-generic/build/include/asm/hardirq.h:5, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/hardirq.h:7, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:11, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/usb.h:15, 
                 from at76c503.c:91: 
/lib/modules/2.6.20-15-generic/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory 
In file included from /lib/modules/2.6.20-15-generic/build/include/asm/hardirq.h:5, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/hardirq.h:7, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:11, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/usb.h:15, 
                 from at76c503.c:91: 
/lib/modules/2.6.20-15-generic/build/include/linux/irq.h: At top level: 
/lib/modules/2.6.20-15-generic/build/include/linux/irq.h:172: error: requested alignment is not a constant 
/lib/modules/2.6.20-15-generic/build/include/linux/irq.h:174: error: &#8216;NR_IRQS&#8217; undeclared here (not in a function) 
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/hardirq.h:7, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:11, 
                 from /lib/modules/2.6.20-15-generic/build/include/linux/usb.h:15, 
                 from at76c503.c:91: 
/lib/modules/2.6.20-15-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant 
In file included from /lib/modules/2.6.20-15-generic/build/include/linux/usb.h:15, 
                 from at76c503.c:91: 
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h: In function &#8216;cli&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:204: warning: implicit declaration of function &#8216;local_irq_disable&#8217; 
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h: In function &#8216;sti&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:208: warning: implicit declaration of function &#8216;local_irq_enable&#8217; 
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h: In function &#8216;save_flags&#8217;: 
/lib/modules/2.6.20-15-generic/build/include/linux/interrupt.h:212: warning: implicit declaration of function &#8216;local_save_flags&#8217; 
In file included from at76c503.c:100: 
at76c503.h: At top level: 
at76c503.h:459: error: field &#8216;tqueue&#8217; has incomplete type 
at76c503.h:465: error: field &#8216;kevent&#8217; has incomplete type 
at76c503.c:182: error: expected &#8216;)&#8217; before string constant 
at76c503.c:188: error: expected &#8216;)&#8217; before string constant 
at76c503.c:192: error: expected &#8216;)&#8217; before string constant 
at76c503.c:196: error: expected &#8216;)&#8217; before string constant 
at76c503.c:200: error: expected &#8216;)&#8217; before string constant 
at76c503.c:204: error: expected &#8216;)&#8217; before string constant 
at76c503.c:208: error: expected &#8216;)&#8217; before string constant 
at76c503.c:213: error: expected &#8216;)&#8217; before string constant 
at76c503.c:217: error: expected &#8216;)&#8217; before string constant 
at76c503.c: In function &#8216;at76c503_remap&#8217;: 
at76c503.c:463: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;get_op_mode&#8217;: 
at76c503.c:479: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;load_ext_fw_block&#8217;: 
at76c503.c:493: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;get_hw_cfg_rfmd&#8217;: 
at76c503.c:503: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;get_hw_cfg_intersil&#8217;: 
at76c503.c:514: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;get_mib&#8217;: 
at76c503.c:613: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;get_cmd_status&#8217;: 
at76c503.c:623: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;set_card_command&#8217;: 
at76c503.c:704: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;wait_completion&#8217;: 
at76c503.c:732: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;set_mib&#8217;: 
at76c503.c:764: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;bss_list_timeout&#8217;: 
at76c503.c:1279: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c:1279: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__dummy2&#8217; 
at76c503.c:1279: warning: comparison of distinct pointer types lacks a cast 
at76c503.c: In function &#8216;handle_mgmt_timeout&#8217;: 
at76c503.c:1336: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;send_mgmt_bulk&#8217;: 
at76c503.c:1427: error: &#8216;USB_ST_URB_PENDING&#8217; undeclared (first use in this function) 
at76c503.c:1466: warning: implicit declaration of function &#8216;FILL_BULK_URB&#8217; 
at76c503.c:1474: error: too few arguments to function &#8216;usb_submit_urb&#8217; 
at76c503.c: In function &#8216;defer_kevent&#8217;: 
at76c503.c:1757: warning: passing argument 2 of &#8216;set_bit&#8217; from incompatible pointer type 
at76c503.c:1758: warning: implicit declaration of function &#8216;schedule_task&#8217; 
at76c503.c: In function &#8216;kevent&#8217;: 
at76c503.c:1782: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1782: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1790: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1794: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1794: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1821: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1825: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1825: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1829: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1832: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1832: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1833: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1838: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1838: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1840: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1877: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1877: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1878: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1930: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c:1948: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1948: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:1949: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:1999: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:1999: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:2000: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:2005: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:2005: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:2006: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c:2014: warning: passing argument 2 of &#8216;constant_test_bit&#8217; from incompatible pointer type 
at76c503.c:2014: warning: passing argument 2 of &#8216;variable_test_bit&#8217; from incompatible pointer type 
at76c503.c:2015: warning: passing argument 2 of &#8216;clear_bit&#8217; from incompatible pointer type 
at76c503.c: In function &#8216;rx_mgmt_auth&#8217;: 
at76c503.c:2411: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;rx_mgmt_beacon&#8217;: 
at76c503.c:2485: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;ieee80211_to_eth&#8217;: 
at76c503.c:2712: error: &#8216;union <anonymous>&#8217; has no member named &#8216;ethernet&#8217; 
at76c503.c: In function &#8216;submit_rx_urb&#8217;: 
at76c503.c:3090: error: too few arguments to function &#8216;usb_submit_urb&#8217; 
at76c503.c: In function &#8216;at76c503_write_bulk_callback&#8217;: 
at76c503.c:3235: error: too few arguments to function &#8216;usb_submit_urb&#8217; 
at76c503.c: In function &#8216;at76c503_tx&#8217;: 
at76c503.c:3321: error: too few arguments to function &#8216;usb_submit_urb&#8217; 
at76c503.c: In function &#8216;at76c503_tx_timeout&#8217;: 
at76c503.c:3346: error: &#8216;USB_ASYNC_UNLINK&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;ioctl_setspy&#8217;: 
at76c503.c:3632: warning: pointer targets in passing argument 1 of &#8216;mac2str&#8217; differ in signedness 
at76c503.c: In function &#8216;ethtool_ioctl&#8217;: 
at76c503.c:3689: error: &#8216;struct net_device&#8217; has no member named &#8216;owner&#8217; 
at76c503.c:3695:41: error: missing binary operator before token "(" 
at76c503.c: In function &#8216;at76c503_ioctl&#8217;: 
at76c503.c:3927: warning: pointer targets in assignment differ in signedness 
at76c503.c:3935: warning: pointer targets in assignment differ in signedness 
at76c503.c:4333: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c: In function &#8216;at76c503_delete_device&#8217;: 
at76c503.c:4346: error: &#8216;rtnl_sem&#8217; undeclared (first use in this function) 
at76c503.c:4353: warning: implicit declaration of function &#8216;flush_scheduled_tasks&#8217; 
at76c503.c: In function &#8216;at76c503_alloc_urbs&#8217;: 
at76c503.c:4384: warning: initialization from incompatible pointer type 
at76c503.c:4390: error: &#8216;struct usb_interface_descriptor&#8217; has no member named &#8216;endpoint&#8217; 
at76c503.c:4396: error: too few arguments to function &#8216;usb_alloc_urb&#8217; 
at76c503.c:4407: error: too few arguments to function &#8216;usb_alloc_urb&#8217; 
at76c503.c:4429: error: too few arguments to function &#8216;usb_alloc_urb&#8217; 
at76c503.c: In function &#8216;at76c503_new_device&#8217;: 
at76c503.c:4463: warning: implicit declaration of function &#8216;INIT_TQUEUE&#8217; 
at76c503.c:4487: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function) 
at76c503.c:4507: warning: assignment from incompatible pointer type 
at76c503.c:4571: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217; 
at76c503.c: In function &#8216;at76c503_do_probe&#8217;: 
at76c503.c:4595: warning: implicit declaration of function &#8216;usb_inc_dev_use&#8217; 
at76c503.c:4597: warning: implicit declaration of function &#8216;usb_get_configuration&#8217; 
at76c503.c:4602: warning: implicit declaration of function &#8216;usb_set_configuration&#8217; 
at76c503.c:4610: error: &#8216;USB_ST_STALL&#8217; undeclared (first use in this function) 
at76c503.c:4625: error: &#8216;struct net_device&#8217; has no member named &#8216;owner&#8217; 
at76c503.c:4640: warning: implicit declaration of function &#8216;usb_dec_dev_use&#8217; 
make: *** [at76c503.o] Error 1 
a@a-laptop:~/at76c503-0.11$  

```

what am i doing wrong?

---

### Post by hessiess on 2007-05-22
bump becose of edit, see above post

---

### Post by dannyboy79 on 2007-05-22
and did you issue the ./configure first? Actually, nevermind, I recall there not being a configure script with this source. Have you tried to gogle this issue, maybe using "make: *** [at76c503.o] Error 1" as the search criteria? Also, I would post this somewhere on the berlios website where you got the source from. They'd be able to help you the best. Per my PM, i;ll try to add the symlink and get it compiled for ya but I don't knwo if it's going to work for me since I don't have the usb device and I thought I read somethign unique about having the correct firmware. Did you download the firmware and follow the instructions exactly.

ALso, I noticed you're using a version of the source that is very old, you're using the 0.11 version from 2003, you should at a min use the 0.13 version or just go with the beta .14beta1 version. the one thing that's weird is that the 0.12 has a later date than the 0.13 so I not sure what that's all about but definitely don't use the 0.11 version, that's 4 years old!

---

### Post by chili555 on 2007-05-22
Do you have *build-essential* and *linux-headers-`uname -r`* installed? You should be able to get these from apt-get if you have enabled the CD.

---

### Post by hessiess on 2007-05-22
> **chili555 said:**
> Do you have *build-essential* and *linux-headers-`uname -r`* installed? You should be able to get these from apt-get if you have enabled the CD.

is it posable to download the newist verson as a .deb in windows? think i added it

ok i found this [website]("http://packages.debian.org/unstable/devel/build-essential")

witch download do i need?

is this the corect[ linux hedders?]("http://packages.debian.org/unstable/devel/linux-headers-2.6-r4k-kn04")

---

### Post by dannyboy79 on 2007-05-22
i think you have the build-essential package correct but definitely NOT the kernel headers!! did you try to use the fiesty cdrom as your repository to download the source files? also, I would use this build-essential package as it's directly from the ubuntu website: ([https://launchpad.net/ubuntu/+source/build-essential/11.3](https://launchpad.net/ubuntu/+source/build-essential/11.3)) and also  here is the linux-source-2.6.20 package for download, ([https://launchpad.net/ubuntu/+source/linux-source-2.6.20/2.6.20-15.27](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/2.6.20-15.27))  I think? I am sorry, I normally just use aptitude to download the kernel source files.

---

### Post by chili555 on 2007-05-22
Those are not correct. Please look here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Be sure to match your version, Feisty, Edgy, etc. and you running kernel version, which you can find with:```
uname -r
```

---

### Post by hessiess on 2007-05-22
```
a@a-laptop:~$ uname -r

2.6.20-15-generic

a@a-laptop:~$
```

---

### Post by dannyboy79 on 2007-05-23
wget [http://ftp.kfki.hu/linux/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb](http://ftp.kfki.hu/linux/ubuntu/pool/main/l/linux-source-2.6.20/linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb)
that is a mirror in Europe, use the above command to download the package to your current directory (home if you haven't cd'd anywhere) and install by either double clicking on it thru nautilus or issuing

sudo dpkg -i packagename
and that will install the package.

If the Europe mirror doesn't work, than chose a different from here: 
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb&md5sum=510cbf1efb528a0322690009cdb9d233&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb&md5sum=510cbf1efb528a0322690009cdb9d233&arch=i386&type=main)

---

### Post by hessiess on 2007-05-24
it ses reinstall pacage, and it still wont compile!

---

### Post by dannyboy79 on 2007-05-24
are you making sure to rmmod at76c503 OR whatever the module name is that came with fiesty, since we are compiling one ourselves I beleive you need to make sure you rmmod it? you also might have to blacklist it with /etc/modprobe.d/blacklist file

when you type in lsmod | grep at
what modules show up? I wonder if there are some interfering because at the bugreport below, he mentions a at76c503-rfmd module versus just at76c503.

I am pretty much out of ideas, what error are you getting when you try to compile it? when you say it says reinstall the package, what are you talking about, we can't help if you're so vague.

---

### Post by hessiess on 2007-05-26
im getting the same errors i  posted before.

---

### Post by dannyboy79 on 2007-05-29
ok, well you're going to have to subscribe to the mailing list or join a forum specifically for hte berlios driver because I can't help you anymore. I tried to compile this myself and create you a .deb but I couldn't compile it either but it obviously CAN be compiled as it's worked for others. I suggest you gogle around for a .deb already for debian or join a forum more related to these drivers. I wish you the best of luck.

---

### Post by Bremenacht on 2007-06-20
Hi again,

A short note to relate my progress so far.

I followed the howto for the serialmonkey drivers and it all worked Ok. However, I can still not connect to my AP. The device appears to be loaded Ok, but it just doesn't seem to work. Here's a snippet from messages that seems relevant:

```
Jun 21 02:48:31 crap-desktop kernel: [34149.216587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

The AP is definitely Ok, as everything else connects Ok. I've tried using iwlist scan, but it will not pick up my network name.

I'm going to try to find some different sources next and try re-compiling them.

---

### Post by Bremenacht on 2007-06-21
Following the commands listed in post #55, I got some interesting(?) info:

```
$ hwinfo --usb
04: USB 00.0: 10a00 Hub                                         
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_0_0_0000_00_07_2_if0
  Unique ID: k4bc.qW3E_3Al3u0
  SysFS ID: /devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.20-16-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: "Linux 2.6.20-16-generic uhci_hcd"
  Device: "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:07.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: usbcore is active
    Driver Activation Cmd: "modprobe usbcore"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_69a_821_noserial_if0
  Unique ID: cLrx.V1ZhSVF3+oC
  Parent ID: k4bc.qW3E_3Al3u0
  SysFS ID: /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0
  SysFS BusID: 1-2:1.0
  Hardware Class: network
  Model: "Askey WLAN controller"
  Hotplug: USB
  Vendor: usb 0x069a "Askey Computer Corp."
  Device: usb 0x0821 
  Revision: "1.00"
  Driver: "at76_usb"
  Driver Modules: "at76_usb"
  Device File: wlan0
  Features: WLAN
  Speed: 12 Mbps
  HW Address: 00:90:96:a0:ec:c2
  **Requires: atmel-firmware**
  Module Alias: "usb:v069Ap0821d0100dcFEdsc01dp00icFFisc00ipFF"
  Driver Info #0:
    Driver Status: at76c503-i3861 is not active
    Driver Activation Cmd: "modprobe at76c503-i3861"
  Driver Info #1:
    Driver Status: at76_usb is active
    Driver Activation Cmd: "modprobe at76_usb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #4 (Hub)
```

"Requires: atmel-firmware" Does that confirm the driver is incomplete? I also tried one of those modprobe commands to see what happened:

```
$ modprobe at76c503-i3861
FATAL: Module at76c503_i3861 not found.
```

Something to do with the firmware as well?

I've downloaded the driver and firmware sourcecode from [http://developer.berlios.de/projects/at76c503a/]("http://developer.berlios.de/projects/at76c503a/"), so I'll have go at compiling it later.

;)

---

### Post by Bremenacht on 2007-06-21
Well, the berlios drivers eventually compiled and installed, but not Ok. First there was a problem with a routine called INIT_WORK, and it also complained about /linux/config.h being missing. I apparently resolved both those issues, but now the machine locks up whenever the Wireless USB device is plugged in. I assume I've cocked the driver up. Annoyingly, all my notes were lost when the CPU locked up, so I cannot show what I did in detail.

Any suggestions as to how to get the original driver back in place? I can run through the driver compilation again and pull out the errors, should anyone want to look at that.

---

### Post by hessiess on 2007-06-22
still wont compile, still using xp for web stuff. rilly whant to fix this, but almost givven up. think part of the problem is the ruter isent setup to use keys :???:

---

