---
title: "Broadcom BCM4318"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by nicholas7 on 2013-09-14
I just installed Ubuntu and love it so much, its so fast now. But i have a problem connecting to the internet.


I checked and saw i have to install the driver Broadcom STA wireless driver but every time i do try to install it it says:


Sorry, installation of this driver failed. Please have a look at the log files for details: /var/log/jockey.log


I went to terminal and copy and pasted the log file name. and when I did it said I have no permission to access this file. I checked on the forums that I have to be on a wired connection. So I plugged my laptop into my router and I got internet then tried to install the driver again. And it was loading then when it got to the end the same message popped up.


Also I have one of those little usb router things you plug into the computer and it gives you internet I have been using that but its to slow. So I want to use the one in my computer but cant.
Ive been trying to fix this issue all day please help me.
Also i tried the command: "sudo modprobe wl" and when i type that command in it says: "FATAL: Module wl not found"


Since, I am so new at this all Ubuntu thing can u explain to me, how to fix this please?


p.s I forgot to mention I am using Ubuntu 12.04.

Thanks Guys :)

---

### Post by Cyril380 on 2013-09-14
Do you consider using Windows driver with **ndisgtk** ?

---

### Post by varunendra on 2013-09-15
Welcome to the forums nicholas7 ! :)

The current version of the broadcom sta driver in the default repositories seems to be broken. The nice people who develop and package these things probably forgot something simple which I hope will be fixed soon.

There is a newer, [fixed version]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504") available at launchpad that we can try, but lets first make sure if it is indeed the best driver for your card. Please open a terminal, and post back the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
```
You may copy paste the above commands to avoid typo.

While posting the outputs, please use 'Code' tags. To see how to use them, please follow the "Using Code Tags" link in my signature.

---

### Post by nicholas7 on 2013-09-15
Thanks alot for the reply here are the commands i got:

[HR][/HR]uname -mr

3.8.0-30-generic i686
[HR][/HR]
lspci -nnk | grep -iA2 net

00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
    Kernel modules: ssb

[HR][/HR]
[HR][/HR][HR][/HR]

---

### Post by varunendra on 2013-09-15
The sta driver won't support your card, the native b43 will. Please purge the sta driver package and install the firmware for b43 instead -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

Then unload (if already loaded) and reload the b43 driver-
```
sudo modprobe -rv b43
sudo modprobe -v b43
```
Wifi active now? Do a reboot if necessary.

---

### Post by nicholas7 on 2013-09-15
Nope still not active, even after reboot. Thanks so much for helping me, hope I can get this problem resolved soon

---

### Post by varunendra on 2013-09-15
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates..

---

### Post by nicholas7 on 2013-09-15
[COLOR=#000000]I forgot to add when i typed in these commands:

Code:
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree[/COLOR]
[COLOR=#000000]
Code:
sudo modprobe -rv b43
sudo modprobe -v b43[/COLOR]

A new option was available on the wireless symbol when i clicked on it, i added the picture as a attacment and, it added that new option there as you can see the one that says "Broadcom BCM..." that was never there before, and it wouldnt let me connet to it, then i did a reboot and it went away back to the way it was before. I just wannted to add that in case it would help you figure this out

So i connected with my ethernet cable and i used that to get internet for a short period of time for The Wireless Script and here is what it said:

wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2013-09-15 17:44:18--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 54.235.183.100
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.183.100|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2013-09-15 17:44:18--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 75.101.144.243
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|75.101.144.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4098 (4.0K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2013-09-15 17:44:19--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropboxusercontent.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 4098 (4.0K) [text/plain]
Saving to: `wireless_script'


100%[=========================>] 4,098       --.-K/s   in 0s      


2013-09-15 17:44:19 (7.93 MB/s) - `wireless_script' saved [4098/4098]

Results saved in "wireless-info.txt".


I found the "wireless-info.txt" that it said where the results but didnt add them because it had my IP, but if you want any inforamtion in the .txt file ill copy and paste it here

Thank You so much again for helping me :D

---

### Post by varunendra on 2013-09-15
Make sure the USB adapter is not plugged in. Then do a reboot and see if the internal Broadcom adapter lets you connect this time. If not, run the script again and post back the fresh output.

The IP you saw is your LAN IP, it is nothing that someone can take advantage of from the 'outside' of your local network. Still if you consider it sensitive, just edit the last part of it (obscure it or delete it).

---

### Post by nicholas7 on 2013-09-16
When I took out my USB adaptor and typed in those codes and then restarted, it didnt have the broadcom option anymore, but them when i did plug in the usb the broadcom option did come back up, but still wouldn't let me connect to it.


Here's what it said in the wireless-info.txt file, i used the offline version of the Wireless Script, in case you needed to no that.
Thanks so much for your help :D



```


*************** info trace ***************


***** uname -a *****


Linux nicholas-Inspiron-530 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
	Subsystem: Dell Inspiron 530 [1028:020d]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
	Kernel modules: ssb


***** lsusb *****


Bus 002 Device 004: ID 0781:5572 SanDisk Corp. 
Bus 007 Device 002: ID 0461:4d63 Primax Electronics, Ltd 
Bus 007 Device 003: ID 03f0:d407 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb


