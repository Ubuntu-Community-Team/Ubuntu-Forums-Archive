---
title: "Broadcom 3410 wireless not working"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by richs360 on 2008-08-08
Please Please Please help... I installed ubuntu 8.04 2 days ago and can stil not get wireless working... non of the threads seem to help as alot of the things i need to do I don't realy understand. This is the first time using a linux os and would just like someone to explain in simple terms how to get my wireless to work. I looked up my devices on terminal and this is what it comes up with..

 *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:83:8b:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-2 ip=192.168.1.4 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Please can someone help me as I am dfesperate to leave windows and start using ubuntu. I have HP 6720 S 3GB ram, 120 gb hd.

---

### Post by pytheas22 on 2008-08-08
I also posted this in the other thread, but I'm not sure if you'll check back there...

Try running these commands:
```

sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

Then reboot and your wireless *should* work.  If not, please post the output of:
```

iwlist scan
lsmod | grep bcm43xx
lshw -C Network
cat /etc/modprobe.d/blacklist
lspci -nn | grep -i broadcom
dmesg | grep -e bcm -e eth1
```

---

### Post by Ayuthia on 2008-08-08
This wireless card currently works with the wl driver or ndiswrapper.  You can try the nidswrapper route:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The wl driver was introduced into Ubuntu around 2.6.24-17 if I recall correctly but has been working off and on.  Since your card is currently saying UNCLAIMED, I am guessing that it is not up to date and you are using the 8.04 install.

Do you have a working wired connection?  If so, can you post the results of the following from the Terminal:
```
uname -a
lsmod|grep -i -e b43 -e wl -e bcm43xx
```

---

### Post by richs360 on 2008-08-09
Thanks 4 the replies...

Ubuntu seems to find my wireless network however I can not connect to it. It keeps asking me to type in wep key which i do. It then tries to connect and and asks me to type in wep again... I have tried connecting manually but this also doesnt work... please help!

Thanks!!

---

### Post by pytheas22 on 2008-08-09
First of all, make sure that in addition to the WEP key, the other settings that you're specifying are correct--Network Manager should also be asking you what kind of key you use (64/128-bit hex or ASCII) and what kind of authentication you use (open or shared).  Sometimes the default options are not correct; try playing around with other ones.  You set all of these options in the same dialogue box where you enter your WEP key.

If you still can't get connected, please post this information so we can figure out where you are now with the situation:
```

lshw -C Network
iwlist scan
```

and please tell us the name of your wireless network.

Also if possible could you try disabling encryption on your router to see if you can connect that way?

---

### Post by CRIMPS on 2008-08-09
> **Ayuthia said:**
> This wireless card currently works with the wl driver or ndiswrapper.  You can try the nidswrapper route:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The wl driver was introduced into Ubuntu around 2.6.24-17 if I recall correctly but has been working off and on.  Since your card is currently saying UNCLAIMED, I am guessing that it is not up to date and you are using the 8.04 install.

Do you have a working wired connection?  If so, can you post the results of the following from the Terminal:
```
uname -a
lsmod|grep -i -e b43 -e wl -e bcm43xx
```


Im am having the exact same problem.  Here is a little more information concerning steps I have taken to resolve.

First, I followed the steps in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"), however, I was not able to see any changes.  Something of note is that when I paste ```
lshw -C network
``` I receive neither "module = ssb" or "module = ndiswrapper".  I receive "module = wl".  

Secondly, here is the output from the commands you posted above:
```
zach@XPS-1530:~/bcm43xx$ uname -a
Linux XPS-1530 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
zach@XPS-1530:~/bcm43xx$ lsmod|grep -i -e b43 -e wl -e bcm43xx
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl

```

Thanks for the assistance.  Im actually wondering if it would just be easier to downgrade to Gutsy in order to get the wireless working.

---

### Post by pytheas22 on 2008-08-09
@CRIMPS,

Please provide this information so we'll know exactly which wireless card you're using and where you're at now:
```

ndiswrapper -l
lshw -C Network
cat /etc/modprobe.d/blacklist
lspci -nn
lsusb
sudo rmmod ssb
sudo rmmod wl
sudo modprobe ndiswrapper
iwconfig
```

I know that's a lot of stuff, but it will help figure out where you are now.  You shouldn't need to downgrade to Gutsy to solve this problem.

---

### Post by CRIMPS on 2008-08-09
I wanted to quickly add some more information I just found:

```
zach@XPS-1530:~/bcm43xx$ lsmod
Module                  Size  Used by
ieee80211_crypt_tkip    11648  0 
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
b44                    28432  0 
ssb                    34308  1 b44
ndiswrapper           192920  0 

