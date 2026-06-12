---
title: "Can't access 802.1X network with Ubuntu 13.04 (Broadcom BCM4313 adapter)"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by alperyilmaz on 2013-09-26
Hi,

My friend has Lenovo G8550 laptop, he installed Ubuntu 13.04 and unfortunately he cannot access his university wireless network, named "yildiz-net".
We tried different solutions but didn't succeed. Our last hope was [this post]("http://ubuntuforums.org/showthread.php?t=2175851").

We used the script mentioned in [this post]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385") and all related information for his case is presented below. 
We'd greatly appreciate if you can help us.

thanks.


```


*************** info trace ***************

***** uname -a *****

Linux lenovo 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:54:42 UTC 2013 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:051b]
	Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Lenovo Device [17aa:3978]
	Kernel driver in use: alx

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 0c45:6455 Microdia 

***** PCMCIA Card Info *****


***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

wl                   2902185  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              436177  1 wl

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         194.27.96.72
    Prefix:          24 (255.255.255.0)
    Gateway:         194.27.96.1

    DNS:             194.27.101.250
    DNS:             194.27.101.249


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    yildiz-net:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    yildiz-net:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WEP
    yildiz-net:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WEP
    HPE710n.2518B9:  Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    yildiz-net:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WEP
    yildiz-net:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WEP



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

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"yildiz-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A79696C64697A2D6E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400020100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319006169722D642D6B6D662D62362D34000003000025
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"HPE710n.2518B9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000E4850453731306E2E323531384239
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"yildiz-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A79696C64697A2D6E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319006169722D642D6B6D662D62362D32000004000025
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"yildiz-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000A79696C64697A2D6E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319006169722D642D6B6D662D61312D32000003000025
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"yildiz-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 25932ms ago
                    IE: Unknown: 000A79696C64697A2D6E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400020100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E00004D000F00FF0318006169722D642D6B6D662D6469732D31000C000025
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000307A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"yildiz-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 25932ms ago
                    IE: Unknown: 000A79696C64697A2D6E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319006169722D642D6B6D662D61312D31000000000025
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"YILDIZ_PARK_YONETIM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 001359494C44495A5F5041524B5F594F4E4554494D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001300000000000000000000000000000000000000
                    IE: Unknown: DD490050F204104A0001101049001E007FC5100018F1E7E8E0E3C8CBDEB5444FACDC0A88953030303030303766104400010210470010D20AC16B902F5CDA90FE9F8CF84DBBAB103C000103
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (0) :
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

***** modinfo *****

filename:       /lib/modules/3.8.0-30-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-30-generic SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


***** udev rules *****

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

***** dmesg *****

[   13.431123] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.468670] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.651584] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   13.670157] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f03)
[  692.210922] ERROR @wl_dev_intvar_get : error (-1)
[  692.210926] ERROR @wl_cfg80211_get_tx_power : error (-1)

****************** done ******************



```

---

### Post by Hadaka on 2013-09-26
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -v brcmsmac

```
thanks.

---

### Post by alperyilmaz on 2013-09-27
Hadaka, 
Thanks for your reply. But I already tried that solution, which was at this URL: [http://ubuntuforums.org/showthread.php?t=2175851](http://ubuntuforums.org/showthread.php?t=2175851), and it didn't work..

---

### Post by varunendra on 2013-09-27
> **alperyilmaz said:**
> ```

***** iwconfig *****

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="#FF0000"]on[/COLOR]**

***** modinfo *****

filename:       /lib/modules/3.8.0-30-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211

```

How have you installed the sta driver (wl), and from where? Two separate blacklist files for blacklisting b43 and team indicate that you have possibly gone through multiple methods/sources to install the sta driver.

What does this return -
```
dpkg -l | grep bcmwl
```?

Also, have you tried turning the power management off? -
```
sudo iwconfig eth1 power off
```

Does the wifi work at other places?

---

### Post by alperyilmaz on 2013-10-01
Hi varunendra,

Thanks for your reply.

As you mentioned we tried different methods and don't quite remember how the wl (or other drivers) were installed. I just checked before I started applying your suggestions, broadcom-sta-common package was installed.

Then I run your command:

$ dpkg -l | grep bcmwl

There was no output. After that, I installed the bcmwl-kernel-source (I assumed you wanted to learn if that package was installed or not)
$ sudo apt-get install bcmwl-kernel-source

Here's the output after I installed the package:
$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source                       6.20.155.1+bdcom-0ubuntu6              i386         Broadcom 802.11 Linux STA wireless driver source


Then I restarted the computer, unfortunately I was still unable to connect to my university's network (I am able to connect other wireless networks)

Finally, I tried your last option, to turn of power management, by the following command:

$ sudo iwconfig eth1 power off   

I tried to connect the university network but it didn't work.

---

### Post by varunendra on 2013-10-02
> **alperyilmaz said:**
> I was still unable to connect to my university's network (I am able to connect other wireless networks)

Does it give you any error about some "ca-certificate"? Please check -
```
sudo cat /etc/NetworkManager/system-connections/<your connection name>
```

Don't post the output here (or remove the security key part before posting). See if there is a line that says -
```
system-ca-certs=true
```
If there is, open the file as root (gksu gedit /etc/NetworkManager/system-connections/<connection name>) and change the "**true**" to "**false**". Proofread, save and close the file and retry to connect.

However, if there is no such line in the file, please download this latest driver [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_i386.deb) , doube-click to install and retry to connect.

If still failed, please download the alternate version of the "wireless_script" (from the bottom link of the same post linked to "Wireless Script" link in my signature), run it when the connection fails and post back the fresh report file it generates.

---

### Post by alperyilmaz on 2013-10-02
Hi varunendra,

Thank you very much for your time and help. Finally it works. 

What I did was, I changed the certicate option from "true" to "false". Then I restarted the computer and it didn't help.

Then, I tried your next suggestion, I installed the latest driver. After restart, I was able to connect my university network. Thank you very much again..

---

### Post by varunendra on 2013-10-02
You're welcome ! :)

If the problem occurs again, the first thing to check would be the same line that you changed. Make sure it is there (only in Enterprise networks like your University's) and is set to "false".

---