***** modinfo *****




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x13b1:0x000d (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****




****************** done ******************



```

---

### Post by varunendra on 2013-09-16
> **nicholas7 said:**
> 
```

[**/etc/modprobe.d/broadcom-sta-common.conf**]
[COLOR="#FF0000"]blacklist b44
blacklist b43legacy
blacklist b43[/COLOR]
....

```

Did you try the first command in my second post? Did it complete successfully? -
```
sudo apt-get purge bcmwl-kernel-source
```
The presence of the blacklist file quoted above suggests that it isn't yet purged, at least not the additional files (above one included) that it creates. Please run the apt-get purge command again and post back it's output.

If it returns messages like it is not installed so nothing to remove/purge, manually delete the above blacklist file -
```
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```
Then reboot or do -
```
sudo modprobe -v b43
```
Does it activate your wireless? If not, please post the output of -
```
dmesg | grep b43
```

---

### Post by nicholas7 on 2013-09-17
Yes i typed all the commands in your post, here are all of the outputs of the commands you gave me:

Input:
```
sudo apt-get purge bcmwl-kernel-source

```

Output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-renderpm libart-2.0-2 python-reportlab-accel
  python-reportlab
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Input:
```
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```

Output:
```
sudo rm /etc/modprobe.d/broadcom-sta-common.confrm: cannot remove `/etc/modprobe.d/broadcom-sta-common.conf': No such file or directory

```

Input:
```
sudo modprobe -v b43
```

Output:
Nothing happened, and wouldnt let me connect to internet and when i rebooted it still didnt work

Input:
```
dmesg | grep b43

```

Output:
```
[ 6334.363548] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[ 6334.580924] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 6334.624030] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[ 6334.920048] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
```

Thanks again so much for the help

---

### Post by varunendra on 2013-09-17
> **nicholas7 said:**
> 
```
sudo rm /etc/modprobe.d/broadcom-sta-common.confrm: [COLOR="#FF0000"]cannot remove `/etc/modprobe.d/broadcom-sta-common.conf': No such file or directory[/COLOR]

```

..which means the script output you attached was run BEFORE purging the driver "wl" ?

Please follow the "Wireless Script" link in my sig. again, download the alternative one from the link at the bottom of the post and use the "No Internet" method to run it again, and post back the fresh report it generates.

Also, since you card only supports g-channel it seems, please try setting your router to use g or b/g mode only. If it has N-channel support, it can be a problem.

---

### Post by nicholas7 on 2013-09-18
I dont know what you mean by purging the driver "wl" i thought you meant the code:
[COLOR=#000000]Code:
sudo apt-get purge bcmwl-kernel-source[/COLOR]
so i ran that code then did the "No Internet" wireless script. I sorry im new at this whole linux thing and dont know alot about it.
Also i dont how to changed my router to g b/g mode. I am using a Cisoco Linksys router so if you can maybe you can give me the steps or more information to see what my router is that would help too. I ran the wireless Script in "No internet" after i ran the "wl" code i though you meant. If i did it wrong ill try again, i just dont know what you mean my "wl" driver, Thanks so much :D

```
*************** info trace ***************

***** uname -a *****


Linux nicholas-Inspiron-530 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
	Subsystem: Dell Inspiron 530 [1028:020d]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
	Kernel driver in use: b43-pci-bridge


***** lsusb *****


Bus 002 Device 005: ID 0781:5572 SanDisk Corp. 
Bus 007 Device 002: ID 0461:4d63 Primax Electronics, Ltd 
Bus 007 Device 003: ID 03f0:d407 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  1 b43


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****


wlan1     No scan results




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     F6F97440A9DA6418F4C2856
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)


filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     14621F6EC014F731244437C
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x13b1:0x000d (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[    9.504274] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    9.526675] ssb: Found chip with id 0x4318, rev 0x02 and package 0x00
[    9.526686] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    9.526693] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    9.526700] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    9.526707] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    9.564248] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   12.028006] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   12.072052] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   21.336068] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   21.400583] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   21.401254] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready


****************** done ******************



