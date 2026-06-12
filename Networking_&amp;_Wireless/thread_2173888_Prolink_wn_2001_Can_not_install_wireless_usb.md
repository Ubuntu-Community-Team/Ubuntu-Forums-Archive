---
title: "Prolink wn 2001: Can not install wireless usb"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by Ferry_Boja_Sabara on 2013-09-11
I use Ubuntu 12:04and from the usb wireless prolink, wn 2001 models and I got an error 


when i use make command


root@topijerami-desktop:/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-23-generic-pae/build M=/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
  CC [M]  /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.o
In file included from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:51:0,
                 from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_cmd.h:88:25: error: field &#8216;event_tasklet&#8217; has incomplete type
In file included from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:53:0,
                 from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_xmit.h:336:24: error: field &#8216;xmit_tasklet&#8217; has incomplete type
In file included from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:54:0,
                 from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_recv.h:185:24: error: field &#8216;recv_tasklet&#8217; has incomplete type
In file included from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/drv_types.h:58:0,
                 from /home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.c:22:
/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/include/rtl871x_io.h:17:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625/cmd/rtl871x_cmd.o] Error 1
make[1]: *** [_module_/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'
make: *** [modules] Error 2
root@topijerami-desktop:/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625# ^C
root@topijerami-desktop:/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625# 






when i use make install command


root@topijerami-desktop:/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625# make install
install -p -m 644 8712u.ko  /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `8712u.ko': No such file or directory
make: *** [install] Error 1
root@topijerami-desktop:/home/topijerami/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625# 



i'm sorry my bad english
 thank you for helping me :)

---

### Post by varunendra on 2013-09-13
Hi, and Welcome to the forums !

Where did you get the driver from? It seems too outdated (25-06-2010)

Please plug in the USB adapter, open a terminal and post back the output of-
```
lsusb
```

While posting, please use 'Code' tags (see the link in my signature)..

---

### Post by mörgæs on 2013-09-13
Slightly off topic: 

I saw that you are using root. This might be worth reading: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ferry_Boja_Sabara on 2013-09-15
> **varunendra said:**
> Hi, and Welcome to the forums !  Where did you get the driver from? It seems too outdated (25-06-2010)  Please plug in the USB adapter, open a terminal and post back the output of- ```
lsusb
```  While posting, please use 'Code' tags (see the link in my signature)..  this displayed when i write code lsusb  
```

root@topijerami-desktop:/# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1a8d:1007 BandRich, Inc. 
Bus 001 Device 003: ID 07b8:8188 AboCom Systems Inc 



```

---

### Post by varunendra on 2013-09-15
> **Ferry_Boja_Sabara said:**
> this displayed when i write code lsusb  
```

Bus 001 Device 002: ID 1a8d:1007 BandRich, Inc. 
Bus 001 Device 003: ID **07b8:8188 AboCom Systems Inc** 

```

Your wireless adapter seems to be supported by two native drivers simultaneously - rtl8192cu and r8712u - indicating that it may possibly be a driver conflict issue.

Please plug-in the adapter, then follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

And why are you using the root account?

---

### Post by Ferry_Boja_Sabara on 2013-09-18
> **varunendra said:**
> Your wireless adapter seems to be supported by two native drivers simultaneously - rtl8192cu and r8712u - indicating that it may possibly be a driver conflict issue.

Please plug-in the adapter, then follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

And why are you using the root account?

```


*************** info trace ***************

***** uname -a *****

Linux topijerami-desktop 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136]
    Kernel driver in use: r8169
    Kernel modules: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1a8d:1007 BandRich, Inc. 
Bus 001 Device 003: ID 07b8:8188 AboCom Systems Inc 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: ttyUSB0  [Telkomsel Default 1] ---------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         182.10.76.46
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             192.168.4.28


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
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


***** iwlist *****


***** resolv.conf *****

nameserver 192.168.4.28
nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211

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

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****


****************** done ******************



```

---

### Post by varunendra on 2013-09-18
While the wifi adapter is plugged in, please try -
```
sudo modprobe -v r8712u
```
Are there any error messages? Does it activate the adapter?

Unplug-replug the adapter if there were no errors but the card isn't activated either. And post back if there were any error messages.

If nothing happens, please post back the outputs of (after trying above, and the USB still plugged in) -
```
lsusb
rfkill list all
modprobe -c | grep -i 07b8.*8188
lsmod | grep r87
dmesg | grep r87
```

---

### Post by Ferry_Boja_Sabara on 2013-10-03
ouh.. still error

---

### Post by Ferry_Boja_Sabara on 2013-10-05
how can i actived my wireless adapter?

---

### Post by varunendra on 2013-10-06
> **Ferry_Boja_Sabara said:**
> ouh.. still error
If I remember correctly, your post before edit was something like - "It worked..". So the discussion was ended.

Please do not edit your posts to remove the content unless it is very necessary. It leaves us in a confused state. For a moment, I lost the entire context.. (thanks to my not-so-good memory, and the name "r8712u" that I immediately recalled where we left it). If necessary, try 'striking out' the the info that you want to change. Striking out is done like this -
[noparse][s]my wrong or obsolete info[/s][/noparse]

It makes it look like this in the post -
[s]my wrong or obsolete info[/s]

> **Ferry_Boja_Sabara said:**
> how can i actived my wireless adapter?
Does this command work ? -
```
sudo modprobe -v r8712u
```
If yes, let me know it does so we can make it permanent. If not, please run the wireless_script again and post back the fresh report it generates. Thanks.

---

