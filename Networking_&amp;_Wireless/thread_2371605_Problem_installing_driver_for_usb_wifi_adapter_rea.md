---
title: "Problem installing driver for usb wifi adapter realtek RTL8811AU"
date: 2017-09-16
forum: Networking &amp; Wireless
---

### Post by jonathan81998 on 2017-09-16
Hello,


I installed ubuntu 16.04. I am trying to install a wifi usb adapter that I just bought because it seemed to be ubuntu compatible. It has been 2 days that I am reading many posts and trying many things but could not have it to work. I would veru much appreciate your help. Here are the infos :

[LIST]
[*]I bought that adapter : [https://www.amazon.com/USB-Wifi-Adapter-Faster-Connection/dp/B06XRC8G1V/](https://www.amazon.com/USB-Wifi-Adapter-Faster-Connection/dp/B06XRC8G1V/)
[*]On windows it works well, and it tells me the device is "Realtek RTL8811AU Wireless LAN 802.11ac USB 2.0 Network Adapter" and the hardware id is "USB\VID_0BDA&PID_A811&REV_0200"
[*]This is the result of the wireless-info script : [http://paste.ubuntu.com/25547122/](http://paste.ubuntu.com/25547122/)
[*]I tried to install via the driver provided by the producer (can be found here : [http://bit.ly/2qLS37h](http://bit.ly/2qLS37h)), but running the install.sh script, there are a bunch of errors. I did not pursue further as I read on this forum that it did not work with recent kernels.
[*]I installed the package listed here : [https://ubuntuforums.org/showthread.php?t=2370297](https://ubuntuforums.org/showthread.php?t=2370297) but it is still not working.
[*]I installed the driver from here : [https://github.com/sloretz/rtl8811au](https://github.com/sloretz/rtl8811au) (and applied the patch from here : [https://github.com/sloretz/rtl8811au/pull/3/commits/0bad5abe25e84e164f5b46e4b4599cd8a7cd514b](https://github.com/sloretz/rtl8811au/pull/3/commits/0bad5abe25e84e164f5b46e4b4599cd8a7cd514b) because before I had errors), but I still don't have wifi.
[/LIST]


Thank you very much for your help.

Jonathan

---

### Post by jeremy31 on 2017-09-16
See [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) use the instructions on the page to compile using dkms

---

### Post by jonathan81998 on 2017-09-16
I just downloaded it and ran ```
sudo make -f Makefile.dkms install
```.
I have an error :
```
make clean
make[1]: Entering directory '/home/jon/Documents/driver wifi rtl8821/rtl8812AU_8821AU_linux-master'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-33-generic/build M=/home/jon/Documents/driver wifi rtl8821/rtl8812AU_8821AU_linux-master clean
make[2]: Entering directory '/usr/src/linux-headers-4.10.0-33-generic'
arch/x86/Makefile:140: CONFIG_X86_X32 enabled but no binutils support
make[2]: *** No rule to make target 'wifi'.  Stop.
make[2]: Leaving directory '/usr/src/linux-headers-4.10.0-33-generic'
Makefile:1605: recipe for target 'clean' failed
make[1]: *** [clean] Error 2
make[1]: Leaving directory '/home/jon/Documents/driver wifi rtl8821/rtl8812AU_8821AU_linux-master'
Makefile.dkms:11: recipe for target 'src_install' failed
make: *** [src_install] Error 2



```

---

### Post by jeremy31 on 2017-09-16
Change the name of the folder "driver wifi rtl8821" to "driver-wifi-rtl8821" as spaces cause problems at times

It worked on my laptop with no spaces in the path
```
$ sudo make -f Makefile.dkms install
make clean
make[1]: Entering directory '/home/jeremy/Pictures/rtl8812AU_8821AU_linux'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.8.0-39-generic/build M=/home/jeremy/Pictures/rtl8812AU_8821AU_linux clean
make[2]: Entering directory '/usr/src/linux-headers-4.8.0-39-generic'
make[2]: Leaving directory '/usr/src/linux-headers-4.8.0-39-generic'
make[1]: Leaving directory '/home/jeremy/Pictures/rtl8812AU_8821AU_linux'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true

Creating symlink /var/lib/dkms/rtl8812au/4.3.14/source ->
                 /usr/src/rtl8812au-4.3.14

DKMS: add completed.
dkms build -m rtl8812au -v 4.3.14

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=4.8.0-39-generic KVER=4.8.0-39-generic.............
```

---

### Post by jonathan81998 on 2017-09-16
Thank you very much !!
After removing the spaces in the folder name, the install went through. And after a reboot, I was welcomed with a message telling me that there were wifi networks available.
My adapter now works perfectly. What a relief.
Thank you very very much !

---

