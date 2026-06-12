---
title: "Broadcom 4306 wireless fail in ubuntu (10.04)"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by movrshakr on 2014-03-11
This is one more of the THOUSANDS of posts by people who cannot get wireless to work in a computer with ubuntu and a Broadcom wireless adapter (BCM 4306 in this case)

This is mostly a rant because, well, because I have to.

I have an older laptop.  It had ubuntu on it--don't remember the version.  Plan to sell it.  Decided to 'clean' it by reinstalling ubuntu. Tried 12.04; wouldn't work...don't remember the fail...
[LATER CORRECTION: The fail was that, at one of the iinstall windows early in the process, it would not "movve on"--the spinning cursor sat there for hours]...
so put on 8.04 because I had the DVD already, upgraded to 10.04 (wired INET), upgraded to 12.04--which failed again but only that video wouldn't work right this time.  Downloaded and installed 10.04.  Hooray...oops....wait for it...no wireless.

At this point, I remember that when I first put ubuntu on the machine a couple of years ago, I had MAJOR problem getting the wireless to work.  The light on the wireless button switch light indicating that the adapter was powered was not even lighted.  That took about six months to solve, then another two months to actually get a wireless connection to work.  Unfortunately, I remember nothing about how I finally resolved it before.

Fast forward to now, and I am back to square one--finally got a 'kind of' working ubuntu on it, but the infamous Broadcom insidious issue is back.  I do not have any reference to wireless whatsoever in the manager--not that it won't connect--there is nothing there period.  And I don't mean no SSIDs showing, I mean no wireless in ipconfig--or in the gui manager.

So, four hours so far reading the thirty ways to fix it, trying seven of them, and still have nothing.

Going to go to sleep now.  Think I will just sell it with wireless not working; it isn't worth the pain.

---

### Post by mörgæs on 2014-03-11
Good night.
I suggest you to switch to a less negative tone if you want to get help. Not written with my moderator hat on, just as an ordinary user.

---

### Post by varunendra on 2014-03-11
Let me know when you are feeling better, and are in a mood to take a little pain, if at all. :)

---

### Post by Bucky Ball on 2014-03-12
10.04 LTS is no longer supported unless you are using the server version. I suggest you try installing 12.04 or 13.10, both directly upgradeable to 14.04 LTS when it comes out (5 years support), and post a new thread in ***Installation & Upgrades*** with a lot more detail about what issues you're getting when and if the installation fails. 

While I understand your frustration, a rant with no details about error messages, what you've tried, or a full description of the problem won't get you a lot of help. This is not really even a support request. You might want to have a look at the third link in my signature. Good luck.

---

### Post by movrshakr on 2014-03-12
10.04 should be supported through 15.04, should it not?

Also, I already said that 12.04 does not work on this computer (apart from the wireless issue).

Impossible to list what I have tried.  As I encountered posts saying "this fixes it," I tried whatever was there.  Any fix from this point would probably best start by removing all packages relating to wireless, and then putting in the "right" ones--assuming there ARE "right" ones that will work.  Obviously, so far I have not found them.

The adapter is BCM4306, PCI-ID [14e4:4320] rev 03.
Confusingly,
[http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)
shows this as being "supported," yet it does not work.

With all that I have tried, there is no telling what has been blacklisted at this point.  I know how to edit, but do not know which file to check nor what changes should be made.

---

### Post by mörgæs on 2014-03-12
10.04 is supported through 15.04 for the server version, as already posted. The desktop version is dead. 

You have still not mentioned which hardware you are using. I assume it's too old for Ubuntu, so Lubuntu 13.10 is a good option.

---

### Post by varunendra on 2014-03-12
Maybe get your video issue fixed first then, on 12.04 of course. If it works on 10.04, I can't imagine it shouldn't work on 12.04.

As for the wireless, BCM4306 _IS_ supported, but you need proprietary firmware for it to work.

If you are interested, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by movrshakr on 2014-03-12
Thanks for the info on LTS.  I never knew there was a different specification for support on desktop vs. server.

