---
title: "Broadcom BCM4352/BCM20702A0 Bluetooth not detected - Ubuntu 14.04"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by polochamps on 2015-01-25
Hi,

This wireless adapter has been a problem on LInux since I bought my motherboard. 
Bluetooth works on 15.04 but doesn't recognized on 14.04 and 14.10.
Can I make it work on 14.04?

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:855c]
    Kernel driver in use: wl


```

Thank you

---

### Post by jeremy31 on 2015-01-25
Should be able to, what is the result of ```
lsusb
```

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> Should be able to, what is the result of ```
lsusb
```

```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 003 Device 002: ID 1b1c:1b07 Corsair 
Bus 003 Device 005: ID 1949:00f2 Lab126, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Thank you

---

### Post by jeremy31 on 2015-01-25
What kernel are you using and I will see if I can patch btusb to work for the current kernel

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> What kernel are you using and I will see if I can patch btusb to work for the current kernel

```
uname -r
3.13.0-44-generic

```

Thanks Jeremy!

---

### Post by jeremy31 on 2015-01-25
See if this works, copy this to your /home directory [https://www.dropbox.com/sh/5wjhy3cuowpnm2h/AAB4PPzImGJRJh-OBhD3OIuUa?dl=0](https://www.dropbox.com/sh/5wjhy3cuowpnm2h/AAB4PPzImGJRJh-OBhD3OIuUa?dl=0)
Then ```
sudo modprobe -r btusb && [FONT=Ubuntu Mono]sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak[/FONT]
```[FONT=Ubuntu Mono]
```
cd ~/polo
```[/FONT]```
[FONT=Ubuntu Mono]sudo cp btusb.ko  /lib/modules/$(uname -r)/kernel/drivers/bluetooth/[/FONT]
```[FONT=Ubuntu Mono]```
sudo modprobe btusb
```
See if it works.
I am hoping it will work this way without the patchram loader, if it doesn't I can change the module and hopefully the firmware can be found

hex file found- [/FONT]http://ubuntuforums.org/showthread.php?t=2231813

---

### Post by praseodym on 2015-01-25
Did you try installing the driver from 15.04?

```
sudo apt-get remove --purge bcmwl-kernel-source
wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb
sudo dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb
```

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> See if this works, copy this to your /home directory [https://www.dropbox.com/sh/5wjhy3cuowpnm2h/AAB4PPzImGJRJh-OBhD3OIuUa?dl=0](https://www.dropbox.com/sh/5wjhy3cuowpnm2h/AAB4PPzImGJRJh-OBhD3OIuUa?dl=0)
Then ```
sudo modprobe -r btusb && [FONT=Ubuntu Mono]sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak[/FONT]
```[FONT=Ubuntu Mono]
```
cd ~/polo
```[/FONT]```
[FONT=Ubuntu Mono]sudo cp btusb.ko  /lib/modules/$(uname-r)/kernel/drivers/bluetooth/[/FONT]
```[FONT=Ubuntu Mono]```
sudo modprobe btusb
```
See if it works.
I am hoping it will work this way without the patchram loader, if it doesn't I can change the module and hopefully the firmware can be found

hex file found- [/FONT]http://ubuntuforums.org/showthread.php?t=2231813

Hi Jeremy,

I'll unzip the package before copying into the home folder right?

```
mv: cannot stat ‘/lib/modules/3.13.0-44-generic/kernel/drivers/bluetooth/btusb.ko’: No such file or directory


```

Thank you

---

### Post by jeremy31 on 2015-01-25
> **polochamps said:**
> Hi Jeremy,

I'll unzip the package before copying into the home folder right?

```
mv: cannot stat ‘/lib/modules/3.13.0-44-generic/kernel/drivers/bluetooth/btusb.ko’: No such file or directory


```

Thank you

It is zipped?  If it is extract to home.  I wonder why you got the error```
ls /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
You might have already ran the command once

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> It is zipped?  If it is extract to home.  I wonder why you got the error```
ls /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
You might have already ran the command once

Yeah I think I had successfully ran the first command once but encountered this-

```
sudo cp btusb.ko  /lib/modules/$(uname-r)/kernel/drivers/bluetooth/
uname-r: command not found
cp: cannot create regular file ‘/lib/modules//kernel/drivers/bluetooth/’: No such file or directory

```

----------------------------------------------------------------------------------------------------------------------

```
ls /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
ath3k.ko    bluecard_cs.ko  btmrvl.ko       btuart_cs.ko  dtl1_cs.ko
bcm203x.ko  bpa10x.ko       btmrvl_sdio.ko  btusb.ko.bak  hci_uart.ko
bfusb.ko    bt3c_cs.ko      btsdio.ko       btwilink.ko   hci_vhci.ko


```


Thank you

---

### Post by jeremy31 on 2015-01-25
Must have missed part when I copied ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp btusb.ko  [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/lib/modules/3.13.0-44-generic/kernel/drivers/bluetooth/btusb.ko[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] unless the file is not in your current directory ```
ls | grep btusb
```[/FONT][/COLOR]

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> Must have missed part when I copied ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp btusb.ko  [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/lib/modules/3.13.0-44-generic/kernel/drivers/bluetooth/btusb.ko[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] unless the file is not in your current directory ```
ls | grep btusb
```[/FONT][/COLOR]

That missing part did the trick! The bluetooth icon appeared and scanned my bluetooth enabled devices but it disappeared after a reboot.

Thank you

---

### Post by jeremy31 on 2015-01-25
> **polochamps said:**
> That missing part did the trick! The bluetooth icon appeared and scanned my bluetooth enabled devices but it disappeared after a reboot.

Thank you
Lets see why ```
lsmod | grep bluetooth
``` and might as well check for errors ```
dmesg | grep -i bluetooth
```

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> Lets see why ```
lsmod | grep bluetooth
``` and might as well check for errors ```
dmesg | grep -i bluetooth
```

```
lsmod | grep bluetooth
bluetooth             391136  10 bnep,rfcomm


```

```
dmesg | grep -i bluetooth
[    8.533711] Bluetooth: Core ver 2.17
[    8.533722] Bluetooth: HCI device and connection manager initialized
[    8.533726] Bluetooth: HCI socket layer initialized
[    8.533727] Bluetooth: L2CAP socket layer initialized
[    8.533729] Bluetooth: SCO socket layer initialized
[    8.535112] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.535113] Bluetooth: BNEP filters: protocol multicast
[    8.535118] Bluetooth: BNEP socket layer initialized
[    8.537322] Bluetooth: RFCOMM TTY layer initialized
[    8.537328] Bluetooth: RFCOMM socket layer initialized
[    8.537330] Bluetooth: RFCOMM ver 1.11


```

---

### Post by jeremy31 on 2015-01-25
```
sudo modprobe -v btusb
``````
echo btusb | sudo tee -a /etc/modules
``````
dmesg | grep -e btusb -e patch
```

---

### Post by polochamps on 2015-01-25
Output from the last command.

> dmesg | grep -e btusb -e patch
[ 1520.141012] usbcore: registered new interface driver btusb

Will try to restart now.

---

### Post by polochamps on 2015-01-25
You nailed it Jeremy!!!

Thank you, Thank you and Thank you so much!!!

---

### Post by jeremy31 on 2015-01-25
There is one issue, when Ubuntu updates the kernel it will fail once again, but then we try something different that I found from searching a while ago, but don't try it before the kernel gets updated
```
echo "install btusb /sbin/modprobe --ignore-install btusb && echo '0b05 17cf' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up" | sudo tee /etc/modprobe.d/bcmbtusb.conf 
```

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> There is one issue, when Ubuntu updates the kernel it will fail once again, but then we try something different that I found from searching a while ago, but don't try it before the kernel gets updated
```
echo "install btusb /sbin/modprobe --ignore-install btusb && echo '0b05 17cf' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up" | sudo tee /etc/modprobe.d/bcmbtusb.conf 
```

Wow! That was advance!

My wireless module seems to be dodging this s***ty mess constantly
Wifi had this problem with the 14.10 and 15.04 kernels. It can detect APs but it wont connect, only here on 14.04 that it's running smoothly.

So far on my system (out of the box):

- 14.04 = Wifi = Yes and Bluetooth = No 
- 14.10 = Wifi = No and Bluetooth = No 
- 15.04 = Wifi = No and Bluetooth = Yes

Thank Jeremy! Many many thanks!

---

### Post by jeremy31 on 2015-01-25
> **polochamps said:**
> Wow! That was advance!

My wireless module seems to be dodging this s***ty mess constantly
Wifi had this problem with the 14.10 and 15.04 kernels. It can detect APs but it wont connect, only here on 14.04 that it's running smoothly.

So far on my system (out of the box):

- 14.04 = Wifi = Yes and Bluetooth = No 
- 14.10 = Wifi = No and Bluetooth = No 
- 15.04 = Wifi = No and Bluetooth = Yes

Thank Jeremy! Many many thanks!

Surprised 15.04 works with bluetooth as a patch was submitted to the linux-next github 4 days ago for that bluetooth
The wifi might need the updated version of bcmwl from [http://packages.ubuntu.com/vivid/bcmwl-kernel-source](http://packages.ubuntu.com/vivid/bcmwl-kernel-source) as it has the patch files for the newer kernels that 14.10 and 15.04 use

---

### Post by polochamps on 2015-01-25
> **jeremy31 said:**
> Surprised 15.04 works with bluetooth as a patch was submitted to the linux-next github 4 days ago for that bluetooth
The wifi might need the updated version of bcmwl from [http://packages.ubuntu.com/vivid/bcmwl-kernel-source](http://packages.ubuntu.com/vivid/bcmwl-kernel-source) as it has the patch files for the newer kernels that 14.10 and 15.04 use

Yeah I do hope that both would work on the upcoming kernel updates without the need for manual patches.
One thing I noticed on the forums is that these Broadcom wireless modules are the most problematic ones.

---

### Post by polochamps on 2015-02-08
You're right buddy, it's not working again with the kernel update.

> 3.13.0-45-generic



---

### Post by jeremy31 on 2015-02-08
This one should work.  I will see about making a dkms module so it survives the kernel updates

dkms version [https://www.dropbox.com/s/voo4ks1jw861gfw/bt-dkms_1.1_all.deb?dl=0](https://www.dropbox.com/s/voo4ks1jw861gfw/bt-dkms_1.1_all.deb?dl=0)

---

### Post by polochamps on 2015-02-08
I forgot to indicate that the bluetooth device is visible but the problem is it can't locate any of my bluetooth devices.
I have tried your new attachment but still the same result.

Thank you

---

### Post by polochamps on 2015-02-08
Mac address of my bluetooth module suddenly showed up on my tablet but can't  pair (also my PC device name didn't appear) and it took almost 10 minutes just to make the mac address appear on my tablet.
After a restart, now it's back to no detection.

Have tried the dkms version but still the same result.

Thank you

---

### Post by polochamps on 2015-02-08
Update:

My PC now detects my tablet but it's showing its mac address only and also took a bit of time to detect.
Still cant pair because it just stuck up on "searching for devices"

---

### Post by jeremy31 on 2015-02-08
Uninstall the dkms version,```
sudo dkms remove bt/1.1 --all
```  and ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko
```
reboot and run ```
dmesg | grep -e hcd -e firmware
```[/FONT][/COLOR]

---

### Post by polochamps on 2015-02-08
Still can't find devices.

> [    0.502375] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.515985] usb usb1: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    0.532013] usb usb2: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    0.532168] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.532175] uhci_hcd: USB Universal Host Controller Interface driver
[    0.532239] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.532242] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.532310] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.532322] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.532363] usb usb3: Manufacturer: Linux 3.13.0-45-generic xhci_hcd
[    0.534536] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.534539] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.534567] usb usb4: Manufacturer: Linux 3.13.0-45-generic xhci_hcd
[    1.315647] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[    1.499419] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.683311] usb 3-5: new low-speed USB device number 3 using xhci_hcd
[    1.815237] usb 3-6: new full-speed USB device number 4 using xhci_hcd
[    2.007120] usb 3-7: new full-speed USB device number 5 using xhci_hcd



---

### Post by jeremy31 on 2015-02-08
[https://www.dropbox.com/s/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd?dl=0](https://www.dropbox.com/s/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd?dl=0)
Hopefully copying it to /lib/firmware/brcm/ will get it functioning again after reboot

---

### Post by polochamps on 2015-02-15
Hi,

Still not working.
I apologize if it took me too long to confirm the result.

Thank you

> dmesg | grep -e hcd -e firmware

> [    0.502959] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.516167] usb usb1: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    0.532178] usb usb2: Manufacturer: Linux 3.13.0-45-generic ehci_hcd
[    0.532335] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.532342] uhci_hcd: USB Universal Host Controller Interface driver
[    0.532415] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.532418] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.532485] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.532497] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.532538] usb usb3: Manufacturer: Linux 3.13.0-45-generic xhci_hcd
[    0.534711] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.534713] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.534740] usb usb4: Manufacturer: Linux 3.13.0-45-generic xhci_hcd
[    1.375676] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.559568] usb 3-5: new low-speed USB device number 3 using xhci_hcd
[    1.691474] usb 3-6: new full-speed USB device number 4 using xhci_hcd
[    1.827400] usb 3-7: new full-speed USB device number 5 using xhci_hcd


---

### Post by jeremy31 on 2015-02-15
Lets see ```
dmesg | grep Bluetooth
```

---

### Post by polochamps on 2015-02-15
Here it is. Thanks!

> 
[    3.178810] Bluetooth: Core ver 2.17
[    3.178819] Bluetooth: HCI device and connection manager initialized
[    3.178823] Bluetooth: HCI socket layer initialized
[    3.178825] Bluetooth: L2CAP socket layer initialized
[    3.178827] Bluetooth: SCO socket layer initialized
[    3.579975] Bluetooth: RFCOMM TTY layer initialized
[    3.579981] Bluetooth: RFCOMM socket layer initialized
[    3.579983] Bluetooth: RFCOMM ver 1.11
[    3.580231] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.580232] Bluetooth: BNEP filters: protocol multicast
[    3.580236] Bluetooth: BNEP socket layer initialized



---

### Post by jeremy31 on 2015-02-15
Since I lost my home partition with 14.04, I am going to try to guide you through doing what I did.
```
[COLOR=#000000][FONT=Ubuntu Mono]mkdir ~/LINUX_SOURCE
[/FONT][/COLOR]cd ~/LINUX_SOURCE
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
cd linux-3.13.0/drivers/bluetooth/
```
Then ```
gedit btusb.c
``` at around line 105 you should see this```
[COLOR=#222222][FONT=Verdana]/* Broadcom BCM20702A0 */[/FONT][/COLOR]   
 { USB_DEVICE(0x0b05, 0x17b5) },
    { USB_DEVICE(0x0b05, 0x17cb) },
    { USB_DEVICE(0x04ca, 0x2003) },
    { USB_DEVICE(0x0489, 0xe042) },
    { USB_DEVICE(0x13d3, 0x3388), .driver_info = BTUSB_BCM_PATCHRAM },
    { USB_DEVICE(0x13d3, 0x3389), .driver_info = BTUSB_BCM_PATCHRAM },
    { USB_DEVICE(0x413c, 0x8197), .driver_info = BTUSB_BCM_PATCHRAM },
    { USB_DEVICE(0x413c, 0x8143), .driver_info = BTUSB_BCM_PATCHRAM },
```
you need to add ```
{ USB_DEVICE(0x0b05, 0x17cf) },
``` and I usually put it under the 0x0b05,0x17cb line, then make sure everything is aligned, a tab before adding is usually needed. then save and exit.  Then in terminal, hopefully you are still in the LINUX-SOURCE.....bluetooth directory then```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
``` ```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```  Hopefully it builds without error and you can use```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r btusb && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo mv /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/btusb.ko.bak[/FONT][/COLOR]
``````
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp btusb.ko  /lib/modules/$(uname -r)/kernel/drivers/bluetooth/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]```
sudo modprobe btusb
``` and hopefully it will work otherwise let me know as if it doesn't work we will need to 


[/FONT][/COLOR]```
make -C /lib/modules/$(uname -r)/build M=$PWD clean
``````
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
``` then edit btusb.c to change the added line to ```
 { USB_DEVICE(0x0b05, 0x17bf), .driver_info = BTUSB_BCM_PATCHRAM }, and then go through the [code]make -C /lib/modules/$(uname -r)/build M=$PWD modules
``` and then use the ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r btusb && [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]```
sudo modprobe btusb
```

You may need to rename the firmware to BCM20702A0-0b05-17bf.hcd to get it to work but it still should be in /lib/firmware/brcm[/FONT][/COLOR]

---

### Post by polochamps on 2015-02-15
Blank page on this
> gedit btusb.c

---

### Post by jeremy31 on 2015-02-15
Are you in ~/LINUX-SOURCE/[COLOR=#000000][FONT=Ubuntu Mono]linux-3.13.0/drivers/bluetooth/ when you try that command?[/FONT][/COLOR]

---

### Post by polochamps on 2015-02-15
Just this ~/LINUX-SOURCE/[COLOR=#000000][FONT=Ubuntu Mono]

When I checked there are also no files inside.
[/FONT][/COLOR]

---

### Post by jeremy31 on 2015-02-15
What do you see from ```
locate linux-3.13.0
```

---

### Post by polochamps on 2015-02-15
None. I wonder where it all go.

Here is the progress on termnal.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux' as source package instead of 'linux-image-3.13.0-45-generic'
The following NEW packages will be installed:
  asciidoc bison build-essential debhelper dh-apparmor docbook-dsssl
  docbook-utils docbook-xml docbook-xsl dpkg-dev flex g++ g++-4.8 gawk jadetex
  kernel-wedge libaudit-dev libbison-dev libdw-dev libdw1 libelf-dev
  libexpat1-dev libfl-dev libiberty-dev libnewt-dev libosp5 libostyle1c2
  libpci-dev libpng12-dev libptexenc1 libpython-dev libpython2.7-dev
  libsgmls-perl libsigsegv2 libslang2-dev libsp1c2 libstdc++-4.8-dev
  libunwind8 libunwind8-dev libxml2-utils luatex lynx lynx-cur m4 makedumpfile
  openjade po-debconf python-dev python2.7-dev sgml-data sgmlspl sharutils sp
  tex-common texlive-base texlive-binaries texlive-fonts-recommended
  texlive-generic-recommended texlive-latex-base texlive-latex-recommended
  tipa transfig xmlto xsltproc zlib1g-dev
0 upgraded, 65 newly installed, 0 to remove and 0 not upgraded.
Need to get 87.7 MB of archives.
After this operation, 250 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://ph.archive.ubuntu.com/ubuntu/ trusty/main m4 amd64 1.4.17-2ubuntu1 [195 kB]
Get:3 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libfl-dev amd64 2.5.35-10.1ubuntu2 [17.2 kB]
Get:4 http://ph.archive.ubuntu.com/ubuntu/ trusty/main flex amd64 2.5.35-10.1ubuntu2 [211 kB]
Get:5 http://ph.archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
1% [5 gawk 480 kB/781 kB 61%]                                 148 kB/s 91% [5 gawk 607 kB/781 kB 78%]                                 148 kB/s 91% [5 gawk 735 kB/781 kB 94%]                                 148 kB/s 91% [Working]                                                  148 kB/s 9                                                                        Get:6 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main libdw1 amd64 0.158-0ubuntu5.2 [174 kB]
1% [6 libdw1 1,167 B/174 kB 1%]                               148 kB/s 92% [6 libdw1 127 kB/174 kB 73%]                               148 kB/s 92% [Working]                                                  148 kB/s 9                                                                        Get:7 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libexpat1-dev amd64 2.1.0-4ubuntu1 [115 kB]
2% [7 libexpat1-dev 1,167 B/115 kB 1%]                        148 kB/s 92% [Working]                                                  148 kB/s 9                                                                        Get:8 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libpython2.7-dev amd64 2.7.6-8 [22.0 MB]
2% [8 libpython2.7-dev 1,165 B/22.0 MB 0%]                    148 kB/s 92% [8 libpython2.7-dev 127 kB/22.0 MB 1%]                     148 kB/s 92% [8 libpython2.7-dev 256 kB/22.0 MB 1%]                     148 kB/s 92% [8 libpython2.7-dev 382 kB/22.0 MB 2%]                     148 kB/s 92% [8 libpython2.7-dev 509 kB/22.0 MB 2%]                     148 kB/s 92% [8 libpython2.7-dev 635 kB/22.0 MB 3%]                     148 kB/s 93% [8 libpython2.7-dev 763 kB/22.0 MB 3%]                     148 kB/s 93% [8 libpython2.7-dev 889 kB/22.0 MB 4%]                     245 kB/s 53% [8 libpython2.7-dev 1,015 kB/22.0 MB 5%]                   245 kB/s 53% [8 libpython2.7-dev 1,142 kB/22.0 MB 5%]                   245 kB/s 53% [8 libpython2.7-dev 1,268 kB/22.0 MB 6%]                   245 kB/s 53% [8 libpython2.7-dev 1,394 kB/22.0 MB 6%]                   245 kB/s 53% [8 libpython2.7-dev 1,520 kB/22.0 MB 7%]                   245 kB/s 54% [8 libpython2.7-dev 1,646 kB/22.0 MB 7%]                   245 kB/s 54% [8 libpython2.7-dev 1,772 kB/22.0 MB 8%]                   245 kB/s 54% [8 libpython2.7-dev 1,900 kB/22.0 MB 9%]                   245 kB/s 54% [8 libpython2.7-dev 2,027 kB/22.0 MB 9%]                   245 kB/s 54% [8 libpython2.7-dev 2,152 kB/22.0 MB 10%]                  245 kB/s 54% [8 libpython2.7-dev 2,278 kB/22.0 MB 10%]                  245 kB/s 54% [8 libpython2.7-dev 2,401 kB/22.0 MB 11%]                  252 kB/s 55% [8 libpython2.7-dev 2,527 kB/22.0 MB 11%]                  252 kB/s 55% [8 libpython2.7-dev 2,646 kB/22.0 MB 12%]                  252 kB/s 55% [8 libpython2.7-dev 2,770 kB/22.0 MB 13%]                  252 kB/s 55% [8 libpython2.7-dev 2,896 kB/22.0 MB 13%]                  252 kB/s 55% [8 libpython2.7-dev 3,022 kB/22.0 MB 14%]                  252 kB/s 55% [8 libpython2.7-dev 3,148 kB/22.0 MB 14%]                  252 kB/s 55% [8 libpython2.7-dev 3,276 kB/22.0 MB 15%]                  252 kB/s 56% [8 libpython2.7-dev 3,402 kB/22.0 MB 15%]                  252 kB/s 56% [8 libpython2.7-dev 3,528 kB/22.0 MB 16%]                  252 kB/s 56% [8 libpython2.7-dev 3,654 kB/22.0 MB 17%]                  252 kB/s 56% [8 libpython2.7-dev 3,780 kB/22.0 MB 17%]                  252 kB/s 56% [8 libpython2.7-dev 3,906 kB/22.0 MB 18%]                  251 kB/s 56% [8 libpython2.7-dev 4,032 kB/22.0 MB 18%]                  251 kB/s 56% [8 libpython2.7-dev 4,156 kB/22.0 MB 19%]                  251 kB/s 57% [8 libpython2.7-dev 4,282 kB/22.0 MB 19%]                  251 kB/s 57% [8 libpython2.7-dev 4,408 kB/22.0 MB 20%]                  251 kB/s 57% [8 libpython2.7-dev 4,534 kB/22.0 MB 21%]                  251 kB/s 57% [8 libpython2.7-dev 4,659 kB/22.0 MB 21%]                  251 kB/s 57% [8 libpython2.7-dev 4,786 kB/22.0 MB 22%]                  251 kB/s 57% [8 libpython2.7-dev 4,802 kB/22.0 MB 22%]                  251 kB/s 57% [8 libpython2.7-dev 4,802 kB/22.0 MB 22%]                  251 kB/s 57% [8 libpython2.7-dev 4,802 kB/22.0 MB 22%]                  251 kB/s 57% [8 libpython2.7-dev 4,802 kB/22.0 MB 22%]                  251 kB/s 57% [8 libpython2.7-dev 4,802 kB/22.0 MB 22%]                   149 kB/s 7% [8 libpython2.7-dev 4,868 kB/22.0 MB 22%]                   149 kB/s 8% [8 libpython2.7-dev 5,079 kB/22.0 MB 23%]                   149 kB/s 8% [8 libpython2.7-dev 5,349 kB/22.0 MB 24%]                   149 kB/s 8% [8 libpython2.7-dev 5,484 kB/22.0 MB 25%]                   149 kB/s 8% [8 libpython2.7-dev 5,603 kB/22.0 MB 25%]                   149 kB/s 9% [8 libpython2.7-dev 6,165 kB/22.0 MB 28%]                  149 kB/s 89% [8 libpython2.7-dev 6,293 kB/22.0 MB 29%]                  149 kB/s 89% [8 libpython2.7-dev 6,420 kB/22.0 MB 29%]                  149 kB/s 89% [8 libpython2.7-dev 6,532 kB/22.0 MB 30%]                  149 kB/s 89% [8 libpython2.7-dev 6,655 kB/22.0 MB 30%]                  149 kB/s 89% [8 libpython2.7-dev 6,783 kB/22.0 MB 31%]                  149 kB/s 810% [8 libpython2.7-dev 6,907 kB/22.0 MB 31%]                 351 kB/s 310% [8 libpython2.7-dev 7,035 kB/22.0 MB 32%]                 351 kB/s 310% [8 libpython2.7-dev 7,159 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,250 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,250 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,250 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,250 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,250 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,250 kB/22.0 MB 33%]                 351 kB/s 310% [8 libpython2.7-dev 7,430 kB/22.0 MB 34%]                 351 kB/s 310% [8 libpython2.7-dev 7,659 kB/22.0 MB 35%]                 351 kB/s 311% [8 libpython2.7-dev 7,854 kB/22.0 MB 36%]                 351 kB/s 311% [8 libpython2.7-dev 7,978 kB/22.0 MB 36%]                 178 kB/s 711% [8 libpython2.7-dev 8,545 kB/22.0 MB 39%]                 178 kB/s 712% [8 libpython2.7-dev 8,671 kB/22.0 MB 39%]                 178 kB/s 712% [8 libpython2.7-dev 8,797 kB/22.0 MB 40%]                 178 kB/s 712% [8 libpython2.7-dev 8,923 kB/22.0 MB 41%]                 178 kB/s 712% [8 libpython2.7-dev 9,049 kB/22.0 MB 41%]                 178 kB/s 712% [8 libpython2.7-dev 9,175 kB/22.0 MB 42%]                 178 kB/s 712% [8 libpython2.7-dev 9,303 kB/22.0 MB 42%]                 178 kB/s 712% [8 libpython2.7-dev 9,427 kB/22.0 MB 43%]                 178 kB/s 713% [8 libpython2.7-dev 9,555 kB/22.0 MB 43%]                  178 kB/s 13% [8 libpython2.7-dev 9,681 kB/22.0 MB 44%]                  178 kB/s 13% [8 libpython2.7-dev 9,804 kB/22.0 MB 45%]                  178 kB/s 13% [8 libpython2.7-dev 9,930 kB/22.0 MB 45%]                 325 kB/s 313% [8 libpython2.7-dev 10.1 MB/22.0 MB 46%]                  325 kB/s 313% [8 libpython2.7-dev 10.2 MB/22.0 MB 46%]                  325 kB/s 313% [8 libpython2.7-dev 10.3 MB/22.0 MB 47%]                  325 kB/s 314% [8 libpython2.7-dev 10.4 MB/22.0 MB 47%]                  325 kB/s 314% [8 libpython2.7-dev 10.6 MB/22.0 MB 48%]                  325 kB/s 314% [8 libpython2.7-dev 10.7 MB/22.0 MB 49%]                  325 kB/s 314% [8 libpython2.7-dev 10.8 MB/22.0 MB 49%]                  325 kB/s 314% [8 libpython2.7-dev 10.9 MB/22.0 MB 50%]                  325 kB/s 314% [8 libpython2.7-dev 11.1 MB/22.0 MB 50%]                  325 kB/s 314% [8 libpython2.7-dev 11.2 MB/22.0 MB 51%]                  325 kB/s 315% [8 libpython2.7-dev 11.3 MB/22.0 MB 51%]                  325 kB/s 315% [8 libpython2.7-dev 11.4 MB/22.0 MB 52%]                  251 kB/s 415% [8 libpython2.7-dev 11.6 MB/22.0 MB 53%]                  251 kB/s 415% [8 libpython2.7-dev 11.7 MB/22.0 MB 53%]                  251 kB/s 415% [8 libpython2.7-dev 11.8 MB/22.0 MB 54%]                  251 kB/s 415% [8 libpython2.7-dev 11.9 MB/22.0 MB 54%]                  251 kB/s 415% [8 libpython2.7-dev 12.1 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.2 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.2 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.2 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.2 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.2 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.2 MB/22.0 MB 55%]                  251 kB/s 416% [8 libpython2.7-dev 12.3 MB/22.0 MB 56%]                  138 kB/s 816% [8 libpython2.7-dev 12.5 MB/22.0 MB 57%]                  138 kB/s 816% [8 libpython2.7-dev 12.7 MB/22.0 MB 58%]                  138 kB/s 816% [8 libpython2.7-dev 12.9 MB/22.0 MB 58%]                  138 kB/s 817% [8 libpython2.7-dev 13.0 MB/22.0 MB 59%]                  138 kB/s 817% [8 libpython2.7-dev 13.6 MB/22.0 MB 62%]                  138 kB/s 817% [8 libpython2.7-dev 13.7 MB/22.0 MB 62%]                  138 kB/s 818% [8 libpython2.7-dev 13.8 MB/22.0 MB 63%]                  138 kB/s 818% [8 libpython2.7-dev 14.0 MB/22.0 MB 63%]                  138 kB/s 818% [8 libpython2.7-dev 14.1 MB/22.0 MB 64%]                  138 kB/s 818% [8 libpython2.7-dev 14.2 MB/22.0 MB 65%]                  138 kB/s 818% [8 libpython2.7-dev 14.3 MB/22.0 MB 65%]                  138 kB/s 818% [8 libpython2.7-dev 14.5 MB/22.0 MB 66%]                  366 kB/s 318% [8 libpython2.7-dev 14.6 MB/22.0 MB 66%]                  366 kB/s 319% [8 libpython2.7-dev 14.7 MB/22.0 MB 67%]                  366 kB/s 319% [8 libpython2.7-dev 14.8 MB/22.0 MB 67%]                  366 kB/s 319% [8 libpython2.7-dev 15.0 MB/22.0 MB 68%]                  366 kB/s 319% [8 libpython2.7-dev 15.1 MB/22.0 MB 69%]                  366 kB/s 319% [8 libpython2.7-dev 15.2 MB/22.0 MB 69%]                  366 kB/s 319% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  366 kB/s 319% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  366 kB/s 319% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  366 kB/s 319% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  366 kB/s 319% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  366 kB/s 319% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  158 kB/s 719% [8 libpython2.7-dev 15.4 MB/22.0 MB 70%]                  158 kB/s 719% [8 libpython2.7-dev 15.6 MB/22.0 MB 71%]                  158 kB/s 720% [8 libpython2.7-dev 15.8 MB/22.0 MB 72%]                  158 kB/s 720% [8 libpython2.7-dev 16.0 MB/22.0 MB 73%]                  158 kB/s 720% [8 libpython2.7-dev 16.1 MB/22.0 MB 73%]                  158 kB/s 721% [8 libpython2.7-dev 16.7 MB/22.0 MB 76%]                  158 kB/s 721% [8 libpython2.7-dev 16.9 MB/22.0 MB 77%]                  158 kB/s 721% [8 libpython2.7-dev 17.0 MB/22.0 MB 77%]                  158 kB/s 721% [8 libpython2.7-dev 17.1 MB/22.0 MB 78%]                  158 kB/s 721% [8 libpython2.7-dev 17.2 MB/22.0 MB 78%]                  158 kB/s 722% [8 libpython2.7-dev 17.4 MB/22.0 MB 79%]                  158 kB/s 722% [8 libpython2.7-dev 17.5 MB/22.0 MB 79%]                  345 kB/s 322% [8 libpython2.7-dev 17.6 MB/22.0 MB 80%]                  345 kB/s 322% [8 libpython2.7-dev 17.7 MB/22.0 MB 81%]                  345 kB/s 322% [8 libpython2.7-dev 17.9 MB/22.0 MB 81%]                  345 kB/s 322% [8 libpython2.7-dev 18.0 MB/22.0 MB 82%]                  345 kB/s 322% [8 libpython2.7-dev 18.1 MB/22.0 MB 82%]                  345 kB/s 323% [8 libpython2.7-dev 18.2 MB/22.0 MB 83%]                  345 kB/s 323% [8 libpython2.7-dev 18.4 MB/22.0 MB 83%]                  345 kB/s 323% [8 libpython2.7-dev 18.5 MB/22.0 MB 84%]                  345 kB/s 323% [8 libpython2.7-dev 18.6 MB/22.0 MB 85%]                  345 kB/s 323% [8 libpython2.7-dev 18.7 MB/22.0 MB 85%]                  345 kB/s 323% [8 libpython2.7-dev 18.9 MB/22.0 MB 86%]                  345 kB/s 323% [8 libpython2.7-dev 19.0 MB/22.0 MB 86%]                  251 kB/s 424% [8 libpython2.7-dev 19.1 MB/22.0 MB 87%]                  251 kB/s 424% [8 libpython2.7-dev 19.3 MB/22.0 MB 87%]                  251 kB/s 424% [8 libpython2.7-dev 19.4 MB/22.0 MB 88%]                  251 kB/s 424% [8 libpython2.7-dev 19.5 MB/22.0 MB 89%]                  251 kB/s 424% [8 libpython2.7-dev 19.6 MB/22.0 MB 89%]                  251 kB/s 424% [8 libpython2.7-dev 19.8 MB/22.0 MB 90%]                  251 kB/s 424% [8 libpython2.7-dev 19.9 MB/22.0 MB 90%]                  251 kB/s 425% [8 libpython2.7-dev 20.0 MB/22.0 MB 91%]                  251 kB/s 425% [8 libpython2.7-dev 20.1 MB/22.0 MB 91%]                  251 kB/s 425% [8 libpython2.7-dev 20.3 MB/22.0 MB 92%]                  251 kB/s 425% [8 libpython2.7-dev 20.4 MB/22.0 MB 93%]                  251 kB/s 425% [8 libpython2.7-dev 20.5 MB/22.0 MB 93%]                  252 kB/s 425% [8 libpython2.7-dev 20.6 MB/22.0 MB 94%]                  252 kB/s 425% [8 libpython2.7-dev 20.8 MB/22.0 MB 94%]                  252 kB/s 426% [8 libpython2.7-dev 20.9 MB/22.0 MB 95%]                  252 kB/s 426% [8 libpython2.7-dev 21.0 MB/22.0 MB 96%]                  252 kB/s 426% [8 libpython2.7-dev 21.1 MB/22.0 MB 96%]                  252 kB/s 426% [8 libpython2.7-dev 21.3 MB/22.0 MB 97%]                  252 kB/s 426% [8 libpython2.7-dev 21.4 MB/22.0 MB 97%]                  252 kB/s 426% [8 libpython2.7-dev 21.5 MB/22.0 MB 98%]                  252 kB/s 426% [8 libpython2.7-dev 21.6 MB/22.0 MB 98%]                  252 kB/s 426% [8 libpython2.7-dev 21.7 MB/22.0 MB 99%]                  252 kB/s 426% [8 libpython2.7-dev 21.7 MB/22.0 MB 99%]                  252 kB/s 427% [Working]                                                 252 kB/s 4                                                                        Get:9 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libunwind8 amd64 1.1-2.2ubuntu3 [48.3 kB]
27% [9 libunwind8 1,168 B/48.3 kB 2%]                         247 kB/s 427% [Working]                                                 247 kB/s 4                                                                        Get:10 http://ph.archive.ubuntu.com/ubuntu/ trusty/main asciidoc all 8.6.9-2ubuntu1 [688 kB]
27% [10 asciidoc 1,167 B/688 kB 0%]                           247 kB/s 427% [10 asciidoc 129 kB/688 kB 19%]                           247 kB/s 427% [10 asciidoc 256 kB/688 kB 37%]                           247 kB/s 427% [10 asciidoc 383 kB/688 kB 56%]                           247 kB/s 427% [10 asciidoc 511 kB/688 kB 74%]                           247 kB/s 428% [10 asciidoc 638 kB/688 kB 93%]                           247 kB/s 428% [Working]                                                 247 kB/s 4                                                                        Get:11 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libbison-dev amd64 2:3.0.2.dfsg-2 [338 kB]
28% [11 libbison-dev 1,167 B/338 kB 0%]                       247 kB/s 428% [11 libbison-dev 129 kB/338 kB 38%]                       247 kB/s 428% [11 libbison-dev 256 kB/338 kB 76%]                       247 kB/s 428% [Working]                                                 247 kB/s 4                                                                        Get:12 http://ph.archive.ubuntu.com/ubuntu/ trusty/main bison amd64 2:3.0.2.dfsg-2 [257 kB]
28% [12 bison 1,167 B/257 kB 0%]                              247 kB/s 428% [12 bison 129 kB/257 kB 50%]                              247 kB/s 428% [Working]                                                 247 kB/s 4                                                                        Get:13 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libstdc++-4.8-dev amd64 4.8.2-19ubuntu1 [1,050 kB]
28% [13 libstdc++-4.8-dev 1,166 B/1,050 kB 0%]                247 kB/s 428% [13 libstdc++-4.8-dev 129 kB/1,050 kB 12%]                241 kB/s 429% [13 libstdc++-4.8-dev 256 kB/1,050 kB 24%]                241 kB/s 429% [13 libstdc++-4.8-dev 382 kB/1,050 kB 36%]                241 kB/s 429% [13 libstdc++-4.8-dev 501 kB/1,050 kB 48%]                241 kB/s 429% [13 libstdc++-4.8-dev 624 kB/1,050 kB 59%]                241 kB/s 429% [13 libstdc++-4.8-dev 750 kB/1,050 kB 71%]                241 kB/s 429% [13 libstdc++-4.8-dev 873 kB/1,050 kB 83%]                241 kB/s 429% [13 libstdc++-4.8-dev 990 kB/1,050 kB 94%]                241 kB/s 430% [Working]                                                 241 kB/s 4                                                                        Get:14 http://ph.archive.ubuntu.com/ubuntu/ trusty/main g++-4.8 amd64 4.8.2-19ubuntu1 [7,038 kB]
30% [14 g++-4.8 1,166 B/7,038 kB 0%]                          241 kB/s 430% [14 g++-4.8 129 kB/7,038 kB 2%]                           241 kB/s 430% [14 g++-4.8 249 kB/7,038 kB 4%]                           241 kB/s 430% [14 g++-4.8 375 kB/7,038 kB 5%]                           241 kB/s 430% [14 g++-4.8 501 kB/7,038 kB 7%]                           241 kB/s 430% [14 g++-4.8 627 kB/7,038 kB 9%]                           244 kB/s 430% [14 g++-4.8 750 kB/7,038 kB 11%]                          244 kB/s 431% [14 g++-4.8 875 kB/7,038 kB 12%]                           244 kB/s 31% [14 g++-4.8 1,002 kB/7,038 kB 14%]                         244 kB/s 31% [14 g++-4.8 1,128 kB/7,038 kB 16%]                         244 kB/s 31% [14 g++-4.8 1,251 kB/7,038 kB 18%]                         244 kB/s 31% [14 g++-4.8 1,375 kB/7,038 kB 20%]                         244 kB/s 31% [14 g++-4.8 1,502 kB/7,038 kB 21%]                         244 kB/s 31% [14 g++-4.8 1,607 kB/7,038 kB 23%]                         244 kB/s 31% [14 g++-4.8 1,722 kB/7,038 kB 24%]                         244 kB/s 32% [14 g++-4.8 1,835 kB/7,038 kB 26%]                         244 kB/s 32% [14 g++-4.8 1,961 kB/7,038 kB 28%]                         244 kB/s 32% [14 g++-4.8 2,090 kB/7,038 kB 30%]                         244 kB/s 32% [14 g++-4.8 2,216 kB/7,038 kB 31%]                         244 kB/s 32% [14 g++-4.8 2,338 kB/7,038 kB 33%]                         244 kB/s 32% [14 g++-4.8 2,464 kB/7,038 kB 35%]                         244 kB/s 32% [14 g++-4.8 2,590 kB/7,038 kB 37%]                         244 kB/s 33% [14 g++-4.8 2,716 kB/7,038 kB 39%]                         244 kB/s 33% [14 g++-4.8 2,842 kB/7,038 kB 40%]                         244 kB/s 33% [14 g++-4.8 2,968 kB/7,038 kB 42%]                         244 kB/s 33% [14 g++-4.8 3,097 kB/7,038 kB 44%]                         244 kB/s 33% [14 g++-4.8 3,223 kB/7,038 kB 46%]                         244 kB/s 33% [14 g++-4.8 3,349 kB/7,038 kB 48%]                        244 kB/s 333% [14 g++-4.8 3,475 kB/7,038 kB 49%]                        244 kB/s 334% [14 g++-4.8 3,601 kB/7,038 kB 51%]                        251 kB/s 334% [14 g++-4.8 3,728 kB/7,038 kB 53%]                        251 kB/s 334% [14 g++-4.8 3,854 kB/7,038 kB 55%]                        251 kB/s 334% [14 g++-4.8 3,980 kB/7,038 kB 57%]                        251 kB/s 334% [14 g++-4.8 4,106 kB/7,038 kB 58%]                        251 kB/s 334% [14 g++-4.8 4,233 kB/7,038 kB 60%]                        251 kB/s 335% [14 g++-4.8 4,361 kB/7,038 kB 62%]                        251 kB/s 335% [14 g++-4.8 4,487 kB/7,038 kB 64%]                        251 kB/s 335% [14 g++-4.8 4,613 kB/7,038 kB 66%]                        251 kB/s 335% [14 g++-4.8 4,739 kB/7,038 kB 67%]                        251 kB/s 335% [14 g++-4.8 4,865 kB/7,038 kB 69%]                        251 kB/s 335% [14 g++-4.8 4,991 kB/7,038 kB 71%]                        251 kB/s 335% [14 g++-4.8 5,043 kB/7,038 kB 72%]                        240 kB/s 335% [14 g++-4.8 5,043 kB/7,038 kB 72%]                        240 kB/s 335% [14 g++-4.8 5,043 kB/7,038 kB 72%]                        240 kB/s 335% [14 g++-4.8 5,043 kB/7,038 kB 72%]                        240 kB/s 335% [14 g++-4.8 5,043 kB/7,038 kB 72%]                        240 kB/s 335% [14 g++-4.8 5,043 kB/7,038 kB 72%]                        240 kB/s 335% [14 g++-4.8 5,227 kB/7,038 kB 74%]                        240 kB/s 336% [14 g++-4.8 5,447 kB/7,038 kB 77%]                        240 kB/s 336% [14 g++-4.8 5,703 kB/7,038 kB 81%]                        240 kB/s 336% [14 g++-4.8 5,831 kB/7,038 kB 83%]                        240 kB/s 336% [14 g++-4.8 5,953 kB/7,038 kB 85%]                        240 kB/s 337% [14 g++-4.8 6,504 kB/7,038 kB 92%]                        240 kB/s 337% [14 g++-4.8 6,632 kB/7,038 kB 94%]                        265 kB/s 337% [14 g++-4.8 6,758 kB/7,038 kB 96%]                        265 kB/s 337% [14 g++-4.8 6,884 kB/7,038 kB 98%]                        265 kB/s 338% [14 g++-4.8 7,010 kB/7,038 kB 100%]                       265 kB/s 338% [Working]                                                 265 kB/s 3                                                                        Get:15 http://ph.archive.ubuntu.com/ubuntu/ trusty/main g++ amd64 4:4.8.2-1ubuntu6 [1,490 B]
38% [15 g++ 1,490 B/1,490 B 100%]                             265 kB/s 338% [Working]                                                 265 kB/s 3                                                                        Get:16 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main dpkg-dev all 1.17.5ubuntu5.3 [726 kB]
38% [16 dpkg-dev 1,167 B/726 kB 0%]                           265 kB/s 338% [16 dpkg-dev 116 kB/726 kB 16%]                           265 kB/s 338% [16 dpkg-dev 242 kB/726 kB 33%]                           265 kB/s 338% [16 dpkg-dev 369 kB/726 kB 51%]                           265 kB/s 338% [16 dpkg-dev 497 kB/726 kB 68%]                           265 kB/s 338% [16 dpkg-dev 624 kB/726 kB 86%]                           265 kB/s 338% [Working]                                                 265 kB/s 3                                                                        Get:17 http://ph.archive.ubuntu.com/ubuntu/ trusty/main build-essential amd64 11.6ubuntu6 [4,838 B]
38% [17 build-essential 1,169 B/4,838 B 24%]                  265 kB/s 338% [Working]                                                 265 kB/s 3                                                                        Get:18 http://ph.archive.ubuntu.com/ubuntu/ trusty/main po-debconf all 1.0.16+nmu2ubuntu1 [210 kB]
38% [18 po-debconf 1,167 B/210 kB 1%]                         265 kB/s 338% [18 po-debconf 76.8 kB/210 kB 37%]                        265 kB/s 339% [Working]                                                 265 kB/s 3                                                                        Get:19 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main dh-apparmor all 2.8.95~2430-0ubuntu5.1 [11.5 kB]
39% [19 dh-apparmor 1,168 B/11.5 kB 10%]                      265 kB/s 339% [Working]                                                 265 kB/s 3                                                                        Get:20 http://ph.archive.ubuntu.com/ubuntu/ trusty/main debhelper all 9.20131227ubuntu1 [604 kB]
39% [20 debhelper 1,167 B/604 kB 0%]                          265 kB/s 339% [20 debhelper 129 kB/604 kB 21%]                          230 kB/s 339% [20 debhelper 255 kB/604 kB 42%]                          230 kB/s 339% [20 debhelper 382 kB/604 kB 63%]                          230 kB/s 339% [20 debhelper 509 kB/604 kB 84%]                          230 kB/s 339% [Working]                                                 230 kB/s 3                                                                        Get:21 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libosp5 amd64 1.5.2-10ubuntu3 [590 kB]
39% [21 libosp5 1,167 B/590 kB 0%]                            230 kB/s 339% [21 libosp5 129 kB/590 kB 22%]                            230 kB/s 340% [21 libosp5 256 kB/590 kB 43%]                            230 kB/s 340% [21 libosp5 374 kB/590 kB 63%]                            230 kB/s 340% [21 libosp5 501 kB/590 kB 85%]                            230 kB/s 340% [Working]                                                 230 kB/s 3                                                                        Get:22 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libostyle1c2 amd64 1.4devel1-21 [828 kB]
40% [22 libostyle1c2 1,167 B/828 kB 0%]                       230 kB/s 340% [22 libostyle1c2 129 kB/828 kB 16%]                       230 kB/s 340% [22 libostyle1c2 256 kB/828 kB 31%]                       230 kB/s 340% [22 libostyle1c2 379 kB/828 kB 46%]                       230 kB/s 341% [22 libostyle1c2 507 kB/828 kB 61%]                       245 kB/s 341% [22 libostyle1c2 631 kB/828 kB 76%]                       245 kB/s 341% [22 libostyle1c2 759 kB/828 kB 92%]                       245 kB/s 341% [Working]                                                 245 kB/s 3                                                                        Get:23 http://ph.archive.ubuntu.com/ubuntu/ trusty/main openjade amd64 1.4devel1-21 [307 kB]
41% [23 openjade 1,167 B/307 kB 0%]                           245 kB/s 341% [23 openjade 129 kB/307 kB 42%]                           245 kB/s 341% [23 openjade 256 kB/307 kB 83%]                           245 kB/s 341% [Working]                                                 245 kB/s 3                                                                        Get:24 http://ph.archive.ubuntu.com/ubuntu/ trusty/main sgml-data all 2.0.9-1 [277 kB]
41% [24 sgml-data 1,167 B/277 kB 0%]                          245 kB/s 341% [24 sgml-data 129 kB/277 kB 46%]                          245 kB/s 342% [24 sgml-data 256 kB/277 kB 92%]                          245 kB/s 342% [Working]                                                 245 kB/s 3                                                                        Get:25 http://ph.archive.ubuntu.com/ubuntu/ trusty/main docbook-xml all 4.5-7.2 [336 kB]
42% [25 docbook-xml 1,167 B/336 kB 0%]                        245 kB/s 342% [25 docbook-xml 129 kB/336 kB 38%]                        245 kB/s 342% [25 docbook-xml 256 kB/336 kB 76%]                        245 kB/s 342% [25 docbook-xml 334 kB/336 kB 100%]                       245 kB/s 342% [Working]                                                 245 kB/s 3                                                                        Get:26 http://ph.archive.ubuntu.com/ubuntu/ trusty/main docbook-dsssl all 1.79-7ubuntu1 [350 kB]
42% [26 docbook-dsssl 1,167 B/350 kB 0%]                      245 kB/s 342% [26 docbook-dsssl 129 kB/350 kB 37%]                      223 kB/s 342% [26 docbook-dsssl 256 kB/350 kB 73%]                      223 kB/s 342% [Working]                                                 223 kB/s 3                                                                        Get:27 http://ph.archive.ubuntu.com/ubuntu/ trusty/main tex-common all 4.04 [621 kB]
42% [27 tex-common 1,167 B/621 kB 0%]                         223 kB/s 343% [27 tex-common 129 kB/621 kB 21%]                         223 kB/s 343% [27 tex-common 256 kB/621 kB 41%]                         223 kB/s 343% [27 tex-common 383 kB/621 kB 62%]                         223 kB/s 343% [27 tex-common 511 kB/621 kB 82%]                         223 kB/s 343% [Working]                                                 223 kB/s 3                                                                        Get:28 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libptexenc1 amd64 2013.20130729.30972-2build3 [33.9 kB]
43% [28 libptexenc1 1,168 B/33.9 kB 3%]                       223 kB/s 343% [Working]                                                 223 kB/s 3                                                                        Get:29 http://ph.archive.ubuntu.com/ubuntu/ trusty/main texlive-binaries amd64 2013.20130729.30972-2build3 [4,059 kB]
43% [29 texlive-binaries 1,166 B/4,059 kB 0%]                 223 kB/s 343% [29 texlive-binaries 129 kB/4,059 kB 3%]                  223 kB/s 343% [29 texlive-binaries 252 kB/4,059 kB 6%]                  223 kB/s 344% [29 texlive-binaries 379 kB/4,059 kB 9%]                  223 kB/s 344% [29 texlive-binaries 505 kB/4,059 kB 12%]                 223 kB/s 344% [29 texlive-binaries 631 kB/4,059 kB 16%]                 245 kB/s 344% [29 texlive-binaries 756 kB/4,059 kB 19%]                 245 kB/s 344% [29 texlive-binaries 882 kB/4,059 kB 22%]                 245 kB/s 344% [29 texlive-binaries 1,008 kB/4,059 kB 25%]               245 kB/s 344% [29 texlive-binaries 1,132 kB/4,059 kB 28%]               245 kB/s 345% [29 texlive-binaries 1,256 kB/4,059 kB 31%]               245 kB/s 345% [29 texlive-binaries 1,382 kB/4,059 kB 34%]               245 kB/s 345% [29 texlive-binaries 1,506 kB/4,059 kB 37%]               245 kB/s 345% [29 texlive-binaries 1,632 kB/4,059 kB 40%]               245 kB/s 345% [29 texlive-binaries 1,758 kB/4,059 kB 43%]               245 kB/s 345% [29 texlive-binaries 1,884 kB/4,059 kB 46%]               245 kB/s 345% [29 texlive-binaries 2,005 kB/4,059 kB 49%]               245 kB/s 346% [29 texlive-binaries 2,131 kB/4,059 kB 52%]               250 kB/s 346% [29 texlive-binaries 2,257 kB/4,059 kB 56%]               250 kB/s 346% [29 texlive-binaries 2,376 kB/4,059 kB 59%]               250 kB/s 346% [29 texlive-binaries 2,497 kB/4,059 kB 62%]                250 kB/s 46% [29 texlive-binaries 2,621 kB/4,059 kB 65%]                250 kB/s 46% [29 texlive-binaries 2,745 kB/4,059 kB 68%]                250 kB/s 46% [29 texlive-binaries 2,846 kB/4,059 kB 70%]                250 kB/s 47% [29 texlive-binaries 2,955 kB/4,059 kB 73%]                250 kB/s 47% [29 texlive-binaries 3,083 kB/4,059 kB 76%]                250 kB/s 47% [29 texlive-binaries 3,209 kB/4,059 kB 79%]                250 kB/s 47% [29 texlive-binaries 3,333 kB/4,059 kB 82%]                250 kB/s 47% [29 texlive-binaries 3,458 kB/4,059 kB 85%]                250 kB/s 47% [29 texlive-binaries 3,563 kB/4,059 kB 88%]               238 kB/s 347% [29 texlive-binaries 3,573 kB/4,059 kB 88%]               238 kB/s 347% [29 texlive-binaries 3,573 kB/4,059 kB 88%]               238 kB/s 347% [29 texlive-binaries 3,573 kB/4,059 kB 88%]               238 kB/s 348% [29 texlive-binaries 3,909 kB/4,059 kB 96%]               238 kB/s 348% [29 texlive-binaries 4,057 kB/4,059 kB 100%]              238 kB/s 348% [29 texlive-binaries 4,057 kB/4,059 kB 100%]              238 kB/s 348% [29 texlive-binaries 4,057 kB/4,059 kB 100%]              238 kB/s 348% [Working]                                                 238 kB/s 3                                                                        Get:30 http://ph.archive.ubuntu.com/ubuntu/ trusty/main luatex amd64 0.76.0-3ubuntu1 [2,776 kB]
48% [30 luatex 0 B/2,776 kB 0%]                               238 kB/s 348% [30 luatex 119 kB/2,776 kB 4%]                            238 kB/s 348% [30 luatex 229 kB/2,776 kB 8%]                            238 kB/s 348% [30 luatex 361 kB/2,776 kB 13%]                           238 kB/s 348% [30 luatex 486 kB/2,776 kB 17%]                           238 kB/s 348% [30 luatex 610 kB/2,776 kB 22%]                           176 kB/s 449% [30 luatex 735 kB/2,776 kB 26%]                           176 kB/s 449% [30 luatex 861 kB/2,776 kB 31%]                           176 kB/s 449% [30 luatex 977 kB/2,776 kB 35%]                           176 kB/s 449% [30 luatex 1,095 kB/2,776 kB 39%]                         176 kB/s 449% [30 luatex 1,216 kB/2,776 kB 44%]                         176 kB/s 449% [30 luatex 1,340 kB/2,776 kB 48%]                         176 kB/s 449% [30 luatex 1,456 kB/2,776 kB 52%]                         176 kB/s 450% [30 luatex 1,551 kB/2,776 kB 56%]                         176 kB/s 450% [30 luatex 1,648 kB/2,776 kB 59%]                         176 kB/s 450% [30 luatex 1,774 kB/2,776 kB 64%]                         176 kB/s 450% [30 luatex 1,880 kB/2,776 kB 68%]                          176 kB/s 50% [30 luatex 2,024 kB/2,776 kB 73%]                          235 kB/s 50% [30 luatex 2,150 kB/2,776 kB 77%]                          235 kB/s 50% [30 luatex 2,278 kB/2,776 kB 82%]                          235 kB/s 51% [30 luatex 2,399 kB/2,776 kB 86%]                          235 kB/s 51% [30 luatex 2,523 kB/2,776 kB 91%]                          235 kB/s 51% [30 luatex 2,647 kB/2,776 kB 95%]                          235 kB/s 51% [30 luatex 2,769 kB/2,776 kB 100%]                         235 kB/s 51% [Working]                                                  235 kB/s                                                                         Get:31 http://ph.archive.ubuntu.com/ubuntu/ trusty/main texlive-base all 2013.20140215-1 [16.2 MB]
51% [31 texlive-base 1,165 B/16.2 MB 0%]                       235 kB/s 51% [31 texlive-base 116 kB/16.2 MB 1%]                        235 kB/s 51% [31 texlive-base 241 kB/16.2 MB 1%]                        235 kB/s 51% [31 texlive-base 346 kB/16.2 MB 2%]                        235 kB/s 51% [31 texlive-base 455 kB/16.2 MB 3%]                        235 kB/s 52% [31 texlive-base 581 kB/16.2 MB 4%]                        235 kB/s 52% [31 texlive-base 707 kB/16.2 MB 4%]                        232 kB/s 52% [31 texlive-base 830 kB/16.2 MB 5%]                        232 kB/s 52% [31 texlive-base 953 kB/16.2 MB 6%]                        232 kB/s 52% [31 texlive-base 1,069 kB/16.2 MB 7%]                      232 kB/s 52% [31 texlive-base 1,202 kB/16.2 MB 7%]                     232 kB/s 252% [31 texlive-base 1,328 kB/16.2 MB 8%]                     232 kB/s 253% [31 texlive-base 1,446 kB/16.2 MB 9%]                     232 kB/s 253% [31 texlive-base 1,565 kB/16.2 MB 10%]                    232 kB/s 253% [31 texlive-base 1,660 kB/16.2 MB 10%]                    232 kB/s 253% [31 texlive-base 1,771 kB/16.2 MB 11%]                    232 kB/s 253% [31 texlive-base 1,867 kB/16.2 MB 12%]                    232 kB/s 253% [31 texlive-base 1,960 kB/16.2 MB 12%]                    232 kB/s 253% [31 texlive-base 2,087 kB/16.2 MB 13%]                    230 kB/s 253% [31 texlive-base 2,180 kB/16.2 MB 13%]                    230 kB/s 254% [31 texlive-base 2,301 kB/16.2 MB 14%]                    230 kB/s 254% [31 texlive-base 2,429 kB/16.2 MB 15%]                    230 kB/s 254% [31 texlive-base 2,555 kB/16.2 MB 16%]                    230 kB/s 254% [31 texlive-base 2,642 kB/16.2 MB 16%]                    230 kB/s 254% [31 texlive-base 2,768 kB/16.2 MB 17%]                    230 kB/s 254% [31 texlive-base 2,888 kB/16.2 MB 18%]                    230 kB/s 254% [31 texlive-base 3,014 kB/16.2 MB 19%]                    230 kB/s 255% [31 texlive-base 3,120 kB/16.2 MB 19%]                    230 kB/s 255% [31 texlive-base 3,217 kB/16.2 MB 20%]                    230 kB/s 255% [31 texlive-base 3,343 kB/16.2 MB 21%]                    230 kB/s 255% [31 texlive-base 3,463 kB/16.2 MB 21%]                    229 kB/s 255% [31 texlive-base 3,589 kB/16.2 MB 22%]                    229 kB/s 255% [31 texlive-base 3,711 kB/16.2 MB 23%]                    229 kB/s 255% [31 texlive-base 3,815 kB/16.2 MB 24%]                    229 kB/s 255% [31 texlive-base 3,857 kB/16.2 MB 24%]                    229 kB/s 255% [31 texlive-base 3,857 kB/16.2 MB 24%]                    229 kB/s 255% [31 texlive-base 3,857 kB/16.2 MB 24%]                    229 kB/s 255% [31 texlive-base 3,857 kB/16.2 MB 24%]                    229 kB/s 255% [31 texlive-base 3,857 kB/16.2 MB 24%]                    229 kB/s 255% [31 texlive-base 3,857 kB/16.2 MB 24%]                    229 kB/s 256% [31 texlive-base 4,012 kB/16.2 MB 25%]                    229 kB/s 256% [31 texlive-base 4,267 kB/16.2 MB 26%]                    229 kB/s 256% [31 texlive-base 4,452 kB/16.2 MB 28%]                    165 kB/s 356% [31 texlive-base 4,568 kB/16.2 MB 28%]                    165 kB/s 356% [31 texlive-base 4,631 kB/16.2 MB 29%]                    165 kB/s 356% [31 texlive-base 4,631 kB/16.2 MB 29%]                    165 kB/s 356% [31 texlive-base 4,631 kB/16.2 MB 29%]                    165 kB/s 356% [31 texlive-base 4,631 kB/16.2 MB 29%]                    165 kB/s 356% [31 texlive-base 4,631 kB/16.2 MB 29%]                    165 kB/s 357% [31 texlive-base 5,398 kB/16.2 MB 33%]                    165 kB/s 357% [31 texlive-base 5,398 kB/16.2 MB 33%]                    165 kB/s 357% [31 texlive-base 5,398 kB/16.2 MB 33%]                    165 kB/s 357% [31 texlive-base 5,408 kB/16.2 MB 33%]                    165 kB/s 358% [31 texlive-base 6,129 kB/16.2 MB 38%]                    165 kB/s 358% [31 texlive-base 6,254 kB/16.2 MB 39%]                     300 kB/s 58% [31 texlive-base 6,378 kB/16.2 MB 39%]                     300 kB/s 58% [31 texlive-base 6,501 kB/16.2 MB 40%]                     300 kB/s 58% [31 texlive-base 6,626 kB/16.2 MB 41%]                     300 kB/s 59% [31 texlive-base 6,752 kB/16.2 MB 42%]                     300 kB/s 59% [31 texlive-base 6,877 kB/16.2 MB 43%]                     300 kB/s 59% [31 texlive-base 6,977 kB/16.2 MB 43%]                     300 kB/s 59% [31 texlive-base 7,105 kB/16.2 MB 44%]                    300 kB/s 159% [31 texlive-base 7,229 kB/16.2 MB 45%]                    300 kB/s 159% [31 texlive-base 7,354 kB/16.2 MB 45%]                    300 kB/s 159% [31 texlive-base 7,477 kB/16.2 MB 46%]                    300 kB/s 160% [31 texlive-base 7,603 kB/16.2 MB 47%]                    300 kB/s 160% [31 texlive-base 7,729 kB/16.2 MB 48%]                    246 kB/s 260% [31 texlive-base 7,852 kB/16.2 MB 49%]                    246 kB/s 260% [31 texlive-base 7,980 kB/16.2 MB 49%]                    246 kB/s 260% [31 texlive-base 8,106 kB/16.2 MB 50%]                    246 kB/s 260% [31 texlive-base 8,232 kB/16.2 MB 51%]                    246 kB/s 260% [31 texlive-base 8,356 kB/16.2 MB 52%]                    246 kB/s 261% [31 texlive-base 8,482 kB/16.2 MB 52%]                    246 kB/s 261% [31 texlive-base 8,608 kB/16.2 MB 53%]                    246 kB/s 261% [31 texlive-base 8,734 kB/16.2 MB 54%]                    246 kB/s 261% [31 texlive-base 8,860 kB/16.2 MB 55%]                    246 kB/s 261% [31 texlive-base 8,986 kB/16.2 MB 56%]                    246 kB/s 261% [31 texlive-base 9,114 kB/16.2 MB 56%]                    246 kB/s 261% [31 texlive-base 9,236 kB/16.2 MB 57%]                    251 kB/s 262% [31 texlive-base 9,362 kB/16.2 MB 58%]                    251 kB/s 262% [31 texlive-base 9,488 kB/16.2 MB 59%]                    251 kB/s 262% [31 texlive-base 9,614 kB/16.2 MB 59%]                    251 kB/s 262% [31 texlive-base 9,740 kB/16.2 MB 60%]                    251 kB/s 262% [31 texlive-base 9,864 kB/16.2 MB 61%]                    251 kB/s 262% [31 texlive-base 9,990 kB/16.2 MB 62%]                    251 kB/s 262% [31 texlive-base 10.1 MB/16.2 MB 63%]                     251 kB/s 263% [31 texlive-base 10.2 MB/16.2 MB 63%]                     251 kB/s 263% [31 texlive-base 10.3 MB/16.2 MB 64%]                     251 kB/s 263% [31 texlive-base 10.3 MB/16.2 MB 64%]                     251 kB/s 263% [31 texlive-base 10.3 MB/16.2 MB 64%]                     251 kB/s 263% [31 texlive-base 10.3 MB/16.2 MB 64%]                      177 kB/s 63% [31 texlive-base 10.3 MB/16.2 MB 64%]                      177 kB/s 63% [31 texlive-base 10.3 MB/16.2 MB 64%]                      177 kB/s 63% [31 texlive-base 10.5 MB/16.2 MB 65%]                      177 kB/s 63% [31 texlive-base 10.7 MB/16.2 MB 66%]                      177 kB/s 63% [31 texlive-base 10.9 MB/16.2 MB 68%]                      177 kB/s 64% [31 texlive-base 11.1 MB/16.2 MB 68%]                      177 kB/s 64% [31 texlive-base 11.2 MB/16.2 MB 69%]                     177 kB/s 264% [31 texlive-base 11.7 MB/16.2 MB 73%]                     177 kB/s 264% [31 texlive-base 11.8 MB/16.2 MB 73%]                     177 kB/s 265% [31 texlive-base 12.0 MB/16.2 MB 74%]                     177 kB/s 265% [31 texlive-base 12.1 MB/16.2 MB 75%]                     177 kB/s 265% [31 texlive-base 12.2 MB/16.2 MB 76%]                     318 kB/s 165% [31 texlive-base 12.3 MB/16.2 MB 76%]                     318 kB/s 165% [31 texlive-base 12.5 MB/16.2 MB 77%]                     318 kB/s 165% [31 texlive-base 12.6 MB/16.2 MB 78%]                     318 kB/s 165% [31 texlive-base 12.7 MB/16.2 MB 79%]                     318 kB/s 166% [31 texlive-base 12.8 MB/16.2 MB 79%]                     318 kB/s 166% [31 texlive-base 12.9 MB/16.2 MB 80%]                     318 kB/s 166% [31 texlive-base 12.9 MB/16.2 MB 80%]                     318 kB/s 166% [31 texlive-base 12.9 MB/16.2 MB 80%]                     318 kB/s 166% [31 texlive-base 12.9 MB/16.2 MB 80%]                     318 kB/s 166% [31 texlive-base 12.9 MB/16.2 MB 80%]                     318 kB/s 166% [31 texlive-base 12.9 MB/16.2 MB 80%]                     318 kB/s 166% [31 texlive-base 13.1 MB/16.2 MB 81%]                     142 kB/s 366% [31 texlive-base 13.3 MB/16.2 MB 82%]                     142 kB/s 366% [31 texlive-base 13.5 MB/16.2 MB 83%]                     142 kB/s 366% [31 texlive-base 13.6 MB/16.2 MB 84%]                     142 kB/s 367% [31 texlive-base 14.2 MB/16.2 MB 88%]                     142 kB/s 367% [31 texlive-base 14.3 MB/16.2 MB 89%]                     142 kB/s 367% [31 texlive-base 14.5 MB/16.2 MB 89%]                     142 kB/s 368% [31 texlive-base 14.6 MB/16.2 MB 90%]                     142 kB/s 368% [31 texlive-base 14.7 MB/16.2 MB 91%]                     142 kB/s 368% [31 texlive-base 14.8 MB/16.2 MB 92%]                     142 kB/s 368% [31 texlive-base 14.9 MB/16.2 MB 92%]                     142 kB/s 368% [31 texlive-base 15.1 MB/16.2 MB 93%]                     142 kB/s 368% [31 texlive-base 15.2 MB/16.2 MB 94%]                     351 kB/s 168% [31 texlive-base 15.3 MB/16.2 MB 95%]                     351 kB/s 169% [31 texlive-base 15.4 MB/16.2 MB 95%]                     351 kB/s 169% [31 texlive-base 15.6 MB/16.2 MB 96%]                     351 kB/s 169% [31 texlive-base 15.7 MB/16.2 MB 97%]                     351 kB/s 169% [31 texlive-base 15.7 MB/16.2 MB 97%]                     351 kB/s 169% [31 texlive-base 15.7 MB/16.2 MB 97%]                     351 kB/s 169% [31 texlive-base 15.7 MB/16.2 MB 97%]                     351 kB/s 169% [31 texlive-base 15.7 MB/16.2 MB 97%]                     351 kB/s 169% [Working]                                                 351 kB/s 1                                                                        Get:32 http://ph.archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-base all 2013.20140215-1 [828 kB]
69% [32 texlive-latex-base 1,167 B/828 kB 0%]                 351 kB/s 170% [32 texlive-latex-base 122 kB/828 kB 15%]                 351 kB/s 170% [32 texlive-latex-base 245 kB/828 kB 30%]                 351 kB/s 170% [32 texlive-latex-base 371 kB/828 kB 45%]                 351 kB/s 170% [32 texlive-latex-base 497 kB/828 kB 60%]                 236 kB/s 170% [32 texlive-latex-base 624 kB/828 kB 75%]                 236 kB/s 170% [32 texlive-latex-base 750 kB/828 kB 91%]                 236 kB/s 170% [Working]                                                 236 kB/s 1                                                                        Get:33 http://ph.archive.ubuntu.com/ubuntu/ trusty/main texlive-fonts-recommended all 2013.20140215-1 [5,715 kB]
70% [33 texlive-fonts-recommended 1,166 B/5,715 kB 0%]        236 kB/s 170% [33 texlive-fonts-recommended 57.2 kB/5,715 kB 1%]        236 kB/s 171% [33 texlive-fonts-recommended 242 kB/5,715 kB 4%]         236 kB/s 171% [33 texlive-fonts-recommended 350 kB/5,715 kB 6%]         236 kB/s 171% [33 texlive-fonts-recommended 466 kB/5,715 kB 8%]         236 kB/s 171% [33 texlive-fonts-recommended 589 kB/5,715 kB 10%]        236 kB/s 171% [33 texlive-fonts-recommended 715 kB/5,715 kB 13%]        236 kB/s 171% [33 texlive-fonts-recommended 837 kB/5,715 kB 15%]        236 kB/s 171% [33 texlive-fonts-recommended 960 kB/5,715 kB 17%]        236 kB/s 172% [33 texlive-fonts-recommended 1,081 kB/5,715 kB 19%]      236 kB/s 172% [33 texlive-fonts-recommended 1,202 kB/5,715 kB 21%]      240 kB/s 172% [33 texlive-fonts-recommended 1,328 kB/5,715 kB 23%]      240 kB/s 172% [33 texlive-fonts-recommended 1,454 kB/5,715 kB 25%]      240 kB/s 172% [33 texlive-fonts-recommended 1,576 kB/5,715 kB 28%]      240 kB/s 172% [33 texlive-fonts-recommended 1,695 kB/5,715 kB 30%]      240 kB/s 172% [33 texlive-fonts-recommended 1,820 kB/5,715 kB 32%]      240 kB/s 173% [33 texlive-fonts-recommended 1,942 kB/5,715 kB 34%]      240 kB/s 173% [33 texlive-fonts-recommended 2,068 kB/5,715 kB 36%]      240 kB/s 173% [33 texlive-fonts-recommended 2,194 kB/5,715 kB 38%]      240 kB/s 173% [33 texlive-fonts-recommended 2,314 kB/5,715 kB 40%]      240 kB/s 173% [33 texlive-fonts-recommended 2,444 kB/5,715 kB 43%]      240 kB/s 173% [33 texlive-fonts-recommended 2,572 kB/5,715 kB 45%]      240 kB/s 173% [33 texlive-fonts-recommended 2,696 kB/5,715 kB 47%]      249 kB/s 174% [33 texlive-fonts-recommended 2,824 kB/5,715 kB 49%]      249 kB/s 174% [33 texlive-fonts-recommended 2,950 kB/5,715 kB 52%]      249 kB/s 174% [33 texlive-fonts-recommended 3,076 kB/5,715 kB 54%]      249 kB/s 174% [33 texlive-fonts-recommended 3,204 kB/5,715 kB 56%]      249 kB/s 174% [33 texlive-fonts-recommended 3,330 kB/5,715 kB 58%]      249 kB/s 174% [33 texlive-fonts-recommended 3,456 kB/5,715 kB 60%]      249 kB/s 174% [33 texlive-fonts-recommended 3,582 kB/5,715 kB 63%]      249 kB/s 175% [33 texlive-fonts-recommended 3,708 kB/5,715 kB 65%]      249 kB/s 175% [33 texlive-fonts-recommended 3,833 kB/5,715 kB 67%]      249 kB/s 175% [33 texlive-fonts-recommended 3,959 kB/5,715 kB 69%]      249 kB/s 175% [33 texlive-fonts-recommended 4,079 kB/5,715 kB 71%]      249 kB/s 175% [33 texlive-fonts-recommended 4,207 kB/5,715 kB 74%]      251 kB/s 175% [33 texlive-fonts-recommended 4,334 kB/5,715 kB 76%]      251 kB/s 175% [33 texlive-fonts-recommended 4,460 kB/5,715 kB 78%]      251 kB/s 176% [33 texlive-fonts-recommended 4,585 kB/5,715 kB 80%]      251 kB/s 176% [33 texlive-fonts-recommended 4,711 kB/5,715 kB 82%]      251 kB/s 176% [33 texlive-fonts-recommended 4,837 kB/5,715 kB 85%]      251 kB/s 176% [33 texlive-fonts-recommended 4,964 kB/5,715 kB 87%]      251 kB/s 176% [33 texlive-fonts-recommended 5,057 kB/5,715 kB 88%]      251 kB/s 176% [33 texlive-fonts-recommended 5,057 kB/5,715 kB 88%]      251 kB/s 176% [33 texlive-fonts-recommended 5,057 kB/5,715 kB 88%]      251 kB/s 176% [33 texlive-fonts-recommended 5,057 kB/5,715 kB 88%]      251 kB/s 176% [33 texlive-fonts-recommended 5,197 kB/5,715 kB 91%]      251 kB/s 177% [Working]                                                 251 kB/s 1                                                                        Get:34 http://ph.archive.ubuntu.com/ubuntu/ trusty/main texlive-latex-recommended all 2013.20140215-1 [7,268 kB]
77% [34 texlive-latex-recommended 1,166 B/7,268 kB 0%]        251 kB/s 177% [34 texlive-latex-recommended 126 kB/7,268 kB 2%]         251 kB/s 177% [34 texlive-latex-recommended 253 kB/7,268 kB 3%]         251 kB/s 177% [34 texlive-latex-recommended 381 kB/7,268 kB 5%]         251 kB/s 177% [34 texlive-latex-recommended 508 kB/7,268 kB 7%]         251 kB/s 178% [34 texlive-latex-recommended 627 kB/7,268 kB 9%]         251 kB/s 178% [34 texlive-latex-recommended 752 kB/7,268 kB 10%]        251 kB/s 178% [34 texlive-latex-recommended 878 kB/7,268 kB 12%]        251 kB/s 178% [34 texlive-latex-recommended 1,005 kB/7,268 kB 14%]      251 kB/s 178% [34 texlive-latex-recommended 1,132 kB/7,268 kB 16%]      251 kB/s 178% [34 texlive-latex-recommended 1,251 kB/7,268 kB 17%]      251 kB/s 178% [34 texlive-latex-recommended 1,379 kB/7,268 kB 19%]      251 kB/s 179% [34 texlive-latex-recommended 1,506 kB/7,268 kB 21%]      245 kB/s 179% [34 texlive-latex-recommended 1,634 kB/7,268 kB 22%]      245 kB/s 179% [34 texlive-latex-recommended 1,760 kB/7,268 kB 24%]      245 kB/s 179% [34 texlive-latex-recommended 1,887 kB/7,268 kB 26%]      245 kB/s 179% [34 texlive-latex-recommended 2,013 kB/7,268 kB 28%]      245 kB/s 179% [34 texlive-latex-recommended 2,140 kB/7,268 kB 29%]      245 kB/s 179% [34 texlive-latex-recommended 2,266 kB/7,268 kB 31%]      245 kB/s 180% [34 texlive-latex-recommended 2,392 kB/7,268 kB 33%]      245 kB/s 180% [34 texlive-latex-recommended 2,518 kB/7,268 kB 35%]      245 kB/s 180% [34 texlive-latex-recommended 2,644 kB/7,268 kB 36%]      245 kB/s 180% [34 texlive-latex-recommended 2,770 kB/7,268 kB 38%]      245 kB/s 180% [34 texlive-latex-recommended 2,896 kB/7,268 kB 40%]      245 kB/s 180% [34 texlive-latex-recommended 3,024 kB/7,268 kB 42%]       253 kB/s 80% [34 texlive-latex-recommended 3,147 kB/7,268 kB 43%]       253 kB/s 81% [34 texlive-latex-recommended 3,273 kB/7,268 kB 45%]       253 kB/s 81% [34 texlive-latex-recommended 3,400 kB/7,268 kB 47%]       253 kB/s 81% [34 texlive-latex-recommended 3,526 kB/7,268 kB 49%]       253 kB/s 81% [34 texlive-latex-recommended 3,652 kB/7,268 kB 50%]       253 kB/s 81% [34 texlive-latex-recommended 3,778 kB/7,268 kB 52%]       253 kB/s 81% [34 texlive-latex-recommended 3,904 kB/7,268 kB 54%]       253 kB/s 81% [34 texlive-latex-recommended 4,030 kB/7,268 kB 55%]       253 kB/s 82% [34 texlive-latex-recommended 4,133 kB/7,268 kB 57%]       253 kB/s 82% [34 texlive-latex-recommended 4,133 kB/7,268 kB 57%]       253 kB/s 82% [34 texlive-latex-recommended 4,133 kB/7,268 kB 57%]       253 kB/s 82% [34 texlive-latex-recommended 4,133 kB/7,268 kB 57%]      185 kB/s 182% [34 texlive-latex-recommended 4,133 kB/7,268 kB 57%]      185 kB/s 182% [34 texlive-latex-recommended 4,133 kB/7,268 kB 57%]      185 kB/s 182% [34 texlive-latex-recommended 4,285 kB/7,268 kB 59%]      185 kB/s 182% [34 texlive-latex-recommended 4,547 kB/7,268 kB 63%]      185 kB/s 182% [34 texlive-latex-recommended 4,753 kB/7,268 kB 65%]      185 kB/s 182% [34 texlive-latex-recommended 4,870 kB/7,268 kB 67%]      185 kB/s 183% [34 texlive-latex-recommended 5,006 kB/7,268 kB 69%]      185 kB/s 183% [34 texlive-latex-recommended 5,534 kB/7,268 kB 76%]      185 kB/s 183% [34 texlive-latex-recommended 5,663 kB/7,268 kB 78%]      185 kB/s 183% [34 texlive-latex-recommended 5,782 kB/7,268 kB 80%]      185 kB/s 184% [34 texlive-latex-recommended 5,894 kB/7,268 kB 81%]      185 kB/s 184% [34 texlive-latex-recommended 6,037 kB/7,268 kB 83%]           317 k84% [34 texlive-latex-recommended 6,163 kB/7,268 kB 85%]           317 k84% [34 texlive-latex-recommended 6,279 kB/7,268 kB 86%]           317 k84% [34 texlive-latex-recommended 6,279 kB/7,268 kB 86%]           317 k84% [34 texlive-latex-recommended 6,279 kB/7,268 kB 86%]           317 k84% [34 texlive-latex-recommended 6,279 kB/7,268 kB 86%]           317 k84% [34 texlive-latex-recommended 6,279 kB/7,268 kB 86%]           317 k84% [34 texlive-latex-recommended 6,279 kB/7,268 kB 86%]           317 k84% [34 texlive-latex-recommended 6,403 kB/7,268 kB 88%]           317 k84% [34 texlive-latex-recommended 6,634 kB/7,268 kB 91%]           317 k85% [Working]                                                      317 k                                                                        Get:35 http://ph.archive.ubuntu.com/ubuntu/ trusty/main texlive-generic-recommended all 2013.20140215-1 [2,114 kB]
85% [35 texlive-generic-recommended 1,166 B/2,114 kB 0%]           317 k85% [35 texlive-generic-recommended 129 kB/2,114 kB 6%]            317 k85% [35 texlive-generic-recommended 256 kB/2,114 kB 12%]           246 k86% [35 texlive-generic-recommended 378 kB/2,114 kB 18%]           246 k86% [35 texlive-generic-recommended 498 kB/2,114 kB 24%]           246 k86% [35 texlive-generic-recommended 612 kB/2,114 kB 29%]           246 k86% [35 texlive-generic-recommended 728 kB/2,114 kB 34%]           246 k86% [35 texlive-generic-recommended 850 kB/2,114 kB 40%]           246 k86% [35 texlive-generic-recommended 977 kB/2,114 kB 46%]           246 k86% [35 texlive-generic-recommended 1,102 kB/2,114 kB 52%]         246 k87% [35 texlive-generic-recommended 1,228 kB/2,114 kB 58%]         246 k87% [35 texlive-generic-recommended 1,355 kB/2,114 kB 64%]         246 k87% [35 texlive-generic-recommended 1,475 kB/2,114 kB 70%]         246 k87% [35 texlive-generic-recommended 1,601 kB/2,114 kB 76%]         246 k87% [35 texlive-generic-recommended 1,726 kB/2,114 kB 82%]         245 k87% [35 texlive-generic-recommended 1,852 kB/2,114 kB 88%]         245 k87% [35 texlive-generic-recommended 1,979 kB/2,114 kB 94%]         245 k88% [35 texlive-generic-recommended 2,105 kB/2,114 kB 100%]        245 k88% [Working]                                                      245 k                                                                        Get:36 http://ph.archive.ubuntu.com/ubuntu/ trusty/main tipa all 2:1.3-19 [3,311 kB]
88% [36 tipa 1,166 B/3,311 kB 0%]                                  245 k88% [36 tipa 60.0 kB/3,311 kB 2%]                                  245 k88% [36 tipa 176 kB/3,311 kB 5%]                                   245 k88% [36 tipa 383 kB/3,311 kB 12%]                                  245 k88% [36 tipa 509 kB/3,311 kB 15%]                                  245 k88% [36 tipa 637 kB/3,311 kB 19%]                                  245 k88% [36 tipa 763 kB/3,311 kB 23%]                                  245 k89% [36 tipa 889 kB/3,311 kB 27%]                                  245 k89% [36 tipa 1,016 kB/3,311 kB 31%]                                245 k89% [36 tipa 1,142 kB/3,311 kB 34%]                                251 k89% [36 tipa 1,270 kB/3,311 kB 38%]                                251 k89% [36 tipa 1,396 kB/3,311 kB 42%]                                251 k89% [36 tipa 1,522 kB/3,311 kB 46%]                                251 k89% [36 tipa 1,648 kB/3,311 kB 50%]                                251 k90% [36 tipa 1,774 kB/3,311 kB 54%]                                251 k90% [36 tipa 1,900 kB/3,311 kB 57%]                                251 k90% [36 tipa 2,027 kB/3,311 kB 61%]                                251 k90% [36 tipa 2,153 kB/3,311 kB 65%]                                251 k90% [36 tipa 2,279 kB/3,311 kB 69%]                                251 k90% [36 tipa 2,405 kB/3,311 kB 73%]                                251 k90% [36 tipa 2,532 kB/3,311 kB 76%]                                251 k91% [36 tipa 2,658 kB/3,311 kB 80%]                                252 k91% [36 tipa 2,784 kB/3,311 kB 84%]                                252 k91% [36 tipa 2,910 kB/3,311 kB 88%]                                252 k91% [36 tipa 3,038 kB/3,311 kB 92%]                                252 k91% [36 tipa 3,165 kB/3,311 kB 96%]                                252 k91% [36 tipa 3,281 kB/3,311 kB 99%]                                252 k91% [Working]                                                      252 k                                                                        Get:37 http://ph.archive.ubuntu.com/ubuntu/ trusty/main jadetex all 3.13-14 [240 kB]
91% [37 jadetex 1,167 B/240 kB 0%]                                 252 k91% [37 jadetex 120 kB/240 kB 50%]                                 252 k92% [37 jadetex 169 kB/240 kB 70%]                                 252 k92% [37 jadetex 169 kB/240 kB 70%]                                 252 k92% [37 jadetex 190 kB/240 kB 79%]                                 252 k92% [Working]                                                      252 k                                                                        Get:38 http://ph.archive.ubuntu.com/ubuntu/ trusty/main lynx-cur amd64 2.8.8pre4-1 [956 kB]
92% [38 lynx-cur 1,167 B/956 kB 0%]                                252 k92% [38 lynx-cur 120 kB/956 kB 13%]                                252 k92% [38 lynx-cur 246 kB/956 kB 26%]                                188 k92% [38 lynx-cur 374 kB/956 kB 39%]                                188 k92% [38 lynx-cur 501 kB/956 kB 52%]                                188 k92% [38 lynx-cur 628 kB/956 kB 66%]                                188 k92% [38 lynx-cur 753 kB/956 kB 79%]                                188 k93% [38 lynx-cur 876 kB/956 kB 92%]                                188 k93% [Working]                                                      188 k                                                                        Get:39 http://ph.archive.ubuntu.com/ubuntu/ trusty/main lynx all 2.8.8pre4-1 [4,184 B]
93% [39 lynx 1,169 B/4,184 B 28%]                                  188 k93% [Working]                                                      188 k                                                                        Get:40 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libsgmls-perl all 1.03ii-32 [29.4 kB]
93% [40 libsgmls-perl 1,168 B/29.4 kB 4%]                          188 k93% [Working]                                                      188 k                                                                        Get:41 http://ph.archive.ubuntu.com/ubuntu/ trusty/main sgmlspl all 1.03ii-32 [11.4 kB]
93% [41 sgmlspl 1,168 B/11.4 kB 10%]                               188 k93% [Working]                                                      188 k                                                                        Get:42 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libsp1c2 amd64 1.3.4-1.2.1-47.3ubuntu1 [1,026 kB]
93% [42 libsp1c2 1,166 B/1,026 kB 0%]                              188 k93% [42 libsp1c2 83.8 kB/1,026 kB 8%]                              188 k93% [42 libsp1c2 236 kB/1,026 kB 23%]                              188 k93% [42 libsp1c2 360 kB/1,026 kB 35%]                              188 k93% [42 libsp1c2 487 kB/1,026 kB 47%]                              188 k93% [42 libsp1c2 613 kB/1,026 kB 60%]                              188 k94% [42 libsp1c2 739 kB/1,026 kB 72%]                              237 k94% [42 libsp1c2 865 kB/1,026 kB 84%]                              237 k94% [42 libsp1c2 991 kB/1,026 kB 97%]                              237 k94% [Working]                                                      237 k                                                                        Get:43 http://ph.archive.ubuntu.com/ubuntu/ trusty/main sp amd64 1.3.4-1.2.1-47.3ubuntu1 [124 kB]
94% [43 sp 1,167 B/124 kB 1%]                                      237 k94% [43 sp 108 kB/124 kB 86%]                                      237 k94% [Working]                                                      237 k                                                                        Get:44 http://ph.archive.ubuntu.com/ubuntu/ trusty/main docbook-utils all 0.6.14-3ubuntu1 [68.0 kB]
94% [44 docbook-utils 1,168 B/68.0 kB 2%]                          237 k94% [Working]                                                      237 k                                                                        Get:45 http://ph.archive.ubuntu.com/ubuntu/ trusty/main docbook-xsl all 1.78.1+dfsg-1 [2,146 kB]
94% [45 docbook-xsl 1,166 B/2,146 kB 0%]                           237 k94% [45 docbook-xsl 112 kB/2,146 kB 5%]                            237 k94% [45 docbook-xsl 238 kB/2,146 kB 11%]                           237 k95% [45 docbook-xsl 365 kB/2,146 kB 17%]                           237 k95% [45 docbook-xsl 486 kB/2,146 kB 23%]                           237 k95% [45 docbook-xsl 598 kB/2,146 kB 28%]                           237 k95% [45 docbook-xsl 721 kB/2,146 kB 34%]                           237 k95% [45 docbook-xsl 836 kB/2,146 kB 39%]                           218 k95% [45 docbook-xsl 959 kB/2,146 kB 45%]                           218 k95% [45 docbook-xsl 1,085 kB/2,146 kB 51%]                         218 k95% [45 docbook-xsl 1,211 kB/2,146 kB 56%]                         218 k96% [45 docbook-xsl 1,338 kB/2,146 kB 62%]                         218 k96% [45 docbook-xsl 1,464 kB/2,146 kB 68%]                         218 k96% [45 docbook-xsl 1,590 kB/2,146 kB 74%]                         218 k96% [45 docbook-xsl 1,718 kB/2,146 kB 80%]                         218 k96% [45 docbook-xsl 1,842 kB/2,146 kB 86%]                         218 k96% [45 docbook-xsl 1,970 kB/2,146 kB 92%]                         218 k97% [45 docbook-xsl 2,097 kB/2,146 kB 98%]                         218 k97% [Working]                                                      218 k                                                                        Get:46 http://ph.archive.ubuntu.com/ubuntu/ trusty/main kernel-wedge all 2.87ubuntu1 [21.9 kB]
97% [46 kernel-wedge 1,168 B/21.9 kB 5%]                           218 k97% [Working]                                                      218 k                                                                        Get:47 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main libelf-dev amd64 0.158-0ubuntu5.2 [47.3 kB]
97% [47 libelf-dev 1,168 B/47.3 kB 2%]                             218 k97% [Working]                                                      218 k                                                                        Get:48 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main libdw-dev amd64 0.158-0ubuntu5.2 [135 kB]
97% [48 libdw-dev 1,167 B/135 kB 1%]                               218 k97% [48 libdw-dev 68.4 kB/135 kB 51%]                              234 k97% [48 libdw-dev 68.4 kB/135 kB 51%]                              234 k97% [48 libdw-dev 106 kB/135 kB 79%]                               234 k97% [Working]                                                      234 k                                                                        Get:49 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libiberty-dev amd64 20131116-1 [135 kB]
97% [49 libiberty-dev 1,167 B/135 kB 1%]                           234 k97% [49 libiberty-dev 122 kB/135 kB 90%]                           234 k97% [Working]                                                      234 k                                                                        Get:50 http://ph.archive.ubuntu.com/ubuntu/ trusty/main zlib1g-dev amd64 1:1.2.8.dfsg-1ubuntu1 [183 kB]
97% [50 zlib1g-dev 1,167 B/183 kB 1%]                              234 k97% [50 zlib1g-dev 129 kB/183 kB 70%]                              234 k97% [Working]                                                      234 k                                                                        Get:51 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libpng12-dev amd64 1.2.50-1ubuntu2 [206 kB]
97% [51 libpng12-dev 1,167 B/206 kB 1%]                            234 k97% [51 libpng12-dev 129 kB/206 kB 62%]                            234 k97% [Working]                                                       234                                                                         Get:52 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libslang2-dev amd64 2.2.4-15ubuntu1 [524 kB]
97% [52 libslang2-dev 1,167 B/524 kB 0%]                            234 98% [52 libslang2-dev 129 kB/524 kB 25%]                            234 98% [52 libslang2-dev 256 kB/524 kB 49%]                            234 98% [52 libslang2-dev 383 kB/524 kB 73%]                            234 98% [52 libslang2-dev 511 kB/524 kB 98%]                            234 98% [Working]                                                       234                                                                         Get:53 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libnewt-dev amd64 0.52.15-2ubuntu5 [68.8 kB]
98% [53 libnewt-dev 1,168 B/68.8 kB 2%]                             183 98% [Working]                                                       183                                                                         Get:54 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libpci-dev amd64 1:3.2.1-1ubuntu5 [43.9 kB]
98% [54 libpci-dev 1,168 B/43.9 kB 3%]                              183 98% [Working]                                                       183                                                                         Get:55 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libpython-dev amd64 2.7.5-5ubuntu3 [7,078 B]
98% [55 libpython-dev 1,169 B/7,078 B 17%]                          183 98% [Working]                                                       183                                                                         Get:56 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libunwind8-dev amd64 1.1-2.2ubuntu3 [375 kB]
98% [56 libunwind8-dev 1,167 B/375 kB 0%]                           183 98% [56 libunwind8-dev 117 kB/375 kB 31%]                           183 98% [56 libunwind8-dev 242 kB/375 kB 64%]                           183 99% [56 libunwind8-dev 367 kB/375 kB 98%]                           183 99% [Working]                                                       183                                                                         Get:57 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main libxml2-utils amd64 2.9.1+dfsg1-3ubuntu4.4 [34.7 kB]
99% [57 libxml2-utils 1,168 B/34.7 kB 3%]                           183 99% [Working]                                                       183                                                                         Get:58 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main makedumpfile amd64 1.5.5-2ubuntu1.1 [124 kB]
99% [58 makedumpfile 1,167 B/124 kB 1%]                             183 99% [Working]                                                       183                                                                         Get:59 http://ph.archive.ubuntu.com/ubuntu/ trusty/main python2.7-dev amd64 2.7.6-8 [269 kB]
99% [59 python2.7-dev 1,167 B/269 kB 0%]                            183 99% [59 python2.7-dev 127 kB/269 kB 47%]                            183 99% [59 python2.7-dev 253 kB/269 kB 94%]                            183 99% [Working]                                                       183                                                                         Get:60 http://ph.archive.ubuntu.com/ubuntu/ trusty/main python-dev amd64 2.7.5-5ubuntu3 [1,166 B]
99% [60 python-dev 1,166 B/1,166 B 100%]                            183 99% [Working]                                                       183                                                                         Get:61 http://ph.archive.ubuntu.com/ubuntu/ trusty/main sharutils amd64 1:4.14-1ubuntu1 [145 kB]
99% [61 sharutils 1,167 B/145 kB 1%]                                183 99% [61 sharutils 129 kB/145 kB 89%]                                183 99% [Working]                                                       183                                                                         Get:62 http://ph.archive.ubuntu.com/ubuntu/ trusty/main transfig amd64 1:3.2.5.e-1ubuntu1 [588 kB]
99% [62 transfig 1,167 B/588 kB 0%]                                 183 99% [62 transfig 129 kB/588 kB 22%]                                 183 100% [62 transfig 256 kB/588 kB 44%]                                218 100% [62 transfig 383 kB/588 kB 65%]                                218 100% [62 transfig 511 kB/588 kB 87%]                                218 100% [Working]                                                      218                                                                         Get:63 http://ph.archive.ubuntu.com/ubuntu/ trusty/main xsltproc amd64 1.1.28-2build1 [13.6 kB]
100% [63 xsltproc 1,168 B/13.6 kB 9%]                               218 100% [Working]                                                      218                                                                         Get:64 http://ph.archive.ubuntu.com/ubuntu/ trusty/main xmlto amd64 0.0.25-2 [30.4 kB]
100% [64 xmlto 1,168 B/30.4 kB 4%]                                  218 100% [Working]                                                      218                                                                         Get:65 http://ph.archive.ubuntu.com/ubuntu/ trusty/main libaudit-dev amd64 1:2.3.2-2ubuntu1 [59.7 kB]
100% [65 libaudit-dev 1,168 B/59.7 kB 2%]                           218 100% [Working]                                                      218                                                                         Fetched 87.7 MB in 6min 6s (239 kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 122393 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Selecting previously unselected package m4.
Preparing to unpack .../m4_1.4.17-2ubuntu1_amd64.deb ...
Unpacking m4 (1.4.17-2ubuntu1) ...
Selecting previously unselected package libfl-dev:amd64.
Preparing to unpack .../libfl-dev_2.5.35-10.1ubuntu2_amd64.deb ...
Unpacking libfl-dev:amd64 (2.5.35-10.1ubuntu2) ...
Selecting previously unselected package flex.
Preparing to unpack .../flex_2.5.35-10.1ubuntu2_amd64.deb ...
Unpacking flex (2.5.35-10.1ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
Selecting previously unselected package gawk.
(Reading database ... 122485 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package libdw1:amd64.
Preparing to unpack .../libdw1_0.158-0ubuntu5.2_amd64.deb ...
Unpacking libdw1:amd64 (0.158-0ubuntu5.2) ...
Selecting previously unselected package libexpat1-dev:amd64.
Preparing to unpack .../libexpat1-dev_2.1.0-4ubuntu1_amd64.deb ...
Unpacking libexpat1-dev:amd64 (2.1.0-4ubuntu1) ...
Selecting previously unselected package libpython2.7-dev:amd64.
Preparing to unpack .../libpython2.7-dev_2.7.6-8_amd64.deb ...
Unpacking libpython2.7-dev:amd64 (2.7.6-8) ...
Selecting previously unselected package libunwind8.
Preparing to unpack .../libunwind8_1.1-2.2ubuntu3_amd64.deb ...
Unpacking libunwind8 (1.1-2.2ubuntu3) ...
Selecting previously unselected package asciidoc.
Preparing to unpack .../asciidoc_8.6.9-2ubuntu1_all.deb ...
Unpacking asciidoc (8.6.9-2ubuntu1) ...
Selecting previously unselected package libbison-dev:amd64.
Preparing to unpack .../libbison-dev_2%3a3.0.2.dfsg-2_amd64.deb ...
Unpacking libbison-dev:amd64 (2:3.0.2.dfsg-2) ...
Selecting previously unselected package bison.
Preparing to unpack .../bison_2%3a3.0.2.dfsg-2_amd64.deb ...
Unpacking bison (2:3.0.2.dfsg-2) ...
Selecting previously unselected package libstdc++-4.8-dev:amd64.
Preparing to unpack .../libstdc++-4.8-dev_4.8.2-19ubuntu1_amd64.deb ...
Unpacking libstdc++-4.8-dev:amd64 (4.8.2-19ubuntu1) ...
Selecting previously unselected package g++-4.8.
Preparing to unpack .../g++-4.8_4.8.2-19ubuntu1_amd64.deb ...
Unpacking g++-4.8 (4.8.2-19ubuntu1) ...
Selecting previously unselected package g++.
Preparing to unpack .../g++_4%3a4.8.2-1ubuntu6_amd64.deb ...
Unpacking g++ (4:4.8.2-1ubuntu6) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../dpkg-dev_1.17.5ubuntu5.3_all.deb ...
Unpacking dpkg-dev (1.17.5ubuntu5.3) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) ...
Selecting previously unselected package po-debconf.
Preparing to unpack .../po-debconf_1.0.16+nmu2ubuntu1_all.deb ...
Unpacking po-debconf (1.0.16+nmu2ubuntu1) ...
Selecting previously unselected package dh-apparmor.
Preparing to unpack .../dh-apparmor_2.8.95~2430-0ubuntu5.1_all.deb ...
Unpacking dh-apparmor (2.8.95~2430-0ubuntu5.1) ...
Selecting previously unselected package debhelper.
Preparing to unpack .../debhelper_9.20131227ubuntu1_all.deb ...
Unpacking debhelper (9.20131227ubuntu1) ...
Selecting previously unselected package libosp5.
Preparing to unpack .../libosp5_1.5.2-10ubuntu3_amd64.deb ...
Unpacking libosp5 (1.5.2-10ubuntu3) ...
Selecting previously unselected package libostyle1c2.
Preparing to unpack .../libostyle1c2_1.4devel1-21_amd64.deb ...
Unpacking libostyle1c2 (1.4devel1-21) ...
Selecting previously unselected package openjade.
Preparing to unpack .../openjade_1.4devel1-21_amd64.deb ...
Unpacking openjade (1.4devel1-21) ...
Selecting previously unselected package sgml-data.
Preparing to unpack .../sgml-data_2.0.9-1_all.deb ...
Unpacking sgml-data (2.0.9-1) ...
Selecting previously unselected package docbook-xml.
Preparing to unpack .../docbook-xml_4.5-7.2_all.deb ...
Unpacking docbook-xml (4.5-7.2) ...
Selecting previously unselected package docbook-dsssl.
Preparing to unpack .../docbook-dsssl_1.79-7ubuntu1_all.deb ...
Unpacking docbook-dsssl (1.79-7ubuntu1) ...
Selecting previously unselected package tex-common.
Preparing to unpack .../tex-common_4.04_all.deb ...
Unpacking tex-common (4.04) ...
Selecting previously unselected package libptexenc1.
Preparing to unpack .../libptexenc1_2013.20130729.30972-2build3_amd64.deb ...
Unpacking libptexenc1 (2013.20130729.30972-2build3) ...
Selecting previously unselected package texlive-binaries.
Preparing to unpack .../texlive-binaries_2013.20130729.30972-2build3_amd64.deb ...
Unpacking texlive-binaries (2013.20130729.30972-2build3) ...
Selecting previously unselected package luatex.
Preparing to unpack .../luatex_0.76.0-3ubuntu1_amd64.deb ...
Unpacking luatex (0.76.0-3ubuntu1) ...
Selecting previously unselected package texlive-base.
Preparing to unpack .../texlive-base_2013.20140215-1_all.deb ...
Unpacking texlive-base (2013.20140215-1) ...
Selecting previously unselected package texlive-latex-base.
Preparing to unpack .../texlive-latex-base_2013.20140215-1_all.deb ...
Unpacking texlive-latex-base (2013.20140215-1) ...
Selecting previously unselected package texlive-fonts-recommended.
Preparing to unpack .../texlive-fonts-recommended_2013.20140215-1_all.deb ...
Unpacking texlive-fonts-recommended (2013.20140215-1) ...
Selecting previously unselected package texlive-latex-recommended.
Preparing to unpack .../texlive-latex-recommended_2013.20140215-1_all.deb ...
Unpacking texlive-latex-recommended (2013.20140215-1) ...
Selecting previously unselected package texlive-generic-recommended.
Preparing to unpack .../texlive-generic-recommended_2013.20140215-1_all.deb ...
Unpacking texlive-generic-recommended (2013.20140215-1) ...
Selecting previously unselected package tipa.
Preparing to unpack .../tipa_2%3a1.3-19_all.deb ...
Unpacking tipa (2:1.3-19) ...
Selecting previously unselected package jadetex.
Preparing to unpack .../jadetex_3.13-14_all.deb ...
Unpacking jadetex (3.13-14) ...
Selecting previously unselected package lynx-cur.
Preparing to unpack .../lynx-cur_2.8.8pre4-1_amd64.deb ...
Unpacking lynx-cur (2.8.8pre4-1) ...
Selecting previously unselected package lynx.
Preparing to unpack .../lynx_2.8.8pre4-1_all.deb ...
Unpacking lynx (2.8.8pre4-1) ...
Selecting previously unselected package libsgmls-perl.
Preparing to unpack .../libsgmls-perl_1.03ii-32_all.deb ...
Unpacking libsgmls-perl (1.03ii-32) ...
Selecting previously unselected package sgmlspl.
Preparing to unpack .../sgmlspl_1.03ii-32_all.deb ...
Unpacking sgmlspl (1.03ii-32) ...
Selecting previously unselected package libsp1c2.
Preparing to unpack .../libsp1c2_1.3.4-1.2.1-47.3ubuntu1_amd64.deb ...
Unpacking libsp1c2 (1.3.4-1.2.1-47.3ubuntu1) ...
Selecting previously unselected package sp.
Preparing to unpack .../sp_1.3.4-1.2.1-47.3ubuntu1_amd64.deb ...
Unpacking sp (1.3.4-1.2.1-47.3ubuntu1) ...
Selecting previously unselected package docbook-utils.
Preparing to unpack .../docbook-utils_0.6.14-3ubuntu1_all.deb ...
Unpacking docbook-utils (0.6.14-3ubuntu1) ...
Selecting previously unselected package docbook-xsl.
Preparing to unpack .../docbook-xsl_1.78.1+dfsg-1_all.deb ...
Unpacking docbook-xsl (1.78.1+dfsg-1) ...
Selecting previously unselected package kernel-wedge.
Preparing to unpack .../kernel-wedge_2.87ubuntu1_all.deb ...
Unpacking kernel-wedge (2.87ubuntu1) ...
Selecting previously unselected package libelf-dev:amd64.
Preparing to unpack .../libelf-dev_0.158-0ubuntu5.2_amd64.deb ...
Unpacking libelf-dev:amd64 (0.158-0ubuntu5.2) ...
Selecting previously unselected package libdw-dev:amd64.
Preparing to unpack .../libdw-dev_0.158-0ubuntu5.2_amd64.deb ...
Unpacking libdw-dev:amd64 (0.158-0ubuntu5.2) ...
Selecting previously unselected package libiberty-dev:amd64.
Preparing to unpack .../libiberty-dev_20131116-1_amd64.deb ...
Unpacking libiberty-dev:amd64 (20131116-1) ...
Selecting previously unselected package zlib1g-dev:amd64.
Preparing to unpack .../zlib1g-dev_1%3a1.2.8.dfsg-1ubuntu1_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...
Selecting previously unselected package libpng12-dev.
Preparing to unpack .../libpng12-dev_1.2.50-1ubuntu2_amd64.deb ...
Unpacking libpng12-dev (1.2.50-1ubuntu2) ...
Selecting previously unselected package libslang2-dev:amd64.
Preparing to unpack .../libslang2-dev_2.2.4-15ubuntu1_amd64.deb ...
Unpacking libslang2-dev:amd64 (2.2.4-15ubuntu1) ...
Selecting previously unselected package libnewt-dev:amd64.
Preparing to unpack .../libnewt-dev_0.52.15-2ubuntu5_amd64.deb ...
Unpacking libnewt-dev:amd64 (0.52.15-2ubuntu5) ...
Selecting previously unselected package libpci-dev.
Preparing to unpack .../libpci-dev_1%3a3.2.1-1ubuntu5_amd64.deb ...
Unpacking libpci-dev (1:3.2.1-1ubuntu5) ...
Selecting previously unselected package libpython-dev:amd64.
Preparing to unpack .../libpython-dev_2.7.5-5ubuntu3_amd64.deb ...
Unpacking libpython-dev:amd64 (2.7.5-5ubuntu3) ...
Selecting previously unselected package libunwind8-dev.
Preparing to unpack .../libunwind8-dev_1.1-2.2ubuntu3_amd64.deb ...
Unpacking libunwind8-dev (1.1-2.2ubuntu3) ...
Selecting previously unselected package libxml2-utils.
Preparing to unpack .../libxml2-utils_2.9.1+dfsg1-3ubuntu4.4_amd64.deb ...
Unpacking libxml2-utils (2.9.1+dfsg1-3ubuntu4.4) ...
Selecting previously unselected package makedumpfile.
Preparing to unpack .../makedumpfile_1.5.5-2ubuntu1.1_amd64.deb ...
Unpacking makedumpfile (1.5.5-2ubuntu1.1) ...
Selecting previously unselected package python2.7-dev.
Preparing to unpack .../python2.7-dev_2.7.6-8_amd64.deb ...
Unpacking python2.7-dev (2.7.6-8) ...
Selecting previously unselected package python-dev.
Preparing to unpack .../python-dev_2.7.5-5ubuntu3_amd64.deb ...
Unpacking python-dev (2.7.5-5ubuntu3) ...
Selecting previously unselected package sharutils.
Preparing to unpack .../sharutils_1%3a4.14-1ubuntu1_amd64.deb ...
Unpacking sharutils (1:4.14-1ubuntu1) ...
Selecting previously unselected package transfig.
Preparing to unpack .../transfig_1%3a3.2.5.e-1ubuntu1_amd64.deb ...
Unpacking transfig (1:3.2.5.e-1ubuntu1) ...
Selecting previously unselected package xsltproc.
Preparing to unpack .../xsltproc_1.1.28-2build1_amd64.deb ...
Unpacking xsltproc (1.1.28-2build1) ...
Selecting previously unselected package xmlto.
Preparing to unpack .../xmlto_0.0.25-2_amd64.deb ...
Unpacking xmlto (0.0.25-2) ...
Selecting previously unselected package libaudit-dev.
Preparing to unpack .../libaudit-dev_1%3a2.3.2-2ubuntu1_amd64.deb ...
Unpacking libaudit-dev (1:2.3.2-2ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 11 added doc-base files...
Processing triggers for sgml-base (1.26+nmu4ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up m4 (1.4.17-2ubuntu1) ...
Setting up libfl-dev:amd64 (2.5.35-10.1ubuntu2) ...
Setting up flex (2.5.35-10.1ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up libdw1:amd64 (0.158-0ubuntu5.2) ...
Setting up libexpat1-dev:amd64 (2.1.0-4ubuntu1) ...
Setting up libpython2.7-dev:amd64 (2.7.6-8) ...
Setting up libunwind8 (1.1-2.2ubuntu3) ...
Setting up asciidoc (8.6.9-2ubuntu1) ...
Setting up libbison-dev:amd64 (2:3.0.2.dfsg-2) ...
Setting up bison (2:3.0.2.dfsg-2) ...
update-alternatives: using /usr/bin/bison.yacc to provide /usr/bin/yacc (yacc) in auto mode
Setting up libstdc++-4.8-dev:amd64 (4.8.2-19ubuntu1) ...
Setting up g++-4.8 (4.8.2-19ubuntu1) ...
Setting up g++ (4:4.8.2-1ubuntu6) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up dpkg-dev (1.17.5ubuntu5.3) ...
Setting up build-essential (11.6ubuntu6) ...
Setting up po-debconf (1.0.16+nmu2ubuntu1) ...
Setting up dh-apparmor (2.8.95~2430-0ubuntu5.1) ...
Setting up debhelper (9.20131227ubuntu1) ...
Setting up libosp5 (1.5.2-10ubuntu3) ...
Setting up libostyle1c2 (1.4devel1-21) ...
Setting up openjade (1.4devel1-21) ...
Setting up sgml-data (2.0.9-1) ...
Setting up tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up libptexenc1 (2013.20130729.30972-2build3) ...
Setting up texlive-binaries (2013.20130729.30972-2build3) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... done.
Setting up luatex (0.76.0-3ubuntu1) ...
texlive-base is not ready, cannot create formats
Setting up texlive-base (2013.20140215-1) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
/usr/bin/tl-paper: setting paper size for dvips to a4.
/usr/bin/tl-paper: setting paper size for dvipdfmx to a4.
/usr/bin/tl-paper: setting paper size for xdvi to a4.
/usr/bin/tl-paper: setting paper size for pdftex to a4.
/usr/bin/tl-paper: setting paper size for dvipdfmx to letter.
/usr/bin/tl-paper: setting paper size for dvips to letter.
/usr/bin/tl-paper: setting paper size for pdftex to letter.
/usr/bin/tl-paper: setting paper size for xdvi to letter.
Running mktexlsr. This may take some time... done.
Building format(s) --refresh.
    This may take some time... done.
Running mktexlsr. This may take some time... done.
Building format(s) --all.
    This may take some time... done.
Setting up lynx-cur (2.8.8pre4-1) ...
update-alternatives: using /usr/bin/lynx to provide /usr/bin/www-browser (www-browser) in auto mode
Setting up lynx (2.8.8pre4-1) ...
Setting up libsgmls-perl (1.03ii-32) ...
Setting up sgmlspl (1.03ii-32) ...
Setting up libsp1c2 (1.3.4-1.2.1-47.3ubuntu1) ...
Setting up sp (1.3.4-1.2.1-47.3ubuntu1) ...
Setting up docbook-xsl (1.78.1+dfsg-1) ...
Setting up kernel-wedge (2.87ubuntu1) ...
Setting up libelf-dev:amd64 (0.158-0ubuntu5.2) ...
Setting up libdw-dev:amd64 (0.158-0ubuntu5.2) ...
Setting up libiberty-dev:amd64 (20131116-1) ...
Setting up zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...
Setting up libpng12-dev (1.2.50-1ubuntu2) ...
Setting up libslang2-dev:amd64 (2.2.4-15ubuntu1) ...
Setting up libnewt-dev:amd64 (0.52.15-2ubuntu5) ...
Setting up libpci-dev (1:3.2.1-1ubuntu5) ...
Setting up libpython-dev:amd64 (2.7.5-5ubuntu3) ...
Setting up libunwind8-dev (1.1-2.2ubuntu3) ...
Setting up libxml2-utils (2.9.1+dfsg1-3ubuntu4.4) ...
Setting up makedumpfile (1.5.5-2ubuntu1.1) ...
Setting up python2.7-dev (2.7.6-8) ...
Setting up python-dev (2.7.5-5ubuntu3) ...
Setting up sharutils (1:4.14-1ubuntu1) ...
Setting up transfig (1:3.2.5.e-1ubuntu1) ...
Setting up xsltproc (1.1.28-2build1) ...
Setting up libaudit-dev (1:2.3.2-2ubuntu1) ...
Processing triggers for sgml-base (1.26+nmu4ubuntu1) ...
Setting up docbook-xml (4.5-7.2) ...
Processing triggers for sgml-base (1.26+nmu4ubuntu1) ...
Setting up xmlto (0.0.25-2) ...
Setting up docbook-dsssl (1.79-7ubuntu1) ...
Processing triggers for tex-common (4.04) ...
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Setting up texlive-generic-recommended (2013.20140215-1) ...
Setting up texlive-latex-base (2013.20140215-1) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
    This may take some time... done.
Setting up texlive-fonts-recommended (2013.20140215-1) ...
Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Setting up texlive-latex-recommended (2013.20140215-1) ...
Setting up tipa (2:1.3-19) ...
Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Setting up jadetex (3.13-14) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/40jadetex.cnf.
    This may take some time... done.
Processing triggers for sgml-base (1.26+nmu4ubuntu1) ...
Setting up docbook-utils (0.6.14-3ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ gedit btusb.c
The program 'gedit' is currently not installed. You can install it by typing:
sudo apt-get install gedit
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dnsmasq-base firefox-locale-en gir1.2-gnomebluetooth-1.0 gnome-bluetooth
  gnome-power-manager gnome-user-share gucharmap indicator-bluetooth
  indicator-keyboard indicator-power iputils-arping libgee2
  libgucharmap-2-90-7 libmbim-glib0 libmm-glib0 libmnl0
  libnetfilter-conntrack3 libnl-route-3-200 libnm-glib-vpn1 libqmi-glib0
  libtimezonemap1 linux-image-generic mobile-broadband-provider-info
  modemmanager network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome obexd-client pptp-linux usb-modeswitch
  usb-modeswitch-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0
Suggested packages:
  gedit-plugins
The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 644 kB of archives.
After this operation, 6,480 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ph.archive.ubuntu.com/ubuntu/ trusty/main gedit-common all 3.10.4-0ubuntu4 [146 kB]
Get:2 http://ph.archive.ubuntu.com/ubuntu/ trusty/main gir1.2-peas-1.0 amd64 1.8.1-2ubuntu2 [5,566 B]
Get:3 http://ph.archive.ubuntu.com/ubuntu/ trusty/main gedit amd64 3.10.4-0ubuntu4 [478 kB]
Get:4 http://ph.archive.ubuntu.com/ubuntu/ trusty/main gir1.2-gtksource-3.0 amd64 3.10.2-0ubuntu1 [13.9 kB]
Fetched 644 kB in 5s (126 kB/s)                
Selecting previously unselected package gedit-common.
(Reading database ... 135338 files and directories currently installed.)
Preparing to unpack .../gedit-common_3.10.4-0ubuntu4_all.deb ...
Unpacking gedit-common (3.10.4-0ubuntu4) ...
Selecting previously unselected package gir1.2-peas-1.0.
Preparing to unpack .../gir1.2-peas-1.0_1.8.1-2ubuntu2_amd64.deb ...
Unpacking gir1.2-peas-1.0 (1.8.1-2ubuntu2) ...
Selecting previously unselected package gedit.
Preparing to unpack .../gedit_3.10.4-0ubuntu4_amd64.deb ...
Unpacking gedit (3.10.4-0ubuntu4) ...
Selecting previously unselected package gir1.2-gtksource-3.0.
Preparing to unpack .../gir1.2-gtksource-3.0_3.10.2-0ubuntu1_amd64.deb ...
Unpacking gir1.2-gtksource-3.0 (3.10.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.42.1-0ubuntu1~14.04~ricotz1) ...
Processing triggers for libglib2.0-0:amd64 (2.42.1-0ubuntu1~14.04~ricotz1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1+elementary2~ubuntu14.04.1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up gedit-common (3.10.4-0ubuntu4) ...
Setting up gir1.2-peas-1.0 (1.8.1-2ubuntu2) ...
Setting up gedit (3.10.4-0ubuntu4) ...
Setting up gir1.2-gtksource-3.0 (3.10.2-0ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ gedit btusb.c
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ sudo gedit btusb.c

(gedit:17215): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ sudo gedit btusb.c

(gedit:17230): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ gedit btusb.c

(gedit:17262): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/polochamps/.local/share/recently-used.xbel', but the parser failed: Failed to open file '/home/polochamps/.local/share/recently-used.xbel': Permission denied.
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ gedit btusb.c
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ locate linux-3.13.0
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE$ cd
polochamps@POLOCHAMPS-DESK:~$ locate linux-3.13.0
polochamps@POLOCHAMPS-DESK:~$ 


```

---

### Post by jeremy31 on 2015-02-15
It might be that this command was overlooked before trying gedit```
[COLOR=#000000][FONT=Ubuntu Mono]cd linux-3.13.0/drivers/bluetooth/
``` hopefully then ```
sudo gedit btusb.c
``` works like it should[/FONT][/COLOR]

---

### Post by polochamps on 2015-02-16
> **jeremy31 said:**
> It might be that this command was overlooked before trying gedit```
[COLOR=#000000][FONT=Ubuntu Mono]cd linux-3.13.0/drivers/bluetooth/[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] hopefully then ```
sudo gedit btusb.c
``` works like it should[/FONT][/COLOR]

It's really strange that after all the progress I'd shown in the terminal log, there is no downloaded file in the LINUX_SOURCE folder.
What I did now was to execute each command at a time:

```
sudo apt-get build-dep linux-image-$(uname -r)
``` 
```
apt-get source linux-image-$(uname -r)
``` 
```
cd linux-3.13.0/drivers/bluetooth/
```

After these commands were executed, I can finally see a folder and files on the LINUX_SOURCE folder.
Then did this

```
sudo gedit btusb.c[COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]
```

up to

```
sudo modprobe btusb[COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]
```

Where the bluetooth icon finally appeared and was still detected after a restart.

First of all I would like to give my sincere thanks for your time and patience. It was very clear to me that the kind of support I got was not only helpful but very informative as well.

Just a question. Would a kernel update mess this up? I was pointing out the incoming HWE (14.04.2)

Many thanks Jeremy!


UPDATE: Ooops. It seems that I'm back with the same problem as before. The bluetooth adapter is detected in my computer (like it should) but during actual usage, it cannot detect any bluetooth device.

---

### Post by jeremy31 on 2015-02-16
Have you tried the btusb.c edit with the ```
[COLOR=#000000]{ USB_DEVICE(0x0b05, 0x17bf), .driver_info = BTUSB_BCM_PATCHRAM }
``` and I edited post 33 to add a command in case there is an error in dmesg ```
dmesg | grep btusb
```

The command is ```
[/COLOR]cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
``` and it should be run before ```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```

---

### Post by polochamps on 2015-02-16
```
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth$ dmesg | grep btusb
[    3.037784] btusb: module verification failed: signature and/or  required key missing - tainting kernel
[    3.038490] usbcore: registered new interface driver btusb
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth$ make -C /lib/modules/$(uname -r)/build M=$PWD modules
make: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
  CC [M]  /home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth/btusb.o
/home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth/btusb.c:109:2: error: expected &#8216;}&#8217; before &#8216;{&#8217; token
  { USB_DEVICE(0x04ca, 0x2003) },
  ^
make[1]: *** [/home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth/btusb.o] Error 1
make: *** [_module_/home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'


```

Which is correct? (Please take note of the bold characters) - 0x17**c**f vs [COLOR=#000000]0x17**b**f[/COLOR]

Post #33
```
{ USB_DEVICE(0x0b05, 0x17cf) }
```

or

Post #41
```
[COLOR=#000000]{ USB_DEVICE(0x0b05, 0x17bf), .driver_info = BTUSB_BCM_PATCHRAM }[/COLOR]
```

Thank you

---

### Post by jeremy31 on 2015-02-16
> **polochamps said:**
> ```
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth$ dmesg | grep btusb
[    3.037784] btusb: module verification failed: signature and/or  required key missing - tainting kernel
[    3.038490] usbcore: registered new interface driver btusb
polochamps@POLOCHAMPS-DESK:~/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth$ make -C /lib/modules/$(uname -r)/build M=$PWD modules
make: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
  CC [M]  /home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth/btusb.o
/home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth/btusb.c:109:2: error: expected &#8216;}&#8217; before &#8216;{&#8217; token
  { USB_DEVICE(0x04ca, 0x2003) },
  ^
make[1]: *** [/home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth/btusb.o] Error 1
make: *** [_module_/home/polochamps/LINUX_SOURCE/linux-3.13.0/drivers/bluetooth] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'


```

Which is correct (Please take note of the bold characters?) - 0x17**c**f vs [COLOR=#000000]0x17**b**f[/COLOR]

Post #33
```
{ USB_DEVICE(0x0b05, 0x17cf) }
```

or

Post #41
```
[COLOR=#000000]{ USB_DEVICE(0x0b05, 0x17bf), .driver_info = BTUSB_BCM_PATCHRAM }[/COLOR]
```

Thank you
Should be cf and could you copy the part of btusb.c that you edited as the make command found a syntax error

And this command before a make might get rid of module verification when run before ```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
``` ```
cp /boot/config-$(uname -r) .config
```
Run the copy config before the make---modules.

---

### Post by HeavyHaulTrucker on 2015-03-16
[B]If you will follow these instructions, I think we can mark this as solved.
[/B]
I am running Zorin Core 9 -- a "customized" Ubuntu 14.04 flavor -- on an Asus ROG G751JM high-end gaming laptop that has the Broadcom 4352 combination wifi/ bluetooth card.  And I have just succeeded in bringing up the wireless and bluetooth with very good performance.  So I wanted to let everyone know how I did it -- it's not very difficult.

**Step 1:**  Install the Ubuntu 3.19 kernel.  This is a very simple and painless process, and is detailed in this article --->  [http://ubuntuhandbook.org/index.php/2015/02/upgrade-linux-kernel-3-19-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2015/02/upgrade-linux-kernel-3-19-ubuntu-14-04/).  Follow the simple instructions, and if you are presently using the "generic" kernel now then download & install the "generic" 3.19 kernel -- I had some slight trouble with the "low latency" kernel, but the "generic" kernel works great -- and it supports the bluetooth device.

**Step 2:**  I have already created the required hcd firmware file for the **0b05:17fd** usb bluetooth devices; the same file will also work for the 0b05:17cf devices, but will probably have to be renamed.  I have put it in my dropbox, and it can be downloaded from this link --->  [https://www.dropbox.com/s/pt356jfaoonqt4z/BCM20702A0-13d3-3404.hcd?dl=0](https://www.dropbox.com/s/pt356jfaoonqt4z/BCM20702A0-13d3-3404.hcd?dl=0).  Download it to your system, and make sure to place it into the "**/lib/firmware/brcm**" directory (you will need to be root to copy it into this system directory).  ***If you have the 0b05:17cf device, and your bluetooth comes up but won't see anything, then simply issue the command "dmesg | grep firmware" to find out what file name the firmware loader was looking for -- and simply rename the firmware file to what the loader is looking for.***

**Step 3:**  Reboot your system into the new 3.19 kernel and, as long as you followed the instructions, you should be greeted by functioning bluetooth that recognizes your devices and will connect to them.

---

### Post by SA6 on 2015-04-27
I have the same problem on Ubuntu 14.04 

> lsmod | grep bluetooth
bluetooth             446409  11 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth


> dmesg | grep -i bluetooth
[   18.127591] Bluetooth: Core ver 2.19
[   18.127604] Bluetooth: HCI device and connection manager initialized
[   18.127609] Bluetooth: HCI socket layer initialized
[   18.127611] Bluetooth: L2CAP socket layer initialized
[   18.127629] Bluetooth: SCO socket layer initialized
[   46.325352] Bluetooth: RFCOMM TTY layer initialized
[   46.325372] Bluetooth: RFCOMM socket layer initialized
[   46.325376] Bluetooth: RFCOMM ver 1.11
[   46.334998] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.335000] Bluetooth: BNEP filters: protocol multicast
[   46.335003] Bluetooth: BNEP socket layer initialized


> uname -r
3.16.0-34-generic


> lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 105b:e065  
Bus 003 Device 004: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 003: ID 1915:7777 Nordic Semiconductor ASA 
Bus 003 Device 009: ID 045e:02ae Microsoft Corp. Xbox NUI Camera
Bus 003 Device 008: ID 045e:02b0 Microsoft Corp. Xbox NUI Motor
Bus 003 Device 007: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 006: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 002: ID 5986:029d Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any suggestions? I've tried using hex2hcd to convert my windows drivers, but that didn't work.

---

### Post by jeremy31 on 2015-04-27
> **SA6 said:**
> I have the same problem on Ubuntu 14.04 









Any suggestions? I've tried using hex2hcd to convert my windows drivers, but that didn't work.

[http://ubuntuforums.org/showthread.php?t=2274335&p=13273812#post13273812](http://ubuntuforums.org/showthread.php?t=2274335&p=13273812#post13273812)

Your kernel doesn't support loading the hcd file, but with my modified code it should work fine

---

### Post by luismita on 2015-06-24
Hi everyone, I've tried everything here but sadly didn't works for me (fresh install of ubuntu 14.04 with kernel 3.16.0-41-lowlatency), fortunately found this: [http://plugable.com/2014/06/23/plugable-usb-bluetooth-adapter-solving-hfphsp-profile-issues-on-linux](http://plugable.com/2014/06/23/plugable-usb-bluetooth-adapter-solving-hfphsp-profile-issues-on-linux) and it works for me. I flowed the instructions but after reboot the Bluetooth icon didn't show up until reinstall the wireless driver and reboot. It seams to work even with newer kernels (3.18+). Let me know if this solve the problem. Thanks!

---

### Post by Akul_Narang on 2015-07-16
Hi jeremy31,

I'm facing problem with my bluetooth as it is not able to find/detect BT  devices. I'm using ubuntu 14.04 install on HP envy 15 notebook.

Output of dmesg | grep Bluetooth:

[   21.394043] Bluetooth: Core ver 2.17
[   21.394058] Bluetooth: HCI device and connection manager initialized
[   21.394065] Bluetooth: HCI socket layer initialized
[   21.394067] Bluetooth: L2CAP socket layer initialized
[   21.394070] Bluetooth: SCO socket layer initialized
[   21.478670] Bluetooth: can't load firmware, may not work correctly
[   23.483179] Bluetooth: hci0 command 0x1003 tx timeout
[   29.072180] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.072184] Bluetooth: BNEP filters: protocol multicast
[   29.072191] Bluetooth: BNEP socket layer initialized
[   29.076724] Bluetooth: RFCOMM TTY layer initialized
[   29.076733] Bluetooth: RFCOMM socket layer initialized
[   29.076737] Bluetooth: RFCOMM ver 1.11

Output of uname -r:
3.13.0-57-generic

---

### Post by jeremy31 on 2015-07-16
Post the result of ```
lsusb
```

---

### Post by Akul_Narang on 2015-07-17
> **jeremy31 said:**
> Post the result of ```
lsusb
```



Bus 001 Device 005: ID 0a5c:216c Broadcom Corp. 
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. 
Bus 001 Device 003: ID 0bda:5775 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The previous problem is resolved automatically as I switched to windows and then back to ubuntu.
I'm facing a new problem that the device is paired but not connected. I want to stream data from Android device to computer via bluetooth for which connection is necessary.
Also the file BCM43142A0-0a5c-216c.hcd disabled the bluetooth and the indicator icon from the tray also disappeared.

---

