---
title: "Broadcom BCM94312"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by denis7 on 2013-09-13
Hello, I am working on getting a comfortable Linux Distro for a Linux newbie.
 The hardware is an Acer Aspire One D150-1BW. I choose ubuntu 12.04. The wlan chipset is BCM94312. I installed firmware-b43-lpphy-installer. 
Now on bootup the network-manager-applet does not show any available networks. Only if I login as root and enter "iwlist scan". It will immediatly connect the device. 
I thought it would only load the b43 module or dependant modules after this command and compared the lsmod outputs, befor and after invocation of the command, but they're identical. I also remove the line "blacklist bcm43xx" in /etc/modprobe.d/blacklist.conf and added the command iwlist scan to /etc/rc.local but it does not work, since it is probably not executed as root. Even if I'd find out howto invoke a command as root on startup, I'd still like to know, why it won't find any ap just until I scan as root?

Thank's for reading.
Denis

---

### Post by varunendra on 2013-09-13
Hello Denis, Welcome to the forums ! :)

> **denis7 said:**
> The wlan chipset is **BCM94312**
Let's make sure of that. Please post back the outputs of-
```
lspci -nnk | grep -iA2 net
lsmod | egrep 'b43|wl|brcm|bcma'
```

Let's clear some misconceptions you have -
> **[COLOR="#FF0000"]Only if I login as root[/COLOR]** and enter "iwlist scan". It will immediatly connect the device. 
I thought it would only load the b43 module or dependant modules after this command
The highlighted part is Strongly discouraged, especially when you are new to Linux ([see why]("https://help.ubuntu.com/community/RootSudo")). And the mechanism you described actually works exactly the opposite way. You first HAVE TO load the driver, only then you'd be able to scan networks. At least this is what I have understood so far..

> I also remove the line "blacklist bcm43xx" in /etc/modprobe.d/blacklist.conf and added the command iwlist scan to /etc/rc.local
Both are unnecessary steps helping nothing. The bcm43xx is blacklisted by default for a good reason, as the comment above it says (replaced by ssb).

> but it does not work, since it is probably not executed as root.
The /etc/rc.local file IS executed as root. The command you added doesn't work because it is not meant to do what you expect from it (load the driver).

Please post the outputs asked above, and we'll see what it needs and why it isn't working as expected.

---

### Post by denis7 on 2013-09-15
Here're the outputs:

root@ubuntu:/home/robertsmith# lspci -nnk |grep iA2 net
grep: net: No such file or directory

root@ubuntu:/home/robertsmith# lsmod |egrep 'b43|wl|brcm|bcma'
b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  1 b43

> The highlighted part is Strongly discouraged, especially when you are new to Linux ([see why]("https://help.ubuntu.com/community/RootSudo")).  And the mechanism you described actually works exactly the opposite  way. You first HAVE TO load the driver, only then you'd be able to scan  networks. At least this is what I have understood so far..


I logged in console in as root, entered 'iwlist scan' and gnome-network-manager connected to the ap. Before I couldn't even see any ap's in gnome-network-manager. So I thought it loads wireless modules only on request of root. I diff'd the lsmod outputs before and after 'iwlist scan' but they're the same. Then I entered 'iwlist scan' in rc.local and I have to correct myself: it now connects to the ap from startup after some time. If I disable it in rc.local it won't connect again. This has not been the case for the first few boots. But today it somewhen showed the restricted drivers message (I did not press any button) and connected to the ap. Now it connects on every start if I have the line 'iwlist scan' in rc.local.

So one could say problem is solved. Still I would like to know, what the problem is, to fill in a bug report to help developers. I was also unable to install the correct driver from the 'restricted driver available' message.

---

### Post by varunendra on 2013-09-15
> **denis7 said:**
> root@ubuntu:/home/robertsmith# lspci -nnk |grep**[COLOR="#FF0000"] iA2[/COLOR]** net
grep: net: No such file or directory

You forgot the hyphen (-) before "i". And the iwlist scan helping when in rc.local doesn't make much sense to me, but there maybe something new for me to learn. Let's just take a look at a detailed report of your setup and proceed accordingly.

To generate such a detailed report, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Apart from the above report, please also post the output of (when you are NOT in root console) :
```
groups
```

Also, make sure the "Available to all" option is enabled for your connection in Network Manager settings.

One more thing - have you tested the connection in a Live session? Does it work fine there?

---