Hardware (told you it was old!)...
Hewlett-Packard Pavilion zv5200 (PF143UA#ABA) F.11
800 megahertz AMD Athlon 64
64 kilobyte primary memory cache
256 kilobyte secondary memory cache		 		
Board: Compal 08A0 32.22
Bus Clock: 133 megahertz
BIOS: Hewlett-Packard F.11 04/30/2004
Drives
44.91 Gigabytes Usable Hard Drive Capacity
27.97 Gigabytes Hard Drive Free Space

HL-DT-ST RW/DVD GCC-4241N [CD-ROM drive]
FUJITSU MHT2060AT PL [Hard drive] (60.01 GB) -- drive 0,  rev 0022, SMART Status: Healthy		 		
512 Megabytes Installed Memory

---

### Post by movrshakr on 2014-03-12
> **varunendra said:**
> ...
If you are interested, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Here it is..
```
*************** info trace ***************
***** uname -a *****

Linux HP-Pavilion 2.6.32-57-generic #119-Ubuntu SMP Wed Feb 19 01:04:55 UTC 2014 i686 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

***** lspci *****

02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Kernel modules: ssb
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)

***** lsusb *****

Bus 003 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05dc:a813 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

***** rfkill *****

***** iw reg get *****

***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

***** lsmod *****

***** nm-tool *****

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.226
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             156.154.70.22

***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

***** NetworkManager.conf *****

nm-system-settings.conf (used up to 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback

***** iwlist *****

***** resolv.conf *****

domain cfl.rr.com
search cfl.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 156.154.70.22

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

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

[/etc/modprobe.d/blacklist-local.conf]
blacklist nvidia_96

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist ssb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

***** udev rules *****

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4320 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****
****************** done ******************


```

---

### Post by wildmanne39 on 2014-03-12
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source bcmwl-modaliases
```
watch for errors but continue even if there are some:

Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:[ATTACH=CONFIG]251076[/ATTACH]
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if it does not work copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by movrshakr on 2014-03-12
I am a bit concerned to start following directions from two people (wildman and varenda) and get things crossed up if you happen to proceed in two different directions.  Guess I will follow wildman; no offense to others, k?

Wildman, did you see that I posted the output of that last data-gathering command in my preceding post?
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by wildmanne39 on 2014-03-12
Yes, I did see that the only thing I see at this time that might need fixed is some modules that are blacklisted, but I want to wait until you run the commands I posted before deciding. It is possible you have everything installed so you can try this command first:
```
sudo modprobe b43
```if it turns wireless on we will need to clean a couple of files.
Varun is very good with these issues, I am pretty sure we would arrive at the same place, though we may do things a little different.
Thanks

---

### Post by movrshakr on 2014-03-12
OK.
"Download the b43 zip file"

Huh?   what file, from where?

---

### Post by movrshakr on 2014-03-12
sudo modprobe b43

WORKED!
The light on the wireless adapter button is ON!

and I have the selections relating to wireless in the manager drop  down

How do you make that survive a reboot?

ADDED: however, I cannot make it establish a connection to my SSID; I enter the passphrase, and it tries for good while, then window up saying authentication required--but the correct one does not complete a coonnection (yes, using right one caps off)

---

### Post by wildmanne39 on 2014-03-12
Run the script again and post a new wireless file so we can see what is going on with the driver loaded.
Thanks

---

### Post by wildmanne39 on 2014-03-12
See if this command will allow you to make a connection:
```
sudo dpkg-reconfigure resolvconf
```
still like to see a new file even if it does we need to see exactly what modules need to be unblacklisted, I do not remember everything about 10.04 it has been a long time since I have helped someone with it so seeing all info is very important.
What commands did you run from my first post?
Thanks

---

### Post by movrshakr on 2014-03-12
The dpkg command produced this:
"dpkg: conflicting actions -e (--control) and -r (--remove)"

I will go run the script again and post in a few minutes
(sorry for the delay; had a meeting and have been out)

WAIT:
I had put dpkg<space>-reconfigure
Reran w/ no space and got
"Package `resolvconf' is not installed and no info is available."

---

### Post by movrshakr on 2014-03-12
Here is the rerun of the script.
```

*************** info trace ***************

***** uname -a *****

Linux HP-Pavilion 2.6.32-57-generic #119-Ubuntu SMP Wed Feb 19 01:04:55 UTC 2014 i686 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

***** lspci *****

02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

***** lsusb *****

Bus 003 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

***** lsmod *****

b43                   163556  0 
ssb                    38934  1 b43
mac80211              205434  1 b43
cfg80211              126528  2 b43,mac80211
led_class               2864  1 b43

***** nm-tool *****

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.226
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             156.154.70.22


- Device: wlan0 ----------------------------------------------------------------
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



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

***** NetworkManager.conf *****

nm-system-settings.conf (used up to 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     No scan results


***** resolv.conf *****

domain cfl.rr.com
search cfl.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 156.154.70.22

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

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

[/etc/modprobe.d/blacklist-local.conf]
blacklist nvidia_96

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist ssb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

filename:       /lib/modules/2.6.32-57-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
firmware:       b43/pcm5.fw
firmware:       b43/n0initvals11.fw
firmware:       b43/n0bsinitvals11.fw
firmware:       b43/n0absinitvals11.fw
firmware:       b43/lp0initvals15.fw
firmware:       b43/lp0initvals14.fw
firmware:       b43/lp0initvals13.fw
firmware:       b43/lp0bsinitvals15.fw
firmware:       b43/lp0bsinitvals14.fw
firmware:       b43/lp0bsinitvals13.fw
firmware:       b43/b0g0initvals9.fw
firmware:       b43/b0g0initvals5.fw
firmware:       b43/b0g0initvals13.fw
firmware:       b43/b0g0bsinitvals9.fw
firmware:       b43/b0g0bsinitvals5.fw
firmware:       b43/b0g0bsinitvals13.fw
firmware:       b43/a0g1initvals9.fw
firmware:       b43/a0g1initvals5.fw
firmware:       b43/a0g1initvals13.fw
firmware:       b43/a0g1bsinitvals9.fw
firmware:       b43/a0g1bsinitvals5.fw
firmware:       b43/a0g1bsinitvals13.fw
firmware:       b43/a0g0initvals9.fw
firmware:       b43/a0g0initvals5.fw
firmware:       b43/a0g0bsinitvals9.fw
firmware:       b43/a0g0bsinitvals5.fw
license:        GPL
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     4AB148BAE42B366ECB1D7DA
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,led-class,cfg80211
vermagic:       2.6.32-57-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/2.6.32-57-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     2E3FB3DF88D3B5B0D753C9E
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
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
vermagic:       2.6.32-57-generic SMP mod_unload modversions 586 


***** udev rules *****

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4320 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[11683.268255] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[11683.274297] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[11683.441327] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[11683.764512] Registered led device: b43-phy0::tx
[11683.766376] Registered led device: b43-phy0::rx
[11683.768705] Registered led device: b43-phy0::radio
[11684.132078] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[11684.240176] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[11684.252529] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[11684.265619] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[11684.392078] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[11684.453836] ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************

```

---

### Post by varunendra on 2014-03-12
> **movrshakr said:**
> I am a bit concerned to start following directions from two people (wildman and varenda) and get things crossed up if you happen to proceed in two different directions.  Guess I will follow wildman; no offense to others, k?

Absolutely not! :D

In fact Wild Man is one of the few people whom I have learnt the wireless troubleshooting stuff from, and is the very same person who has created that script, I'm just a user of it.

In fact not following more than one troubleshooting strategy is something we personally recommend to everyone, no matter how trustworthy the strategies may be.

So.. I'd just sit back and watch the show unless Wild Man has to leave and he explicitly asks me to carry on from where he left. :)

---

### Post by wildmanne39 on 2014-03-12
Did you manually set this up? > ***** resolv.conf *****

domain cfl.rr.com
search cfl.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 156.154.70.22
Also I am pretty sure in 10.04 network manager will not let your wifi connect as long as you have your ethernet connected.
Thanks

---

### Post by movrshakr on 2014-03-12
Cool deal, varunendra.
I have done the steps he provided, but had to leave for a meeting;
and I think now he is not watching because I disappeared, but i will wait patiently for his next post.

I did do the last thing he posted while I was out--but it failed due to a pkg not being installed.
Maybe I will go install it and try that again since he isn't here right now.

---

### Post by movrshakr on 2014-03-12
> **Wild Man said:**
> Did you manually set this up? 
Also I am pretty sure in 10.04 network manager will not let your wifi connect as long as you have your ethernet connected.
Thanks

I did not manually put those in; it could only get those from the router (ipconfig does "see" those )

Also, I did try once to connect with the TP eth0 wire out; same result; all other tries have been with it in

---

### Post by movrshakr on 2014-03-12
maybe an oops.
I installed the pkg resolvconf, and ran the command you provided earlier.
Result--
~$ sudo dpkg-reconfigure resolvconf
[sudo] password for user: 
update-rc.d: warning: resolvconf stop runlevel arguments (none) do not match LSB Default-Stop values (0 6)

---

### Post by wildmanne39 on 2014-03-12
That is bug.
[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/750423](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/750423)
You did not actually change any settings right? I think you just installed it then it showed the error.

---

### Post by movrshakr on 2014-03-12
> **Wild Man said:**
> That is bug.
[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/750423](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/750423)
You did not actually change any settings right? I think you just installed it then it showed the error.
I installed the resolvconf pkg, then ran the command string as shown in the previous post,
with the error result as shown.

Other than running the command, I did not change anything; 
IT may have changed something--I don't know about that, or maybe the failure meant it did nothing.
Unknown to me.

---

### Post by wildmanne39 on 2014-03-12
Run this command and see if the same stuff is in the file as before:
```
gksudo gedit /etc/resolv.conf
```
Thanks

---

### Post by movrshakr on 2014-03-12
> **Wild Man said:**
> Run this command and see if the same stuff is in the file as before:
```
gksudo gedit /etc/resolv.conf
```
]Current contents
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 156.154.70.22
search cfl.rr.com

Before had a domain cfl.rr.com line in it
and different order

Looks like resolveconf DID make some minor changes.

I did try again with eth0 TP unplugged; no dice on wifi connect

---

### Post by movrshakr on 2014-03-12
I have to call a time out to go night night.
And tomorrow I am busy from wake up through about 1430 EDT US, 1830Z.

Thanks so much for the help. I will post here when back on.

---

### Post by wildmanne39 on 2014-03-12
We need to clean up the blacklist file and check a couple of other things but I am to tired to night I have not even stopped to eat.

So I will check in tomorrow and if varun wants he is more then welcome to step in, he is a lot younger then me and does not require as much sleep.

---

### Post by varunendra on 2014-03-12
> **Wild Man said:**
> he is a lot younger then me and does not require as much sleep.

I choose to take it as a compliment, even though I know its hidden meaning is - "that geeky idiot needs to get a life!" :|

---

### Post by movrshakr on 2014-03-13
Everyone will be delighted to know that all my appointments have been completed, so I am back.
Isn't that wonderful?!  <grin>

---

### Post by wildmanne39 on 2014-03-13
I am having been looking for my files on 10.04 but I guess I deleted them to do some house keeping, so I have been researching other information to make sure as much as possible on file location because many files moved between 10.04 and newer version.

We need to change this:
> nm-system-settings.conf (used up to 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=[COLOR="#FF0000"]false[/COLOR]to[COLOR="#FF0000"]true[/COLOR] so network manager will control it.
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```a window will open type your user password then the file should open change false to true, save, close gedit and reboot.

---

### Post by movrshakr on 2014-03-13
Ok, I did that.  After the reboot, the light showing wireless ON is now OFF again. 
 I think that is because before, when we did the modprobe thing, that only put it in for the current session.  
After reboot, that modprobe insert is no longer active.

---

### Post by wildmanne39 on 2014-03-13
You are correct, we need to unblacklist the modules:
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf
```
Then reboot and see if the driver loads on its own if not we will make it.
Thanks

---

### Post by movrshakr on 2014-03-13
OK, here is what I have done...
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
Changed false to 'true'
Reboot > light on wireless button OFF
```
sudo modprobe b43
```
Light on wireless button ON but I see it blink every now and then if trying to connect.
```
sudo gedit /etc/modules
```
...and added b43 in the list (was only one other one there).
LATER:  I did a test reboot, and the wireless light came on, so b43 is loading during boot.

If there is a better way to get b43 to load on boot, I can un-do these

****However, at this point, I still cannot get it to connect to my SSID, which I usually try through 'Connect to a hidden network', but then select MY network from the popdown inside that dialog (it does show there--the only one other than "NEW").  It tries for about 30 seconds, then changes to a dialog saying Authentication required.

---

### Post by chili555 on 2014-03-13
The Wild Man is off for a while and has asked his Jedi master to pick up the light saber. Let's see where we are so far. Please run and post:```
dmesg | grep -e wlan -e b43
iwconfig
sudo iwlist wlan0 scan
```You don't have to post the whole thing; just tell us if you see your own network.>  which I usually try through 'Connect to a hidden network'Is your SSID actually hidden? It's usually only a hinderance, not a help.

---

### Post by movrshakr on 2014-03-13
SSID is not hidden; shows on other computers.
I use that method (Connect to hidden) because I see no other way to tell the system to try to connect to a network you KNOW is available, but does not show anywhere to "click on".

Here are results
```
user@HP-Pavilion:~$ dmesg|grep -e wlan -e b43
[   19.913390] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   20.299635] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.477595] Registered led device: b43-phy0::tx
[   20.477618] Registered led device: b43-phy0::rx
[   20.477641] Registered led device: b43-phy0::radio
[   20.560303] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.656490] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.668899] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.681974] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.842192] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.965362] ADDRCONF(NETDEV_UP): wlan0: link is not ready