```

---

### Post by Ayuthia on 2008-08-10
> **CRIMPS said:**
> I wanted to quickly add some more information I just found:

```
zach@XPS-1530:~/bcm43xx$ lsmod
Module                  Size  Used by
ieee80211_crypt_tkip    11648  0 
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
b44                    28432  0 
ssb                    34308  1 b44
ndiswrapper           192920  0 

```

You will want to do what pytheas22 requested in post 7.  You have the wl driver conflicting with the ndiswrapper driver. I forgot that the no-fluff site has not been updated to deal with the wl driver.  If pytheas22's steps work, it will just be a matter of added wl to the blacklist.

---

### Post by burgsprinta on 2008-08-10
I am having a slightly Different Problem on a Dell Latitude D830 Notebook.  The Wireless Card is a Dell Wireless 1390 (Broadcom 4311 Chipset).  I installed the driver using ndiswrapper as I have done with other distros, but i get an error saying 

SIOCGIFFLAGS error: No such device. I do not know what this means or what to do from here

---

### Post by pytheas22 on 2008-08-10
> I am having a slightly Different Problem on a Dell Latitude D830 Notebook. The Wireless Card is a Dell Wireless 1390 (Broadcom 4311 Chipset). I installed the driver using ndiswrapper as I have done with other distros, but i get an error saying

SIOCGIFFLAGS error: No such device. I do not know what this means or what to do from here

Probably you need to add the right modules to /etc/modprobe.d/blacklist.  Please post the output of the following commands:
```

lsmod | grep ndis
lshw -C Network
uname -m
ndiswrapper -l
cat /etc/modprobe.d/blacklist
```

so that we can figure out what's going on and how to solve it.

---

### Post by CRIMPS on 2008-08-11
> **pytheas22 said:**
> @CRIMPS,

Please provide this information so we'll know exactly which wireless card you're using and where you're at now:
```

ndiswrapper -l
lshw -C Network
cat /etc/modprobe.d/blacklist
lspci -nn
lsusb
sudo rmmod ssb
sudo rmmod wl
sudo modprobe ndiswrapper
iwconfig
```

I know that's a lot of stuff, but it will help figure out where you are now.  You shouldn't need to downgrade to Gutsy to solve this problem.

Thank you for your help.  I must have missed this post.  Below is the return of the code that you provided above.
```
zach@XPS-1530:~$ ndiswrapper -l
bcmwl5 : driver installed
zach@XPS-1530:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:57:23:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.3 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:d8:05:e0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
zach@XPS-1530:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx
blacklist bcm43xx
zach@XPS-1530:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
zach@XPS-1530:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
zach@XPS-1530:~$ sudo rmmod ssb
[sudo] password for zach: 
ERROR: Module ssb is in use by b44
zach@XPS-1530:~$ sudo rmmod wl
zach@XPS-1530:~$ sudo modprobe ndiswrapper
zach@XPS-1530:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

zach@XPS-1530:~$ 
```

---

### Post by pytheas22 on 2008-08-11
> Thank you for your help. I must have missed this post. Below is the return of the code that you provided above.

Your situation seems a little strange...lshw reports your chipset as 4312, but lspci gives it as 14e4:4315.  So I'm not sure what's going on (in any case, you have a different chipset from the original poster in this thread, so richs360: please disregard any instructions given to CRIMPS).

The Broadcom ndiswrapper page says that your chipset is supported by ndiswrapper, but some users report having to do extra tweaking to get it working (search the page for "14e4:4315" for their testimonies)--although others don't.  To start off, please run this code to get ndiswrapper set up as per the instructions on the wiki, and we'll take it from there if it still doesn't work for you:
```

sudo -s
apt-get remove --purge ndiswrapper*
apt-get install ndiswrapper*
echo 'blacklist wl' >> /etc/modprobe.d/blacklist
wget http://myspamb8.googlepages.com/R174291-pruned.zip
unzip R174291-pruned.zip
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
rmmod wl
ifconfig wlan0 up
```

Now see if the command:

```
iwlist scan
```

shows you your wireless networks.  If not, try rebooting.  If it still doesn't work, please post the output of:
```