```

---

### Post by QDR06VV9 on 2013-09-18
> **nicholas7 said:**
> 


Also I have one of those little usb router things you plug into the computer and it gives you internet I have been using that but its to slow. So I want to use the one in my computer but cant.
Ive been trying to fix this issue all day please help me.
Also i tried the command: "sudo modprobe wl" and when i type that command in it says: "FATAL: Module wl not found"


Since, I am so new at this all Ubuntu thing can u explain to me, how to fix this please?


p.s I forgot to mention I am using Ubuntu 12.04.

Thanks Guys :)

Have you tried: 
```
sudo apt-get install linux-frimware-nonfree
```
You will have to reboot..:)

---

### Post by nicholas7 on 2013-09-19
yes i did try that code already and it did not work even after reboot.

---

### Post by QDR06VV9 on 2013-09-19
> **nicholas7 said:**
> yes i did try that code already and it did not work even after reboot.

Strange I have the same card on a laptop and that has never failed?
And I have never seen varunendra not get someone wifi to work..
But this may help,[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers]("http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers")
Good Luck But one last question you have the swicth on right(wifi)?
Regards

---

### Post by varunendra on 2013-09-20
Sorry for a late response, I'm out of home, didn't get an opportunity to reply earlier..

Anyway, it seems you did the purge part correctly, and the report is also unable to give me any significant hints. So my first suspect is the router configuration.> **nicholas7 said:**
> 
Also i dont how to changed my router to g b/g mode.
Please refer to the manual of your router. The settings and ways to access/change them are quite different across different models, so there is no 'general' guide to cover that aspect for all.

If you can't find the channel/mode setting for your router, please give us its exact model no., and maybe I can try to look it up for you.

Also, please try -
```
sudo rfkill unblock all
```
..then post the full outputs of -
```
rfkill list all
sudo iwlist scan
lsmod
```

> **runrickus said:**
> And I have never seen varunendra not get someone wifi to work..
Well.. I've seen that happen many times before, but not with these 'easy-to-fix' broadcom cards :(

---

### Post by QDR06VV9 on 2013-09-20
> **varunendra said:**
> 


Well.. I've seen that happen many times before, _but not with these 'easy-to-fix' broadcom cards _:(

I Should have been more specific:)

---

### Post by amanchesterman on 2013-09-20
Hi, I just noticed this thread, or I would have contributed earlier.

I have an Acer laptop which has the BCM4318 network card. As others have said, the standard driver packaged with Ubuntu doesn't work. To install a working replacement, I simply opened Synaptic Package Manager and got it to install 'firmware-b43-installer'. That installs some other stuff that is needed and (in my experience) it gets the network card working quickly and easily.

I hope that's some help to you.
Good wishes
John

---

### Post by varunendra on 2013-09-21
@ amanchesterman,

Nice to see you are interested in contributing. Since you seem to have remembered that particular fix, I think what that fix actually does may also be interesting for you. Both these packages - "linux-firmware-nonfree" and "firmware-b43-installer" do more or less the same thing - they install the required firmware files for the b43 driver (linux-firmware-nonfree installs more files, but those are unrelated).

It is notable that some "LowPower" (LP) and "legacy" cards need slightly different types of firmware for which "firmware-b43-lpphy-installer" and "firmware-b43legacy-installer" packages are used instead. These packages are not firmware themselves, but they download the required firmware files from authentic sources and install (just copy) them to correct location (b43 or b43legacy dir in /lib/firmware).

The "linux-firmware-nonfree" package is itself a collection of all these firmware files (plus many other 'nonfree' ones for different kind of devices). So it is more useful in the sense that it can also be installed on offline systems (download the single package on another system, install on the target one with double-click).

These firmware files can't be distributed with the Ubuntu CD/DVD due to licencing issues. But it is perfectly legal for the users to download and install them for their personal use.

That being explained, however, nicholas7 seems to already have the required firmware installed -
> **nicholas7 said:**
> 
***** dmesg *****
.....
[   12.072052] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   21.336068] **b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)**
[/CODE]
..which means the problem lies somewhere else. Let's hope we can uncover it soon with little cooperation and persistence. :)

---

### Post by amanchesterman on 2013-09-21
@ Varunendra: Many thanks for your clear and interesting explanation, and for responding to my post in a constructive way. I've used Linux (mainly different versions of Ubuntu) for a few years now but I'm still very much a beginner when it comes to fixing it: like many users, I guess, I mainly want to *use* the computer to do things and I haven't spent a lot of time finding out how it works. But some technical knowledge certainly comes in handy, and I'm picking up bits as I go along -- often from browsing in these forums.

Let's hope, as you say, that Nicholas7 manages to get his system working soon.
Good wishes
John

---

### Post by nicholas7 on 2013-09-21
Hi, thanks so much for all of your help. Here is the commands output you told me to post, also i was looking for how to change the b/g mode thing on my router and i found it. Theres multiple chocies for me to pick:
*Mixed
*disabled
*b-only
*g-only
right now its currently on Mixed and dont know which one to put it to. 
Heres the command outputs:

Code:

```
rfkill list all
```

Output

```
0: phy0: Wireless LAN	Soft blocked: no
	Hard blocked: no
```

Code:

```
sudo iwlist scan
```

Output:

```
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan1     No scan results
```

Code:
```
lsmod
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48053  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
arc4                   12509  2 
b43                   364596  0 
snd_hda_codec_realtek    65004  1 
mac80211              541819  1 b43
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
i915                  550344  3 
cfg80211              453853  2 b43,mac80211
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
drm_kms_helper         47749  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   233935  4 i915,drm_kms_helper
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
coretemp               13324  0 
snd_timer              28931  2 snd_pcm,snd_seq
bcma                   39810  1 b43
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13316  1 i915
soundcore              12600  1 snd
ssb                    51554  1 b43
joydev                 17329  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
psmouse                82769  0 
video                  19116  1 i915
lpc_ich                17048  0 
dcdbas                 14065  0 
serio_raw              13031  0 
microcode              18433  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12484  0 
usbhid                 46125  0 
hid                    83037  2 hid_generic,usbhid
floppy                 60183  0 
e1000e                181539  0

---

### Post by varunendra on 2013-09-21
> **nicholas7 said:**
> Theres multiple chocies for me to pick:
*Mixed
*disabled
*b-only
*g-only
right now its currently on Mixed and dont know which one to put it to.

Looks like it is already a b/g mode router. As such, I don't think it will make any difference, but let's just try it to rule out the possibility - please choose "g-only" > save and reboot the router. Then in Ubuntu, please try -
```
sudo modprobe -rv b43
sudo modprobe -v b43
sudo iwlist scan
```
Does the last command return any scan results? If not, leave it to g-only mode in the router if you can, so that we can test other things without any doubt on the router part.

---

### Post by jsn-mllkn on 2013-09-21
That did it for me, Varun! Thank you very much, you are a god among men.

---

### Post by nicholas7 on 2013-09-21
Well I tried to make my router to G-Only but then it wouldn;t let me connect to my router and it went back to Mixed by itself and it took out my password and i had to reset the password for my router. I dont think its going to work. 

So i tried the commands you gave me and again still doesn't work, when i typed in
```
sudo iwlist
```

it said the same thing as before and wasn't scanning. I dont know if i should have my Ubuntu Desktop with the problem to be pluged into my router for it to be able to scan, because right now i dont have any internet, and if i need internet for the scan then ill plug it into the ethernet cable, so it scanns.


Thanks alot for all of your guys help. I really hope you can help me get this fixed. :D

---

### Post by varunendra on 2013-09-21
> **jsn-mllkn said:**
> That did it for me, Varun! Thank you very much, you are a god among men.
Thanks a lot for your overgenerous compliments, but what did it for you? The firmware package?
Oh, and Welcome to the forums ! :)