user@HP-Pavilion:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

user@HP-Pavilion:~$ sudo iwlist wlan0 scan
[sudo] password for user: 
wlan0     Interface doesn't support scanning : Device or resource busy

```

---

### Post by chili555 on 2014-03-13
Please try something for an old-timer:```
sudo modprobe -r b43
sudo modprobe b43legacy
sudo iwlist wlan0 scan
dmesg | grep b43
```We are looking for entries after 20.965362. Thanks.

---

### Post by movrshakr on 2014-03-13
```
user@HP-Pavilion:~$ sudo modprobe -r b43
user@HP-Pavilion:~$ sudo modprobe b43legacy
user@HP-Pavilion:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

user@HP-Pavilion:~$ dmesg|grep b43
[   19.913390] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   20.299635] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.477595] Registered led device: b43-phy0::tx
[   20.477618] Registered led device: b43-phy0::rx
[   20.477641] Registered led device: b43-phy0::radio
[   20.560303] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.656490] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.668899] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.681974] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.842192] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7748.230837] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
[ 7764.808124] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17

``` 
[SIZE=3]When I loaded b43 legacy, the wireless button light DID NOT come on.[/SIZE]

---

### Post by chili555 on 2014-03-13
Do you have each of the firmware files requested?```
ls /lib/firmware/b43
```Any ACPI or IRQ difficulty?```
dmesg | grep -i error
```Quite a little mystery we have here.

Off for the evening, I'll check in early tomorrow.

---

### Post by movrshakr on 2014-03-13
Results ```
user@HP-Pavilion:~$ ls /lib/firmware/b43
a0g0bsinitvals5.fw   a0g1initvals5.fw     lp0bsinitvals13.fw  n0initvals11.fw
a0g0bsinitvals9.fw   a0g1initvals9.fw     lp0bsinitvals14.fw  pcm5.fw
a0g0initvals5.fw     b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode11.fw
a0g0initvals9.fw     b0g0bsinitvals5.fw   lp0initvals13.fw    ucode13.fw
a0g1bsinitvals13.fw  b0g0bsinitvals9.fw   lp0initvals14.fw    ucode14.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw    lp0initvals15.fw    ucode15.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw     n0absinitvals11.fw  ucode5.fw
a0g1initvals13.fw    b0g0initvals9.fw     n0bsinitvals11.fw   ucode9.fw


user@HP-Pavilion:~$ dmesg | grep -i error
user@HP-Pavilion:~$ 
```
Should we go back to b43 vs. b43legacy, since b43 turned on the wireless light?

---

### Post by varunendra on 2014-03-14
> **movrshakr said:**
> ****However, at this point, I still cannot get it to connect to my SSID, which I usually try through 'Connect to a hidden network', but then select MY network from the popdown inside that dialog (it does show there--the only one other than "NEW").  It tries for about 30 seconds, **then changes to a dialog saying Authentication required.**

And did you provide the security key when it asked for Authentication? If yes, but it doesn't accept it, I suggest you delete all existing wireless connections in Network Manager settings, and try the above again.

To make the networks appear automatically in NM, you may try this dirty trick -
```
sudo sed -i '/^exit 0/i iwlist scan' /etc/rc.local
```
It will insert a line "iwlist scan" just above the last line "exit 0" in your **/etc/rc.local** file. It works with a similar problem with BCM4318, not sure if it'll work here too.

As for this -
> Should we go back to b43 vs. b43legacy, since b43 turned on the wireless light?
I think it is happening automatically since you have added "b43" to your /etc/modules file. The b43legacy driver will only load if you load it manually, not by itself unless you add it too to the same file.

---

### Post by movrshakr on 2014-03-14
Yes on providing the security phrase.
It works like this: the first time I select my SSID when using the 'connect to a hidden...' everything is already filled in and grayed out.  Say GO.  It tries, then fails ; shows the authentication needed dialog.  Now, I CAN put in the passphrase (which it already has--and it is correct), say GO again, and again it tries and fails.

I will t ry your sed trick later; two appts again today; will be back about 1300E and will post here then.

b43: I asked that because he had me modprobe it to b43legacy and there has been no reboot since then.

c ya later today.

---

### Post by movrshakr on 2014-03-14
It is 1450 now; I am back for about 3 hours, if the gurus are around.

I did run the sed insert into rc.local and rebooted.  It did not cause the NM dropdown to show my network.  
However it now seems to not time-out on trying to connect when I command it to.
REMEMBER...from before..
"user@HP-Pavilion:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning."

The reboot loaded b43 of course; wireless light is ON.

---

### Post by chili555 on 2014-03-14
You have all the firmware needed, as far as I can see. I am mystified as to why this usually dependable device isn't starting right up. Please detach the ethernet and reboot and log in. Before you do anything else, run:```
dmesg > wifi.txt
cat /etc/network/interfaces >> wifi.txt
```Hook up the ethernet and get connected and paste the result here: [http://paste.ubuntu.com](http://paste.ubuntu.com) Give us the link in your reply.

---

### Post by movrshakr on 2014-03-14
Here is what requessted

[http://paste.ubuntu.com/7092174/](http://paste.ubuntu.com/7092174/)

---

### Post by chili555 on 2014-03-14
> **movrshakr said:**
> [SIZE=3]Here is what requessted[/SIZE]

[http://paste.ubuntu.com/7092174/](http://paste.ubuntu.com/7092174/)Varun, Wild Man, et al; please check along with me.

---

### Post by movrshakr on 2014-03-14
I notice that /etc/network/interfaces has nothing about wlan in it.

---

### Post by chili555 on 2014-03-14
Fascinating. Although b43 and ssb use the xx80211 stack, we see no activity like here from my system:> [111354.443533] cfg80211: Calling CRDA for country: US
[111354.431334] Restarting tasks ... done.
[111354.447499] video LNXVIDEO:00: Restoring backlight state
[111354.458686] cfg80211: Regulatory domain changed to country: US
[111354.458693] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[111354.458695] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
<snip>Let's see what is loaded:```
lsmod | grep -e b43 -e 80211
```And let's see what b43 requires in 10.04. I'd look myself, except I haven't anything that old.```
modinfo b43 | grep depends
```

---

### Post by chili555 on 2014-03-14
> **movrshakr said:**
> [SIZE=3]I notice that /etc/network/interfaces has nothing about wlan in it.
[/SIZE]If Network Manager is going to run things, that is the correct method.

---

### Post by wildmanne39 on 2014-03-14
I looked over the file twice chili555 and I did not see anything that looked wrong with what was present but I thought something was missing.

Edit: chili555 in post 32 what I asked him to do is correct for 10.04 right?

---

### Post by movrshakr on 2014-03-14
```
user@HP-Pavilion:~$ lsmod | grep -e b43 -e 80211
b43                   163556  0 
ssb                    38934  1 b43
mac80211              205434  1 b43
cfg80211              126528  2 b43,mac80211
led_class               2864  1 b43

```

```

