---
title: "[SOLVED] Option iCon 225 installed well, but still no connection"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by janmartin on 2008-10-23
Hi all,

I am running a Asus Eee PC 901 with Ubuntu-eee 8.04.1.

Internet connection works well with LAN and WLAN.

Now Í need to get the Option iCon 225 USB stick to work for 3G.

I have followed this How-to:
[http://www.blogeee.net/2008/03/14/tutorial-une-cle-3g-sur-votre-ultraportable-pour-30e/#more-445](http://www.blogeee.net/2008/03/14/tutorial-une-cle-3g-sur-votre-ultraportable-pour-30e/#more-445)

To connect I do:
Network Manager Icon: Rightclick and untick "Enable Wireless"
Insert Option iCon 225.

Run ./connect.sh up as root:

```

root@901:/home/jan# ./connect.sh up
Initializing...
Trying internet ...
Connecting...
trying
trying-
trying--
Connected
Setting IP address to  172.18.213.251
Adding route
Setting nameserver
Done.
root@901:/home/jan# 

```

However there is still no internet connection by 3g.
```

root@901:/home/jan# ping www.spiegel.de
ping: unknown host www.spiegel.de

```


This is the output of dmesg right after I plugged in the USB stick:
```

  717.297052] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  717.421011] usb 1-2: configuration #1 chosen from 1 choice
[  717.422570] scsi3 : SCSI emulation for USB Mass Storage devices
[  717.424539] usb-storage: device found at 2
[  717.424558] usb-storage: waiting for device to settle before scanning
[  717.582173] hso: /home/adamm/git/ubuntu-hardy-lum/debian/build/build-eeepc/wireless/hso.c: 1.3 Option Wireless
[  717.582249] usbcore: registered new interface driver hso
[  721.167885] usb-storage: device scan complete
[  721.170119] scsi 3:0:0:0: CD-ROM            ZCOPTION HSDPA Modem      3.00 PQ: 0 ANSI: 2
[  721.172211] scsi 3:0:0:0: Attached scsi generic sg3 type 5
[  721.262083] Driver 'sr' needs updating - please use bus_type methods
[  721.286869] sr0: scsi-1 drive
[  721.286888] Uniform CD-ROM driver Revision: 3.20
[  721.287109] sr 3:0:0:0: Attached scsi CD-ROM sr0
[  721.515006] usb 1-2: USB disconnect, address 2
[  721.515653] scsi 3:0:0:0: rejecting I/O to dead device
[  721.515679] scsi 3:0:0:0: rejecting I/O to dead device
[  721.515793] scsi 3:0:0:0: rejecting I/O to dead device
[  722.580481] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  722.702507] usb 1-2: configuration #1 chosen from 1 choice
[  722.705404] hso0: Disabled Privacy Extensions
root@901:

```

conninfo.ini:
(I disabled PIN check using a mobile phone!)
```

# this file contains the connection information for your subscription
APN=internet
# USER=
# PASS=
PIN=

```

**What else to do?**

And yes, I did try reboot.

More Info:

```

root@901:/home/jan# ifconfig hso0
hso0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.18.213.251  P-t-P:172.18.213.251  Mask:255.255.255.255
          POINTOPOINT NOARP MULTICAST  MTU:1486  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:707 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:0 (0.0 B)  TX bytes:58148 (56.7 KB)

root@901:/home/jan# 


```

---

### Post by janmartin on 2008-10-25
Hi,

just to let you know that finally i managed to get the 
Option icon 225 3G USB stick (t-mobile Germany web'n'walk)
to work on my 
Asus Eee PC 901 running Ubuntu-eee 8.04.1.

**Files needed:**

hso-1.6.tar.gz
udev.tar.gz
hsoconnect-py2.5_1.1.83_all.deb
hsolink_1.0.46-1_i386.deb

for your convenience provided bundled here:
[http://data.mybestprojects.com/4-files_for_HSO.tar.gz](http://data.mybestprojects.com/4-files_for_HSO.tar.gz)
If you read this after November 2008 check for newer versions first!

**Preparations:**
On a newly installed Ubuntu 8.04(.1) or Ubuntu-eee 8.04.1:
sudo apt-get install libusb-dev 
sudo apt-get install build-essential linux-headers-$(uname -r) 

In System -> Administration -> Users and Groups create a new group named **dialout**. 
Make sure root and your user name are in the dialout group.

**Installation:**
Extract
hso-1.6.tar.gz
udev.tar.gz

Recompile both:
sudo make
sudo make install

Install by double clicking:
hsoconnect-py2.5_1.1.83_all.deb
hsolink_1.0.46-1_i386.deb

Reboot.

**Connect**

Applications -> Internet -> HSOconnect

Enter your Settings.
List of settings for German 3G providers: 
[http://www.teltarif.de/i/gprs-config.html](http://www.teltarif.de/i/gprs-config.html)

Settings for mine (t-mobile Germany):
In Preferences enter
APN =internet.t-mobile
Username = anything
Password = anything
Save

Click "Connect".

And it works!


**Troubleshooting:**

Check if HSOlinkcontrol is there:
ls -al `which hsolinkcontrol` 
should have this result:
-rwsr-sr-x 1 root root 5048 2008-05-04 01:07 /usr/bin/hsolinkcontrol

What a successful connection looks like in HSOconnect debug window:
[http://data.mybestprojects.com/Debug_Window.txt](http://data.mybestprojects.com/Debug_Window.txt)

Option icon 225 in 3G mode?
Reboot, then wait 30 seconds.
dmesg 
now should display something like this:

[  610.876167] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  611.041197] usb 3-1: configuration #1 chosen from 1 choice
[  612.222218] usb 3-1: USB disconnect, address 2
[  613.102111] hso: /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/wireless/hso.c: 1.3 Option Wireless
[  613.143760] usb 3-1: new full speed USB device using uhci_hcd and address 3
[  613.178909] usb 3-1: configuration #1 chosen from 1 choice
[  613.185085] hso0: Disabled Privacy Extensions
[  613.185757] usbcore: **registered new interface driver hso**
[  613.219295] usbcore: **registered new interface driver libusual**

Start HSOconnect manually in Terminal for extra output in Terminal window:
sudo python -m hsoc

Your linux kernel: 
uname -a

**List of Sites without I never would have succeeded**

[http://www.pharscape.org](http://www.pharscape.org)
[http://www.blogeee.net](http://www.blogeee.net)
[http://www.teltarif.de/i/gprs-config.html](http://www.teltarif.de/i/gprs-config.html)

Special thanks to Paul from Pharscape.

Any hints to improve the setup are very welcome!

---

### Post by attila1964 on 2008-12-09
Hi,

my name is Attila (male) and I'm writing You from Hungary.

Since two weeks I have a MSI VR601X notebook (1,86 NHz, 2 GB RAM, etc) and before 3 days I buyed a T-Mobile web'n'walk stick (Option225)

Today I did all what You suggested in forum, all works, but after about 3-5 minutes my system freezes and I got a failure message "Problem talking to modem"... I can only reset my notebook...

I tried the modem with older rezero to, because I readed somewhere that there are problems with the new udev, but my system freezes too...

Can You help me?

Thanks!

(Sorry for my English, but I seak onlay Hungarian and German fluently...)

---

### Post by Czubek on 2008-12-17
> **janmartin said:**
> Hi,

just to let you know that finally i managed to get the 
Option icon 225 3G USB stick (t-mobile Germany web'n'walk)
to work on my 
Asus Eee PC 901 running Ubuntu-eee 8.04.1.

(...)


Thank's. It works well with polish BlueConnect on Ubuntu 8.04.1. Almost... when i tested it more I get:

> **attila1964 said:**
> Hi,
(...)Today I did all what You suggested in forum, all works, but after about 3-5 minutes my system freezes and I got a failure message "Problem talking to modem"... I can only reset my notebook... (...a)


---

### Post by tampax on 2009-06-07
Hello, i tried everything here, get an ip address and connect. I am using T-mobile in the Netherlands... but i try to connect to web such as nslookup i get no results ( i see data is transfered back and forth..), I try to ping and get the message that the packet is filtered.

From 10.233.66.130 icmp_seq=61 Packet filtered

NGrep out put:

I 10.46.47.251 -> 89.18.172.66 8:0
  ...TU.+J.%.......................... !"#$%&'()*+,-./01234567                                                                                            
#
I 10.233.66.130 -> 10.46.47.251 3:13
  ....E..T..@.>..+../.Y..B...G...S                                                                                                                        
#


any ideas on what to do? could the provider be blocking me somehow?

Also at times, my keyboard locks up after 5 minutes of using this, any insight would be helpful

---

