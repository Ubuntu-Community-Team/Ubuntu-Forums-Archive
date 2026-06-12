---
title: "Can't get Linksys WAG354G to go wireless"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by SilverSatori on 2007-01-20
Hey peepz,

N00b to Ubuntu here, got my wired net connection running a ok (hence being on here! ) :guitar: ... however, I cannot get my wireless to work.

I've spent a few hours looking around the forum and the docs but cannot find anything that has helped .... not that I have understood most of it!!

I can understand as much as enabling the wireless in >>system>>administration>>networking, but I don't know what it means by Network Essid .... I know what ssid is for my router (WAG354G) so is Essid the same?... and I also don't know what it means when asking for network password ... I don't use one ... being in the middle of nowhere and having no neighbours!!

Any hoo, here are the results from my terminal queries...

LSPCI:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:01.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)

LSUSB:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

IWCONFIG:

lo no wireless extensions.

eth0 no wireless extensions.

eth2 IEEE 802.11b ESSID:""
Mode:Auto Channel=1 Access Point: Invalid
Sensitivity=0/200
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

.....

Any help will be most appreciated .... I feel like I am back in the stone ages using wires again!!:lolflag: 

Cheerz

SilverSatori

---

### Post by teaker1s on 2007-01-20
install
[COLOR="Red"]network-manager-gnome[/COLOR]

it appears your wireless is alive

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them. Shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key
___

---

### Post by SilverSatori on 2007-01-21
right, I installed network-manager gnome, went to networking, and unticked wired and made sure wireless was unticked too ... shutdown, removed ethernet cable, booted up, turned on the wireless card, and left clicked the network applet.

it didn't have anything in it, so I tried to add a network, called it the same as is on the router set up ... and the network applet changed to 2 little blobs going round in circles type thingys!?! .... but then said it couldn't connect!!! 

So I am still stuck .... I did notice that when I go to terminal and IWCONFIG ... the channel of the wirless card has changed...

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


... as you'll see from my first post in this topic, the channel was '1' before ... 

I haven't done anything purposely to change it!!

Man this is frustrating....

Any more advice??

---

### Post by teaker1s on 2007-01-21
okay you could try this to force the wireless to become wlan in terminal
 comment out the eth line assigned to the wireless in /etc/iftab. 

[COLOR="Red"]sudo gedit /etc/iftab[/COLOR]
put a [COLOR="Red"]#[/COLOR] at the front of the line
If you don't comment out the eth entry, you won't be able to alias the device as wlan0.)
save file
if it doesn't work just remove the [COLOR="Red"]#[/COLOR]

---

### Post by SilverSatori on 2007-01-21
> **teaker1s said:**
> okay you could try this to force the wireless to become wlan in terminal
 comment out the eth line assigned to the wireless in /etc/iftab. 

[COLOR="Red"]sudo gedit /etc/iftab[/COLOR]
put a [COLOR="Red"]#[/COLOR] at the front of the line
If you don't comment out the eth entry, you won't be able to alias the device as wlan0.)
save file
if it doesn't work just remove the [COLOR="Red"]#[/COLOR]

OK, terminaled sudo gedit /etc/iftab ... but it only comes up with eth0 and eth1 ... and my wirless is on eth2 apparently!?!

maaaan](*,)

---

### Post by teaker1s on 2007-01-21
I'm not up on this model, I'm afraid I don't know the answer, you would do better posting chipset and problems rather than model to get responses;)

---

