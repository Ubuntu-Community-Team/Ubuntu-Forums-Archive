---
title: "ar9271 detected, but not used"
date: 2013-10-31
forum: Networking &amp; Wireless
---

### Post by al3xmail on 2013-10-31
So I recently bought an external wifi card for my ubuntu laptop, as I have one for my windows machine and it works great.
The problem is that ubuntu will not use the wifi card over the internal. When I try to 'modprobe -r' my internal, the usb does not take over.

```
iwconfig
mlan0     IEEE 802.11abgn  ESSID:"SKY***CB"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 7C:4C:A5:30:8A:2D   
          Bit Rate=78 Mb/s   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.


```
Here is an lsusb:
```

Bus 001 Device 002: ID 0424:3503 Standard Microsystems Corp. 
Bus 003 Device 002: ID 058f:b001 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]


```
as you can see, it detects the AR9271.

Ubuntu version is 3.4.0 armv7l

Thank you ^-^

---

### Post by chili555 on 2013-10-31
The driver for your device, ath9k_htc, requires firmware. In many cases, it is not installed and the wireless device won't start. You might check the message logs:```
dmesg | grep ath9
```If the problem is firmware, install it with:```
sudo apt-get install linux-firmware
sudo modprobe -r ath9k_htc
sudo modprobe ath9k_htc
```Then, I'd blacklist the internal, although all evidence suggests it's working quite well:```
sudo -i
echo "blacklist <internal_driver>"  >>  /etc/modprobe.d/blacklist.conf
exit
```Of course, substitute the actual internal driver here. Now unload the internal:```
sudo modprobe -r <internal_driver>
```Check to see if the USB has created an interface, probably wlan1:```
iwconfig
```Does it scan?```
sudo iwlist wlan1 scan
```If it scans, it will probably connect.

I know almost nothing about 3.4.0 armv7l, except that it isn't Ubuntu. There is a chance that ath9k_htc isn't present in 3.4.0 armv7l which is a whole new, interesting problem!

---

### Post by al3xmail on 2013-10-31
Thanks for the tips, but alass, it seems to fail at step 1.
I think the ath9k_htc drivers are not in armv7l & I can't compile compat-wireless(or drivers) for the ath9k_htc drivers either.

```

sudo modprobe -r ath9k_htc
FATAL: Module ath9k_htc not found.

```

---

### Post by chili555 on 2013-10-31
> I can't compile compat-wireless(or drivers) for the ath9k_htc drivers either.And why not? What have you tried so far?

---

### Post by al3xmail on 2013-10-31
I get build error's upon using 'make'.

I have tried:
Most recent version of compat-drivers.
An older version of compat-drivers.
I know it should be wlan0(and the internal is mlan0) so I changed Wcid to use wlan0. Nothing.
I have build essential too.

EDIT:
Error
```

make -C /lib/modules/3.4.0/build M=/home/user/Downloads/compat-wireless-3.6.8-1 modules
make: *** /lib/modules/3.4.0/build: No such file or directory.  Stop.
make: *** [modules] Error 2


```

---

### Post by chili555 on 2013-10-31
It appears that you do not have linux-headers, however. Please install and try again.

---

### Post by al3xmail on 2013-10-31
It seems their are many linux headers, what one do I choose?

---

### Post by chili555 on 2013-10-31
> **al3xmail said:**
> It seems their are many linux headers, what one do I choose?In Ubuntu, I'd select linux-headers-generic, which is a meta-package that installs whatever is needed automagically. As a temporary step, you could install linux-headers matching your running kernel version; i.e. linux-headers-3.4.0 armv7l. As I said, I know about nothing about  3.4.0 armv7l (Sabayon??), so I really can't help much.

---

### Post by howefield on 2013-10-31
> **al3xmail said:**
> It seems their are many linux headers, what one do I choose?

The one that matches your installed kernel.

If you are using the terminal try...

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by al3xmail on 2013-10-31
I tried
```

sudo apt-get install linux-headers-$(uname -r)

```

and it shouts at me about there not being linux headers for 3.4.0 >.>
I have found arm headers for 3.4.0-5, on the ubuntu software center; even goes as far as to state my device name.
After installing that and rebooting, doing uname -r tells me I'm on the 3.4.0-5 headers.
I'm still getting build errors though. Its complaining about there being no 3.4.0/build folder.

In my /lib/modules I have 3 folders, '3.4.0', '3.4.0-5' & '3.8.0-32-generic'
3.4.0 does not contain a build, but yet 3.4.0-5 does...

---

### Post by chili555 on 2013-10-31
Let's see:```
uname -r
sudo dpkg -s linux-headers-`uname -r`
```Thanks.

---

### Post by al3xmail on 2013-10-31
uname -r is
```