user@HP-Pavilion:~$ modinfo b43 | grep depends
depends:        ssb,mac80211,led-class,cfg80211]
```

---

### Post by chili555 on 2014-03-14
> Edit: chili555 in post 32 what I asked him to do is correct for 10.04 right? Yes.He has nothing but loopback in /etc/network/interfaces so it really shouldn't help or hurt either way. I do think that I remember that NM was a little twitchy in 10.04; I hope that's not the underlying issue.

Your modules b43, ssb, cfg80211 and mac80211 look just perfect. Again, nothing wrong that's fixable and explains NMs stubborn behavior.

Googling, studying and hatching a plan...back in a few.

---

### Post by Iowan on 2014-03-14
Please refer to the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

---

### Post by movrshakr on 2014-03-14
Is there any chance that using WPA2-Personal and AES is causing it?

Is it supposed to "see" all network SSIDs in the vicinity and display those to me in a list?  
There are some in the neighborhood that occasionally show up on my other computers.

---

### Post by wildmanne39 on 2014-03-14
That is the best settings to use.

---

### Post by chili555 on 2014-03-14
> **movrshakr said:**
> [SIZE=3]Is there any chance that using WPA2-Personal and AES is causing it?

Is it supposed to "see" all network SSIDs in the vicinity and display those to me in a list?  
There are some in the neighborhood that occasionally show up on my other computers.[/SIZE]Yes, NM should see many networks like this: [http://nfgk.files.wordpress.com/2013/08/network-manager.jpg?w=540](http://nfgk.files.wordpress.com/2013/08/network-manager.jpg?w=540) Does it? And does it see yours?

---

### Post by movrshakr on 2014-03-14
I was just chastized by iowan for using font size 3.
Wow.
OK, I will comply, but am shocked.

---

### Post by movrshakr on 2014-03-14
> **chili555 said:**
> Yes, NM should see many networks like this: [http://nfgk.files.wordpress.com/2013/08/network-manager.jpg?w=540](http://nfgk.files.wordpress.com/2013/08/network-manager.jpg?w=540) Does it?
No, all I ever see in the Wireless section is
disconnected (gray)
VPN Connections
Connect to Hidden Wireless Network
Create New Wireless Network

UNLESS

I command through Connect to Hidden to try to connect to my SSID, Then IT shows while the searching is in process--disappears after that fails and dialogs are closed.

---

### Post by chili555 on 2014-03-14
When you scan:```
sudo iwlist wlan0 scan
```Does it see your network?

---

### Post by movrshakr on 2014-03-14
```
user@HP-Pavilion:~$ sudo iwlist wlan0 scan
[sudo] password for user: 
wlan0     No scan results

```

Aside:
What screen capture program do you use?

---

### Post by chili555 on 2014-03-14
> **movrshakr said:**
> ```
user@HP-Pavilion:~$ sudo iwlist wlan0 scan
[sudo] password for user: 
wlan0     No scan results

```

Aside:
What screen capture program do you use?I just use the screenshot utility in Ubuntu. The link I gave you of NM was just from the web, so I guess I used Google images!

Is it UP BROADCAST RUNNING ?```
ifconfig
```If not, can you bring it up and then scan?```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Is the switch still off?```
rfkill list all
```Is this a stay-at-home computer or do you need to roam down to Sixbucks Coffee?

---

### Post by movrshakr on 2014-03-14
Wireless light is ON
It is an old laptop, but screen broken --have to use monitor with it
Windows computers in the house are connecting to my SSID.
```
user@HP-Pavilion:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:07:0e:5f  
          inet addr:192.168.0.226  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe07:e5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3986441 (3.9 MB)  TX bytes:1086928 (1.0 MB)
          Interrupt:18 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:5b:15:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@HP-Pavilion:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by movrshakr on 2014-03-14
I can't tell all of you how much I appreciate your guru-ness here..
but we have a dinner date and I will be offline again in about 10 minutes

---

### Post by chili555 on 2014-03-14
I suggest we try the last ditch thing any of us, who have been PMing behind the scenes, know to do. Please do:```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
``` Change managed=true back to managed=false. Proofread, save and close gedit. Now do:```
gksudo gedit /etc/network/interfaces
```Amend the file to read:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid <your_network>
wpa-psk <your_secret_password>
```Of course, substitute your details here. Proofread, save and close gedit. Now reboot and give us a good report.

Off for supper, I'll check back a bit later.

---

### Post by movrshakr on 2014-03-14
Did all that.
Nogo.  Wireless still does not show in NM pulldown.
(Rebooted with eth0 disconnected)

I have to go NOW.  Back tomorrow

---

### Post by wildmanne39 on 2014-03-14
When you filled in those settings you need to open a broswer and see if you can connect because those settings bypass network manager.

---

### Post by movrshakr on 2014-03-14
> **Wild Man said:**
> When you filled in those settings you need to open a broswer and see if you can connect because those settings bypass network manager.

OH.  Disconnected the eth0 and tries to hit web pages.  Nogo.

The NM icon still animates when I connect or disconnect the cable, so some part of NM is still active.

Off to nite nite.  Be back on sometime tomorrow.

---

### Post by varunendra on 2014-03-14
Not likely on an old machine, but please also check the BIOS to see if there is a thing called "IOMMU" in it. If there is, try enabling it (or disable if it is already enabled).

Like my two gurus above, I too couldn't find anything unusual in the dmesg you posted, EXCEPT that _there is not much usual OR unusual activity about the wireless_ in it - again something already noted by both. As such, I would have immediately blamed it to hardware/BIOS.

