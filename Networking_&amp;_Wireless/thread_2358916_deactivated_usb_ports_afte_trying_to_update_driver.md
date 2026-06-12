---
title: "deactivated usb ports afte trying to update driver for EW-7811un"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by andrea987 on 2017-04-18
I am new to the forum and a not very experienced ubuntu user... apology for potential incorrectness. 

After an update for 14.04.5 LTS, 4.4.0-72 generic, my dell xps 13 (9343) was not able to connect to the wifi, due to a well known problem of the Broadcom wireless driver. To overcome this issue without buying an usb-to-ethernet-connector I was trying to use my ew-7811un and whilst updating - unsuccessfully - the troublesome driver following this link ([https://ubuntuforums.org/showthread.php?t=2261392](https://ubuntuforums.org/showthread.php?t=2261392)) I somehow deactivated/removed/changed the usb ports that way, that they are not recognized anymore. Now I am having the joy of having a laptop without wifi, ethernet or usb. Help to get the usb back to work is very much appreciated!

lsusb
BUS 001 Device 002: ID 8087:8001 Intel Corp.
.
.
Bus 002 Device 006: ID 7392:7811 Edimax...

That looks like the port still recognizes the device but I somehow dont know how to access it.
Any ideas?

---

### Post by wildmanne39 on 2017-04-18
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2017-04-18
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by andrea987 on 2017-04-18
sudo fdisk -l

shows 
/dev/sda1   ....
/dev/sda2   .....
/dev/sda5   ....

but no sdb or anything


ls /dev/ | grep sd

sda
sda1
sda2
sda5

with or without usb device does not change the output

---

### Post by wildmanne39 on 2017-04-18
Where did I ask to see that information?

---

### Post by andrea987 on 2017-04-18
Thank you very much for helping!
I can not copy paste, since nether usb nor internet is working wherefore I have to write manually what I see in the terminal...

```
cat /etc/lsb-release; uname -a

DISTRIB_ID_Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="UBUNTU 14.04.5 LTS
4.40-72-generic #93~14.04.1-Ubuntu SMP
```

```
lspci -nnk | grep -iA2 net

02:00.0 Network controller [0280]:Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev03)
Subsystem: Dell Device [1028:0019]
```

---

### Post by wildmanne39 on 2017-04-18
It is strange that the usb is not working if you can see:
Bus 002 Device 006: ID 7392:7811 Edimax...
to me it is working in some capacity.

Shutdown your system and move the usb device to a different port.

You have no usb devices working at the moment? I do not think trying to install the driver for the wifi caused the issue, but I can not be 100 percent sure.

---

### Post by andrea987 on 2017-04-18
```
lsusb

BUS 001 Device 002: ID 8087:8001 Intel Corp.
BUS 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
BUS 001 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
BUS 001 Device 003: ID 0c45:670c Microdia
BUS 001 Device 002: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
BUS 001 Device 001: ID Linux Foundation 2.0 root hub
```

I was re-starting the system several times and used both usb ports to check... they do not show up unfortunately

```
iwconfig
lo no wireless extension
```

```
rfkill list all

(no output at all)
```

```
lsmod

rtsx_pci_sdmmc  24576   0
psmouse            126976  0  
ahci                    36864   2
libahci                 32768  1 ahci
rtsx_pci              53248   1  rtsx_pci_sdmmc
sdhci_acpi           16384  0 
sdhci                   45056  1 sdhci_acpi
fjes                     28672  0
```

no usb is working but it shows up when I look for them via 

```
lsusb
```

re-starting using both ports wasnt helping...I am clueless

---

### Post by wildmanne39 on 2017-04-18
> **andrea987 said:**
> I was re-starting the system several times and used both usb ports to check... they do not show up unfortunately
What does not show up? the wifi adapter? I do not see that but your usb ports are working at least some of them.

I see:
```
lsusb

BUS 001 Device 002: ID 8087:8001 Intel Corp.
BUS 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
BUS 001 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
BUS 001 Device 003: ID 0c45:670c Microdia
BUS 001 Device 002: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
BUS 001 Device 001: ID Linux Foundation 2.0 root hub 
```
What is wrong with your internet wifi, you said it is a well known issue, do you have a link?

---

### Post by andrea987 on 2017-04-18
I can not access the usb device

the wifi problem is 
[http://www.dell.com/support/article/uk/en/ukbsdt1/HOW10806/how-to-install-broadcom-wireless-driver-on-xps-13-9343-from-ubuntu-1504-install-media?lang=EN](http://www.dell.com/support/article/uk/en/ukbsdt1/HOW10806/how-to-install-broadcom-wireless-driver-on-xps-13-9343-from-ubuntu-1504-install-media?lang=EN)

---

### Post by wildmanne39 on 2017-04-18
I see, that kernel has been breaking internet, wifi for sure, reboot your computer and go into the grub menu and choose the last working kernel.

---

### Post by andrea987 on 2017-04-18
May I ask you to give me a couple of more detailed hints how to do that?

in the GRUB I see:

*Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

---

### Post by wildmanne39 on 2017-04-18
Reboot, as soon as the computer starts to boot back up press and hold the shift key and you should see the grub menu with the other kernels choose one, not recovery of course.

You have to be fasted pressing the shift key.

---

### Post by andrea987 on 2017-04-18
Should I choose just any of the previous kernels?
and if yes: recovery mode or not?

---

### Post by wildmanne39 on 2017-04-18
See jeremy31's answer.

---

### Post by andrea987 on 2017-04-18
You have been right, the kernel messed it up!
I choose recovery mode and wifi, as well as usb do work now! :)

How do I remove the kernel that way, that it doesnt get loaded when I start the computer?

---

### Post by jeremy31 on 2017-04-18
Actually I deleted my answer but wildmanne must have seen it before that.  

Please post results for ```
dpkg -l | grep linux-image
```

I suspect you are missing the linux-image-extra for the 4.4.0-72 kernel

---

### Post by wildmanne39 on 2017-04-18
> **jeremy31 said:**
> Actually I deleted my answer but wildmanne must have seen it before that.  

Please post results for ```
dpkg -l | grep linux-image
```

I suspect you are missing the linux-image-extra for the 4.4.0-72 kernel

That is probably exactly what happened since the modules needed are in that package these days and has been for a while.

---

### Post by jeremy31 on 2017-04-18
If linux-image-extra-4.4.0-72-generic doesn't show in the results
```
sudo apt-get install --reinstall linux-image-extra-4.4.0-72-generic
```
Reboot and see if everything works in the 4.4.0-72 kernel

---

### Post by andrea987 on 2017-04-18
alright, I was wondering if I missed something...

I am now able to go online, as well as mounting usb devices normally when I am choosing via grub a former kernel in recovery mode.
tbh it would be ideally to fix it that way, that I do not need to go via grub to actually use the laptop....

```

code dpkg -l | grep linux-image
code/rc  linux-image-3.16.0-30-generic                         3.16.0-30.40~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-52-generic                         3.16.0-52.71~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-53-generic                         3.16.0-53.72~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-55-generic                         3.16.0-55.74~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-59-generic                         3.16.0-59.79~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-51-generic                         3.19.0-51.58~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-56-generic                         3.19.0-56.62~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-58-generic                         3.19.0-58.64~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-59-generic                         3.19.0-59.66~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-68-generic                         3.19.0-68.76~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-80-generic                         3.19.0-80.88~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-72-generic                          4.4.0-72.93~14.04.1                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-30-generic                   3.16.0-30.40~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-52-generic                   3.16.0-52.71~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-53-generic                   3.16.0-53.72~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-55-generic                   3.16.0-55.74~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-59-generic                   3.16.0-59.79~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-51-generic                   3.19.0-51.58~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-56-generic                   3.19.0-56.62~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-58-generic                   3.19.0-58.64~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-59-generic                   3.19.0-59.66~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-68-generic                   3.19.0-68.76~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-80-generic                   3.19.0-80.88~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-72-generic                    4.4.0-72.93~14.04.1                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                         3.19.0.80.62                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-xenial                        4.4.0.72.59                                         amd64        Generic Linux kernel image


```

Since the requested linux-image-extra-4.4.0-72-generic shows up, I am not sure what to do (sorry still not sure about the syntax for the forum)

---

### Post by wildmanne39 on 2017-04-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by andrea987 on 2017-04-18
Re-installing gave me the mountable usb ports back and now I am back from where I started some hours ago.

Thank you very much for help and support
Awesome first forum experience for me!

---

### Post by wildmanne39 on 2017-04-18
Glad we could help.
Your welcome and Enjoy.:)

---

