---
title: "Compiling and installing Sky98ln"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Master-of-None on 2008-05-18
I've had it with sky2 dropping my connections all the time. However, I can't get the wireless driver for NDIS Wrapper, either, because I don't own a computer with Windows, and WINE doesn't run the install program.

so my only option is the sky98ln driver, which is the official proprietary driver. Surprise! I need to do kernel editing! I got to compile it! I got to back up half my computer to even do it! Tell me... How can I attempt this feat of gigabyte acrobatics?

I need a copy of the Ubuntu Linux Kernal. Where can I get that?

I need to know how to compile and configure the driver. How do I do that?

I need the help of an expert to guide me through the process of editing the kernel, because I don't know anything about it.

---

### Post by chili555 on 2008-05-18
I will be glad to help. Please give me a link to your sk98lin, so I can follow along. In the meantime, open up Synaptic and get:
build-essential
linux-headers
linux-source

You can get the 'generic' and it will pull in the specific package you need.

Generally, there is a README in the .tar.gz which tells you the usually simple steps you need to take to compile. You can open a terminal and:```
tar zxvf <ur_file>.tar.gz
```It will create a new directory usually named the same, which you can open and read the README.

The items mentioned above will be mandatory before you proceed.

We can solve the problem with ndiswrapper and the Windows driver after that.> How can I attempt this feat of gigabyte acrobatics?
It's actually pretty easy or an old white beard like me wouldn't ever try it.

---

### Post by chili555 on 2008-05-18
First, please try:```
sudo rmmod -f sky2
sudo modprobe sky2 disable_msi=1
```See if that helps. If so, we can add this to */etc/modules.*

---