### Post by denis7 on 2013-09-16
Sorry man here's the correct output:

root@ubuntu:/home/robertsmith# lspci -nnk |grep -iA2 net
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e018]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: Acer Incorporated [ALI] Device [1025:019c]
    Kernel driver in use: ATL1E

```
> 
... the iwlist scan helping when  in rc.local doesn't make much sense to me, but there maybe something new  for me to learn.

The iwlist scan in bash as root helping is what I wonder about too.
When is /etc/network/if-pre-up.d/wireless-tools invoked?

Please ask for specific commands I shall enter, not downloading unknown scripts.

Here's the group output:
 adm cdrom sudo dip plugdev lpadmin sambashare

Wonder what that could help?

Also the "Availible for all" option was set. As I said I could not see any networks before I entered iwlist scan as root. Also iwlist scan as normal user did not give any output. Why is the restricted driver availible message assuming a wrong driver?

---

### Post by varunendra on 2013-09-16
> **denis7 said:**
> 
When is /etc/network/if-pre-up.d/wireless-tools invoked?
Judging by the comment included in that script - AFTER the driver is loaded and BEFORE the interface is brought UP. So clearly, the first stage of this sequence is loading of driver (should be done at boot time) and scanning of network comes last (after the driver is loaded and parameters set).

> Please ask for specific commands I shall enter, not downloading unknown scripts.
That script has been developed by some most reputed forum members, which you would have found out had you read the linked post, and is very frequently being used in these forums. Just browse through the threads posted in last couple of days and you'll see for yourself. An example post with its output : [http://ubuntuforums.org/showthread.php?t=2169868&p=12779115#post12779115](http://ubuntuforums.org/showthread.php?t=2169868&p=12779115#post12779115)

It would be very cumbersome to give you all the specific commands it covers (and filters the output too, thus providing more security than you are concerned of).

> Here's the group output:
adm cdrom sudo dip plugdev lpadmin sambashare

Wonder what that could help?
In fact, it seems to have helped a lot **if it is a complete output**, not stripped off. It simply shows that you are not a member of your own user-group, or even worse, probably your group doesn't exist anymore ! That may the answer why you can't connect from your normal account.

Is it from the first user created during installation? Did you do something experimental with user IDs?

Let us see how many users you have and what their group memberships are -
```
for user in `ls /home`; do id $user; echo; done
```


**PS:**
Explanation to your last question/doubt -
> I could not see any networks before I entered iwlist scan as root. Also iwlist scan as normal user did not give any output. Why is the restricted driver availible message assuming a wrong driver?
From "man iwlist" -
> Triggering  scanning  is  a privileged operation (root only) and
              normal users can only read left-over scan results.
And restricted driver is not assuming a wrong driver. It is just that your card happens to be supported by both the native b43 as well as proprietary wl driver that "Additional Drivers" is proposing ([see here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices")).

Most of us here believe the native b43 performs better on this one, so we try that first.

---

### Post by denis7 on 2013-09-16
> **if it is a complete output**,

I'm sorry sir, it's not. I stripped off my user group

> And restricted driver is not assuming a wrong driver. It is just  that your card happens to be supported by both the native b43 as well as  proprietary wl driver that "Additional Drivers" is proposing ([see here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices")).

If it's not, it still doesn't install on request, but gives an error message.

Here's the stripped off output of the script. I don't want to publish my detailed network configuration...
Since the script is issuing the iwlist scan command I get a different output if i invoce the script a second time.

So here's the first output:
```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e018]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: Acer Incorporated [ALI] Device [1025:019c]
    Kernel driver in use: ATL1E

***** lsusb *****

Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
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
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback

auto wlan0


***** iwlist *****

wlan0     No scan results


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

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.604207] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.604229] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.604246] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.604262] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.604278] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.676487] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[   15.149603] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.192480] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   22.656194] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   28.105873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.106720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```


```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 17:33:45 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e018]
    Kernel driver in use: b43-pci-bridge
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: Acer Incorporated [ALI] Device [1025:019c]
    Kernel driver in use: ATL1E

***** lsusb *****

Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****



***** rfkill *****

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
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

State: connected (global)

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
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback

auto wlan0



***** resolv.conf *****