My suggestion (apart from checking BIOS for "IOMMU") would be to try resetting the BIOS to factory defaults (assuming it is NOT a UEFI based setup - it shouldn't be, since it is old and 32 bit), AND/OR try a Live DVD/USB of Xubuntu 12.04 and see if miracles are possible in this mortal world.

I guess my 'expertise' ended many-many posts ago, so I'll just watch and cheer now.

---

### Post by chili555 on 2014-03-15
> **movrshakr said:**
> Did all that.
Nogo.  Wireless still does not show in NM pulldown.
(Rebooted with eth0 disconnected)That's good! The intent here was to *NOT* use NM but, instead, use manual methods. Our suspicion was and is that perhaps NM is not doing its job properly. Our collective faint recollections of 10.04 suggest that as a possible culprit. Please make us an updated wifi.txt after a reboot with no ethernet and paste it as above.

---

### Post by movrshakr on 2014-03-15
> **chili555 said:**
> ... Please make us an updated wifi.txt after a reboot with no ethernet and paste it as above.

See next post also about another thing I tried.

wifi.txt
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-57-generic (buildd@lamiak) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #119-Ubuntu SMP Wed Feb 19 01:04:55 UTC 2014 (Ubuntu 2.6.32-57.119-generic 2.6.32.61+drm33.26)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF write-back
[    0.000000]   D4000-D4FFF write-protect
[    0.000000]   D5000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  modified: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  modified: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  modified: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 7000-c000
[    0.000000] RAMDISK: 1782f000 - 17fd38dc
[    0.000000] ACPI: RSDP 000f7280 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 1ff7a89f 00034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 1ff7ee34 00074 (v01 NVIDIA CK8      06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 1ff7a8d3 04561 (v01 NVIDIA      CK8 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 1ff7ffc0 00040
[    0.000000] ACPI: APIC 1ff7eea8 0005A (v01 NVIDIA NV_APIC_ 06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 1ff7ef02 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 1ff7ef2a 000D6 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000]   node 0 low ram: 00000000 - 1ff70000
[    0.000000]   node 0 bootmap 00008000 - 0000bff0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ff70000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e7ef8]    TEXT DATA BSS ==> [0000100000 - 00008e7ef8]
[    0.000000]   #4 [001782f000 - 0017fd38dc]          RAMDISK ==> [001782f000 - 0017fd38dc]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008e8000 - 00008eb138]              BRK ==> [00008e8000 - 00008eb138]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  0x0001ff70 -> 0x0001ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130827
[    0.000000] free_area_init_node: node 0, pgdat c07a2800, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dff80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129804
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-57-generic root=UUID=aa2761cf-18bb-4087-a97b-33141d4ff844 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2618560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 499868k/523712k available (4705k kernel code, 23096k reserved, 2130k data, 664k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc07ad000 - 0xc0853000   ( 664 kB)
[    0.000000]       .data : 0xc0598427 - 0xc07acdc8   (2130 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0598427   (4705 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.879 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.75 BogoMIPS (lpj=3191516)
[    0.004046] Security Framework initialized
[    0.004089] AppArmor: AppArmor initialized
[    0.004106] Mount-cache hash table entries: 512
[    0.004338] Initializing cgroup subsys ns
[    0.004347] Initializing cgroup subsys cpuacct
[    0.004357] Initializing cgroup subsys memory
[    0.004375] Initializing cgroup subsys devices
[    0.004381] Initializing cgroup subsys freezer
[    0.004387] Initializing cgroup subsys net_cls
[    0.004423] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004430] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004439] mce: CPU supports 5 MCE banks
[    0.004467] Performance Events: AMD PMU driver.
[    0.004486] ... version:                0
[    0.004490] ... bit width:              48
[    0.004495] ... generic registers:      4
[    0.004501] ... value mask:             0000ffffffffffff
[    0.004506] ... max period:             00007fffffffffff
[    0.004511] ... fixed-purpose events:   0
[    0.004516] ... event mask:             000000000000000f
[    0.004525] Checking 'hlt' instruction... OK.
[    0.021537] SMP alternatives: switching to UP code
[    0.035839] Freeing SMP alternatives: 19k freed
[    0.035874] ACPI: Core revision 20090903
[    0.048019] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048030] ftrace: allocating 21852 entries in 43 pages
[    0.056275] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056665] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.097711] CPU0: AMD Athlon(tm) XP Processor 3000+ stepping 00
[    0.100006] Brought up 1 CPUs
[    0.100006] Total of 1 processors activated (1595.75 BogoMIPS).
[    0.100006] CPU0 attaching NULL sched-domain.
[    0.100006] devtmpfs: initialized
[    0.100006] regulator: core version 0.5
[    0.100006] Time: 23:30:33  Date: 03/15/14
[    0.100006] NET: Registered protocol family 16
[    0.100006] EISA bus registered
[    0.100006] ACPI: bus type pci registered
[    0.100006] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.100006] PCI: Using configuration type 1 for base access
[    0.100552] bio: create slab <bio-0> at 0
[    0.102068] ACPI: EC: Look up EC in DSDT
[    0.105716] ACPI: Interpreter enabled
[    0.105724] ACPI: (supports S0 S3 S4 S5)
[    0.105766] ACPI: Using IOAPIC for interrupt routing
[    0.164994] ACPI: EC: GPE = 0x21, I/O: command/status = 0x66, data = 0x62
[    0.165364] ACPI: No dock devices found.
[    0.165552] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.165641] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.165788] pci 0000:00:01.1: reg 20 io port: [0x2040-0x207f]
[    0.165798] pci 0000:00:01.1: reg 24 io port: [0x2000-0x203f]
[    0.165825] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.165832] pci 0000:00:01.1: PME# disabled
[    0.165869] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xe8000fff]
[    0.165909] pci 0000:00:02.0: supports D1 D2
[    0.165915] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165922] pci 0000:00:02.0: PME# disabled
[    0.165952] pci 0000:00:02.1: reg 10 32bit mmio: [0xe8001000-0xe8001fff]
[    0.165991] pci 0000:00:02.1: supports D1 D2
[    0.165997] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166004] pci 0000:00:02.1: PME# disabled
[    0.166035] pci 0000:00:02.2: reg 10 32bit mmio: [0xe8004000-0xe80040ff]
[    0.166075] pci 0000:00:02.2: supports D1 D2
[    0.166081] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166088] pci 0000:00:02.2: PME# disabled
[    0.166130] pci 0000:00:06.0: reg 10 io port: [0x1400-0x14ff]
[    0.166140] pci 0000:00:06.0: reg 14 io port: [0x1c00-0x1c7f]
[    0.166149] pci 0000:00:06.0: reg 18 32bit mmio: [0xe8002000-0xe8002fff]
[    0.166183] pci 0000:00:06.0: supports D1 D2
[    0.166213] pci 0000:00:06.1: reg 10 io port: [0x1800-0x18ff]
[    0.166222] pci 0000:00:06.1: reg 14 io port: [0x1c80-0x1cff]
[    0.166232] pci 0000:00:06.1: reg 18 32bit mmio: [0xe8003000-0xe8003fff]
[    0.166266] pci 0000:00:06.1: PME# supported from D3cold
[    0.166273] pci 0000:00:06.1: PME# disabled
[    0.166320] pci 0000:00:08.0: reg 20 io port: [0x2080-0x208f]
[    0.166592] pci 0000:02:01.0: reg 10 io port: [0x7000-0x70ff]
[    0.166603] pci 0000:02:01.0: reg 14 32bit mmio: [0xe8104000-0xe81040ff]
[    0.166652] pci 0000:02:01.0: supports D1 D2
[    0.166658] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.166665] pci 0000:02:01.0: PME# disabled
[    0.166693] pci 0000:02:02.0: reg 10 32bit mmio: [0xe8100000-0xe8101fff]
[    0.166761] pci 0000:02:04.0: reg 10 32bit mmio: [0xe8102000-0xe8102fff]
[    0.166792] pci 0000:02:04.0: supports D1 D2
[    0.166798] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166805] pci 0000:02:04.0: PME# disabled
[    0.166845] pci 0000:02:04.1: reg 10 32bit mmio: [0xe8103000-0xe8103fff]
[    0.166875] pci 0000:02:04.1: supports D1 D2
[    0.166881] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.166888] pci 0000:02:04.1: PME# disabled
[    0.166925] pci 0000:02:04.2: reg 10 io port: [0x7400-0x743f]
[    0.167019] pci 0000:00:0a.0: bridge io port: [0x3000-0x7fff]
[    0.167027] pci 0000:00:0a.0: bridge 32bit mmio: [0xe8100000-0xe97fffff]
[    0.167115] pci 0000:01:00.0: reg 10 32bit mmio: [0xea000000-0xeaffffff]
[    0.167127] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.167139] pci 0000:01:00.0: reg 18 32bit mmio pref: [0xfc000000-0xfc07ffff]
[    0.167165] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.167258] pci 0000:00:0b.0: bridge 32bit mmio: [0xea000000-0xeaffffff]
[    0.167267] pci 0000:00:0b.0: bridge 32bit mmio pref: [0xf8000000-0xfc0fffff]
[    0.167283] pci_bus 0000:00: on NUMA node 0
[    0.167291] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.167469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.167553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP0._PRT]
[    0.193175] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 18 19) *0
[    0.193494] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 18 19) *0
[    0.193807] ACPI: PCI Interrupt Link [LNK3] (IRQs 17) *0
[    0.194117] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 18 19) *0, disabled.
[    0.194430] ACPI: PCI Interrupt Link [LNK5] (IRQs 16 18 19) *0
[    0.194734] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22) *0
[    0.195039] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *0
[    0.195343] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *0
[    0.195647] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *0
[    0.195952] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22) *0, disabled.
[    0.196267] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22) *0
[    0.196579] ACPI: PCI Interrupt Link [LMCI] (IRQs 20 21 22) *0
[    0.196891] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22) *0, disabled.
[    0.197210] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0, disabled.
[    0.197446] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.197452] vgaarb: loaded
[    0.197720] SCSI subsystem initialized
[    0.197862] libata version 3.00 loaded.
[    0.198020] usbcore: registered new interface driver usbfs
[    0.198049] usbcore: registered new interface driver hub
[    0.198104] usbcore: registered new device driver usb
[    0.198421] ACPI: WMI: Mapper loaded
[    0.198425] PCI: Using ACPI for IRQ routing
[    0.198714] NetLabel: Initializing
[    0.198719] NetLabel:  domain hash size = 128
[    0.198723] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.198753] NetLabel:  unlabeled traffic allowed by default
[    0.198869] Switching to clocksource tsc
[    0.200044] AppArmor: AppArmor Filesystem Enabled
[    0.200082] pnp: PnP ACPI init
[    0.200116] ACPI: bus type pnp registered
[    0.227233] pnp: PnP ACPI: found 12 devices
[    0.227239] ACPI: ACPI bus type pnp unregistered
[    0.227246] PnPBIOS: Disabled by ACPI PNP
[    0.227273] system 00:01: ioport range 0x8000-0x807f has been reserved
[    0.227281] system 00:01: ioport range 0x8080-0x80ff has been reserved
[    0.227289] system 00:01: ioport range 0x8400-0x847f has been reserved
[    0.227296] system 00:01: ioport range 0x8480-0x84ff has been reserved
[    0.227304] system 00:01: ioport range 0x8800-0x887f has been reserved
[    0.227312] system 00:01: ioport range 0x8880-0x88ff has been reserved
[    0.227320] system 00:01: ioport range 0x2040-0x207f has been reserved
[    0.227328] system 00:01: ioport range 0x2000-0x203f has been reserved
[    0.227345] system 00:02: iomem range 0xfff80000-0xffffffff has been reserved
[    0.227353] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.227362] system 00:02: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.227370] system 00:02: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.227385] system 00:03: ioport range 0x200-0x20f has been reserved
[    0.227393] system 00:03: ioport range 0x680-0x6ff has been reserved
[    0.227401] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.227409] system 00:03: ioport range 0xfe00-0xfe01 has been reserved
[    0.262365] pci 0000:02:04.0: BAR 16: can't allocate mem resource [0xec000000-0xe97fffff]
[    0.262375] pci 0000:02:04.1: BAR 16: can't allocate mem resource [0xec000000-0xe97fffff]
[    0.262385] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.262392] pci 0000:02:04.0:   IO window: 0x003000-0x0030ff
[    0.262401] pci 0000:02:04.0:   IO window: 0x003400-0x0034ff
[    0.262409] pci 0000:02:04.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.262418] pci 0000:02:04.1: CardBus bridge, secondary bus 0000:07
[    0.262424] pci 0000:02:04.1:   IO window: 0x003800-0x0038ff
[    0.262432] pci 0000:02:04.1:   IO window: 0x003c00-0x003cff
[    0.262440] pci 0000:02:04.1:   PREFETCH window: 0x24000000-0x27ffffff
[    0.262449] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.262455] pci 0000:00:0a.0:   IO window: 0x3000-0x7fff
[    0.262463] pci 0000:00:0a.0:   MEM window: 0xe8100000-0xe97fffff
[    0.262472] pci 0000:00:0a.0:   PREFETCH window: 0x20000000-0x27ffffff
[    0.262484] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:01
[    0.262489] pci 0000:00:0b.0:   IO window: disabled
[    0.262498] pci 0000:00:0b.0:   MEM window: 0xea000000-0xeaffffff
[    0.262506] pci 0000:00:0b.0:   PREFETCH window: 0xf8000000-0xfc0fffff
[    0.262526] pci 0000:00:0a.0: setting latency timer to 64
[    0.263000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    0.263008]   alloc irq_desc for 19 on node -1
[    0.263013]   alloc kstat_irqs on node -1
[    0.263028] pci 0000:02:04.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    0.263475] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[    0.263482]   alloc irq_desc for 18 on node -1
[    0.263487]   alloc kstat_irqs on node -1
[    0.263498] pci 0000:02:04.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    0.263517] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.263524] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.263532] pci_bus 0000:02: resource 0 io:  [0x3000-0x7fff]
[    0.263539] pci_bus 0000:02: resource 1 mem: [0xe8100000-0xe97fffff]
[    0.263546] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x27ffffff]
[    0.263554] pci_bus 0000:03: resource 0 io:  [0x3000-0x30ff]
[    0.263560] pci_bus 0000:03: resource 1 io:  [0x3400-0x34ff]
[    0.263567] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.263575] pci_bus 0000:07: resource 0 io:  [0x3800-0x38ff]
[    0.263581] pci_bus 0000:07: resource 1 io:  [0x3c00-0x3cff]
[    0.263588] pci_bus 0000:07: resource 2 pref mem [0x24000000-0x27ffffff]
[    0.263596] pci_bus 0000:01: resource 1 mem: [0xea000000-0xeaffffff]
[    0.263603] pci_bus 0000:01: resource 2 pref mem [0xf8000000-0xfc0fffff]
[    0.263685] NET: Registered protocol family 2
[    0.263893] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.264548] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.264724] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.264897] TCP: Hash tables configured (established 16384 bind 16384)
[    0.264903] TCP reno registered
[    0.265057] NET: Registered protocol family 1
[    0.265673] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.265682]   alloc irq_desc for 22 on node -1
[    0.265687]   alloc kstat_irqs on node -1
[    0.265702] pci 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, low) -> IRQ 22
[    0.533138] pci 0000:00:02.0: PCI INT A disabled
[    0.533583] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[    0.533590]   alloc irq_desc for 21 on node -1
[    0.533594]   alloc kstat_irqs on node -1
[    0.533606] pci 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 21 (level, low) -> IRQ 21
[    0.801170] pci 0000:00:02.1: PCI INT B disabled
[    0.801609] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.801616]   alloc irq_desc for 20 on node -1
[    0.801621]   alloc kstat_irqs on node -1
[    0.801633] pci 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 20 (level, low) -> IRQ 20
[    0.801655] pci 0000:00:02.2: PCI INT C disabled
[    0.801721] pci 0000:01:00.0: Boot video device
[    0.801849] Simple Boot Flag at 0x37 set to 0x1
[    0.802080] cpufreq-nforce2: No nForce2 chipset.
[    0.802137] Scanning for low memory corruption every 60 seconds
[    0.802389] audit: initializing netlink socket (disabled)
[    0.802418] type=2000 audit(1394926233.801:1): initialized
[    0.827821] Trying to unpack rootfs image as initramfs...
[    0.853878] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.861011] VFS: Disk quotas dquot_6.5.2
[    0.861149] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.862491] fuse init (API version 7.13)
[    0.862679] msgmni has been set to 977
[    0.870060] alg: No test for stdrng (krng)
[    0.870252] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.870259] io scheduler noop registered
[    0.870264] io scheduler anticipatory registered
[    0.870269] io scheduler deadline registered
[    0.870371] io scheduler cfq registered (default)
[    0.870618] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.870671] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.872299] ACPI: AC Adapter [ACAD] (on-line)
[    0.872452] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.872461] ACPI: Power Button [PWRB]
[    0.872568] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.874038] ACPI: Lid Switch [LID]
[    0.874193] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.874201] ACPI: Power Button [PWRF]
[    0.874575] Marking TSC unstable due to TSC halts in idle
[    0.874662] processor LNXCPU:00: registered as cooling_device0
[    0.876860] Switching to clocksource acpi_pm
[    0.902701] ACPI: Invalid active0 threshold
[    0.908049] thermal LNXTHERM:01: registered as thermal_zone0
[    0.908074] ACPI: Thermal Zone [THRM] (54 C)
[    0.917086] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.918285] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[    0.918297] serial 0000:00:06.1: PCI INT B -> Link[LMCI] -> GSI 22 (level, low) -> IRQ 22
[    0.918310] serial 0000:00:06.1: PCI INT B disabled
[    0.920296] isapnp: Scanning for PnP cards...
[    0.926712] brd: module loaded
[    0.927920] loop: module loaded
[    0.932927] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.933308] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.934087] Fixed MDIO Bus: probed
[    0.934172] PPP generic driver version 2.4.2
[    0.934280] tun: Universal TUN/TAP device driver, 1.6
[    0.934285] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.934470] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.934502] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 20 (level, low) -> IRQ 20
[    0.934533] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.934540] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.934622] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.934680] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.934715] ehci_hcd 0000:00:02.2: irq 20, io mem 0xe8004000
[    0.978492] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.978717] usb usb1: configuration #1 chosen from 1 choice
[    0.978793] hub 1-0:1.0: USB hub found
[    0.978812] hub 1-0:1.0: 6 ports detected
[    0.978938] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.978967] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, low) -> IRQ 22
[    0.978992] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.978999] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.979089] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.979130] ohci_hcd 0000:00:02.0: irq 22, io mem 0xe8000000
[    1.066567] usb usb2: configuration #1 chosen from 1 choice
[    1.066688] hub 2-0:1.0: USB hub found
[    1.066710] hub 2-0:1.0: 3 ports detected
[    1.066821] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 21 (level, low) -> IRQ 21
[    1.066853] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    1.066860] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    1.066952] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    1.066999] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe8001000
[    1.158147] usb usb3: configuration #1 chosen from 1 choice
[    1.158217] hub 3-0:1.0: USB hub found
[    1.158240] hub 3-0:1.0: 3 ports detected
[    1.158356] uhci_hcd: USB Universal Host Controller Interface driver
[    1.158530] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.167951] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.184674] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.188671] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.188765] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.188820] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.188875] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.189259] mice: PS/2 mouse device common for all mice
[    1.189591] rtc_cmos 00:06: RTC can wake from S4
[    1.189685] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.189723] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.190166] device-mapper: uevent: version 1.0.3
[    1.190424] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.193369] device-mapper: multipath: version 1.1.0 loaded
[    1.193378] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.193705] EISA: Probing bus 0 at eisa.0
[    1.193719] Cannot allocate resource for EISA slot 1
[    1.193724] Cannot allocate resource for EISA slot 2
[    1.193730] Cannot allocate resource for EISA slot 3
[    1.193735] Cannot allocate resource for EISA slot 4
[    1.193740] Cannot allocate resource for EISA slot 5
[    1.193745] Cannot allocate resource for EISA slot 6
[    1.193751] Cannot allocate resource for EISA slot 7
[    1.193756] Cannot allocate resource for EISA slot 8
[    1.193761] EISA: Detected 0 cards.
[    1.197650] cpuidle: using governor ladder
[    1.197768] cpuidle: using governor menu
[    1.198742] TCP cubic registered
[    1.199156] NET: Registered protocol family 10
[    1.200995] NET: Registered protocol family 17
[    1.201066] powernow-k8: Found 1 AMD Athlon(tm) XP Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[    1.204301] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6
[    1.204311] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18
[    1.210748] Using IPI No-Shortcut mode
[    1.210890] PM: Resume from disk failed.
[    1.210908] registered taskstats version 1
[    1.211174]   Magic number: 6:28:555
[    1.211228] pci_link PNP0C0F:06: hash matches
[    1.211281] rtc_cmos 00:06: setting system clock to 2014-03-15 23:30:34 UTC (1394926234)
[    1.211285] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.211287] EDD information not available.
[    1.219228] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.320504] ACPI: Battery Slot [BAT1] (battery present)
[    1.575076] Freeing initrd memory: 7826k freed
[    1.627287] isapnp: No Plug & Play device found
[    1.627346] Freeing unused kernel memory: 664k freed
[    1.628196] Write protecting the kernel text: 4708k
[    1.628235] Write protecting the kernel read-only data: 1848k
[    1.655919] udev: starting version 151
[    1.928056] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    1.931310] pata_amd 0000:00:08.0: version 0.4.1
[    1.931376] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.938163] scsi0 : pata_amd
[    1.943703] scsi1 : pata_amd
[    1.944563] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    1.944568] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    1.945247] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.945271] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.124523] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.124528] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.124561] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    2.142035] usb 3-1: configuration #1 chosen from 1 choice
[    2.156638] ata1.00: configured for UDMA/100
[    2.156791] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.156998] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.157408] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.157467] sd 0:0:0:0: [sda] Write Protect is off
[    2.157471] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.157502] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.157677]  sda: sda1 sda2 < sda5 >
[    2.221249] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.320302] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0C29, max MWDMA2
[    2.320338] ata2: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:600:0x12)
[    2.336254] ata2.00: configured for MWDMA2
[    2.342391] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0C29 PQ: 0 ANSI: 5
[    2.356224] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.356230] Uniform CD-ROM driver Revision: 3.20
[    2.356381] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.356459] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.363983] 8139too Fast Ethernet driver 0.9.28
[    2.364079] 8139too 0000:02:01.0: PCI INT A -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    2.365228] eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:07:0e:5f, IRQ 18
[    2.374195] usbcore: registered new interface driver hiddev
[    2.384308] input: HID 1241:1177 as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input5
[    2.384441] generic-usb 0003:1241:1177.0001: input,hidraw0: USB HID v1.00 Mouse [HID 1241:1177] on usb-0000:00:02.1-1/input0
[    2.384476] usbcore: registered new interface driver usbhid
[    2.384480] usbhid: v2.6:USB HID core driver
[    2.781872] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.960057] floppy0: no floppy controllers found
[   19.177057] udev: starting version 151
[   19.179062] Adding 1486840k swap on /dev/sda5.  Priority:-1 extents:1 across:1486840k 
[   19.805301] cfg80211: Calling CRDA to update world regulatory domain
[   19.809714] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   19.809744] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   19.818649] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.838652] Linux agpgart interface v0.103
[   19.863737] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:17/LNXVIDEO:00/input/input6
[   19.863914] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.875140] parport_pc 00:0b: reported by Plug and Play ACPI
[   19.875194] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.896921] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[   19.896931] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[   19.896939] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[   19.910417] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   20.038515] [drm] Initialized drm 1.1.0 20060810
[   20.061987] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   20.062007] yenta_cardbus 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[   20.062011] yenta_cardbus 0000:02:04.0:   IO window: 0x003000-0x0030ff
[   20.062016] yenta_cardbus 0000:02:04.0:   IO window: 0x003400-0x0034ff
[   20.062021] yenta_cardbus 0000:02:04.0:   PREFETCH window: 0x20000000-0x23ffffff
[   20.062026] yenta_cardbus 0000:02:04.0:   MEM window: 0xe8400000-0xe87fffff
[   20.062032] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   20.062037] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   20.062040] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   20.062046] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   20.063102] ppdev: user-space parallel port driver
[   20.070702] type=1505 audit(1394926253.356:2):  operation="profile_load" pid=542 name="/sbin/dhclient3"
[   20.071081] type=1505 audit(1394926253.356:3):  operation="profile_load" pid=542 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.071299] type=1505 audit(1394926253.356:4):  operation="profile_load" pid=542 name="/usr/lib/connman/scripts/dhclient-script"
[   20.213983] cfg80211: World regulatory domain updated:
[   20.213989] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.213994] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.213998] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.214002] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.214005] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.214009] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.300660] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 19
[   20.300666] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   20.300672] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   20.300686] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   20.300691] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: clean.
[   20.301875] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[   20.301879] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[   20.304580] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   20.304599] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   20.304602] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   20.304607] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   20.313370] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input7
[   20.336891] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   20.336905] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   20.337217] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[   20.337225]   alloc irq_desc for 16 on node -1
[   20.337227]   alloc kstat_irqs on node -1
[   20.337239] nouveau 0000:01:00.0: PCI INT A -> Link[LNK5] -> GSI 16 (level, low) -> IRQ 16
[   20.337434] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   20.360135] [drm] nouveau 0000:01:00.0: failed to evaluate _DSM: 5
[   20.366286] [drm] nouveau 0000:01:00.0: Detected an NV10 generation card (0x017600a5)
[   20.366373] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[   20.366380] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   20.366384] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   20.433073] [drm] nouveau 0000:01:00.0: ... BIOS checksum invalid
[   20.433077] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PCIROM
[   20.433283] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   20.433556] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   20.433560] [drm] nouveau 0000:01:00.0: BMP version 5.41
[   20.433563] [drm] nouveau 0000:01:00.0: Bios version 04.17.20.46
[   20.433568] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2
[   20.433573] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000100 000088b8
[   20.433578] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 03010223 00000004
[   20.433581] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 020203f1 00000003
[   20.433817] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode
[   20.433822] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xF26A
[   20.433869] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xF784
[   20.433886] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xF392
[   20.537172] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xFA98
[   20.537184] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xFAC5
[   20.537192] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0xF570
[   20.561754] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x0c38, PCI irq 18
[   20.561760] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   20.561765] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   20.561778] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   20.561783] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff:
[   20.562408] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0xF71F
[   20.568773]  clean.
[   20.568776] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[   20.568781] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[   20.579360] [TTM] Zone  kernel: Available graphics memory: 254360 kiB.
[   20.579377] [drm] nouveau 0000:01:00.0: 32 MiB VRAM
[   20.579457] agpgart-amd64 0000:00:00.0: AGP 2.0 bridge
[   20.579479] agpgart-amd64 0000:00:00.0: putting AGP V2 device into 4x mode
[   20.579530] nouveau 0000:01:00.0: putting AGP V2 device into 4x mode
[   20.579534] [drm] nouveau 0000:01:00.0: 128 MiB GART (aperture)
[   20.579731] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   20.580199] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   20.580211] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   20.580221] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   20.660629] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[   20.660638]   alloc irq_desc for 17 on node -1
[   20.660641]   alloc kstat_irqs on node -1
[   20.660653] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   20.673627] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   20.673637] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   20.673673] Intel ICH 0000:00:06.0: setting latency timer to 64
[   20.687333] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[   20.698607] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   20.698970] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
[   20.800474] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   20.802742] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   20.802748] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 1)
[   20.802754] [drm] nouveau 0000:01:00.0: Calling LVDS script 1:
[   20.802759] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[   20.802764] [drm] nouveau 0000:01:00.0: 0xE3F5: Parsing digital output script table
[   20.804040] AC'97 0 analog subsections not ready
[   20.840881] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   20.842629] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   20.843399] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   20.844072] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   20.844904] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   20.918000] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   21.077226] phy0: Selected rate control algorithm 'minstrel'
[   21.078163] Registered led device: b43-phy0::tx
[   21.078185] Registered led device: b43-phy0::rx
[   21.078211] Registered led device: b43-phy0::radio
[   21.078303] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   21.116953] lp0: using parport0 (interrupt-driven).
[   21.210595] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   21.216104] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   21.219138] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   21.219946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   21.220923] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   21.221792] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   21.254742] type=1505 audit(1394926254.540:5):  operation="profile_load" pid=763 name="/usr/share/gdm/guest-session/Xsession"
[   21.259053] type=1505 audit(1394926254.544:6):  operation="profile_replace" pid=764 name="/sbin/dhclient3"
[   21.259457] type=1505 audit(1394926254.544:7):  operation="profile_replace" pid=764 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.259685] type=1505 audit(1394926254.544:8):  operation="profile_replace" pid=764 name="/usr/lib/connman/scripts/dhclient-script"
[   21.273836] type=1505 audit(1394926254.560:9):  operation="profile_load" pid=765 name="/usr/bin/evince"
[   21.279282] type=1505 audit(1394926254.564:10):  operation="profile_load" pid=765 name="/usr/bin/evince-previewer"
[   21.282821] type=1505 audit(1394926254.568:11):  operation="profile_load" pid=765 name="/usr/bin/evince-thumbnailer"
[   21.372046] intel8x0_measure_ac97_clock: measured 55223 usecs (2680 samples)
[   21.372052] intel8x0: clocking to 47475
[   21.397961] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   21.552734] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   21.588054] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[   21.637228] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   21.644075] [drm] nouveau 0000:01:00.0: Load detected on output A
[   21.732280] [drm] nouveau 0000:01:00.0: allocated 1280x800 fb: 0x49000, bo dd7fbc00
[   21.732452] fb0: nouveaufb frame buffer device
[   21.732454] registered panic notifier
[   21.732462] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   21.735077] vga16fb: initializing
[   21.735084] vga16fb: mapped to 0xc00a0000
[   21.735093] vga16fb: not registering due to another framebuffer present
[   21.800732] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   21.800740] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
[   21.841506] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 1 using output A
[   21.841512] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[   21.841516] [drm] nouveau 0000:01:00.0: 0xE458: Parsing digital output script table
[   21.843844] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   21.872130] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 1)
[   21.872136] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[   21.872141] [drm] nouveau 0000:01:00.0: 0xE382: Parsing digital output script table
[   21.872160] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 1 using output A
[   21.873727] Console: switching to colour frame buffer device 128x48
[   21.988236] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.990410] eth0: link down
[   21.990652] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.528106] [drm] nouveau 0000:01:00.0: Load detected on output A
[   22.620038] [drm] nouveau 0000:01:00.0: Load detected on output A
[   22.678484] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   22.679821] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   22.770824] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 1)
[   22.770831] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[   22.770837] [drm] nouveau 0000:01:00.0: 0xE3F5: Parsing digital output script table
[   22.820046] floppy0: no floppy controllers found
[   23.575464] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 1 using output A
[   23.575470] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[   23.575475] [drm] nouveau 0000:01:00.0: 0xE458: Parsing digital output script table
[   23.592078] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 1)
[   23.592082] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[   23.592085] [drm] nouveau 0000:01:00.0: 0xE382: Parsing digital output script table
[   23.592103] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 1 using output A
[   25.264039] [drm] nouveau 0000:01:00.0: Load detected on output A
[   25.352040] [drm] nouveau 0000:01:00.0: Load detected on output A
[   25.444040] [drm] nouveau 0000:01:00.0: Load detected on output A
[   33.260039] [drm] nouveau 0000:01:00.0: Load detected on output A
[   33.348039] [drm] nouveau 0000:01:00.0: Load detected on output A
[   33.436039] [drm] nouveau 0000:01:00.0: Load detected on output A
[   39.328145] [drm] nouveau 0000:01:00.0: Load detected on output A
```

---

### Post by movrshakr on 2014-03-15
Also, I tied Xubuntu 12.04 as a live CD.  During it starting up, there were some text messages onscreen that had b43... in them, but they disappeared before I could start to read.  

And, after it was 'up,' a message appeared in the upper right corner advising that I could install proprietary [drivers]? for additional functionality--but nothing about how or where or which ones.

The wireless light was OFF so clearly it did not put in wifi "stuff."

---

### Post by chili555 on 2014-03-15
> **movrshakr said:**
> Also, I tied Xubuntu 12.04 as a live CD.  During it starting up, there were some text messages onscreen that had b43... in them, but they disappeared before I could start to read.  

And, after it was 'up,' a message appeared in the upper right corner advising that I could install proprietary [drivers]? for additional functionality--but nothing about how or where or which ones.

The wireless light was OFF so clearly it did not put in wifi "stuff."We see no change in your wifi.txt. The hardware calls the driver and firmware and stops. I frankly don't know what's wrong. I do think that beating on a problem in an end-of-life version is fruitless. My colleagues and I were willing to give it a shot because most Broadcoms work quite well with the right driver. We hoped we could make an easy slam dunk. We have had 70+ replies to try and it isn't going to happen. 

If you can get 12.04 to run, I'd install it! Beware that the the proprietary driver that's offered is _wrong_ for your device. You will cause yourself another big headache to unravel if you give in to the temptation. Once you are installed, simply do:```
sudo apt-get install firmware-b43-installer 
```Detach the ethernet, reboot and enjoy.

---

### Post by movrshakr on 2014-03-15
I agree that it is becoming 'not worth the effort.'  The only part that bugs me is that, before I decided to reinstall ubuntu in order to clear out histories and any other data-associated-with-me, wifi was working fine.  I simply don't remember how I got it to work a couple of years ago--and that annoys me.  I did it once and cannot again.

And it annoys me that it is so hard.

I will just sell it with wifi not working; was going to get next to nothing for it anyway.  The Windows disks are with it, so somebody can put that back on it.

Thanks sincerely to everybody who contributed to this effort; apart from the annoyance about not finding the key (may be unfindable), the attempt was fun, and I definitely learned a lot.

Regards to eveyone.

---

### Post by Bucky Ball on 2014-03-15
Mammoth effort here and unfortunately no resolution. I'm still where I was at the beginning. 10.04 LTS is no longer supported. Perhaps try a supported release and see if you have more luck. ... ;)

---

### Post by varunendra on 2014-03-16
> **chili555 said:**
> We see no change in your wifi.txt....Once you are installed, simply do:```
sudo apt-get install firmware-b43-installer 
```Detach the ethernet, reboot and enjoy.
I completely agree with this and the rest that is said here.

> **movrshakr said:**
> The only part that bugs me is that, before I decided to reinstall ubuntu in order to clear out histories and any other data-associated-with-me, wifi was working fine.

Easy enough to test - as easy as running a single command that Dr. chili suggested above (while being connected to internet via cable or any means).

If getting internet on the live session is a problem, you can download the attached firmware archive and manually extract it to your /lib/firmware directory. If this method is needed -

[INDENT]**1)** Download the attached .tar.bz2 archive, keep it ready on a thumb drive for copying.
**2)** Boot into Xubuntu Live session > copy the downloaded archive (b43.tar.bz2) onto the desktop.
**3)** Open a terminal and extract the archive with -
```
sudo tar xjf Desktop/b43.tar.bz2 /lib/firmware/
```
**4)** Reload the driver -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```[/INDENT]