### Post by Master-of-None on 2008-05-18
[http://www.marvell.com/drivers/search.do]("http://www.marvell.com/drivers/search.do")

That site has the driver, Select Network Controller and then choose the operating system Ubuntu resembles most, and tell me which one it is, so I can get on track.

---

### Post by chili555 on 2008-05-18
Please select Linux Kernel 2.4.20 and higher. After you download the file, you should be able to right click it and select 'Extract Here.' A directory (file folder, for those Windows zombies) will be created called DriverInstall. Open a terminal and: ```
cd DriverInstall/
sudo gedit install.sh
```Change the very first line from **#!/bin/sh** to **#!/bin/bash**. Save and close gedit. Then do:```
./install.sh
```The terminal text should guide you through the installation. I followed it until it wanted me to insert my device, which I don't have.

Open up the README with Text Editor and it will help you, as well. Let me know if you get stuck.

---

### Post by Master-of-None on 2008-05-18
well, I think I got it working now, to an extent. The problem is it asks for the kernel (which I don't know where to download the source of.)

Can you tell me where to get the kernel source?

---

### Post by Master-of-None on 2008-05-18
Alright, I have the Linux Kernel. Now its telling me I can't install it. It says it can't find the headers. More specificly 

> Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux


I don't get what its asking me to do.

---

### Post by chili555 on 2008-05-18
> I don't get what its asking me to do.It hopes you will open up Synaptic and install *linux-headers-generic* which will automagically determine your kernel version and install the correct package.

Please see my post #3. Did you try that? Any drops since then?

---

### Post by Master-of-None on 2008-05-18
they were already installed.

---

### Post by Master-of-None on 2008-05-19
I have the headers and source installed, but it still gives me that error, what now?

---

### Post by chili555 on 2008-05-19
Please try this:```
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
```I'm not at all sure this will do it and we can remove the link later if it's an error.

Those are backticks; the symbol that's on the same key as ~. uname -r is a convenient way to say, 'please match my running kernel.'

Let us know.

---

### Post by Master-of-None on 2008-05-19
now its giving me a new error, and I can't post it on these forums, else my connection drops.

---

### Post by Master-of-None on 2008-05-19
bump

---

### Post by chili555 on 2008-05-19
> a new error, and I can't post it on these forums, else my connection dropsHard to diagnose. Can you jot down the highlights and post from another computer?

---

### Post by Master-of-None on 2008-05-20
It says this a couple of times in the log: > /tmp/Sk98IrDUjWaIlhqHPjpDhgYUQ/all/skge.c:483: error: 'struct net_device' has no member named 'poll'
/tmp/Sk98IrDUjWaIlhqHPjpDhgYUQ/all/skge.c:484: error: 'struct net_device' has no member named 'weight'

but with different numbers.

This twice: > /tmp/Sk98IrDUjWaIlhqHPjpDhgYUQ/all/skge.c:2342: error: too few arguments to function 'netif_rx_schedule_prep'
/tmp/Sk98IrDUjWaIlhqHPjpDhgYUQ/all/skge.c:2345: error: too few arguments to function '__netif_rx_schedule'

---

### Post by Master-of-None on 2008-05-22
bump

---

### Post by Master-of-None on 2008-05-24
bump

---

### Post by chili555 on 2008-05-24
I have tried to help you all I can. I don't have the device, so I can't really follow through and test the compile and installation myself. I do have three thoughts; first, did you try the suggestion in post #3 above, that is, can we get the native driver to work better?

Second, perhaps the errors which don't permit a proper compilation is a peculiarity of kernel 2.6.24, which changed a bit from 2.6.22. Can you interrupt the boot process with ESC, go into the GRUB menu and select a prior kernel, posssibly 2.6.22-14, and get it to compile correctly?

Third, and a last resort, contact the developers of *sk98lin* which you should be able to find in the folder you created when you extracted the .tar.gz, possibly in the README. Describe your compile issues, point them to this thread and see if they have a solution.

Sorry I can't be of more help.

---

### Post by Master-of-None on 2008-05-24
I appreciate that you did try to help.

The only thing the Sky2 driver is capable of, in my experience, is becoming worse.

I'll try to contact the developers, perhaps they'll tell me straight what is going on... providing I can send an e-mail without getting disconnected...

Also, the command you given me in post 3 seems to make everything on the internet load slower than 28k dial-up(I know for a fact, that its slower than 56k dialup.) This is so slow that Firefox will give up loading the page. If it can be sped up, I'll not need Sky98lin.

---

### Post by Master-of-None on 2008-05-25
bump

---

### Post by Master-of-None on 2008-05-26
bump

---

### Post by Master-of-None on 2008-05-27
bump

---

### Post by wvn on 2009-06-19
disgrace. apparently, not only we are $M$ haters but now we hate the internet

well, it is not like half the planet's pc's are using marvell yukon's nic.

bump bump bump

---

### Post by wvn on 2009-06-29
Bump!!!!!!!!!!!!1

---

### Post by moe458 on 2009-09-03
> **chili555 said:**
> Please try this:```
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
```I'm not at all sure this will do it and we can remove the link later if it's an error.

Those are backticks; the symbol that's on the same key as ~. uname -r is a convenient way to say, 'please match my running kernel.'

Let us know.

Hi, I had the similar issue and was able to get this far. however my installtion of the sk98lin failed during the course when it was trying to recompile the .  I am attaching the log for your convenience, would be able to provide guidance for me.  I appreciate your help, thanks !!
-----------------------------------

Disconnect alternative devices:  (done)                              [   OK   ]
Unload alternative driver (done)                                     [   OK   ]
Create tmp dir (/tmp/Sk98IpGcBJXoAgWXOmCbGenYn)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.27-14-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture./functions: line 325: arch: command not found
 (found)                                                             [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.3.2) (Kernel:4.3.2 == gcc:4.3.2)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/usr/src/linux)                           [   OK   ]
Check sources for .config file (/usr/src/linux/.config)              [   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (highmem)                                [   OK   ]
Change IOMMU (disabled)                                              [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check modpost availability (available)                               [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check firmware availability (not available)                          [   OK   ]
Check kernel header version (Kernel:2.6.27 == Header:2.6.27)         [   OK   ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.

---

### Post by moe458 on 2009-09-08
> **moe458 said:**
> Hi, I had the similar issue and was able to get this far. however my installtion of the sk98lin failed during the course when it was trying to recompile the .  I am attaching the log for your convenience, would be able to provide guidance for me.  I appreciate your help, thanks !!


An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.



I got the issue resolved by using the ndiswrapper with mrv8knt drivers. apprently the system was crashing with the drivers it came with but thoses ones i downloaded from net and they worked like a charm.
Drivers I used were Marvell_v2.7.1.2-client. it came with following files.
MRV8KNT.INF
MRV8K51.sys
MRV8K50.sys
MRV8Kx64.sys

issue resolved thx guys ;-)

---

### Post by wipmonkey on 2009-11-12
> **moe458 said:**
> I got the issue resolved by using the ndiswrapper with mrv8knt drivers. apprently the system was crashing with the drivers it came with but thoses ones i downloaded from net and they worked like a charm.
Drivers I used were Marvell_v2.7.1.2-client. it came with following files.
MRV8KNT.INF
MRV8K51.sys
MRV8K50.sys
MRV8Kx64.sys

issue resolved thx guys ;-)

This did not work for me. I'm using Ubuntu 9.10

---