3.4.0

```
again...

and the dpkg command outputs
```

Package `linux-headers-3.4.0' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

So one thing says its there and another says it not?
Thanks for giving up some time to help me with this btw ^-^

---

### Post by chili555 on 2013-10-31
That means you are running kernel version 3.4.0 and although you may have headers installed for 3.4.0-5 or 3.4.0-819, you do not yet have headers matching your running kernel. Since they are not actually available:> it shouts at me about there not being linux headers for 3.4.0 >.>Then you could try to find a kernel image for 3.4.0-5, install it and reboot and then compile compat-wireless. You would then have matching kernel version and linux-headers.

---

### Post by al3xmail on 2013-10-31
Okay, I will try that!

---

### Post by al3xmail on 2013-10-31
If its not clear, I am still quite new to linux;
Can you help me install this kernel ([https://launchpad.net/ubuntu/saucy/armhf/linux-image-3.4.0-5-chromebook/3.4.0-5.1](https://launchpad.net/ubuntu/saucy/armhf/linux-image-3.4.0-5-chromebook/3.4.0-5.1))
I have tried and when I reboot, It still shows as 3.4.0 and won't compile.

---

### Post by chili555 on 2013-10-31
I suggest you first also look to see if you can find linux-headers-3.5.0-5-chromebook-3.4.0-5.1-armhf. If so, download both deb files and install both:```
sudo dpkg -i linux*.deb
```Note and post any errors, warnings, etc.

---

### Post by al3xmail on 2013-10-31
Image first
```

sudo dpkg -i linux-image-3.4.0-5-chromebook_3.4.0-5.1_armhf.deb
(Reading database ... 148851 files and directories currently installed.)
Preparing to replace linux-image-3.4.0-5-chromebook 3.4.0-5.1 (using linux-image-3.4.0-5-chromebook_3.4.0-5.1_armhf.deb) ...
Done.
Unpacking replacement linux-image-3.4.0-5-chromebook ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.4.0-5-chromebook /boot/vmlinuz-3.4.0-5-chromebook
Setting up linux-image-3.4.0-5-chromebook (3.4.0-5.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.4.0-5.1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.4.0-5.1 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.4.0-5-chromebook /boot/vmlinuz-3.4.0-5-chromebook
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.4.0-5-chromebook /boot/vmlinuz-3.4.0-5-chromebook
update-initramfs: Generating /boot/initrd.img-3.4.0-5-chromebook
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.4.0-5-chromebook /boot/vmlinuz-3.4.0-5-chromebook
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.4.0-5-chromebook /boot/vmlinuz-3.4.0-5-chromebook

```

Headers
```

sudo dpkg -i linux-headers-3.4.0-5-chromebook_3.4.0-5.1_armhf.deb
(Reading database ... 148851 files and directories currently installed.)
Preparing to replace linux-headers-3.4.0-5-chromebook 3.4.0-5.1 (using linux-headers-3.4.0-5-chromebook_3.4.0-5.1_armhf.deb) ...
Unpacking replacement linux-headers-3.4.0-5-chromebook ...
Setting up linux-headers-3.4.0-5-chromebook (3.4.0-5.1) ...

```

This look normal before I restart?

---

### Post by chili555 on 2013-10-31
Looks great. Please reboot and check again:```
sudo dpkg -s linux-headers-$(uname -r)
```If you see, then, that you finally have headers matching your running kernel, you are ready to compile compat-wireless.

---

### Post by al3xmail on 2013-10-31
oh for gods'sake.

```

Package `linux-headers-3.4.0' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

One step forward and a few steps back.

---

### Post by chili555 on 2013-10-31
In the first few moments of booting, can you hold down the Shift key and get to the GRUB menu and see if 3.4.0-5 is selectable? We wonder if and why not GRUB was updated.

---

### Post by al3xmail on 2013-10-31
Ahh, as its a weird chromebook dual boot, there is no GRUB or if there is; its not responding the the shift key.

---

### Post by chili555 on 2013-10-31
Generally, installation of a newer kernel updates GRUB. Evidently not here. You need assistance over on General Help to sort out the kernel and GRUB issue. Once solved, compile, get the firmware and you should be good to go.

---

### Post by al3xmail on 2013-10-31
Okay, thanks muchly for your time ^-^

---

