---
title: "Lenovo s10-3 xubuntu wireless problem."
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by Rene-Andre_Kaljust on 2014-02-07
Hi

I'm running xubuntu 12.04 on my Lenovo s10-3 machine. At first rfkill list said that it was hard blocked so i used lspci-k to identify my card and under additional drivers I installed the correct propietary driver ( Broadcom STA wireless driver ). Everything seems to be fine except it can not find any single wireless connection at all.
I'm quite new to ubuntu so take it slow with me. 
Thank you

---

### Post by varunendra on 2014-02-07
Hi, Welcome to Ubuntu Forums ! :)

Please open a terminal (Ctrl-Alt-T) and post back the full output of following command (you may copy-paste it):
```
lspci -nnk | grep -iA2 net
```

It will show us the device ID of your card so we can see if the sta driver is the correct driver for it or not.

---

### Post by Rene-Andre_Kaljust on 2014-02-07
Hi, thanks for the fast answer.

Heres what you requested:

```

lspci -nnk | grep -iA2 net
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
Subsystem: Broadcom Corporation Device [14e4:0510]
Kernel driver in use: wl
```

---

### Post by varunendra on 2014-02-08
> **Rene-Andre_Kaljust said:**
> 
lspci -nnk | grep -iA2 net
09:00.0 Network controller [0280]: Broadcom Corporation **BCM4313** 802.11bgn Wireless Network Adapter **[14e4:4727]** (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: **[COLOR="#FF0000"]wl[/COLOR]**

Most of us here believe that the native "brcmsmac" driver works better with that card. To try it, please purge the current "wl" driver -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and see if the connection is any better. If purged correctly, the native driver will automatically load since next boot.

If that doesn't solve the problem, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by praseodym on 2014-02-08
Maybe you need to install the package "linux-firmware-nonfree" for the native driver.

---

### Post by Rene-Andre_Kaljust on 2014-02-11
Hi again, i tried that purge code but it did not help me, now im back to my wireless being hard blocked.

Here's my wireless script result:

```



*************** info trace ***************


***** uname -a *****


Linux sandra-Lenovo 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:40:43 UTC 2013 i686 i686 i386 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


***** lspci *****


09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: brcmsmac


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 04f2:b1b8 Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 12d1:1039 Huawei Technologies Co., Ltd. Ideos (tethering mode)


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


***** rfkill *****


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


***** lsmod *****


bcma                   25651  0 
brcmsmac              540923  0 
mac80211              436493  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178877  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12518  1 brcmsmac


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.211
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             unavailable
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


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




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
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     722AA6B08A43CF879452476
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     DB27B1DE461446E6FBADCFE
depends:        
intree:         Y
vermagic:       3.2.0-58-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   12.651468] brcmsmac 0000:09:00.0: bus 9 slot 0 func 0 irq 255
[   12.651502] brcmsmac 0000:09:00.0: enabling device (0104 -> 0106)
[   12.651526] brcmsmac 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.651550] brcmsmac 0000:09:00.0: setting latency timer to 64
[   14.147788] ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************

```

EDIT: I can see that in this code my rfkill shows soft blocked not hard blocked so I used ```
sudo rfkill unblock all
``` and now after that its hard blocked instead.

```
[COLOR=#000000][FONT=Ubuntu Mono]2: phy0: Wireless LAN[/FONT][/COLOR]    Soft blocked: no
    Hard blocked: yes

```

---

### Post by praseodym on 2014-02-11
For kernel 3.2 you need the updated driver:
```

sudo apt-get install linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$(uname -r | cut -c10-23) linux-headers-generic build-essential dkms linux-firmware-nonfree
```
Reboot. If the hard block is still there, check these steps:


[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by Rene-Andre_Kaljust on 2014-02-12
After 
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$(uname -r | cut -c10-23) linux-headers-generic build-essential dkms linux-firmware-nonfree[/FONT][/COLOR]
```[COLOR=#000000]
trying to press Enable Wireless the system now totally hangs and wont move until i force quit the computer.

I followed the 3 steps on that link but it's still the same, i  boot, try to press Enable Wireless and it just hangs forever.

[/COLOR]

---

### Post by praseodym on 2014-02-13
Have you checked the steps from the link?

---

### Post by Rene-Andre_Kaljust on 2014-02-14
Yes I have.

---

### Post by varunendra on 2014-02-14
I suggest you try upgrading your kernel and xorg stack as suggested here : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

It is not guaranteed to offer a better stability or performance (it even has a *slight* chance to break some), but unless you are using non-standard third party packages/programs, it should be a smooth and good transition.

The brcmsmac driver that we are suggesting here had become significantly better since kernel 3.8, and current Enablement Stack should offer you kernel 3.11 (with other kernels in-between).

You may check your repositories (via software center, or terminal command "apt-cache show linux-image*" or via Synaptic Package Manager (my preferred method)) to see which versions of newer kernels are available for you.

**_Alternatively_**, and a relatively safer option for a nicely working system, you may choose to install only the one particular driver (with its supporting ones) - the brcmsmac - via backported package modules.

If you prefer this alternative method, you may follow the instructions in this post : [http://ubuntuforums.org/showthread.php?t=2204773&p=12928915#post12928915](http://ubuntuforums.org/showthread.php?t=2204773&p=12928915#post12928915)
*[**Note :** Replace the command "make defconfig-ar5523" with "**make defconfig-brcmsmac**" in step 3 in above link, and ignore the "dmesg.." check in step 4]*

But I'd like to confirm with **praseodym** first if he thinks it would be a good way to proceed.

---

### Post by Rene-Andre_Kaljust on 2014-02-17
EDIT: didn't notice the second page >.<

---

### Post by varunendra on 2014-02-17
Did you try the 'Alternative' option? That is, following the link I gave to install a newer, backported driver?

This card and driver combinations usually work very nicely. I wouldn't give up so easily if I were you. :)

---

### Post by windowsfree on 2014-04-18
Having same issue with S10-2.  Found that if I tap the wireless switch (above the keyboard) while booting, device is no longer hard blocked.  Very inconvenient, but it works.

---