lshw -C Network
ndiswrapper -l
lsmod | grep -e ndis -e wl -e b43
dmesg | grep -e ndis -e wlan
```

---

### Post by CRIMPS on 2008-08-12
> **pytheas22 said:**
> 

If not, try rebooting.  If it still doesn't work, please post the output of:
```

lshw -C Network
ndiswrapper -l
lsmod | grep -e ndis -e wl -e b43
dmesg | grep -e ndis -e wlan
```

Unfortunately, I still have no wireless networks, even after rebooting.  Here is the requested output:
```
zach@XPS-1530:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:57:23:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.3 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
zach@XPS-1530:~$ ndiswrapper -l
bcmwl5 : driver installed
zach@XPS-1530:~$ lsmod | grep -e ndis -e wl -e b43
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd
zach@XPS-1530:~$ dmesg | grep -e ndis -e wlan
[   28.592470] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.632622] usbcore: registered new interface driver ndiswrapper
[   32.258790] usbcore: deregistering interface driver ndiswrapper
[   32.381626] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   32.398103] usbcore: registered new interface driver ndiswrapper

```

---

### Post by pytheas22 on 2008-08-12
ndiswrapper doesn't seem to think that the Windows driver that you installed is the right one for your card.  I'm not sure why, because the tutorial said that it should work.

But try these steps to remove the Windows driver and install a new one that, according to the ndiswrapper wiki, works (the driver is from [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe), but because that's a huge download, I uploaded just the files that you need to another site) :
```

sudo ndiswrapper -r bcmwl5
wget http://burnthesorbonne.com/files/Broadcom_4315_driver.tar.gz
tar -xzvf Broadcom*
cd Broadcom*
sudo ndiswrapper -i bcmwl5.inf
```

Then reboot and see if that helps.  If not, does:
```

ndiswrapper -l
```

still not mention "device present?"

---

### Post by CRIMPS on 2008-08-12
Thanks Pytheas22 for your help so far.  I feel I am really close.  
> But try these steps to remove the Windows driver and install a new one that, according to the ndiswrapper wiki, works (the driver is from [http://ftp.us.dell.com/network/Dell_...17_R174291.exe](http://ftp.us.dell.com/network/Dell_...17_R174291.exe), but because that's a huge download, I uploaded just the files that you need to another site) :
Code:

sudo ndiswrapper -r bcmwl5
wget [http://burnthesorbonne.com/files/Broadcom_4315_driver.tar.gz](http://burnthesorbonne.com/files/Broadcom_4315_driver.tar.gz)
tar -xzvf Broadcom*
cd Broadcom*
sudo ndiswrapper -i bcmwl5.inf

 
I made an assumption here and instead used this code:
```
sudo ndiswrapper -r bcmwl5
wget http://burnthesorbonne.com/files/Broadcom_4315_driver.tar.gz
tar -xzvf Broadcom*
[COLOR="Red"]cd DRIVER_US[/COLOR]
sudo ndiswrapper -i bcmwl5.inf
```
Is this incorrect?

> Then reboot and see if that helps. If not, does:
Code:

ndiswrapper -l

still not mention "device present?" 

I receive this output:
```
zach@XPS-1530:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present (alternate driver: wl)

```
Currently, I am able to select a wireless network and I am prompted to enter a passphrase.  However, I just can't seem to get any further than this.  I don't really receive any error, just no connection is ever made.  I cant even connect to an unsecured wifi network.

Is this still an issue with the driver or are we on to another issue now?

Thanks again!

---

### Post by pytheas22 on 2008-08-12
> I made an assumption here and instead used this code:

Yes, you were right; I made a mistake when I typed out the code.
> 
Currently, I am able to select a wireless network and I am prompted to enter a passphrase. However, I just can't seem to get any further than this. I don't really receive any error, just no connection is ever made. I cant even connect to an unsecured wifi network.

That's good news that you can see networks now...that's definitely a step in the right direction.  The first thing to do to try to figure out why you can't connect would be to try connecting from the command line.  If you post the output here of:
```

iwlist scan
```

I can give you the commands to connect manually (please make sure that there's at least one unsecured network with a decent signal in range, because it's best to test with an unsecured network first).

Also, do you have roaming mode enabled?

---

### Post by CRIMPS on 2008-08-12
Here is the requested output of said code:

```
zach@XPS-1530:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:5B:F9:CD:C9
                    ESSID:"2WIRE844"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1E:2A:72:3C:55
                    ESSID:"NETGEAR-0255"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-14 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:12:17:09:97:76
                    ESSID:"SYS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:1C:10:E8:C8:40
                    ESSID:"Centrino_Mobile"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:14:95:A9:13:09
                    ESSID:"2WIRE105"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:0D:72:65:8B:C9
                    ESSID:" "
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



