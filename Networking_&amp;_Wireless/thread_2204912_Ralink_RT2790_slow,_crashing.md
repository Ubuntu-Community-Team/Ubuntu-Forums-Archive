---
title: "Ralink RT2790 slow, crashing"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by prashanta2 on 2014-02-10
Hi guys,
I just arrived at the forum.

I have a Asus Eeepc 1000h with a Ralink RT2790 wifi device. Internet is very slow, the conection crashes very often, and I have tried all I could find on the forum and nothing seems to make it better. Rigth now I have no access to the web whatsoever, so I am using another laptop. I can access the router and navigate all the info, but as I write, I have no access to the internet at all. I guess some of the solutions I tried even got it worse...

I had ubuntu 13.04 until yesterday, after the upgrade to 13.10 I got the additional trouble of a missing Network Manager Icon.

Any help will be truly appreciated.

Thanks,
Pedro

---

### Post by varunendra on 2014-02-11
> **prashanta2 said:**
> I just arrived at the forum, so I can't seem to be able to create a new post.
Not sure what problem you had, but there is no such restriction to prevent 'New' users from posting a thread, and evidently, you have now [posted]("http://ubuntuforums.org/showthread.php?t=2204913") one of your own where I just replied your question about the nm-applet.

But since the question there was only about nm-applet, I only answered that.

I'm going to request the mods to move this post of yours to its own thread so it can be addressed properly, without cluttering this or the other one you posted.

Once it is moved, please post the details of the problem, whatever you can remember about having tried to solve it, and along with all those details, a report created by "wireless_script" which you can find in the "Wireless Script" link in my signature below.

**EDIT:** Oops! Looks like Bucky Ball could read my mind! Already did the job before I could report. Thanks BB! :P

---

### Post by prashanta2 on 2014-02-11
Hello,

first of all, sorry for hijacking a thread. I could only discover the new thread button after doing the 2 posts.

I am posting here the output of the wireless script.

```


*************** info trace ***************


***** uname -a *****


Linux prashanta-1000H 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
    Subsystem: Ralink corp. Device [1814:2790]
    Kernel driver in use: rt2800pci
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E


***** lsusb *****


Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 177f:0402 Sweex 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"kolbi hogar"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:482  Invalid misc:273   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


***** lsmod *****


rt2800pci              18290  0 
rt2800lib              70115  1 rt2800pci
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  1 rt2800pci
rt2x00lib              48933  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
mac80211              517444  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              401762  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
crc_ccitt              12627  1 rt2800lib


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [kolbi hogar] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *kolbi hogar:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"kolbi hogar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002b80a0f58
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000B6B6F6C626920686F676172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1


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


filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     259E8826760AAB9E718FD85
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     6FD0985B470AF52D6303639
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8422005AAAD8B7D2F811DC4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EB7C454417ADECB5D8A7F2A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   20.435253] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 2872, rev 0200 detected
[   20.456054] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0003 detected
[   21.675794] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[   27.779462] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   27.836930] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   27.894266] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.401297] wlan0: authenticate with <MAC address removed>
[   30.412928] wlan0: send auth to <MAC address removed> (try 1/3)
[   30.416676] wlan0: authenticated
[   30.420086] wlan0: associate with <MAC address removed> (try 1/3)
[   30.430630] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   30.430744] wlan0: associated
[   30.430822] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************
```

Will appreciate any help... wireless is so slow it is useless...

Thanks in advance

---

### Post by varunendra on 2014-02-11
Have you tried the usual "nohwcrypt=Y" trick yet? That is -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
This will be a temporary change that will be lost at next boot. So try connecting without rebooting after this, and if it improves the performance, we can make it permanent.

