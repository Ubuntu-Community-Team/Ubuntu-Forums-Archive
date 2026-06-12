---
title: "Building QF9700 driver"
date: 2023-03-08
forum: Networking &amp; Wireless
---

### Post by gdesilva on 2023-03-08
I am running Ubuntu Mate 22.04. Linux kernel 5.15.0-67-generic and trying to build the driver QF9700 to a generic usb to ethernet adapter.

lsusb tells me Bus 001 Device 006: ID 0fe6:9702 ICS Advent USB 2.0 10/100M Ethernet Adaptor is connected but the driver is not loaded. The device works OK with Windows 10.

Upon doing some research I found out that this device requires QF9700 driver.

I downloaded the source files from elsewhere and tried to compile it but the process failed due to missing Linux kernel  files. I then searched  kernel/git/tovalds/linux.git and added the required kernel file and attempted to compile again.  While this fixed the original error I kept encountering more missing kernel files each time I added one. In one post I read that this is an issue with distributions leaving out some kernel files.

Is there a simple way to synchronise original Linux kernel files and distribution kernel files to overcome this issue rather than having to add one file at a time?

Alternatively is there any place I could find the binary driver file?

Thanks.

---

### Post by chili555 on 2023-03-08
Please try:

```
sudo apt update
sudo apt install linux-headers-generic build-essential bc
```

And try again.

Please give us a link to the driver file you downloaded so we may try ourselves.

---

### Post by gdesilva on 2023-03-08
@chili555, thanks for the response but I have the latest build-essentials

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
bc is already the newest version (1.07.1-3build1).
bc set to manually installed.
build-essential is already the newest version (12.9ubuntu3).
linux-headers-generic is already the newest version (5.15.0.67.65).
linux-headers-generic set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.


I think I got the source code from [www.pccables.com/drivers/RD9700Driver.zip]("http://www.pccables.com/drivers/RD9700Driver.zip")


I did manage to add all the missing files but now I get this error....

# make
Building QF9700 USB2NET chip driver...
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-67-generic'
  HOSTLD  arch/x86/tools/relocs
/usr/bin/ld: arch/x86/tools/relocs_common.o: in function `main':
relocs_common.c:(.text.startup+0x18e): undefined reference to `process_32'
/usr/bin/ld: relocs_common.c:(.text.startup+0x1fe): undefined reference to `process_64'
collect2: error: ld returned 1 exit status
make[2]: *** [scripts/Makefile.host:104: arch/x86/tools/relocs] Error 1
make[1]: *** [arch/x86/Makefile:211: archscripts] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-67-generic'
make: *** [Makefile:10: all] Error 2

Any suggestions will be greatly appreciated. Thanks.

---

### Post by gdesilva on 2023-03-08
Tried a few suggestions given here....[https://unix.stackexchange.com/questions/722131/usb-ethernet-adapter-not-working](https://unix.stackexchange.com/questions/722131/usb-ethernet-adapter-not-working)


It appears that the system recognises it as a USB Mass Storage device rather than as a network adaptor

inxi -nxxx
Network:
  Device-1: Realtek RTL8822BE 802.11a/b/g/n/ac WiFi adapter
    vendor: Hewlett-Packard driver: rtw_8822be v: N/A pcie: speed: 2.5 GT/s
    lanes: 1 port: 1000 bus-ID: 01:00.0 chip-ID: 10ec:b822 class-ID: 0280
  IF: wlo1 state: up mac: d8:9c:67:05:89:cf
  Device-2: ICS Advent USB 2.0 10/100M Ethernet Adaptor type: USB
    driver: usb-storage bus-ID: 1-3:6 chip-ID: 0fe6:9702 class-ID: 0806

---

### Post by chili555 on 2023-03-08
> /usr/bin/ld: arch/[COLOR="#FF0000"]x86[/COLOR]/tools/relocs_common.o: in function `main':I doubt that your system is x86; i.e. 32-bit. Check:

```
arch
```I'm guessing it is x86_64; i.e. 64-bit. I also notice that these files were created in 2010, when 32-bit was common and when old Chili still had hair! This file is too old to compile on any modern Linux version.

I also note this: [https://www.reddit.com/r/linuxquestions/comments/zrzl1n/usbtoethernet_issue/](https://www.reddit.com/r/linuxquestions/comments/zrzl1n/usbtoethernet_issue/) where it says: 

> Return it and get one that is known to work. I mean every Realtek and ASIX based USB to Ethernet ones work, so you must have found the only one which doesn't.

What you see is a little storage device, part of the USB-to-ethernet dongle that contains Windows drivers.

Since every other usb-to-ethernet device works out of the box, just return it and get one that works.I regretfully agree.

And this: [https://unix.stackexchange.com/questions/722131/usb-ethernet-adapter-not-working](https://unix.stackexchange.com/questions/722131/usb-ethernet-adapter-not-working) The result was no solution at all.

---

### Post by gdesilva on 2023-03-09
It is a 64 bit CPU although the directory is listed as /usr/src/linux-headers-5.15.0-67-generic/arch/x86  

I also tried many options with usb_modeswitching command but cannot get the device to switch to mode 0206 which is network adaptor. It stubbornly stays on 0806 - mass storage device. 

Something interesting about this is that it initially comes up as a mass storage device which contains its Windows and Mac drivers. But it appears once the driver software is installed it switches to mode 0206 as a network device. How the Windows driver is able to do that is interesting. I tried usb_modeswitch command with option -C 0206 to change the device class but did not succeed in getting it to switch to that mode. It appears it is something simple but not having much luck.

I have already ordered another unit which specifically say that it supports Linux.:(

Thanks for your time.

---