If it works, we don't mind coffee and cakes. If it doesn't, I didn't do or say anything..

**PS:**
For the record, the attached firmware package extracted from "linux-firmware-nonfree_1.14ubuntu1.tar.gz" archive downloaded from official repository, then repacked as tar.bz2 by myself here (for smaller size). It's contents are same as you would get by installing the package with "apt-get intall.." command.


**PPS:**
> **movrshakr said:**
> And it annoys me that it is so hard.
In my 6284 post history, most of the time it required just one or two posts to get it working. At most a couple of pages when we needed to clean unnecessary mess and external factors were involved too. In my experience, your case is unique where we couldn't even determine the problem.

---

### Post by movrshakr on 2014-03-16
After all your help here, I owe you a status report...

I installed Xubuntu 12.04, then 
```
sudo apt-get install firmware-b43-installer
```
Reboot
(Somewhere along these steps, I also did a normal update manager run too)
Wireless light was out ($%&$W*^)
Installed gedit, changed some appearance settings, manually entered my wifi name and WPA passwd.
Rebooted.
Connection to my wifi network came up!
Unplugged eth0.
Wifi stays working.

Go figure!

Aside:  Boot time in xubuntu seems to be FAR longer, and app startup is slower as well,
but I am not trying to fix that <GRIN>.

