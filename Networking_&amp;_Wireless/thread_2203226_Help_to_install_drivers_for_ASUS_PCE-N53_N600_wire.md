---
title: "Help to install drivers for ASUS PCE-N53 N600 wireless card (Ralink RT5592)"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by george27 on 2014-02-02
Hi! I'm a little bit new to Linux Ubuntu and I'm not an advanced user of Linux in general. I want help to install the drivers for my wireless card.

I just bought the [ASUS PCE-N53 N600]("http://www.asus.com/Networking/PCEN53/") wireless card for my desktop PC. The card uses Ralink RT5592 Dual-Band chip. I put it inside my PC but my Linux Ubuntu 12.04 didn't recognise it automatically. So I download the Linux drivers from ASUS [from here]("http://www.asus.com/support/Download/11/1/PCEN53/5/") , file: [Linux_PCE_N53_1008.zip]("http://dlcdnet.asus.com/pub/ASUS/wireless/PCE-N53/Linux_PCE_N53_1008.zip") .

I unzip the zip file and untar the tar.bz2 file inside it and i read the [ATTACH]250028[/ATTACH] (click to download it). The file says:

1>Install compile tool 
    $yum install gcc-c++

* -->I did it.*

2>check kernel source code exists /usr/src/kernels/ "kernel name" 
 
    Download your kernel source code 
    *[[COLOR=#008080]http://www.kernel.org/pub/linux/kernel/]("http://www.kernel.org/pub/linux/kernel/")

[I] -->I did it. There wasn't a "kernels" directory inside /usr/src/ so i create it.
Also I download the 3.13.1 stable kernel from [http://www.kernel.org/](http://www.kernel.org/) and I untar it inside /usr/src/kernels/linux-3.13.1/ directory.[/I]


The difficult part starts from here and onwards. The file [ATTACH]250028[/ATTACH] says the below "Build Instructions":

2> In Makefile
      
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
      
     define the linux kernel source include file path LINUX_SRC
      
     modify to meet your need.

*--> I can't find MODE variable inside Makefile and set it to STA. Neither the TARGET var. How can i change it?*

3> In os/linux/config.mk 
     
     define the GCC and LD of the target machine
     
     define the compiler flags CFLAGS

     modify to meet your need.

*-->How to do that?*

** Build for being controlled by NetworkManager or wpa_supplicant wext functions
        
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
               
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d 

** Build for being controlled by WpaSupplicant with Ralink Driver
        
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
        
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

*-->What of the two choises should i select?*


Please, is there a more easier way to install the drivers? If yes, tell me that way. But if not, please help me with the above questions (and also, please, to the steps 4 to 7 inside [ATTACH]250028[/ATTACH]).

Thank you.

---

### Post by chili555 on 2014-02-02
First, the correct way to get the necessary source is not the source code itself from kernel.org, but the headers:```
sudo apt-get install linux-headers-generic
```Second, in the README, it says:> Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. You are running 3.13-xx. In short, the package you are trying to install is far too old to install in kernel version 3.13-xx. We no longer use wooden wheels on our sleek black BMWs.

Let's identify your card first and proceed from there. Please open a terminal and run and post:```
lspci -nn | grep 0280
```

---

### Post by george27 on 2014-02-02
Ok, i understand.

--

> **chili555 said:**
> First, the correct way to get the necessary source is not the source code itself from kernel.org, but the headers:```
sudo apt-get install linux-headers-generic
```

```
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

--

> **chili555 said:**
> Please open a terminal and run and post:```
lspci -nn | grep 0280
```

```
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5592]
```

---

### Post by chili555 on 2014-02-02
I am not encouraged: [https://wikidevi.com/wiki/ASUS_PCE-N53](https://wikidevi.com/wiki/ASUS_PCE-N53)> Probable Linux driver
**none**
PCI ID not yet observed in any mainline kernel / this listAnd this: [http://www.linux-hardware-guide.com/2013-07-30-asus-pce-n53-n600-pcie-2x-300-mbits](http://www.linux-hardware-guide.com/2013-07-30-asus-pce-n53-n600-pcie-2x-300-mbits)> The card can currently not be used together with other kernel versions (at least not with severe additional effort). There are some kernel patches available to use the driver together with other kernel version, but this approach needs detailed Linux knowledge and is often not successful. Therefore, it is not recommended to use PCE-N53 together with Linux.Do you have the option to return the device in favor of a supported device?

---

### Post by george27 on 2014-02-02
> **chili555 said:**
> Do you have the option to return the device in favor of a supported device?

No, that's not possible since I’ve open the package (it would be only if the card is broken). But it's not broken, in Windows VISTA works fine...

Is there any other way to install these drivers in my kernel? I don't want the extra Dual-Band features of the card to run in Linux, i want to use just a single channel to have Internet access from my router....

---

### Post by chili555 on 2014-02-02
A colleague and I are feverishly trying to work it out. If necessary, would you reinstall a 3.2.0-xx kernel? We may stand a better chance installing an older package on an older kernel. Don't do so yet, but tell us if this is a possibility.

---

### Post by george27 on 2014-02-03
> **chili555 said:**
> If necessary, would you reinstall a 3.2.0-xx kernel?

Chilli555, if i am not wrong, I think I already use a 3.2.0-xx kernel in Ubuntu 12.04.

```


george@george-ubuntu64:~$ dpkg --list | grep linux-image

rc  linux-image-3.0.0-12-generic     3.0.0-12.20     Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic     3.0.0-16.29     Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic     3.0.0-17.30     Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic     3.0.0-19.33     Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic     3.0.0-20.34     Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-26-generic     3.0.0-26.42     Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-58-generic     3.2.0-58.88     Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-generic              3.2.0.58.69     Generic Linux kernel image


george@george-ubuntu64:~$ uname -r

3.2.0-58-generic


```

Is there a need to reinstall?

---

### Post by chili555 on 2014-02-03
From your first post, I thought you were using 3.13. No?

---

### Post by george27 on 2014-02-03
> **chili555 said:**
> From your first post, I thought you were using 3.13. No?

No... I didn't say that anywhere...

> **george27 said:**
> 

2>check kernel source code exists /usr/src/kernels/ "kernel name"

Download your kernel source code
*[COLOR=#008080]http://www.kernel.org/pub/linux/kernel/

-->I did it. There wasn't a "kernels" directory inside /usr/src/ so i create it.
Also I download the 3.13.1 stable kernel from [http://www.kernel.org/](http://www.kernel.org/) and I untar it inside /usr/src/kernels/linux-3.13.1/ directory.



Well, is there a solution for 3.2.0-xx kernel i have?

---

### Post by chili555 on 2014-02-03
> I didn't say that anywhere...> Also I download the 3.13.1 stable kernel from [http://www.kernel.org/](http://www.kernel.org/)Silly me! I assumed you'd download and install the source matching your running kernel. > Well, is there a solution for 3.2.0-xx kernel i have? Working on it. My friend Varun thinks so, but I am going to try to compile it myself on a 12.04 LTS machine I test on. I'll be back in a while.

---

### Post by george27 on 2014-02-03
Ok! Thank you. Waiting....

---

### Post by chili555 on 2014-02-03
Please get a temporary wired ethernet connection and install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```I downloaded the file you referenced and compiled it. All the needed changes as mentioned in the Quick Start are already made; you need do nothing extra.

Assuming the file is in Downloads, be sure the compressed file within is also extracted by right-clicking it and selecting 'Extract Here.' Now, back to the terminal:```
cd ~/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
sudo su
make
make install
modprobe rt5592sta
exit
```On my 3.2.0-58 32-bit machine, it makes with several warnings but no errors. If the device works as expected, then all is well. If not, we'll try something else.

---

### Post by george27 on 2014-02-03
It worked !!!!!!!!!!!!!!!!

Thank you very much Chili555!!

:D

---

### Post by chili555 on 2014-02-03
Awesome! 

You have compiled the driver for your currently running kernel only. When Update Manager installs a newer kernel version and asks you to reboot, you must recompile:```
cd ~/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326
sudo su
[COLOR="#FF0000"]make clean[/COLOR]
make
make install
modprobe rt5592sta
exit
```Please retain the file and these instructions for that time.

Please use thread tools at the top to mark Solved.

---

