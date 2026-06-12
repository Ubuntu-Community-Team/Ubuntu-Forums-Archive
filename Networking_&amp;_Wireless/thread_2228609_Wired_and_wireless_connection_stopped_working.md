---
title: "Wired and wireless connection stopped working"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by paul138 on 2014-06-08
Hi there,

I did an update and appear to have broken a working laptops internet connection.

[This ]("http://ubuntuforums.org/showthread.php?t=2197693&highlight=network+unclaimed+physical")thread appears to be very similar but i attempted the fix suggested by varunendra and it did not work for me.

Output of lshw -C network

```
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f68fc000-f68fffff ioport:de00(size=256)
```

Output of the wireless script

```

*************** info trace ***************

***** uname -a *****

Linux Inspirion 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:08:16 UTC 2014 i686 i686 i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

***** lspci *****

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]

***** lsusb *****

Bus 002 Device 003: ID 1221:3234  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: disconnected


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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

***** modinfo *****


***** udev rules *****

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****


****************** done ******************


```

thanks for your time

---

### Post by praseodym on 2014-06-08
No drivers loaded:
```

sudo modprobe -v sky2
sudo modprobe -v wl
echo -e "sky2\nwl" | sudo tee -a /etc/modules
```

---

### Post by paul138 on 2014-06-08
thanks for the response

```
sudo modprobe -v sky2
modprobe: FATAL: Module sky2 not found.
sudo modprobe -v wl
modprobe: FATAL: Module wl not found.
```


```
echo -e "sky2\nwl" | sudo tee -a /etc/modules
sky2
wl
```

---

### Post by praseodym on 2014-06-09
Ok, remove "sky2" and "wl" from the file via
```

gksudo gedit /etc/modules
```
Save and close the editor. Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Installation:
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Remove the STA driver:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
Reboot.

---

### Post by paul138 on 2014-06-09
Thanks for the response, 

Removed the wl sky2 entries and downloaded / extracted the files ok.

Then this

```
julia@Inspirion:~$ sudo apt-get remove --purge bcmwl-kernel-sourceReading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
julia@Inspirion:~$ 
julia@Inspirion:~$ 
julia@Inspirion:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.confrm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory
julia@Inspirion:~$ 
julia@Inspirion:~$ sudo rm /etc/modprobe.d/broadcom-sta-common.confrm: cannot remove ‘/etc/modprobe.d/broadcom-sta-common.conf’: No such file or directory
julia@Inspirion:~$ 
julia@Inspirion:~$ 
julia@Inspirion:~$ sudo rm /etc/modprobe.d/broadcom-sta-dkms.confrm: cannot remove ‘/etc/modprobe.d/broadcom-sta-dkms.conf’: No such file or directory
julia@Inspirion:~$ 
julia@Inspirion:~$ 
julia@Inspirion:~$ sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sed: no input files
julia@Inspirion:~$ sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sed: no input files
julia@Inspirion:~$ sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sed: no input files
julia@Inspirion:~$ sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*)
sed: no input files


```

---

### Post by praseodym on 2014-06-09
Thats Ok. Now reboot

---

### Post by paul138 on 2014-06-09
Sorry, i did,

still no wired or wireless :(

---

### Post by praseodym on 2014-06-09
Load the driver by hand:
```

sudo modprobe -v b43
dmesg | grep b43
iwconfig
rfkill list
lsmod
```

---

### Post by paul138 on 2014-06-09
Thanks, 

```
julia@Inspirion:~$ sudo modprobe -v b43
[sudo] password for julia: 
modprobe: FATAL: Module b43 not found.
julia@Inspirion:~$ dmesg | grep b43
julia@Inspirion:~$ lwconfig
The program 'lwconfig' is currently not installed. You can install it by typing:
sudo apt-get install likewise-open
julia@Inspirion:~$ rfkill list
julia@Inspirion:~$ lsmod
Module                  Size  Used by
joydev                 17101  0 
serio_raw              13230  0 
video                  18903  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usb_storage            48417  0 
ahci                   25579  2 
psmouse                91033  0 
libahci                26754  1 ahci
julia@Inspirion:~$ 

```

---

### Post by praseodym on 2014-06-09
Ok, I see that you are using the backports sources. Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.13.0-27-generic_3.13.0-27.50_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.13.0-27-generic_3.13.0-27.50_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-27-generic_3.13.0-27.50_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-27-generic_3.13.0-27.50_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-27_3.13.0-27.50_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-27_3.13.0-27.50_all.deb)

Its reinstalling the kernel.

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot.

---

### Post by paul138 on 2014-06-09
```
julia@Inspirion:~$ sudo dpkg -i /home/julia/Downloads/kernel/*.deb
[sudo] password for julia: 
(Reading database ... 191201 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-27_3.13.0-27.50_all.deb ...
Unpacking linux-headers-3.13.0-27 (3.13.0-27.50) over (3.13.0-27.50) ...
Preparing to unpack .../linux-headers-3.13.0-27-generic_3.13.0-27.50_i386.deb ...
Unpacking linux-headers-3.13.0-27-generic (3.13.0-27.50) over (3.13.0-27.50) ...
Preparing to unpack .../linux-image-3.13.0-27-generic_3.13.0-27.50_i386.deb ...
Done.
Unpacking linux-image-3.13.0-27-generic (3.13.0-27.50) over (3.13.0-27.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Setting up linux-headers-3.13.0-27 (3.13.0-27.50) ...
Setting up linux-headers-3.13.0-27-generic (3.13.0-27.50) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Setting up linux-image-3.13.0-27-generic (3.13.0-27.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-27.50 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-27.50 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
julia@Inspirion:~$
```


Rebooted, no connection,

---

### Post by praseodym on 2014-06-09
Now
```

sudo modprobe -v b43
```
If its not working, then reboot, hold the SHIFT button during boot-up to enter the grub bootloader. Choose "previous ubuntu versions" there and then another kernel with a number smaller than "27" (not the "recovery mode"). Check the connection there.

---

### Post by paul138 on 2014-06-09
Both wired and wireless are working again, thank you very much for your help, appreciated.

Not sure if i should mark this as solved?

Should i try updating again?

You mentioned using backports earlier, im happy to not do whatever that is if it will help, this is the mothers laptop which she uses to look at her email and nothing else.

---

### Post by praseodym on 2014-06-09
Uninstall kernel "27":
```

sudo apt-get remove --purge linux-image-3.13.0-27-generic linux-headers-3.13.0-27*
```
Go to the update-manager->Settings and untick the backports and proposed sources. Close it and run
```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
```
After a reboot the current kernel should be used again:
```

uname -a
```
Kernel version corrected!

---

### Post by paul138 on 2014-06-09
I think there was a typo, i ran 3.13.0-27 

```
sudo apt-get remove --purge linux-image-3.13.0-27-generic linux-headers-3.13.0-27*
```

Everything else seems to be ok now. After reboot uname -a gives me the -24 kernel,


Thanks

---

### Post by praseodym on 2014-06-09
Sorry, you're right. 

You're welcome.

---