Everything else looks good to me *(except that you may wish to remove the 'Space' between the words in the Access-Point's SSID. Not related to current problem, but a space in the SSID may cause connectivity problems sometimes)*.

---

### Post by prashanta2 on 2014-02-11
So far so good!!
I am pushing the connection and checking to see if it crashes. Normally I can surf for 15 to 20 minutes, and then it starts crashing continuously. But this time everything looks ok.

Will came back later on and report the situation

Thanks!

---

### Post by prashanta2 on 2014-02-11
Quite funny! or not...
Just as I was about to post saying that my wifi was great, it broke... I pressed the post reply comment and at that very moment wifi broke, and is unstable again... going into a cycle of asking for password and confirmation to connect to wifi but never actually connects...
Other solutions?

---

### Post by Nathal on 2014-02-12
Telling the truth: week ago i have the seem problem whit RT5390. Have learned this is not a driver problem but a distance problem between your laptop/desktop and router/modem.
 Link Quality=28/70

My old topic: [http://ubuntuforums.org/showthread.php?t=2204194](http://ubuntuforums.org/showthread.php?t=2204194)


This is a distance problem, nothing else.

---

### Post by varunendra on 2014-02-12
> **Nathal said:**
> Have learned this is not a driver problem but a distance problem between your laptop/desktop and router/modem.
 Link Quality=28/70

Yup, less than 40/70 IS a problem, but the lower signal quality is not always due to longer distance. Sometimes it can also be caused due to poor handling or power management by the driver. Some experimental drivers even show 0/70 signal strength, yet keep working.

So.. prashanta2, what is your distance from the access-point?

**PS:**
Glad to see you around Nathal :)

---

### Post by Nathal on 2014-02-12
> **varunendra said:**
> 
**PS:**
Glad to see you around Nathal :)

:)

---

### Post by prashanta2 on 2014-02-12
Where I am should be 5 meters away from the router. All other laptops around mine work perfectly. I get 40% signal.
The thing is even if I sit just next to the router it happens all the same. I get 90% signal but still the connection crashes and cannot reconnect, or takes many many attempts until it finally connects with very slow speed.

Of course over LAN everything is just perfect.

---

### Post by varunendra on 2014-02-12
Does the same trick with nohwcrypt=Y still work? Some improvement or no improvement?

Considering we may have to install backports driver, let's see which versions do you have available. Please post the output of-
```
apt-cache show linux-backports-modules* | grep Package
```
If you don't get any output, open "Software Center" (Alt-F2 > type "software-properties-gtk" > press 'Enter') > goto "Updates" tab and make sure "Unsupported Updates" are enabled. Then do -
```
sudo apt-get update
```
..then retry the apt-cache.. command above.

[Note: Unnecessary "Unsupported Updates" tend to break features in the OS, so it is recommended to disable it > run "sudo apt-get update" again after our purpose is solved.]

---

### Post by prashanta2 on 2014-02-12
Here is the output

```
prashanta@prashanta-1000H:~$ apt-cache show linux-backports-modules* | grep Package
E: No packages found
```

After enabling the unsupported updates and updating, still this is the output. No packages found.


The other command only worked first time. After that it seemed to fail to work again.

---

### Post by varunendra on 2014-02-12
Hmm.. probably they are available for LTS only. I've no idea since I only use LTS versions.

Anyway, we can do it the other way. Please install the headers and build-essential beforehand -
```
sudo apt-get install linux-headers-generic build-essential
```

Then,

[indent]
**1)** Download the "backports-3.12.8-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Right-click the downloaded package > Extract here

**3)** Assuming this extracted folder is in your Downloads folder (within you Home), run the following commands in a terminal -
```
cd Downloads/backports-3.12.8-1
make defconfig-wifi
make
sudo make install
```[/indent]
Then reboot and check connectivity. Any better? With the nohwcrypt=Y if not?

---

### Post by prashanta2 on 2014-02-12
So far so good!
Seems all is working great, either near or far from the router. 
Will test it a little longer before considering this a victory. Will come back soon with news...

---

### Post by varunendra on 2014-02-12
..I'll keep my fingers and toes crossed :|

---

### Post by prashanta2 on 2014-02-14
Ok!
Working nicely and stable! Thank you very much my friend!

I am marking this post solved.

---

### Post by varunendra on 2014-02-14
Yeah, crossing fingers (and toes) definitely works..
..Hence _Proved_.

:P

Thanks for the confirmation!

---

