---
title: "[SOLVED] Beklin Wireless G Desktop Card 7000 is not detected"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by okey666 on 2007-08-18
I have Ubuntu Feisty Fawn 7.04 with a Beklin Wireless G Desktop Card 7000. I want to connect to my wire less Inventel router but the card is not recognized by Ubuntu? Does anyone have any idea about it? It is a PCI 32bit card. I have tried the ndiswrapper, it installs the driver but says the hardware is not present. Hardware information says that the card is there but it is unknown and all that identifies it is the vendor.

---

### Post by okey666 on 2007-08-18
I have tried the ndiswrapper, it installs the driver but says the hardware is not present. Hardware information says that the card is there but it is unknown and all that identifies it is the vendor.

---

### Post by defconoii on 2007-08-18
I had the same problem, u gotta grab the rt73 driver from [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) or wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
then follow the README instructions

Installation instructions for the Legacy rt73 module
[[http://rt2x00.serialmonkey.com]](http://rt2x00.serialmonkey.com])


==================
Build Instructions
==================

1. Unpack the driver sources and go to the Module directory:
$ tar -xvzf rt73-cvs-daily.tar.gz
$ cd ./rt73-cvs-YYYYMMDDHH/Module

2. Compile the driver sources:
$ make

3. Install the driver (as root):
# make install

4. Check your install (load module, bring interface up and scan):
# modprobe rt73 [debug=<mask>]

<mask> is a decimal or hex number. See TESTING file. Ignored
if driver compiled without debug support.

# ifconfig wlan0 up
# iwlist wlan0 scan

If everything is ok, you should see a list of surrounding Access
Points. It means you can jump to the configuration section.
Otherwise, check out the following install notes...

_________
NOTES:

* Firmware file (rt73.bin)

The rt73 chipset uses a firmware file which is loaded in device
memory using the kernel firmware_class facility. 'make install'
copy the firmware file to the standard firmwares location:
/lib/firmware.

However some linux distributions divert from the standard and e.g.
use /lib/firmware/<KERNEL_VERSION>. If this is your case, you will
have to manually move the firmware file to the right location.
If you have problems with firmware loading, please ask on your
distro's support media (forum, etc).

* Driver alias

rt73 uses wlan* as its modprobe alias. This means you can have
several devices and they will be named wlan0, wlan1, etc.

If for some reason you want this interface number 'static' (e.g.
if you have several wlan devices and their numbers change on
reboot) you can change the rt73 alias in /etc/modprobe.conf back
to wlan0 (or wlan1, etc).

However the proper way to achieve this purpose is to use a udev
rule based on the wlan MAC address, for example:
KERNEL=="wlan*", SYSFS{address}=="00:de:ad:be:ef:00", NAME="wlan0"
(See:
[http://www.reactivated.net/writing_u...#example-netif](http://www.reactivated.net/writing_u...#example-netif))

* Module parameters

You can load the rt73 module with two optional parameters:
firmName=<FILE_NAME> Use another firmware file.
debug=<DEBUG_MASK> Set debug verbosity (see below).


==============================
Wireless Station Configuration
==============================

The wlan interface should be configured using standard wireless
extension tools.

GUI CONFIG:

If you're looking for a GUI config tool we provide RutilT on our
download page
[[http://rt2x00.serialmonkey.com/wiki/...php/Downloads]](http://rt2x00.serialmonkey.com/wiki/...php/Downloads]).

MANUAL CONFIG:

1. Set the interface mode and bring it up
# iwconfig wlan0 mode managed
# ifconfig wlan0 up

2. Set your target network / Access Point
If you just want to join a wireless network, set its ESSID:
# iwconfig wlan0 essid <ESSID>
If you want to associate with a specific AP, set its MAC
address:
# iwconfig wlan0 ap <BSSID>

3. Set encryption if needed

a) WEP (802.11b)
Choose the authentication mode (open/restricted):
# iwconfig wlan0 key open
Or:
# iwconfig wlan0 key restricted
Set the encryption key:
# iwconfig wlan0 key <KEY>

b) WPA (802.11g)
Set the authentication mode:
# iwpriv wlan0 set AuthMode=WPAPSK
Set the encryption key:
# iwpriv wlan0 set WPAPSK=<KEY>
Set the encryption type:
# iwpriv wlan0 set EncrypType=TKIP

c) WPA2 (802.11i)
Set the authentication mode:
# iwpriv wlan0 set AuthMode=WPA2PSK
Set the encryption key:
# iwpriv wlan0 set WPAPSK=<KEY>
Set the encryption type:
# iwpriv wlan0 set EncrypType=AES

4. Check that you're associated with an AP
# iwconfig wlan0

If everything's ok, you can now configure the wlan0 interface
statically or dynamically (DHCP). If you need more wireless config
details and examples (Adhoc mode e.g.), see iwpriv_usage.txt (included
in driver sources). Otherwise, read the following config notes...

_________
NOTES:

* Auto-load on boot

If you want your device to come up on boot the best is to use your
specific linux distribution's tools (boot scripts, etc).
If you need support doing so, ask on your distro's support media.

* wpa_supplicant

wpa_supplicant is a userland WPA/WPA2/802.1X layer. This driver is
not compatible with it. As most wpa_supplicant features are
embedded into our driver, you should not need it though.
If you need to use a feature that only wpa_supplicant provides:
- either use our next-generation rt2x00 driver which
is compatible with wpa_supplicant
- or patch wpa_supplicant to make it work with rt73 (more info:
[http://mjh.name/Ralink_rt73_wpa_supplicant_rt2x00_wpa2](http://mjh.name/Ralink_rt73_wpa_supplicant_rt2x00_wpa2))


==================
Misc. information
==================

* hostapd

hostapd allows your wlan device to act like an Access Point. Legacy
drivers are _not_ compatible with it, but our next-generation
rt2x00 drivers are.

* Network auditing

Our drivers allow you to peform in-depth wireless network auditing.
Most of the following settings require that you bring the
interface down beforehand.

You can set a custom MAC address as you would do for any other
ethernet interface:
# ifconfig wlan0 hw ether <MAC_ADDRESS>

You can put your wlan interface in promiscuous mode as you would
do for any other interface:
# ifconfig wlan0 promisc

You can put your interface in monitor mode and have it listen to all
802.11 frames around:
# iwconfig wlan0 mode monitor

You can also inject 802.11 frames on the fly. To enable injection,
run:
# iwpriv wlan0 rfmontx 1

* Testing / debugging

If you experience any driver related problem you can ask for
support on our mailing list or our legacy driver forum.
Before asking for help, read the TESTING file and follow its
advice. Do *not* post messages like: "wlan does not work. please
help!".

---

### Post by okey666 on 2007-08-19
OK Ill try that, but my x server just broke and I have to fix that before I can do it!

---

### Post by compuniversal on 2007-08-19
Hi, My name is Alex and i have ubuntu fetsy in my PC, i dont try to selling products but i work for some company and thath company give good prices in computer product. I buy friday the netgear WPN311NA and this one work very good with my PC desktop and my ubuntu. If you want you can contact me and i give you good prices. **Remember i dont try to do marketing i just try to help ubuntu community to get good prices and hardward support Linux.** Th U

---

### Post by okey666 on 2007-09-02
I tried the serialmonkey drivers and when I try to "make" or even "sudo make" I get the following message:
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'

What do I do?(I'm new to linux!)

When trying to continue with "sudo make install", everything seems to work well. But I am not sure what to put in the mask section of, "modprobe rt73 [debug=<mask>]", I have tried it without the debug bit at all which seems to work but then doesn't later.

From the next to comands I get "wlan0: ERROR while getting interface flags: No such device
" and "wlan0     Interface doesn't support scanning."

With ndiswrapper the system log says " Sep  2 12:20:00 oscar-desktop loadndisdriver: loadndisdriver: load_driver(33 8 ) : coudln't find valid drivers files for driver blkwgdv7"


HELP!!!!!!!!!!!!!!!!!!!!!!!!
](*,)

---

### Post by defconoii on 2007-09-02
strip -S rt73.ko
modprobe rt73

---

### Post by okey666 on 2007-09-03
Right, now my card is recognized by Ubuntu, but I am having trouble connecting to my Orange Inventel Livebox wireless network. The instructions that come with the driver do not seem to do much, I complete going through them and nothing happens!

Ubuntu picks up my card, lets me select a network but then can not verify the wep key. I have even tried disabling all security.

Also when I reboot, the drivers uninstall

---

### Post by chris027 on 2007-09-03
Hi. I've been having the same exact problem with a belkin 7050 (2571chip). I've tried like 3 or 4 different drivers and a bunch of different tutorials, but am getting the same results as you...detects wireless but won't connect. Also, when i type in ifconfig, it shows an ethernet and a lo(?), but never anything that says wlan.  Please post if it works out for you. I'm going to try to figure out that ndiswrapper thing. 
Hang in there, I think this system will be a lot easier to figure out once you actually get online. Good Luck.
EDIT- oh, maybe that last driver i put in yesterday did something, I'm now getting a wlan0 on ifconfig, but it still won't connect to the network.

---

### Post by MajorOwned on 2007-09-08
same thing here, just wont connect to the livebox

---

### Post by okey666 on 2008-05-12
All fixed on Gutsy and Hardy

---

