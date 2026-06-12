---
title: "zd1211rw couldn't load firmware problem on Hardy Server fresh installation"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by yawong on 2008-05-25
Hello people,

Just started using Ubuntu server, and enjoyed the juice out of Hardy so far. Now I am trying to install a Hardy server on a old dual PIII machine, and run into a big headache.

First of all, I have a D-Link TX530+ NIC which Hardy does not autoconfigure at the installation process. So wired network is NO-GO.

Next, I have a Airlink AWLL3026 USB WIFI NIC which should be working out of box according to the ubuntu users. But I am always seeing DHCP failure after the ESSID, WEP is entered.

On the busybox tty4 which is the output of the installation process, I see several times of following message before the DHCP failure.


[DATE&TIME] kernel: [ XXXX.XXXXXX] usb 1-1: couldn't load firmware Error number -2
[DATE&TIME] firmware_helper[XXXX]: main: error loading '/lib/firmware/zd1211/zd1211b_ub'for device 'devices/pci0000:00/0000:00:07.2/usb1/1-1/firmware/1- with driver '(unknown)'


Is there any solution for this? Since this is the beginning of the installation process, there is no much thing can be done.
And if I ignore this error and continue the installation, then it will turn out as interruption of installation due to needed packages could not be download off the network. (It will hang when the installer try to install kernel-server.)


Does it mean I need to buy a new realtek NIC for the installation?

If anybody has solution for the wireless network card issue, please let me know.

Thanks a lot!

---

### Post by chili555 on 2008-05-25
> error loading '/lib/firmware/zd1211/zd1211b_ub'I think it's looking in the wrong place. A way to fix this is to put a copy where it is looking.```
sudo su
cd /lib/firmware
mkdir zd1211
updatedb
locate zd1211u_ub
```Whatever the last line is, is the one that corresponds to the kernel version you are running. For example, on my computer:```
chili@LAPTOP60:~$ locate zd1211b_ub
/lib/firmware/2.6.20-16-generic/zd1211/zd1211b_ub
/lib/firmware/2.6.22-14-generic/zd1211/zd1211b_ub
/lib/firmware/2.6.24-16-generic/zd1211/zd1211b_ub
```So, we want to copy the most recent firmware to the directory we created. Substitute your details if you are not running *2.6.24-16-generic.*```
cp /lib/firmware/2.6.24-16-generic/zd1211/zd1211b_ub /lib/firmware/zd1211
```Then see if it works.

---

### Post by yawong on 2008-05-25
OK. Thanks for Chili555's advise, but as I stated ealier, I am in the process of installing new system. The partitioning and stuff has not been done yet at this point, and the system is the installation Busybox means minimal things has been loaded on to the RAMDisk. No locate nor the driver exists.

So what I did here.

Chili555's advise gave me hint that, yeah, I can just copy needed files into the RAMDisk File System.

So I went on the sourceforge driver download page. (With my Windows Laptop)

[http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875](http://sourceforge.net/project/showfiles.php?group_id=129083&package_id=187875)

Downloaded the version 1.4 driver, unzip, untar and saved the files on a folder on the desktop.

And since I have a CDRW, so I burned a cd with the files I extract.

Luckly, I have two CDROM drives in my server machine, so mounting the second CDROM I just burn was no problem.
(Well, if you have onely one cdrom drive, press Alt-2 and get into the shell, unmount the installation cdrom, and mount the driver cd to copy the files into the system.)

After the drivers are copied into the file system(/lib/firmware/zd1211/), press ALT-1 to back to the installation process. Now the WIFI network can be searched.

---

### Post by dmcbob on 2008-11-04
I just compiled and installed intrepid with a few minor modifications and ran into this problem (couldn't load firmware). It was a simple fix to copy /lib/firmware/2.6.24-21-generic/zd1211* to /lib/firmware/$(uname -r).

I'm wondering what I did wrong at compile time. Is there an option I missed when running "make menuconfig/xconfig"? Did I not have all the right sources?

Thanks for any replies.

[EDIT]

I looked in the sources that I built from and read this in drivers/net/wireless/zd1211/Kconfig:
 "Device firmware is required alongside this driver. You can download the firmware distribution from 
[http://zd1211.ath.cx/get-firmware]("http://zd1211.ath.cx/get-firmware")"

Anyways...all I wanted was to start with the generic installation and then make my own mods. Is there not a simple way to do that?

[/EDIT]

---

