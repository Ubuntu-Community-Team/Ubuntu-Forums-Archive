---
title: "spankin new to ubuntu-wireless not working"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by ajisdragon on 2007-08-18
Can anyone help me setup my wireless card.  I've been using help and how to's but none of them is specific enough to tell me what to do if I can't accomplish the next step.

Additionally, I have attempted to load ndiswrapper numerous times, but after I do and restart my computer, my screen is black.  I think this has to do with my screen settings being deleted when I install ndiswrapper.  I remember seeing a thread about this previously, but didn't save it on my external hard drive and therefore keep having to reload Ubuntu from the disk.

I have a Belkin Wireless G Desktop Card F5E7000 Version 7000 and have attempted to use  
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin).  Directions are cryptic in the Belkin F5D7000  comments sections that refer me to use "See Belkin F5D7011ef. Have to manually set frequency to that of your router using sudo iwconfig <wlan0> channel <channel>. To find your router's frequency use iwlist <wlan0> scan. bcmw15a.inf can be found as part of R74092us.exe" and then under " Belkin F5D7011ef, I see "It is recognized by Ubuntu as Broadcom Corporation BCM4306 80211b/g Wireless Lan Controler. See Truemobile 1350 below" and i don't see Truemobile below. . .  

I'm getting weary about using the terminal and loading things that will cause me to have to reload Ubuntu after I've already done it about 4 times and reinstalled updates etc.  

Here's the readouts from a couple of queries i've run using [https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)
if this helps to vector anyone towards what I need to do.  

ajisdragon@ajisdragon-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
01:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
01:0b.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0d.0 Ethernet controller: Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem
01:0d.1 Computer telephony device: Broadcom Corporation BCM4212 v.90 56k modem
ajisdragon@ajisdragon-desktop:~$ 

ajisdragon@ajisdragon-desktop:~$ tail -f /var/log/messages
Aug 18 15:34:20 ajisdragon-desktop kernel: [17254019.140000]  sdb: sdb1
Aug 18 15:34:20 ajisdragon-desktop kernel: [17254019.156000] sd 1:0:0:0: Attached scsi removable disk sdb
Aug 18 15:34:20 ajisdragon-desktop kernel: [17254019.156000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.164000] SCSI device sdc: 958999 512-byte hdwr sectors (491 MB)
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.172000] sdc: Write Protect is off
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.184000] SCSI device sdc: 958999 512-byte hdwr sectors (491 MB)
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.188000] sdc: Write Protect is off
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.188000]  sdc: sdc1
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.212000] sd 2:0:0:0: Attached scsi removable disk sdc
Aug 18 15:34:21 ajisdragon-desktop kernel: [17254019.212000] sd 2:0:0:0: Attached scsi generic sg2 type 0

ajisdragon@ajisdragon-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ajisdragon@ajisdragon-desktop:~$ 

ajisdragon@ajisdragon-desktop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Help.  I feel like such a noob :confused:

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
     [http://www.reactivated.net/writing_udev_rules.html#example-netif](http://www.reactivated.net/writing_udev_rules.html#example-netif))

* Module parameters

    You can load the rt73 module with two optional parameters:
       firmName=<FILE_NAME>  Use another firmware file.
       debug=<DEBUG_MASK>    Set debug verbosity (see below).


==============================
Wireless Station Configuration
==============================

The wlan interface should be configured using standard wireless
extension tools.

GUI CONFIG:

    If you're looking for a GUI config tool we provide RutilT on our
    download page
    [[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]).

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

### Post by defconoii on 2007-08-18
btw unplug your belkin usb card before u install the driver

---

### Post by ajisdragon on 2007-08-18
Ok, I unplugged my wireless card, downloaded "rt73-cvs-daily.tar.gz."
I opened a terminal and this is  the response:

ajisdragon@ajisdragon-desktop:~$ tar -xvzf rt73-cvs-daily.tar.gz
tar: rt73-cvs-daily.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ajisdragon@ajisdragon-desktop:~$

I know I can extract the file: rt73-cvs-2007081819/Module by opening the tar.gz file, but there's probably something missing in my system, right?  (since the terminal isn't letting me extract the file)

---