### Post by prashanta2 on 2014-02-17
Actually, the connection is still crashing once in a while. But I guess that it might just be the best that my low-powered EeePC 1000H can do...
I am still considering it solved, but just in case someone has an additional thought on this subject, I will appreciate.

Thanks,

---

### Post by varunendra on 2014-02-18
Keep the wireless_script ready in your Home or Desktop, and run it when the connection crashes. Post back the fresh report and let's see if we can still find some clues to make it better.

---

### Post by prashanta2 on 2014-02-18
Ok, here it goes...

```


*************** info trace ***************


***** uname -a *****


Linux prashanta-1000H 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


***** lspci *****


01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
	Subsystem: Ralink corp. Device [1814:2790]
	Kernel driver in use: rt2800pci
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
	Kernel driver in use: ATL1E


***** lsusb *****


Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 177f:0402 Sweex 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"kolbihogar"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:403  Invalid misc:119   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


rt2800pci              18289  0 
rt2800lib              82919  1 rt2800pci
rt2x00pci              13111  1 rt2800pci
rt2x00mmio             13395  1 rt2800pci
rt2x00lib              48885  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
mac80211              446527  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              404464  2 mac80211,rt2x00lib
eeprom_93cx6           13168  1 rt2800pci
compat                 13217  3 cfg80211,mac80211,rt2800pci
crc_ccitt              12627  1 rt2800lib


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [kolbihogar] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *kolbihogar:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2


  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
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
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"kolbihogar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001aaca947cd
                    Extra: Last beacon: 140ms ago
                    IE: Unknown: 000A6B6F6C6269686F676172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1
search Home


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


filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     686DC1AE3A83A5F72A29352
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00mmio,rt2x00pci,compat,eeprom_93cx6
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     58E093A28E393BC04809CEF
depends:        rt2x00lib,mac80211,crc-ccitt
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     02CC1E24BB5BAC5A5F51DCB
depends:        rt2x00lib,mac80211
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CE52FA50FDEEEE7D1FA2A73
depends:        rt2x00lib
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-17-generic/updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B976F132653F95EC8835376
depends:        mac80211,cfg80211
vermagic:       3.11.0-17-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   21.414320] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 2872, rev 0200 detected
[   21.434219] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0003 detected
[   21.482258] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[   27.803580] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   27.907760] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   27.952691] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.399620] wlan0: authenticate with <MAC address removed>
[   30.412735] wlan0: send auth to <MAC address removed> (try 1/3)
[   30.416921] wlan0: authenticated
[   30.420438] wlan0: associate with <MAC address removed> (try 1/3)
[   30.423587] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   30.423701] wlan0: associated
[   30.423775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  389.202219] wlan0: authenticate with <MAC address removed>
[  389.216622] wlan0: send auth to <MAC address removed> (try 1/3)
[  389.221588] wlan0: authenticated
[  389.224221] wlan0: associate with <MAC address removed> (try 1/3)
[  389.227349] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  389.227525] wlan0: associated
[  389.227647] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  574.290244] wlan0: authenticate with <MAC address removed>
[  574.304504] wlan0: send auth to <MAC address removed> (try 1/3)
[  574.308263] wlan0: authenticated
[  574.312206] wlan0: associate with <MAC address removed> (try 1/3)
[  574.315374] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  574.315531] wlan0: associated
[  584.217132] wlan0: authenticate with <MAC address removed>
[  584.228633] wlan0: send auth to <MAC address removed> (try 1/3)
[  584.231956] wlan0: authenticated
[  584.236192] wlan0: associate with <MAC address removed> (try 1/3)
[  584.239277] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  584.239428] wlan0: associated
[  590.242525] wlan0: authenticate with <MAC address removed>
[  590.256630] wlan0: send auth to <MAC address removed> (try 1/3)
[  590.258800] wlan0: authenticated
[  590.260436] wlan0: associate with <MAC address removed> (try 1/3)
[  590.263590] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  590.263724] wlan0: associated
[  595.278265] wlan0: authenticate with <MAC address removed>
[  595.292624] wlan0: send auth to <MAC address removed> (try 1/3)
[  595.294187] wlan0: authenticated
[  595.297041] wlan0: associate with <MAC address removed> (try 1/3)
[  595.300357] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  595.300518] wlan0: associated
[  603.228185] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  791.414483] wlan0: authenticate with <MAC address removed>
[  791.432479] wlan0: send auth to <MAC address removed> (try 1/3)
[  791.434047] wlan0: authenticated
[  791.440146] wlan0: associate with <MAC address removed> (try 1/3)
[  791.443290] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[  791.443438] wlan0: associated


****************** done ******************
```