Also, every reboot command (as opposed to a shutdown) creates a failed startup--displays a grub list of kernels to pick; going into the recovery one, then selecting continue to normal boot works,
but I am not trying to fix that <GRIN>.

---

### Post by Bucky Ball on 2014-03-16
But these things should be fixable when you do post new threads about them. You have a supported release, wireless seems to be working consistently, great! ;)

---

### Post by wildmanne39 on 2014-03-16
I am glad it is working!

---

### Post by varunendra on 2014-03-17
> **movrshakr said:**
> Aside:  Boot time in xubuntu seems to be FAR longer, and app startup is slower as well,
but I am not trying to fix that <GRIN>.

Also, every reboot command (as opposed to a shutdown) creates a failed startup--displays a grub list of kernels to pick; going into the recovery one, then selecting continue to normal boot works,
but I am not trying to fix that <GRIN>.
I should have kept post #8 in mind and should have suggested Lubuntu accordingly :( -
> **movrshakr said:**
> **800 megahertz AMD Athlon 64**
....
Bus Clock: **133 megahertz**
....	 		
**512 Megabytes** Installed Memory

With above configuration, I'm surprised if Xubuntu is even usable at all ! :confused:

---

### Post by movrshakr on 2014-03-17
> **varunendra said:**
> ...With above configuration, I'm surprised if Xubuntu is even usable at all ! :confused:
Actually, before I started all of this, even the version of straight ubuntu ran decently.  I THINK it was 10.04 (because I did not like the GUI desktop interface of 12.04 when it came out)...but I cannot swear to that.

I am going on the kubuntu IRC channel to ask if there is a way to add the Places launcher to Kubuntu.  That is the only other thing I found that I miss very much (after installing gedit)

---