> **nicholas7 said:**
> Well I tried to make my router to G-Only but then it wouldn;t let me connect to my router and it went back to Mixed by itself and it took out my password and i had to reset the password for my router. I dont think its going to work.

Were you connected wirelessly to the router? You'd need to be connected via cable to be able to save the changes in the channel mode.

PS:
Please don't expect too much from me (although I'm not going to give up so easily on this one :P). I'm just this guy who is learning from experience and feedbacks from users like you. I need you more than you need me. :)

---

### Post by nicholas7 on 2013-09-21
Ok i put my router to G-only but when i run the scan command on my desktop with ubuntu it still says its unable to scan, does my desktop need to be connect to my router though the ethernet cable in order to run the scan?

Thanks alot :D

---

### Post by Hadaka on 2013-09-21
Hi, the BRCM 4318 is a very simple broadcom card.
which means it can be also eaisly confused. How do i know?
I am currently running 3 4318 cards in 3 different laptops.
You have been hammering in alot of commands, messing about 
with the router and plugging the ethernet cable in and out. sooooo
please try this..in this order

*Disconnect the ethernet cable
*power down the router
*power down the computer
*Have a sandwich..
*power up the router...let it sync up 3 minutes
*power up the computer
Is it working now?

---

### Post by varunendra on 2013-09-21
So evidently Hadaka rules these cards :P Please try immediately what he suggested. And have the sandwich large enough to keep you busy for at least 4 minutes (usually long enough for electronic cards to fully reset). ;)

Just to answer your last question -
> **nicholas7 said:**
> does my desktop need to be connect to my router though the ethernet cable in order to run the scan?

No, you don't need to be connected via cable. The "scan" command scans for available wireless networks. There's no point in having the capability to scan if you need a wired connection for it to complete, right ? :P

---

### Post by nicholas7 on 2013-09-21
I did the reboot router and everything in the right steps and it still isnt working :'( 

I was looking for a solution to this problem and i got a error when trying to do the command

```
sudo apt-get install bcmwl-kernel-source
```

the crashreport said
"Sorry, a problem occured when trying to install the software."

I really hope we cab solve this, thanks so far for your help guys> :D

---

### Post by Hadaka on 2013-09-21
Hi, that is not the correct driver for your card and if it had
loaded it would have blacklisted the b43 driver that you need.
lts do this, start from scratch. Enter all these commands one at
a time. if you get a error saying "not found" that is ok..enter 
the next command anyway. please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
```
sudo apt-get remove --purge linux-firmware-nonfree
```
```
sudo modprobe -r ssb
```
this will remove current drivers
Now lets load the b43 driver..please do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
also check your netowork mgr settings..they should look like the attached.
[ATTACH=CONFIG]246414[/ATTACH]

---

### Post by nicholas7 on 2013-09-21
Thanks for the reply.

When i did the first 2 commands they removed and had no problems, then when i typed in:

[COLOR=#000000]Code:
sudo modprobe -r ssb[/COLOR]
[COLOR=#000000]nothing happened.
Then when i did:

[/COLOR][COLOR=#000000]Code:
sudo apt-get install b43-fwcutter firmware-b43-installer
[/COLOR]
[COLOR=#000000]it said its already installed, and when i typed in:

[/COLOR][COLOR=#000000]Code:
sudo modprobe b43[/COLOR]
[COLOR=#000000]nothing happened. And i still wasnt able to connect wirelessly to the internet. Thanks alot for the help :D :D




[/COLOR]

---

### Post by Hadaka on 2013-09-21
please post the output of..
```
lsmod
cat /etc/modules
rfkill list all
```
thanks

---

### Post by nicholas7 on 2013-09-21
Thanks for the reply, here are the outputs:

Code:
```
lsmod
```

Output:
```
Module                  Size  Used bynls_iso8859_1          12617  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
b43                   364596  0 
snd_hda_codec_realtek    65004  1 
coretemp               13324  0 
joydev                 17329  0 
hid_generic            12484  0 
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              541819  1 b43
i915                  550344  3 
usbhid                 46125  0 
snd_hwdep              13276  1 snd_hda_codec
hid                    83037  2 hid_generic,usbhid
cfg80211              453853  2 b43,mac80211
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
drm_kms_helper         47749  1 i915
snd_seq_midi           13132  0 
drm                   233935  4 i915,drm_kms_helper
snd_rawmidi            25157  1 snd_seq_midi
psmouse                82769  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14065  0 
serio_raw              13031  0 
bcma                   39810  1 b43
microcode              18433  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                17048  0 
i2c_algo_bit           13316  1 i915
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              12600  1 snd
video                  19116  1 i915
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
floppy                 60183  0 
ssb                    51554  1 b43
usb_storage            48053  1 
e1000e                181539  0 
cat 
```



Code:
```
cat /ect/modules
```


Ouput:
```
cat: /ect/modules: No such file or directory
```

Code:
```
rfkill listall
```

Output:
```
Usage:    rfkill [options] commandOptions:
    --version    show version (0.4-1ubuntu2 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm


```


Thanks so so much for the help :D :D :D :D

---

### Post by Hadaka on 2013-09-21
Hi, with the ethernet cable disconnected please do..
```
sudo modprobe -r b43
sudo modprobe -v b43
dmesg | grep b43
```
post the output please
thanks.

---

### Post by nicholas7 on 2013-09-21
Thanks for the reply heres the output of the commands

Code:
```
sudo modprobe -r b43 
```

Output:
Didnt do anything at all

Code:
```
sudo modprobe -v b43
```

Output:
```
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko 
```


Code:
```
dmesg | grep b43
```

Output:
```
[    1.758929] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    9.728876] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    9.772035] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   10.001526] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.001592] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.001650] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5635.931259] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 5635.972033] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[ 5636.013516] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5636.013524] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5636.013528] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Thanks lot for the help :D

---

### Post by Jonathan Precise on 2013-09-21
(I think I) Found the errors causing it:
> **nicholas7 said:**
> ```
[    1.758929] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[    9.728876] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    9.772035] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   10.001526] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.001592] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.001650] b43-phy0 _**ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43**_ #devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 5635.931259] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 5635.972033] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[ 5636.013516] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 5636.013524] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 5636.013528] b43-phy0 _**ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43**_ #devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Please read EVERYTHING in the site:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Also (don't know if helpful or not, as not a networking expert) try setting your router to "b only" after downloading the driver.

---

### Post by Hadaka on 2013-09-21
Hi, from a wired connection connected to the internet please do..
```
sudo apt-get update
sudo apt-get upgrade
```
this should take care of those error codes.
this will take a little time
when its done..boot.
thanks

---

### Post by nicholas7 on 2013-09-21
Ok i did the update and then upgrade and it worked and downloaded successfully.

Before when you asked my to post the output of the command:

```
cat /etc/modules
```

before it siad it wasnt a directory and now it says...:

```
# /etc/modules: kernel modules to load at boot time.#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp



```

Thanks alot for the help :D

---

### Post by Hadaka on 2013-09-21
ok,from a wired connection please do...
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
Now do you have wireless?

---

### Post by nicholas7 on 2013-09-21
nope it still doesnt work, i took of the picture of the error i get when i try to install the driver. It installs 3/4 then the error in the picture pops up, i think that might be the problem? Also sometimes when i try to install the driver another error pops up asking me to send an error report, it says there was a problem installing the bcmwl-kernernel-scource i added a pic of that too in the attachments.

Thanks alot for the help. :D even though were not making much progress.

---

### Post by Hadaka on 2013-09-21
WHY? do you insist on attempting to load bcmwl-kernnel-scource??????
that is the WRONG driver.
when your computer asks you if you want to load a proprietary driver say NO !
youcard...4318 uses the b43 driver..not the WL...wl is the brcmwl-kernel-source.

---

### Post by nicholas7 on 2013-09-21
i was just showing you the error of what comes up maybe it will show you how to fix it, i wasn't attempting to load the bcmwl-kernel-scource it pops up every time i restart my computer or try to a command you tell me to do in terminal. Im so new at this whole thing. Im sorry if i did something wrong I just want to use ubuntu because its so fast and my computer with windows is so slow.

---

### Post by Hadaka on 2013-09-21
ok, something is telling it to load that driver...anyway
lets try this one more time..and please do only the commands
i give you ..ignore anything the the os suggests..
please do..from a wired connection..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
post the output of..
```
sudo iwlist wlan0 scan
```
thanks.

---

### Post by varunendra on 2013-09-21
@ nicholas7,

Let's take a look at current overall setup. Please download [this alternate script]("http://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script") (right-click the link > save as..), and run it as you did with the previous one (No internet method). Post back the fresh report it generates.

---

### Post by nicholas7 on 2013-09-22
Thanks guys for the help:

Code:
```
sudo iwlist wlan0 scan
```

Output:
```
wlan0     Interface doesn't support scanning.
```

Wireless Script Without Internet:

```
************** info trace ***************

***** uname -a *****


Linux nicholas-Inspiron-530 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
	Subsystem: Dell Inspiron 530 [1028:020d]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
	Kernel modules: ssb


***** lsusb *****


Bus 002 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 007 Device 002: ID 0461:4d63 Primax Electronics, Ltd 
Bus 007 Device 003: ID 03f0:d407 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x13b1:0x000d (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****




****************** done ******************



```

---

### Post by varunendra on 2013-09-22
As per the result above, the required driver b43 didn't even try to load, which is unexpected. Please post back the outputs of -
```
modprobe -c | grep -i 14e4.*4318
dmesg | grep -e b43 -e ssb
ls /lib/firmware/b43
```

**PS:**
Are you using a USB wireless adapter too? Does it work always?

---

### Post by nicholas7 on 2013-09-22
Thanks for the help here are the command outputs:

```
modprobe -c | grep -i 14e4.*4318
```

Output:
```
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ssb
```

Code:
```
[    1.732658] b43-pci-bridge 0000:02:00.0: setting latency timer to 64[    1.752078] ssb: Found chip with id 0x4318, rev 0x02 and package 0x00
[    1.752092] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.752099] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.752106] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.752113] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.792218] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    9.633990] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    9.676045] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   20.500050] b43-phy0: Loading firmware version 508.1084 (2009-01-

```

Code:
```
ls /lib/firmware/b43
```


Output:
```
ls: cannot open directory /lib/firmware/b43: Permission denied
```

Thanks

---

### Post by Hadaka on 2013-09-22
Hi, let's try this.
remove the usb wifi if its plugged in
then.
 from a wired connection please do..
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer

```
then do..
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
disconnect the wired ethernet cable
boot
ignore any proprietay drivr windows..just close them
wireless working now?

---

### Post by nicholas7 on 2013-09-22
Nope still isn't working.
The closest we got was when vanerana gave me a few codes and then the new option came up. I took 2 pictures. One picture as it looks now and other picture on how it looked when he gave me those codes before. I dont know if this helps at all but it seems where not getting close to the problem :(
the one that doesn't say broadcom driver is the one right now. Thanks :) hope this somehow help you.

---

### Post by Hadaka on 2013-09-22
The reason for that is..the screeen shot on
the left..is without the usb wifi plugged in
the screen shot on the right is with the usb wifi inserted.
we are trying to get the 4318 internal broadcom card working
and need to leave the usb wifi disconnected.
with the usb removed...please do..
```
sudo modprobe -r b43
sudo modprobe b43
```
then do..
```
dmesg | grep b43
```
post the output please
thanks.

---

### Post by nicholas7 on 2013-09-22
Oh ok thats why. I haven't had the usb wifi thing plugged in at all for a week the picture was with the usb wifi 2 weeks ago. Also maybe the wifi thing is not plugged in all the way? i doubt that becuase it was working fine in windows vista and all of a sudden when i download ubuntu it doesn't work i dont know :/  Ok thanks for your help :D here are the commands:

Code:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r b43
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe b43[/FONT][/COLOR]
```

Whenever i type those 2 codes in nothing happens at all.

Code:
```
[COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep b43[/FONT][/COLOR]
```

Ouptut:
```
[    1.754870] b43-pci-bridge 0000:02:00.0: setting latency timer to 64[    9.794476] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    9.836043] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   21.408044] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[ 2919.650767] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[ 2919.692027] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[ 2919.904033] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)



```

Thanks alot

---

### Post by Hadaka on 2013-09-22
please post the output of..
```
iwconfig
```
```
ifconfig
```
```
lsmod
```
```
lsusb
```
thanks.

---

### Post by nicholas7 on 2013-09-22
Thanks for the help. You didn't specify to do the first 2 commands with or without the ethernet plugged in so i did both. Here are the commands:

 Code-without ethernet cable

```
iwconfig
```

Output:
```
lo        no wireless extensions.

eth0      no wireless extensions.


wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Code-with ethernet 

```
iwconfig
```

```
lo        no wireless extensions.


eth0      no wireless extensions.


wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Code- without internet

```
ifconfig
```

Output:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:76:45:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1337080 (1.3 MB)  TX bytes:418381 (418.3 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92689 (92.6 KB)  TX bytes:92689 (92.6 KB)


wlan1     Link encap:Ethernet  HWaddr 00:1d:60:d7:12:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Code-with ethernet:

```
ifconfig
```

```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:76:45:5d  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe76:455d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1335828 (1.3 MB)  TX bytes:417591 (417.5 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92689 (92.6 KB)  TX bytes:92689 (92.6 KB)


wlan1     Link encap:Ethernet  HWaddr 00:1d:60:d7:12:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Code:
```
lsmod
```

```
Module                  Size  Used by
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
ssb                    51554  1 b43
bcma                   39810  1 b43
nls_iso8859_1          12617  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211435  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12509  2 
snd_hda_codec_realtek    65004  1 
joydev                 17329  0 
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
hid_generic            12484  0 
coretemp               13324  0 
snd_hwdep              13276  1 snd_hda_codec
i915                  550344  3 
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
usbhid                 46125  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
hid                    83037  2 hid_generic,usbhid
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
psmouse                82769  0 
drm_kms_helper         47749  1 i915
snd_timer              28931  2 snd_pcm,snd_seq
drm                   233935  4 i915,drm_kms_helper
dcdbas                 14065  0 
serio_raw              13031  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
microcode              18433  0 
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13316  1 i915
mac_hid                13077  0 
lpc_ich                17048  0 
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
floppy                 60183  0 
usb_storage            48053  1 
e1000e                181539  0 
```

Code:
```
lsusb
```

Output:

```
Bus 002 Device 005: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 007 Device 002: ID 0461:4d63 Primax Electronics, Ltd 
Bus 007 Device 003: ID 03f0:d407 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I dont know if there is any differnce bettween posting with the ethernet or without ethernet so i just put both
Thanks for the help :D

---

### Post by Hadaka on 2013-09-22
ok, with the ethernet cable disconnected
please do and post..
```
sudo iwlist wlan1 scan
```
thanks.

---

### Post by nicholas7 on 2013-09-22
Ok i typed the code in without the ethernet cable plugged in and it said:

```
wlan1 no scan results
```

---

### Post by Hadaka on 2013-09-22
ok, with the ethernet cable attached
please do..
```
grep blacklist /etc/modprobe.d/blacklist.conf
```
post the output
thanks.

---

### Post by nicholas7 on 2013-09-22
Thanks for the help heres the commands:

```
[COLOR=#000000][FONT=Ubuntu Mono]grep blacklist /etc/modprobe.d/blacklist.conf[/FONT][/COLOR]
```

Output:
```
blacklist evbugblacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac



```

---

### Post by Hadaka on 2013-09-22
ok, with the ethernet connected and connected to the internet
please do and post the entire output of..
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer

```
then..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by nicholas7 on 2013-09-22
Here are the commands:

Input:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge b43-fwcutter firmware-b43-installer[/FONT][/COLOR]
```

Output:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu python-renderpm libart-2.0-2 python-reportlab-accel python-reportlab
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  b43-fwcutter* firmware-b43-installer*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 111 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 211384 files and directories currently installed.)
Removing firmware-b43-installer ...
Deleting old extracted firmware...
Purging configuration files for firmware-b43-installer ...
Removing b43-fwcutter ...
Processing triggers for man-db ...
```


Input:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install b43-fwcutter firmware-b43-installer[/FONT][/COLOR]
```

Output:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu python-renderpm libart-2.0-2 python-reportlab-accel python-reportlab
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/22.4 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Selecting previously unselected package b43-fwcutter.
(Reading database ... 211374 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2013-09-22 17:37:41--  http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... 46.4.11.11
Connecting to mirror2.openwrt.org (mirror2.openwrt.org)|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1.5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'


100%[============================================================================================>] 1,596,823    449K/s   in 3.5s    


2013-09-22 17:37:47 (449 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]


broadcom-wl-5.10.56.27.3/driver/
broadcom-wl-5.10.56.27.3/driver/Makefile
broadcom-wl-5.10.56.27.3/driver/aiutils.c
broadcom-wl-5.10.56.27.3/driver/bcmsrom.c
broadcom-wl-5.10.56.27.3/driver/bcmutils.c
broadcom-wl-5.10.56.27.3/driver/hnddma.c
broadcom-wl-5.10.56.27.3/driver/hndpmu.c
broadcom-wl-5.10.56.27.3/driver/include/
broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h
broadcom-wl-5.10.56.27.3/driver/include/aidmp.h
broadcom-wl-5.10.56.27.3/driver/include/arminc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h
broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h
broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h
broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h
broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h
broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h
broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h
broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h
broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h
broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h
broadcom-wl-5.10.56.27.3/driver/include/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/igs/
broadcom-wl-5.10.56.27.3/driver/include/epivers.h
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev
broadcom-wl-5.10.56.27.3/driver/include/etioctl.h
broadcom-wl-5.10.56.27.3/driver/include/flash.h
broadcom-wl-5.10.56.27.3/driver/include/flashutl.h
broadcom-wl-5.10.56.27.3/driver/include/hndarm.h
broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h
broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/hnddma.h
broadcom-wl-5.10.56.27.3/driver/include/hndgige.h
broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h
broadcom-wl-5.10.56.27.3/driver/include/hndmips.h
broadcom-wl-5.10.56.27.3/driver/include/hndpci.h
broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h
broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h
broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h
broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h
broadcom-wl-5.10.56.27.3/driver/include/linuxver.h
broadcom-wl-5.10.56.27.3/driver/include/min_osl.h
broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h
broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h
broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h
broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h
broadcom-wl-5.10.56.27.3/driver/include/nicpci.h
broadcom-wl-5.10.56.27.3/driver/include/osl.h
broadcom-wl-5.10.56.27.3/driver/include/pci_core.h
broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h
broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h
broadcom-wl-5.10.56.27.3/driver/include/proto/
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h
broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h
broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h
broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h
broadcom-wl-5.10.56.27.3/driver/include/rts/
broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h
broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h
broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h
broadcom-wl-5.10.56.27.3/driver/include/sbgige.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h
broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h
broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h
broadcom-wl-5.10.56.27.3/driver/include/sflash.h
broadcom-wl-5.10.56.27.3/driver/include/siutils.h
broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h
broadcom-wl-5.10.56.27.3/driver/include/typedefs.h
broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h
broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h
broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h
broadcom-wl-5.10.56.27.3/driver/linux_osl.c
broadcom-wl-5.10.56.27.3/driver/nicpci.c
broadcom-wl-5.10.56.27.3/driver/nvram_stub.c
broadcom-wl-5.10.56.27.3/driver/sbutils.c
broadcom-wl-5.10.56.27.3/driver/siutils.c
broadcom-wl-5.10.56.27.3/driver/siutils_priv.h
broadcom-wl-5.10.56.27.3/driver/wl_apsta/
broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_dbg.h
broadcom-wl-5.10.56.27.3/driver/wl_export.h
broadcom-wl-5.10.56.27.3/driver/wl_iw.c
broadcom-wl-5.10.56.27.3/driver/wl_iw.h
broadcom-wl-5.10.56.27.3/driver/wl_linux.c
broadcom-wl-5.10.56.27.3/driver/wl_linux.h
broadcom-wl-5.10.56.27.3/driver/wlc_key.h
broadcom-wl-5.10.56.27.3/driver/wlc_pub.h
broadcom-wl-5.10.56.27.3/nas_exe.o
broadcom-wl-5.10.56.27.3/shared/
broadcom-wl-5.10.56.27.3/shared/Makefile
broadcom-wl-5.10.56.27.3/shared/UdpLib.c
broadcom-wl-5.10.56.27.3/shared/bcmcvar.h
broadcom-wl-5.10.56.27.3/shared/bcmtimer.h
broadcom-wl-5.10.56.27.3/shared/ctype.c
broadcom-wl-5.10.56.27.3/shared/linux_timer.c
broadcom-wl-5.10.56.27.3/shared/netconf.h
broadcom-wl-5.10.56.27.3/shared/opencrypto.h
broadcom-wl-5.10.56.27.3/shared/rte_timers.c
broadcom-wl-5.10.56.27.3/shared/shutils.c
broadcom-wl-5.10.56.27.3/shared/shutils.h
broadcom-wl-5.10.56.27.3/shared/wl.c
broadcom-wl-5.10.56.27.3/shared/wl_linux.c
broadcom-wl-5.10.56.27.3/shared/wlutils.h
broadcom-wl-5.10.56.27.3/wl_exe.o
This file is recognised as:
  filename   :  wl_prebuilt.o
  version    :  508.1084
  MD5        :  490d4e149ecc45eb1a91f06aa75be071
Extracting b43/ucode19.fw
Extracting b43/lp0initvals14.fw
Extracting b43/ucode16_lp.fw
Extracting b43/ucode16_sslpn.fw
  ucode revision: 1084
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/sslpn2bsinitvals17.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/ucode16_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/sslpn2initvals17.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ucode17.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/ucode20.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw



```

Input:
```
sudo modprobe b43
```

and nothing happend on that command

thanks for the help.

---

### Post by Hadaka on 2013-09-22
ok,looks like that loaded ok.
please do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
then do a hard boot..shutdown..
once booted back up..please do and post the output of.
```
ifconfig
```
and try to post a screen shot of the network connection...like post #9
thanks.

---

### Post by nicholas7 on 2013-09-22
I did the first command did a shutdown and turned it back on i dont know if thats the same as a hard boot shutdown.
And i have a pic of how the wifi looks in the attachment

Then i did the ifconfig heres the output of what it said with the ethernet cable and without the cable:


with the ethernet 

```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:76:45:5d  
          inet addr:---.---.---.---  Bcast:---.---.---  Mask:
          inet6 addr: fe80::21d:9ff:fe76:455d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111892 (111.8 KB)  TX bytes:19525 (19.5 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2719 (2.7 KB)  TX bytes:2719 (2.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1d:60:d7:12:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

without the ethnet

```


eth0      Link encap:Ethernet  HWaddr 00:1d:09:76:45:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111892 (111.8 KB)  TX bytes:19525 (19.5 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2719 (2.7 KB)  TX bytes:2719 (2.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1d:60:d7:12:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

---

### Post by Hadaka on 2013-09-22
ok, now go to that same network mgr  you just posted and
click Edit Networks.
set your ssid name...ipv4 and set ipv6 no ignore.
most importantly check the box in the upper left corner..connect automatically.
then save your settings
boot.
tell me  have wireless

---

### Post by Hadaka on 2013-09-22
set it to look like this

[ATTACH=CONFIG]246444[/ATTACH]

---

### Post by nicholas7 on 2013-09-22
i have no idea what i did but i did what you told me to then i did connect to hidden wireless network and typed in my network name and it worked thanks all of you so sos so so so so much :D

---

### Post by Hadaka on 2013-09-22
GREAT !!!  glad its finally working !!
please mark your thread solved.
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by varunendra on 2013-09-23
Yay! Party on Hadaka :P

> **nicholas7 said:**
> i have no idea what i did..

I would be interested in the current outputs of -
```
cat /etc/udev/rules.d/70-persistent-net.rules
rfkill list
iwconfig
nm-tool
```
..especially the output of the first one, rest are just to see the effects.. :)

---

### Post by nicholas7 on 2013-09-23
Ok we'll i ran into a problem. I spoke too soon about this begin totally fixed. I did mange to get internet by doing what he told, but when i shut down and turn back on it doesn't work anymore. The wireless doesn't automatically connect so i have to manually delete my old mgr settings thing, create a new one then i have to click "join hidden network" and it seems easy but took me 20 minutes. 

Problem 2: I was trying to fix it and i went to try to install my broadcom driver, and it still wasn't installed. So i tried to install it thinking it will work, and insted it came up with the 2 error mesages and then made it even worse. Now it wont even let me see the wireless thing. Ill take a picture and add it into the attachments on how it looked yesterday when it worked and today after i tried to install the driver.


What i think is happinging is like was said before, something is telling the bcmwl-kernel-source to run when its not the right driver for my broadcom, and it wont let me install the driver.

I can still connect to the internet if i delete bcmwcl-kernel-source and dont run the broadcom installation driver, and every time i restart it will take me 20 min to connect to the internet.

---

### Post by Hadaka on 2013-09-23
Hi, please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo su
echo b43 >> /etc/modules
exit 0
```
boot.
does it connect now?

---

### Post by nicholas7 on 2013-09-25
Sorry for late response I figured out a way to connect to the internet in 2 min. It still doesn't connect automatically I have to manually do it but I'm fine with that. It's better hen having no internet at all.

thanks so very much for the help &#128516;

---

### Post by xdecalmanx on 2013-10-13
> **varunendra said:**
> The sta driver won't support your card, the native b43 will. Please purge the sta driver package and install the firmware for b43 instead -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

Then unload (if already loaded) and reload the b43 driver-
```
sudo modprobe -rv b43
sudo modprobe -v b43
```
Wifi active now? Do a reboot if necessary.

This worked perfectly on my Gateway MX6441 with the same wifi card.  I had to disconnect my usb wifi adapter for the last two code to work.

[[http://i1095.photobucket.com/albums/i479/axsepul/UBUNTU/BCM4318UBUNTUFIXED_zps041cc81c.png](http://i1095.photobucket.com/albums/i479/axsepul/UBUNTU/BCM4318UBUNTUFIXED_zps041cc81c.png)](http://s1095.photobucket.com/user/axsepul/media/UBUNTU/BCM4318UBUNTUFIXED_zps041cc81c.png.html)

This also fixed my Ubuntu 12.04 LTS not shutting down properly problem.

I was getting this when i tried to shutdown and restart ubuntu 12.04 lts

[[http://i1095.photobucket.com/albums/i479/axsepul/UBUNTU/PicsArt_1381538433830_zpsefc10b5f.jpg](http://i1095.photobucket.com/albums/i479/axsepul/UBUNTU/PicsArt_1381538433830_zpsefc10b5f.jpg)](http://s1095.photobucket.com/user/axsepul/media/UBUNTU/PicsArt_1381538433830_zpsefc10b5f.jpg.html)

now it will restart and shutdown.

Thank You very much!!!

---

### Post by varunendra on 2013-10-13
> **xdecalmanx said:**
> This worked perfectly on my Gateway MX6441 with the same wifi card.
....
This also fixed my Ubuntu 12.04 LTS not shutting down properly problem.


You're welcome. And your feedback is much appreciated, thanks ! :)

---

### Post by Great Blue Heron on 2014-01-31
[QUOTE=varunendra]
The sta driver won't support your card, the native b43 will. Please purge the sta driver package and install the firmware for b43 instead -

Code:

sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree

Then unload (if already loaded) and reload the b43 driver-

Code:

sudo modprobe -rv b43
sudo modprobe -v b43

Wifi active now? Do a reboot if necessary.[/QUOTE]

I would like to post and say that this also worked for me! :D

I am using an old Compaq Presario V5000 laptop running Linux Mint 16 XFCE edition. I hope this is able to help somebody else. :)

---