thanks

---

### Post by varunendra on 2014-02-18
Hmm.. signal is weak, rest of everything looks good.

Are you still just 5 mtrs away from the router?

And is the "**nohwcrypt=Y**" parameter effective? I don't remember having made it permanent. Let's see -
```
cat /sys/module/rt2800pci/parameters/nohwcrypt
```
Is it "N" or "Y" ??

If it is "N", make it permanently "Y" -
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800pci.conf
```

Then remove and reload the driver -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci
```

..and let me know if there is any improvement.

---

### Post by prashanta2 on 2014-02-18
Did as you instructed. No results. Crashing and unstable slow connection.
Considering the laptop is always in the same place (around 5 meters away with some obstables) and the problem is inconsistent, for example yesterday was kind of okay, but today is unusable... can it be software?

---

### Post by varunendra on 2014-02-18
So far wireless has been a very unpredictable domain for me. There are so many factors that it is easy to get confused and start working in a wrong direction.

The common factors that commonly affect the connectivity can range from something as simple as a loose antenna to as complex as voltage regulation problems at router's end or the nature of traffic.

There can be a long list to check and at the end we may still be empty handed. The quickest and easiest way to confirm whether the problem is internal or external is to test the connectivity with a different card/adapter that works really well with Linux. But assuming you don't have such a spare adapter, I am just focusing on what is clearly visible - the low signal quality.

When the connection was apparently strong, what was the signal quality ("Link quality" and "Signla level" in iwconfig)? Is it stable or fluctuating all the time?

If it varies significantly, it may be a loose antenna (check the antenna connection at the card if it is accessible) or a voltage problem at the router's end.

If it is fluctuating all the time and the connection stability is still sometimes strong, sometimes unstable, then it may be the nature of traffic, surrounding interference etc.

For now, try setting the MTU value in Network Manager to 1492 or 1392 (try them both for some time, with similar traffic). I'm suggesting this seeing the "Excessive retries" and "Invalid misc." count in iwconfig, but they may also be due to low signal quality. Give it a shot and post back the result.

One more thing - when it seems too unstable, power off the router and keep it off for about 30 seconds to about four minutes. This is usually enough time to let all the electronic parts reset. Then power it on again and check the connectivity. Does it make any difference?

And lastly, let me assure you that I have still not started my 'shots in the dark'. Whatever I have suggested above are all quite reasonable and common causes for "Unexplainable" connectivity problems, and there are probably more that I can't think off my sleepy head right now. Let's hope we don't have to try more. ;)

---

### Post by prashanta2 on 2014-02-18
Hi!

I am posting the iwconfig output of my crashing wireless

```
prashanta@prashanta-1000H:~$ iwconfigwlan0     IEEE 802.11bgn  ESSID:"kolbihogar"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:FE:E3:51:B6:51   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:804  Invalid misc:207   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.
```

I changed the MTU for the first level. But still we see a high number of excessive retries e invalid misc.

Have not tried to reset the router yet. Right now the connection is fine, can use youtube... but a few minutes ago was crashing. I fell it is not so bad has in the beggining. But ealier today it was getting disconnected a few times...

---

### Post by varunendra on 2014-02-19
With Link Quality=28/70 and Signal level=-82, I'm surprised you are even connected :P

I'll wait for 'Events' and your descriptions of them.

**PS:**
I am facing one of those periods when my Internet celebrates "Dry-Day", and I may be travelling next couple of days. So please don't mind if you don't get faster replies from me for next 2-3 days, although I'll be quick at it whenever I get the opportunity to check on the forums.

---

