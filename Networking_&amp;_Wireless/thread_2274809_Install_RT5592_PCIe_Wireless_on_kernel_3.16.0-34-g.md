---
title: "Install RT5592 PCIe Wireless on kernel 3.16.0-34-generic"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by Alexander_Mogren on 2015-04-22
Hi everyone. I have this problem installing these drivers that i know is old but have seen that is may be possible but not just in my case.
I have downloaded the drivers from the vendor, we are talking about: DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326

Here is what i have done.

1. Installed the build essentials and headers + gcc

2. Unpacked the file.

3. Go to Terminal and done the following.

    sudo su
    make
    make install
    modprobe rt5592sta

When running the make i get the following at the end:
   
    make[2]: *** [/home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../sta/sta_cfg.o] Error 1
    Makefile:1345: recipe for target '_module_/home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux' failed
    make[1]: *** [_module_/home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux] Error 2
    make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-34-generic'
    Makefile:381: recipe for target 'LINUX' failed
    make: *** [LINUX] Error 2

Then when i run the "make install" i get:

   make -C /home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
   make[1]: Entering directory '/home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
   mkdir: cannot create directory ‘/etc/Wireless’: File exists
   rm -rf /etc/Wireless/RT2860STA
   mkdir /etc/Wireless/RT2860STA
   cp /home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
   install -d /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/
   install -m 644 -c rt5592sta.ko /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/
   install: cannot stat ‘rt5592sta.ko’: No such file or directory
   Makefile.6:294: recipe for target 'install' failed
   make[1]: *** [install] Error 1
   make[1]: Leaving directory '/home/mogren3000/Downloads/wireless/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
   Makefile:474: recipe for target 'install' failed
   make: *** [install] Error 2

And then the last is the modprobe rt5592sta i get:
  
    modprobe: FATAL: Module rt5592sta not found. 

So what do i need to do here to get this working?
Have I missed to install something?

Thanks.

---

### Post by chili555 on 2015-04-22
Please see: [http://ubuntuforums.org/showthread.php?t=2203226](http://ubuntuforums.org/showthread.php?t=2203226)> You are running 3.13-xx. In short, the package you are trying to install is far too old to install in kernel version 3.13-xx. We no longer use wooden wheels on our sleek black BMWs.Your 3.16.0-xx kernel is even *further* out of step. You might possibly (or possibly not!) install a 3.2.0-xx kernel and headers and build tools and get it to work. Maybe.

By the way, all you driver builders out there, when you see this:> make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-34-generic'
Makefile:381: recipe for target 'LINUX' failed
[COLOR="#FF0000"]make: *** [LINUX] Error 2[/COLOR]
Stop. All further steps will also end in error.

---

