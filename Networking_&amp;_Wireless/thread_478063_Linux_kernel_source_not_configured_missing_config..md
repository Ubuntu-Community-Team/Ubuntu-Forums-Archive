---
title: "Linux kernel source not configured: missing config.h"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by sunshine12 on 2007-06-18
When I try to install drivers for my new ethernet(wired) card, it gives me following error message,

Linux kernel source not configured: missing config.h

There is no config.h in /usr/src/LINUX_VERSION/include/linux.....

there are configfs.h and autoconf.h files..... so what should I do now? Please help

Ethernet card is : Hangzhou silan microelectronics, sc92031

---

### Post by sunshine12 on 2007-06-19
Someone can help to compile the source file.....
thanks

---

### Post by chili555 on 2007-06-19
Do you have *linux-headers-`uname -r`* installed?

---

### Post by sunshine12 on 2007-06-20
> **chili555 said:**
> Do you have *linux-headers-`uname -r`* installed?

Yes I have, what to do next..?

---

### Post by Bachstelze on 2007-06-20
> **sunshine12 said:**
> 
Linux kernel source not configured: missing config.h

There is no config.h in /usr/src/LINUX_VERSION/include/linux.....

there are configfs.h and autoconf.h files..... so what should I do now? Please help

Make config.h a symlink to autoconf.h.

---

### Post by sunshine12 on 2007-06-20
> **HymnToLife said:**
> Make config.h a symlink to autoconf.h.

that means...

     ln -s autoconf.h config.h

or anything else.. please reply

---

### Post by chili555 on 2007-06-20
Please try this:```
cd /usr/src/linux-headers-2.6.20-16-generic/include/linux
```Substitute your version here if it's not 2.6.20-16-generic.```
sudo ln -s  autoconf.h config.h
```Then go back to your sc92031 directory and retry 'make.' It worked for me, with some warnings, but no errors.

---

### Post by sunshine12 on 2007-06-20
will do it, let's see what happens, bytheway **chili555** you have the same ethernet card??
where you find the drivers for linux kernel 2.6.x , the cd that came with the NIC has the support for only 2.4.x-2.5..x only
thanks

---

### Post by chili555 on 2007-06-20
I do not have the card. When someone is having trouble compiling, I often download the .tar.gz and try to compile it myself to see if I can see what the trouble may be. I searched to web for 'sc92031 tar.gz' and I found a file to download named sc92031-2.6.tar.gz, downloaded it, extracted it and, after making the link above, ran 'make' successfully. It created a sc92031.ko. When I do these experiments, I never 'make install.'

It's really bad, because the kernel developers are working furiously on this for kernel 2.6.21 which will, hopefully, fully support this card...a few months from now.

[http://gurukumara.googlepages.com/](http://gurukumara.googlepages.com/)

---

### Post by sunshine12 on 2007-06-20
It will be supported in kernel 2.6.21, but have to wait for that..

I have downloaded the same file done some change and somehow succeded to install the driver, but getting frequent disconnections, every 5-10minutes of downloading(about 50mb)... error message shows "message from kernel: disabling irq 11"

---

### Post by chili555 on 2007-06-20
Please let us see:```
sudo cat /var/log/messages | grep -i irq
sudo cat /var/log/messages | grep eth0
```These commands will probably produce many lines of output; let's see the last 10. Thanks.

---

### Post by sunshine12 on 2007-06-21
just installed ndiswrapper and used xp drivers, everything seems working fine, but don't know what will happen...

the last ten lines are...

Jun 21 10:58:29 ssss-desktop kernel: [   19.655062] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Jun 21 10:58:29 ssss-desktop kernel: [   19.655079] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun 21 10:58:29 ssss-desktop kernel: [   19.655423] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ef40
Jun 21 10:58:29 ssss-desktop kernel: [   19.757503] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
Jun 21 10:58:29 ssss-desktop kernel: [   19.757521] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
Jun 21 10:58:29 ssss-desktop kernel: [   19.757644] uhci_hcd 0000:00:1f.4: irq 10, io base 0x0000ef80
Jun 21 10:58:29 ssss-desktop kernel: [   38.839218] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Jun 21 10:58:29 ssss-desktop kernel: [   40.165901] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
Jun 21 10:58:29 ssss-desktop kernel: [   40.165918] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
Jun 21 10:58:29 ssss-desktop kernel: [   40.847804] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
Jun 21 11:00:36 ssss-desktop kernel: [  180.537391] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
Jun 21 11:00:36 ssss-desktop kernel: [  180.537406] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
Jun 21 11:00:36 ssss-desktop kernel: [  180.743457] ndiswrapper: using IRQ 11

---

### Post by chili555 on 2007-06-21
ndiswrapper will probably make all the difference in the world! Post back if you have more difficulty.

Your IRQ entries do not point to any abnormalities, as far as I can see.

---

### Post by sunshine12 on 2007-06-28
> **chili555 said:**
> ndiswrapper will probably make all the difference in the world! Post back if you have more difficulty.

Your IRQ entries do not point to any abnormalities, as far as I can see.

No more difficulties chill555,

Ndiswrapper solved my problem. and now I can stay online and can download without disconnections.
No hardware conflicts, no Irq problems..

Thanks to all.....

---

### Post by lost_poet on 2007-08-05
I have been having difficulty staying online even after ndiswrapper. But the problem only starts when I update and move from 2.15 to 2.16 (something to do with something called Linux Imgae, sorry, am a newbie).

Before the update I am fione online for hours. But after update I get d/c every 2/3 minutes. Am I doing somethign wrong?

Here's my other post [http://ubuntuforums.org/showthread.php?p=3137140#post3137140](http://ubuntuforums.org/showthread.php?p=3137140#post3137140)

---

### Post by sunshine12 on 2007-08-07
It is working perfect even after that update...
please elaborate more

---

### Post by axavierraj on 2007-09-18
Dear Friends

I am newbie to Linux and Ubuntu.

I have a system with Windows XP SP2 in one of my hardrive (40 GB * 3 partitions) and Ubuntu 7.04(Live CD from Canonical) in another harddrive (8 GB).

I have two ports for Internet,

One is onboard VIA Rhine and it got repaired when one lightning occurs and i added another network card using PCI slot which is 
Realtek 8139. 

I found no difficulties in Windows for installing the driver for this network card. But i found difficulties in  Ubuntu to install the driver for it.

Later i searched this post from web and followed the steps to compile the source given in the URL [http://gurukumara.googlepages.com/](http://gurukumara.googlepages.com/) by chili555.

I installed the module and configured the IP address and DNS address, Gateway etc., for that 'eth1' 'Wired Connection'.

But my browser in Ubuntu has no access to web and i don't know why. 

Can anyone give solution for my problem? If i need to post with any details kindly tell me the steps how to extract those details and from where to find those details (Since i am a newbie for Ubuntu)

Looking forward for helping hand.

With regards

Xavier Raj Antony Samy.

---