```

For what its worth, the network I will be connecting to is the 'NETGEAR-0255' wireless network.  However, there are two unsecured networks in the list available.

---

### Post by pytheas22 on 2008-08-12
Thanks.  Please try this to see if you can connect:
```

sudo iwconfig eth1 essid "SYS" mode managed channel 6 rate 11M
sudo dhclient eth1
```

That should get you connected wirelessly.  Try it a couple of times, since the signal from SYS is weak.  If it doesn't work, you may want to disable encryption on your own router, and try to connect to it with:
```

sudo iwconfig eth1 essid "NETGEAR-0255" channel 8 mode managed rate 11M
sudo dhclient eth1
```

Let me know how it goes.

---

### Post by CRIMPS on 2008-08-13
> **pytheas22 said:**
> Thanks.  Please try this to see if you can connect:
```

sudo iwconfig eth1 essid "SYS" mode managed channel 6 rate 11M
sudo dhclient eth1
```

That should get you connected wirelessly.  Try it a couple of times, since the signal from SYS is weak.  If it doesn't work, you may want to disable encryption on your own router, and try to connect to it with:
```

sudo iwconfig eth1 essid "NETGEAR-0255" channel 8 mode managed rate 11M
sudo dhclient eth1
```

Let me know how it goes.

Ok, I actually ran this code as I think I you meant to give me this:
```
sudo iwconfig [COLOR="Red"]wlan0[/COLOR] essid "NETGEAR-0255" channel 8 mode managed rate 11M

```

That worked!  Im scared to reboot... I don't want to have to redo this.  Any other words of wisdom from here?

---

### Post by pytheas22 on 2008-08-13
> Ok, I actually ran this code as I think I you meant to give me this:
Code:

sudo iwconfig wlan0 essid "NETGEAR-0255" channel 8 mode managed rate 11M

That worked! Im scared to reboot... I don't want to have to redo this. Any other words of wisdom from here?

Yes, once again, thanks for fixing my mistakes :)

Anyway, since you're able to connect manually, then the problem is most likely with Network Manager--your wireless card itself must be working alright.  You might want to try using [wicd]("http://wicd.sourceforge.net") instead; most people have better luck with it.

In the meantime, you should be able to connect again after a reboot, if necessary, by running those commands.  But once wicd gets installed, it will connect you automatically like Network Manager is supposed to do (and wicd should be able to handle secured networks without a problem).  Let me know how it goes.

---

### Post by CRIMPS on 2008-08-19
Hi Pytheas22.  I feel I should start a new thread as I have completely hijacked this thread (sorry to all).  However, my history of this issue is still available here.

Ok, here is the status of my wireless endeavor.  I can currently connect via my wireless card.  Great!  The problem is in order to connect after I boot into Ubuntu I must take these two steps:
 1.  Refresh the wl driver to make sure the driver is enabled and in use.
 2.  Manually select the wireless network using wicd to connect to.

The problem is that if I were to suspend or hibernate, I would lose my connection.  I might have to play with the connection configuration for 10 to 15 minutes in order to reconnect.  

I was under the impression that I shouldn't be using the wl driver, that it should be an alternative, is that correct?  

Thanks for any help.  This community is awesome!
Z

---

### Post by pytheas22 on 2008-08-19
I think the wl driver that you have is Broadcom's closed-source driver, which was released a few weeks ago (did you install it by following this [thread]("http://ubuntuforums.org/showthread.php?t=880218")?).  Most people report it working quite well for them, although some seem to have issues with ssh for some reason.  It's not free (by the Richard Stallman definition), but unless you have objections to that, there's no reason not to use it, as it seems to work better than the open-source drivers (which were reverse-engineered because until very recently, Broadcom had not been cooperative with the Linux community at all and had refused to release any kind of driver).

I think there may be another driver named wl as well, but I'm not sure.

Anyway, which commands do you run to refresh the wl driver after a reboot/suspend/hibernate?  Because if we know the commands, we can put them into a script that will run automatically whenever the computer boots or wakes back up.

If you post the URL of your new thread, I'll reply there.

---