nameserver 127.0.0.1


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

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    2.604238] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.604260] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.604278] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.604295] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.604311] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.676242] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
[   16.513594] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   16.556087] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   18.252116] init: network-interface (wlan0) pre-start process (765) terminated with status 1
[   23.052157] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   28.509873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.510715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.505887] wlan0: authenticate with <MAC address removed>
[  115.528471] wlan0: send auth to <MAC address removed> (try 1/3)
[  115.534712] wlan0: authenticated
[  115.536086] wlan0: associate with <MAC address removed> (try 1/3)
[  115.540409] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[  115.541400] wlan0: associated
[  115.541491] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************

```

---

### Post by Hadaka on 2013-09-16
Hi denis7, try this **without** the rc.local...iwlist scan 
please do..
```
sudo su
echo b43 >> /etc/modules
exit 0
```
boot
that work for you?

---

### Post by varunendra on 2013-09-17
> **denis7 said:**
> I'm sorry sir, it's not. I stripped off my user group

Denis, you may have security concerns and I'm not going to doubt or question them. But at one hand, you fear even disclosing your user-group or even local network addresses, and on the other you are using net with root access (security goes right down the drain, unless you are a pro security/firewall specialist).

Be reasonable. How can you expect someone to be able to help you if you keep giving them incomplete, incorrect even manipulated information, and don't even tell them you have stripped something off of the supplied info? :)

You may have valid reasons to not disclose many details, but with limited information, the help that can be offered gets severely limited too. Not only that, but with wrong info, there is a very good chance that you'll get wrong advice too - good enough to further mess up your system in a wonderful way, good enough to make people say - "Wow ! How did you manage that?". I hope you understand that.

Anyway, that was not to criticize you, neither was any frustration on my part. I'm just trying to be reasonable and asking you to be the same.

Okay, lecture period over, let's move on with what we have at hand -

> If it's not, it still doesn't install on request, but gives an error message.
See [this]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1095751") bug. If you wish to try the restricted driver anyway, you can try what is suggested in comment #55 in the bug report page, OR you can try an even newer version of the fixed driver from [here]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504"). But the latter one is packaged for 64 bit, so am not sure if it'll install on your 32 bit setup or not.

But I doubt ANY driver is going to help as long as you have this -
```

***** interfaces *****

auto lo
iface lo inet loopback

**[COLOR="#FF0000"]auto wlan0[/COLOR]**

```
..in your /etc/network/interfaces file.

Assuming you are managing all your physical interfaces with Network Manager, which is the default way, the above file should contain ONLY the first two lines. Unless the above record is a stripped one too (other lines to do the rest of the job that normally NM takes care of), I suggest you delete the "auto wlan0" entry from the file. To do so, open the file and edit it so that it looks like -
> auto lo
iface lo inet loopback.. nothing else. Proofread, save and close, and reboot to see if it fixed your issue.

---

### Post by denis7 on 2013-09-17
```

Hi denis7, try this **without** the rc.local...iwlist scan 
please do..
 	Code:
 	sudo su
echo b43 >> /etc/modules
exit 0 
boot
that work for you?

```

Tanks for joining. modprobe all the necessary drivers after boot was something I tried first. Also putting it in /etc/modules. But ubuntu developers seem to go there own way, using different methods, to load drivers at boot, because also b43 is loaded at bootup even though it's not in /etc/modules. To mee it seems, that every necessary driver is loaded, but ubuntu has messed up some of their configuration programs. 

```

You may have valid reasons to not disclose many details, but with  limited information, the help that can be offered gets severely limited  too. Not only that, but with wrong info, there is a very good chance  that you'll get wrong advice too - good enough to further mess up your  system in a wonderful way, good enough to make people say - "Wow ! How  did you manage that?". I hope you understand that.

```

I think you miss the point. I don't need your help but you need mine. I already found a solution and infact the second window is the unchanged output of the script. Did you ask me for a second, sir?
Don't want to argue about security issues either.

I'll try your suggestion on /etc/network/interfaces and post again if it will not fix it, and the owner won't have gotten his netbook back.

---

### Post by denis7 on 2013-09-17
Did not work.

I could imagine, that it is a driver problem. The wifi is not fully activated yet, and we won't find any solution, besides mine.

---

### Post by varunendra on 2013-09-17
> **denis7 said:**
> I think you miss the point. I don't need your help but you need mine.

> **denis7 said:**
> Did not work.

I could imagine, that it is a driver problem. The wifi is not fully activated yet, and we won't find any solution, besides mine.

I graciously bow out then. :)

---

### Post by denis7 on 2013-09-18
Please move this thread to specialized support, I think it is something the ubuntu programmers should take a look at.

---