### Post by defconoii on 2007-08-18
try wgetting that again, 
wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) 
tar zxvf rt73-cvs-daily.tar.gz 
cd rt73*
cd M*
make
strip -S rt73.ko
make install
modprobe rt73
plug it in
modprobe rt73
should work now

---

### Post by ajisdragon on 2007-08-18
Ok, here's where I'm at.  I used wget and then "$ tar zxvf rt73-cvs-daily.tar.gz" next i used
"$ cd rt73-cvs-2007081821/Module" and then "$ make":  see terminal readout below. . .

ajisdragon@ajisdragon-desktop:~$ wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) 
--22:06:33--  [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
           => `rt73-cvs-daily.tar.gz'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 302,542 (295K) [application/x-tar]

100%[====================================>] 302,542      154.86K/s             

22:06:36 (154.14 KB/s) - `rt73-cvs-daily.tar.gz' saved [302542/302542]

ajisdragon@ajisdragon-desktop:~$ tar zxvf rt73-cvs-daily.tar.gz
rt73-cvs-2007081821/
rt73-cvs-2007081821/FAQ
rt73-cvs-2007081821/THANKS
rt73-cvs-2007081821/CHANGELOG
rt73-cvs-2007081821/CVS/
rt73-cvs-2007081821/CVS/Root
rt73-cvs-2007081821/CVS/Repository
rt73-cvs-2007081821/CVS/Entries.Log
rt73-cvs-2007081821/CVS/Entries
rt73-cvs-2007081821/LICENSE
rt73-cvs-2007081821/Module/
rt73-cvs-2007081821/Module/auth.c
rt73-cvs-2007081821/Module/rt73.h
rt73-cvs-2007081821/Module/rt73.bin
rt73-cvs-2007081821/Module/rt2x00debug.h
rt73-cvs-2007081821/Module/md5.c
rt73-cvs-2007081821/Module/rtusb_data.c
rt73-cvs-2007081821/Module/rtmp_main.c
rt73-cvs-2007081821/Module/rt_config.h
rt73-cvs-2007081821/Module/assoc.c
rt73-cvs-2007081821/Module/CVS/
rt73-cvs-2007081821/Module/CVS/Root
rt73-cvs-2007081821/Module/CVS/Repository
rt73-cvs-2007081821/Module/CVS/Entries
rt73-cvs-2007081821/Module/wpa.c
rt73-cvs-2007081821/Module/sync.c
rt73-cvs-2007081821/Module/rtmp_info.c
rt73-cvs-2007081821/Module/iwpriv_usage.txt
rt73-cvs-2007081821/Module/rtusb_bulk.c
rt73-cvs-2007081821/Module/mlme.h
rt73-cvs-2007081821/Module/connect.c
rt73-cvs-2007081821/Module/rtmp_tkip.c
rt73-cvs-2007081821/Module/auth_rsp.c
rt73-cvs-2007081821/Module/oid.h
rt73-cvs-2007081821/Module/rtmp_init.c
rt73-cvs-2007081821/Module/TESTING
rt73-cvs-2007081821/Module/rtusb_io.c
rt73-cvs-2007081821/Module/rtmp.h
rt73-cvs-2007081821/Module/mlme.c
rt73-cvs-2007081821/Module/md5.h
rt73-cvs-2007081821/Module/wpa.h
rt73-cvs-2007081821/Module/rtmp_wep.c
rt73-cvs-2007081821/Module/rtmp_def.h
rt73-cvs-2007081821/Module/Makefile
rt73-cvs-2007081821/Module/rtmp_type.h
rt73-cvs-2007081821/Module/sanity.c
rt73-cvs-2007081821/README
ajisdragon@ajisdragon-desktop:~$ cd rt73-cvs-2007081821/Module
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtmp_main.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/mlme.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/connect.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtusb_bulk.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtusb_io.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/sync.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/assoc.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/auth.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/auth_rsp.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtusb_data.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtmp_init.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/sanity.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtmp_wep.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtmp_info.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rtmp_tkip.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/wpa.o
  CC [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/md5.o
  LD [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rt73.o
  Building modules, stage 2.
  MODPOST
  CC      /home/ajisdragon/rt73-cvs-2007081821/Module/rt73.mod.o
  LD [M]  /home/ajisdragon/rt73-cvs-2007081821/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
*** Module rt73.ko built successfully
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$

NOW, i'm going to follow:
strip -S rt73.ko
make install
modprobe rt73
plug it in (meaning the wireless card?)
modprobe rt73 

here goes!

Here's what happened

ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ strip -S rt73.ko
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ make install
*** Install module in /lib/modules/2.6.17-12-generic/extra ...
make -C /lib/modules/2.6.17-12-generic/build SUBDIRS=/home/ajisdragon/rt73-cvs-2007081821/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
mkdir: cannot create directory `/lib/modules/2.6.17-12-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
make: *** [modules_install] Error 2
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
FATAL: Module rt73 not found.
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ strip -S rt73.ko
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ make install
*** Install module in /lib/modules/2.6.17-12-generic/extra ...
make -C /lib/modules/2.6.17-12-generic/build SUBDIRS=/home/ajisdragon/rt73-cvs-2007081821/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
mkdir: cannot create directory `/lib/modules/2.6.17-12-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
make: *** [modules_install] Error 2
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
FATAL: Module rt73 not found.
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ plug it in
bash: plug: command not found
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
FATAL: Module rt73 not found.
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
FATAL: Module rt73 not found.
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ 

I plugged the wireless card in after the first modprobe and than did another one.  I'm getting a FATAL: Module rt73 not found. . .

---

### Post by defconoii on 2007-08-19
damn im sorry bro, the only reason your having problems is because your "Not Root" type sudo -s and issue all those commands, you did it right this time just didnt have permission as a normal user

---

### Post by defconoii on 2007-08-19
u should use root wisely, u should issue sudo "command" like sudo make, sudo make install etc..
or if u feel confident you wont rm -rf your whole computer sudo -s to be root

---

### Post by ajisdragon on 2007-08-19
So, how do I setup/remanufacture/reformat my computer to be sudo -s root?  If I did this my terminal would display:

sudo: $

Right?  instead of ajisdragon@ajisdragon-desktop: $

Do I need to reload Ubuntu again or is there something else I can do? 
Any tips on how to make this change?

ajisdragon@ajisdragon-desktop:~$ sudo tar zxvf rt73-cvs-daily.tar.gz
Password:
rt73-cvs-2007081821/
rt73-cvs-2007081821/FAQ
rt73-cvs-2007081821/THANKS
rt73-cvs-2007081821/CHANGELOG
rt73-cvs-2007081821/CVS/
rt73-cvs-2007081821/CVS/Root
rt73-cvs-2007081821/CVS/Repository
rt73-cvs-2007081821/CVS/Entries.Log
rt73-cvs-2007081821/CVS/Entries
rt73-cvs-2007081821/LICENSE
rt73-cvs-2007081821/Module/
rt73-cvs-2007081821/Module/auth.c
rt73-cvs-2007081821/Module/rt73.h
rt73-cvs-2007081821/Module/rt73.bin
rt73-cvs-2007081821/Module/rt2x00debug.h
rt73-cvs-2007081821/Module/md5.c
rt73-cvs-2007081821/Module/rtusb_data.c
rt73-cvs-2007081821/Module/rtmp_main.c
rt73-cvs-2007081821/Module/rt_config.h
rt73-cvs-2007081821/Module/assoc.c
rt73-cvs-2007081821/Module/CVS/
rt73-cvs-2007081821/Module/CVS/Root
rt73-cvs-2007081821/Module/CVS/Repository
rt73-cvs-2007081821/Module/CVS/Entries
rt73-cvs-2007081821/Module/wpa.c
rt73-cvs-2007081821/Module/sync.c
rt73-cvs-2007081821/Module/rtmp_info.c
rt73-cvs-2007081821/Module/iwpriv_usage.txt
rt73-cvs-2007081821/Module/rtusb_bulk.c
rt73-cvs-2007081821/Module/mlme.h
rt73-cvs-2007081821/Module/connect.c
rt73-cvs-2007081821/Module/rtmp_tkip.c
rt73-cvs-2007081821/Module/auth_rsp.c
rt73-cvs-2007081821/Module/oid.h
rt73-cvs-2007081821/Module/rtmp_init.c
rt73-cvs-2007081821/Module/TESTING
rt73-cvs-2007081821/Module/rtusb_io.c
rt73-cvs-2007081821/Module/rtmp.h
rt73-cvs-2007081821/Module/mlme.c
rt73-cvs-2007081821/Module/md5.h
rt73-cvs-2007081821/Module/wpa.h
rt73-cvs-2007081821/Module/rtmp_wep.c
rt73-cvs-2007081821/Module/rtmp_def.h
rt73-cvs-2007081821/Module/Makefile
rt73-cvs-2007081821/Module/rtmp_type.h
rt73-cvs-2007081821/Module/sanity.c
rt73-cvs-2007081821/README
ajisdragon@ajisdragon-desktop:~$ sudo cd rt73-cvs-2007081821/Module
sudo: cd: command not found
ajisdragon@ajisdragon-desktop:~$ cd rt73-cvs-2007081821/Module
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ make install
*** Install module in /lib/modules/2.6.17-12-generic/extra ...
make -C /lib/modules/2.6.17-12-generic/build SUBDIRS=/home/ajisdragon/rt73-cvs-2007081821/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
mkdir: cannot create directory `/lib/modules/2.6.17-12-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
make: *** [modules_install] Error 2
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo make install<<<<<<<<<<  Is this right?
*** Install module in /lib/modules/2.6.17-12-generic/extra ...
make -C /lib/modules/2.6.17-12-generic/build SUBDIRS=/home/ajisdragon/rt73-cvs-2007081821/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
  INSTALL /home/ajisdragon/rt73-cvs-2007081821/Module/rt73.ko
  DEPMOD  2.6.17-12-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check config ...
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo modprobe rt73
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo strip -s rt73.ko
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ strip -S rt73.ko
strip: st2we22C: Permission denied
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo strip -S rt73.ko
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ make install
*** Install module in /lib/modules/2.6.17-12-generic/extra ...
make -C /lib/modules/2.6.17-12-generic/build SUBDIRS=/home/ajisdragon/rt73-cvs-2007081821/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
  INSTALL /home/ajisdragon/rt73-cvs-2007081821/Module/rt73.ko
cp: cannot create regular file `/lib/modules/2.6.17-12-generic/extra/rt73.ko': Permission denied
make[2]: *** [/home/ajisdragon/rt73-cvs-2007081821/Module/rt73.ko] Error 1
make[1]: *** [_emodinst_] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
make: *** [modules_install] Error 2
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo modprobe rt73
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-12-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-12-generic'
*** Module rt73.ko built successfully
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo stip -S rt73.ko
sudo: stip: command not found
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ strip -S rt73.ko
strip: stNs0tqW: Permission denied
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe t73
FATAL: Module t73 not found.
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ modprobe rt73
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$ sudo modprobe rt73
ajisdragon@ajisdragon-desktop:~/rt73-cvs-2007081821/Module$

---

### Post by defconoii on 2007-08-21
sorry about the timeliness of this message, I was away all day
u type sudo -s and then type in your administration password u gave
when u installed ubuntu

---

### Post by defconoii on 2007-08-21
.

---

### Post by defconoii on 2007-08-21
All u gotta do is type sudo -s or sudo bash which do the same thing, they change user to root at the command prompt, make sure you sudo with the original username u used in the install when you were asked for a password, then enter in the password then run the install again, you need to be root to install programs and/or/devices
root=administrator equivalent

u must be root like root@computername like so
defcon@ion:~$ whoami
defcon
defcon@ion:~$ id
uid=1001(defcon) gid=1001(defcon) groups=4(adm),20(dialout),21(fax),24(cdrom),25(flo ppy),26(tape),29(audio),30(dip),46(plugdev),104(sc anner),117(admin),119(fuse),1001(defcon),1002(true crypt)
defcon@ion:~$ sudo -s
root@ion:~# whoami
root
root@ion:~# id
uid=0(root) gid=0(root) groups=0(root),119(fuse),1002(truecrypt)
after you sudo to root you will be able to do any administrative work

---

### Post by bondo on 2008-05-15
sudo make install

should help you out there.

---

