---
title: "Internet connection problems"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by keentolearn on 2008-08-20
This is my very first post so apologies if I am in the wrong place and Sorry for long post. It has taken me 5/6 weeks to get this far having previously spent 20 mins or so on Linux Ubuntu 7.04 Live CD demo. Much study/work was required to learn how to use Linux, soooo different to Windows. 

My BT Broadband Basic landline is about 5 kms from exchange and operates at 512 Kbps. It has been improved with the additional data-throughput of compression app ONSPEED. It also has USB BT Voyager 105 modem and associated problems.

I had decided to go for a dual-boot with XP and Ubuntu 8.04 Hardy. Used Ubuntu CDROM to install the software which went 
reasonably well with few problems. 

Carried out Hardware App test in System/Administration section and it indicated problems with "Detecting your network controller(s): Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15) Is this correct? -Yes but no Internet available to send it!

After web research I came up with a recent driver from Marvell Yukon website for LINUX drivers for 88E8053 Gigabit ethernet controller chipset but so far have not found out how to install it, hopefully correcting a major part of my problem. [Hopefully I'm at the right place]

THe USB modem problem was a known issue (to all except me!), so downloaded Eciadsl BT Voyager 105 driver and PPPoe files and relevant info to enable config of necessary drivers. Eventually I succeeded in getting the Config correct and Synch to work 
but it then stuck in "awaiting Service Provider" mode. This is where the above 88E8053 problem connects.

In order to remove any doubt about possible errors I changed my Broadband Access Password. Later I then realised the implication of ONSPEED being installed between the USB modem and Internet and realised that the ONSPEED software would have to be implemented in Ubuntu as well Win XP. I went to ONSPEED website and found that they will not be providing Linux driver support
but do say that their software 'will' work with Linux 'WINE' app using Windows compatability Layer. Data is given by ONSPEED for settings in web browser (Mozilla Firefox) etc when WINE is OK. This will be done after success with Wine.

I downloaded WINE from the relevant HQ website and after much research attempted to load the program after transferring via USB mem stick. This then stated that one was Broken and had  "Dependancy Problems". "Error: Dependency is not 
satisfiable:libldap2". Status bar showed 1487 items had been loaded OK and that there appears to be just one 'broken' problem. I was unable to take matters any further on my own without some advice. So had to call it a day (6 weeks actually). Since I had in fact 'closed the circle' in terms of being unable to access the Internet with Ubuntu 8.04 and decided to seek help. 

Details of lots of selected tests carried out are not added due to post length.

---

### Post by keentolearn on 2008-08-21
Forgive me for using the "reply to thread facility" if that is not correct way to add another para to previous entry. I'm a slow learner on web forums.

Please can anyone help me on this. I am gettting desperate to make some progress with this.

The first stage for me is to find how to use the new Linux driver for the 88E8053 gigabit ethernet controller obtained from the Marvell site two days ago.

filename1 = install_v10.60.2.3.tar.bz2 (28/4/2008 old issue)
filename2 = install_v10.70.1.3.tar.bz2 (latest, in last week)

Could anyone please let me know how to make this operate with Ubuntu 8.04 Hardy Please.

Would really appreciate the help. Many thanks in anticipation.

---

### Post by Belatra on 2008-08-22
> **keentolearn said:**
> 
..how to use the new Linux driver for the 88E8053 gigabit ethernet controller obtained from the Marvell site two days ago.

filename1 = install_v10.60.2.3.tar.bz2 (28/4/2008 old issue)
filename2 = install_v10.70.1.3.tar.bz2 (latest, in last week)

Could anyone please let me know how to make this operate with Ubuntu 8.04 Hardy Please.I used last week edition of the driver. It seems to be working fine.
Create /temp directory
```
sudo mkdir /temp
```move the file into /temp and unpack it
```
sudo mv *YOUR_TAR.BZ2_DIRECTORY*/install_v10.70.1.3.tar.bz2 /temp
cd /temp
sudo tar xjf install_v10.70.1.3.tar.bz2
cd DriverInstall
```Now you have to edit the first line in "install.sh" script and change the offending "sh" to "bash".
```
sudo gedit install.sh
```Change first line from **#!/bin/sh**" to **#!/bin/bash** and save file
Close your 88E8056 device
```
sudo ifconfig eth**X** down
```
replace X to your interface ID (e.g. eth0 or eth1 ...)
Run installation script
```
sudo ./install.sh
```

Follow on-screen instructions
Chose 
1 - installation
2 - Disconnect device
3 - Enjoy

---

### Post by keentolearn on 2008-08-22
Thanks very much Belatra for your welcome reply. I will not be able to try it tonight, but hopefully will have a go tomorrow. Thanks for taking the trouble to provide an old-newbie to make progress. It should make Ubuntu much better when I have the Internet available. 
Thanks again, marvellous!!

Sorrry about the thanks star -it deserves togo to you -selfish aren't I?

---

### Post by keentolearn on 2008-08-23
I had a go at dealing with the driver as per your info. I did get somewhat confused with a couple of minor points. The first being the fact that you stated "88E8056" whereas my device is a 88E8053.

I ran the script programme and at the initial installation stage I chose "1" for installation as you stated. Then I rapidly got lost altogether.

Here is a copy of my terminal screen as best I can copy/display it due to formatting difference between windows notepad and the terminal window itself.

Unclear to me exactly what to do (and memory sometimes lets me down afterwards as to exactly what I have done when writing it up)
I have 5 files in DriverInstall directory, namely "functions" + "install.sh" + "README" + "sk98lin.4" + "sk98lin.tar.bz2" + 
"install.sh~"[which is a Hidden file]
--------------------
*** Here is the last part of my effort shown in terminal window:-***

pete@pete-desktop:~/temporary/DriverInstall$ sudo ifconfig eth0 down
pete@pete-desktop:~/temporary/DriverInstall$ 

sudo ./install.sh

Installation script for sk98lin driver.
Version 10.70.1.3 (Jun-30-2008)
(C)Copyright 2003-2008 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================

1) installation
2) generate patch
3) exit
Choose 

your favorite installation method: 1 
Exit.
pete@pete-desktop:~/temporary/DriverInstall$ dir
functions  install.sh  install.sh~  README  sk98lin.4  sk98lin.tar.bz2
pete@pete-desktop:~/temporary/DriverInstall$ 
*** -------------------------------------------------------- ***
I put "your favorite installation method:" to  "1" since that is what you said to chose.
With hindsight is that correct since the next line is "Exit", which presumably means it exited the script?

I read the "Readme" file but this is mainly over my head at the moment as I am a self-confessed newbie and have never done anything too complicated so far.

Would it be possible for you to give me additional input details to enable me to re-run the script again.

Sorry for appearing to be so stupid, hopefully in 20 years or so (at this rate) I may be able to do it myself with no problems!!

What a pity you can't just click a setup.exe file or something similar, ahhh dream on windows....

---

### Post by Belatra on 2008-08-24
> my device is a 88E8053.
According to [http://www.marvell.com/drivers/search.do](http://www.marvell.com/drivers/search.do) the driver 10.70.1.3 is compatible with your device as well.
The main problem is that originally driver was developed for Fedora, not for Ubuntu. That's why we have to edit the first line in the installation script.

> 
I have 5 files in DriverInstall directory, namely "functions" + "install.sh" + "README" + "sk98lin.4" + "sk98lin.tar.bz2" + 
"install.sh~"[which is a Hidden file]  Last one looks strange. Probably it is a backup result of your editing. I would recommend to delete it just in case. Just leave the edited file.
The command
**head install.sh** and **head install.sh~** will help you identify the files

> ```

sudo ./install.sh
...
1) installation
2) generate patch
3) exit
Choose your favorite installation method: 1 
Exit.

```The steps look fine but last response "Exit"
Normally you should see a few messages showing the progress. *Install.log* file should be created.
I have a suspicion that something wrong in the install.sh file.
You can check it when compare with your original extracted file using **diff** command
```
sudo diff /path/to/file-one /path/to/file-two
```
the difference should be in first line ONLY

AS far as I understand from your first post your Ubuntu could not detect your NIC at all.
Is any Marvell device listed in pci devices list?
```
lspci
```
Should be something like this
```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Ethernet Controller
``` 
What does **ifconfig** command return?
You also have to have kernel headers installed. Check it *System -> Administration -> Synaptic Package Manager -> Search* type string "*header 2.6.24-19*"
[B]Header files related to Linux kernel version 2.6.24
Linux kernel headers for version 2.6.24 on x86/x86_64[/B] should be marked as installed.
You can also make sure if check */usr/src* directory. The directories "*linux-headers-X.X.XX-XX*" should exist.
The same for compiler *gcc* or *cpp* **The GNU C compiler** should be installed as well.

As a result after the driver sk98lin is installed you can check it with ```
ethtool --driver eth0
```
you should get
```
driver: sk98lin
version: 10.70.1.3 (01)
firmware-version: N/A
bus-info: 0000:03:00.0
```


> hopefully in 20 years or so (at this rate) I may be able to do it myself with no problems!!Why so pessimistic? Remember yourself 20 years ago and extrapolate your progress into your future :lol: Should be much faster!!!
I have tried Linux at the beginning of this year. Just in six+ months I got the NIC driver installed.\\:D/

> What a pity you can't just click a setup.exe file or something similar, ahhh dream on windows....Don't remind me windows. I shudder to think of it. To go through the only gate built by Bill - that's terrible. It's much more interesting to build the own gate breaching a wall by the forehead. Am I right? :mrgreen: That's what we are doing together in this community.](*,)](*,)](*,)
Talking seriously the similar tool is in Ubuntu called ".deb package". Just one click and your package is installed.\\:D/

---

### Post by keentolearn on 2008-08-29
Hi Belatra, sorry for delay but have had daugter &Grand-daughter over for 3 dyas-NO PC!!

I read over again your instructions and found in one of the docs that the temp folder you referred to should be called TMP_DIR. I had tried to call my directory Temp and I got error saying folder 'templates' already existed, so I called the folder "temporary". I do not know if that would make a difference, but it did not work at all!. I decided to remove all related files and start process again. Here is code 


Inserted Terminal text for actual code input/operation:- some earlier code has been removed so as to shorten text. Notice the "-s" parameter automatically set for "install.sh -s" which operates "without user-intervention".

First 2 lines of code are remainder of my "checking here to see tar files expanded OK"


```
pete@pete-desktop:~/TMP_DIR/DriverInstall$ dir
functions  install.sh  install.sh~  README  sk98lin.4  sk98lin.tar.bz2 
pete@pete-desktop:~/TMP_DIR/DriverInstall$ sudo ifconfig eth0 down
pete@pete-desktop:~/TMP_DIR/DriverInstall$ sudo ./install.sh -s

Installation script for sk98lin driver.
Version 10.70.1.3 (Jun-30-2008)
(C)Copyright 2003-2008 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


IMPORTANT INFORMATION!

We found an alternative driver for your Marvell product on this system.
The alternative driver is _NOT_ directly supported by Marvell and does not
include all features provided by your device. If you want to use the
sk98lin driver developed by Marvell, you may choose either to deactivate
or remove the alternative driver.

[PRESS ANY KEY FOR FURTHER INSTRUCTIONS]


Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that the alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be
  loaded.

Deactivate driver:
  - The alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed


1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 3  [**** this option chosen *** ]

Disconnect alternative devices:  (done)                                                         [   OK   ]
Unload alternative driver (done)                                                                [   OK   ]
Create tmp dir (/tmp/Sk98IPbNBBEUYIPGmRZSWadnb)                                                 [   OK   ]
Check user id (0)                                                                               [   OK   ]
Check kernel version (2.6.24-16-generic)                                                        [   OK   ]
Check kernel symbol file (/proc/kallsyms)                                                       [   OK   ]
Check kernel type (SMP)                                                                         [   OK   ]
Check number of CPUs (1)                                                                        [   OK   ]
Check architecture./functions: line 326: arch: command not found
 (found)                                                                                        [   OK   ]
Set architecture (i386)                                                                         [   OK   ]
Check compiler (/usr/bin/gcc)                                                                   [   OK   ]
Check mcmodel flags (none)                                                                      [   OK   ]
Check module support (/sbin/insmod)                                                             [   OK   ]
Check make (/usr/bin/make)                                                                      [   OK   ]
Check kernel gcc version (4.2.3) (Kernel:4.2.3 == gcc:4.2.3)                                    [   OK   ]
Check sk98lin driver availability (not loaded)                                                  [   OK   ]
Check kernel header files (not found)                                                           [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of package failed.
Delete temp directories (done)                                                                  [   OK  ]
pete@pete-desktop:~/TMP_DIR/DriverInstall$ 
```

Tried further tests 18:000 Hrs 30/08/2008
checked & Linux Headers are in filesystem /usr/src/linux-headers-2.6.24-16 & /usr/src/linux-headers-2.6.24-16-generic. They are also installed on app CDROM although when I tried to get Synaptic to find them it could not (or would not?)find them. CDROM said they had beeen loaded/installed version 2.6.24-16.

Also 
They are in filesystem at /usr/src/linux-headers-2.6.24-16 & /usr/src/linux-headers-2.6.24-16-generic.

Also tried additional test, results below

pete@pete-desktop:~$ ethtool --driver eth0

driver: forcedeth
version: 0.61
firmware-version: 
bus-info: 0000:00:0a.0
pete@pete-desktop:~$ 
---------------------- additional items added 22:16 30/08/2008

Notes added prior to above additions!
Notes:- So big improvement on first effort and getting better in using terminal etc. Not sure what to do next but had to stop and close all linux apps and open windows again for more advice.

Do I have to repeat the whole process again before adding the last bit about "kernal header files etc".

I await your response with a little more intelligent eagerness. Amazing what a bit of progress can do. Progress, one small step.
I think that I'm getting frustrated at not making quick enough progress, which I then blame on my ability. You are rigt however, soldier onwards, learning as we go.
Thanks for your assistance, it is greatly appreciated.

---

### Post by keentolearn on 2008-09-01
Hi Belatra,

Have made some progress with the driver. As above it reccommended removing a similar driver and then installing the sk98 driver. I have ttried it many times now and it always fails with 

"Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux 

I have tried a number of remedies off various sites and still get the same problem. 
The files /usr/src/2.6.24-16 & /usr/src/2.6.24-16-generic are present on my system.  I have tried symbolic link solution and still no luck.

I would be much obliged if you could suggest any furhter actions.

Thanks again for your anticipated help.

---

### Post by Belatra on 2008-09-03
I would say you are on the right way
Now just remove your incorrect link
```
cd /TMP_DIR/DriverInstall
rm /usr/src/linux
```
and make new one
```
ln -s /usr/src/linux-headers-2.6.24-16 /usr/src/linux
```
Run the script again
```
./install.sh
```
I believe you will get it done

---

### Post by Daveski on 2008-09-03
> **keentolearn said:**
> 
I downloaded WINE from the relevant HQ website and after much research attempted to load the program after transferring via USB mem stick. This then stated that one was Broken and had  "Dependancy Problems". "Error: Dependency is not 
satisfiable:libldap2". Status bar showed 1487 items had been loaded OK and that there appears to be just one 'broken' problem. I was unable to take matters any further on my own without some advice. So had to call it a day (6 weeks actually). Since I had in fact 'closed the circle' in terms of being unable to access the Internet with Ubuntu 8.04 and decided to seek help.

Like most things in Ubuntu, life is *MUCH* easier if you download and install applications from the official repositories. WINE is available as a simple one tick, and click install from Synaptic (or Add/Remove).

---

### Post by keentolearn on 2008-09-03
No matter what I try the sk98lin driver refuses to be installed. I have been back to Marvell site and have D/L another driver ie latest drivers for my hardware device. This is now "install_v10.61.3.3.tar.bz2" which has replaced later issue "install_v10.70.1.3.tar.bz2" for some reason-problems??. 

So I tried that as well and get the same result.

Error Reported:-

Check kernel header files (not found)              [ failed ]
Kernel header not found. Please install the linux header files 
development package or create a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

This has been repeated (many times) and Error still reports that the "header files are still missing at /usr/src" when in fact **they are all there**.

There are two folders [File1:- /usr/src/linux-headers-2.6.24-16]
[File2:- /usr/src/linux-headers-2.6.24-16-generic]. I obtained info from looking at the install.log file and that informed me that the kernal was the generic version installed, so therefore would use the 'generic' ref folder type in /usr/src/  folder. 

Also includes linux folder /usr/src/linux which [I presume] is the symbolic link file produced by script. If I click on the "linux" folder though, it informs me it is "Broken".

I used "sudo" for all relevant commands. Should I have to be the "big administator SU" to have the right permissions.

I am so frustratingly close to installation I feel. One last hurdle for the driver bit.

In addition  what should "ifconfig" show in respect of eth0 and eth1 when both are recognised by system. What is different about mine (shown at top) compared to yours. Are there some test/error
mesage bits etc.

Is it that the ports are physically OK but that my data path is incorrect etc. Or is a data test done on-chip without external data.

---

### Post by keentolearn on 2008-09-03
> Like most things in Ubuntu, life is MUCH easier if you download and install applications from the official repositories. WINE is available as a simple one tick, and click install from Synaptic (or Add/Remove).

I would if I could.... That's the reason -- No Internet available to me yet. Thanks fo ryour advice anyhow, cheers.

---

### Post by Daveski on 2008-09-03
> **keentolearn said:**
> I would if I could.... That's the reason -- No Internet available to me yet. Thanks fo ryour advice anyhow, cheers.

Sorry about that - I get carried away sometimes. I have been fortunate in never owning a USB / DSL modem (thankfully), and I have a service where I provided the equipment (ADSL router and separate Wifi access point).

Plugging your normal network card into an internet connected LAN is *THE* best and simplest way to get online in Linux as pretty much all NICs are supported. I forget that some service providers give crappy modems without decent support for anything other than Windows.

---

### Post by Belatra on 2008-09-04
> **keentolearn said:**
> 
There are two folders [File1:- /usr/src/linux-headers-2.6.24-16]
[File2:- /usr/src/linux-headers-2.6.24-16-generic]. I obtained info from looking at the install.log file and that informed me that the kernal was the generic version installed, so therefore would use the 'generic' ref folder type in /usr/src/  folder. 

Also includes linux folder /usr/src/linux which [I presume] is the symbolic link file produced by script. If I click on the "linux" folder though, it informs me it is "Broken"It means that you have to replace broken link with a correct one.
Step1 - remove your existing link
```
 sudo rm /usr/src/linux
```
Step2 - make new link to "generic" kernel (as you are asked)
```
 sudo ln -s /usr/src/linux-headers-2.6.24-16-generic /usr/src/linux
```
Step3 - run your installation script again (of course from **DriverInstall** directory)
```
 sudo ./install.sh
```

> I used "sudo" for all relevant commands. Should I have to be the "big administator SU" to have the right permissions.No matter.

---

### Post by keentolearn on 2008-09-04
Have re-done tests as u suggested, with results here.
Should the first line input be sudo ./install.shQuote: 
or should it be sudo ./install.shQuota:
 [see Errors at very bottom]
I replaced this with my previous method again in lines 3&4

Results of test SEp 4th 22:00 approx

[CODE]pete@pete-desktop:~/TMP_DIR/DriverInstall$ sudo ./install.shQuote: 
sudo: ./install.shQuote:: command not found
pete@pete-desktop:~/TMP_DIR/DriverInstall$ sudo ifconfig eth0 down  
pete@pete-desktop:~/TMP_DIR/DriverInstall$ sudo ./install.sh -s

Installation script for sk98lin driver.
Version 10.61.3.3 (Jul-07-2008)
(C)Copyright 2003-2008 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


IMPORTANT INFORMATION!

We found an alternative driver for your Marvell product on this system. The alternative driver is _NOT_ directly supported by Marvell and does not include all features provided by your device. If you want to use the sk98lin driver developed by Marvell, you may choose either to deactivate or remove the alternative driver.

[PRESS ANY KEY FOR FURTHER INSTRUCTIONS]

Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be loaded.

Deactivate driver:
  - alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 3

Disconnect alternative devices:  (done)                [   OK   ]
Unload alternative driver (done)                       [   OK   ]
Create tmp dir (/tmp/Sk98IZjdDLAplMEEfXdkEpHAl)        [   OK   ]
Check user id (0)                                      [   OK   ]
Check kernel version (2.6.24-16-generic)               [   OK   ]
Check kernel symbol file (/proc/kallsyms)              [   OK   ]
Check kernel type (SMP)                                [   OK   ]
Check number of CPUs (1)                               [   OK   ]
Check architecture./functions: line 325: arch: command not found
 (found)                                               [   OK   ]
Set architecture (i386)                                [   OK   ]
Check compiler (/usr/bin/gcc)                          [   OK   ]
Check mcmodel flags (none)                             [   OK   ]
Check module support (/sbin/insmod)                    [   OK   ]
Check make (/usr/bin/make)                             [   OK   ]
Check kernel gcc version (4.2.3) (Kernel:4.2.3 == gcc:4.2.3) [OK]
Check sk98lin driver availability (not loaded)         [   OK   ]
Check kernel header files (/usr/src/linux)             [   OK   ]
Check sources for .config file (/usr/src/linux/.config)[   OK   ]
Copy and check .config file (done)                     [   OK   ]
Check the mem address space (highmem)                  [   OK   ]
Change IOMMU (disabled)                                [   OK   ]
Create new .config file (done)                         [   OK   ]
Execute: make oldconfig (done)                         [   OK   ]
Check modpost availability (available)                 [   OK   ]
Unpack the sources (done)                              [   OK   ]
Check firmware availability (not available)            [   OK   ]
Check kernel header version (Kernel:2.6.24 == Header:2.6.24)[OK ]
Check kernel functions (Changed: nothing)              [   OK   ]
Compile the kernel (error)                             [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.[CODE]
-----------------------------------------------------------------
Results - Install.log
----------------------

Results - Install.log

+++ Kernel version 2.6.24-16-generic
+++ smp_count=1
+++ cpu_number=1
+++ kernel_machine=i686
+++ Architecture: i386
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.4/
2.4/skdim.c
2.4/sky2.c
2.4/skethtool.c
2.4/Makefile
2.4/skge.c
2.4/h/
2.4/h/skdrv1st.h
2.4/h/skdrv2nd.h
2.4/skproc.c
2.6/
2.6/skdim.c
2.6/sky2.c
2.6/skethtool.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skproc.c
common/
common/skgehwt.c
common/skgeasf.c
common/sk98lin.htm
common/skgeinit.c
common/sktwsi.c
common/skvpd.c
common/sky2le.c
common/sk98lin.4
common/skfops.c
common/skgespilole.c
common/skgeasfconv.c
common/skgemib.c
common/skaddr.c
common/skcsum.c
common/skgepnmi.c
common/vpdcheck.c
common/sklm80.c
common/skqueue.c
common/sktimer.c
common/skrlmt.c
common/skgespi.c
common/skxmac2.c
common/skgesirq.c
common/h/
common/h/sktypes.h
common/h/skpcidevid.h
common/h/skqueue.h
common/h/skrlmt.h
common/h/skgepnm2.h
common/h/skgeasfconv.h
common/h/skaddr.h
common/h/skdebug.h
common/h/mvyexhw.h
common/h/skgehw.h
common/h/skgehwt.h
common/h/skfops.h
common/h/sktimer.h
common/h/skgepnmi.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skerror.h
common/h/sktwsi.h
common/h/skcsum.h
common/h/skversion.h
common/h/xmac_ii.h
common/h/sky2le.h
common/h/skgeasf.h
common/h/skgespi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/lm80.h
common/h/skgedrv.h
common/sk98lin.txt
misc/
misc/Kconfig
misc/Configure.help

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.o
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c: In function  'sk98lin_init_device'
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:483: error: 'struct net_device' has no member named  'poll' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:484: error: 'struct net_device' has no member named  'weight' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:489: error: 'struct net_device' has no member named  'poll' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:490: error: 'struct net_device' has no member named  'weight' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:611: error: 'struct net_device' has no member named  'poll' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:612: error: 'struct net_device'  has no member named  'weight' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:617: error: 'struct net_device'  has no member named  'poll' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:618: error: 'struct net_device'  has no member named  'weight' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c: In function  'SkGeIsr' :
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:2315: error: too few arguments to function  'netif_rx_schedule_prep' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:2318: error: too few arguments to function  '__netif_rx_schedule' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c: In function   'SkGeIsrOnePort' :
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:2486: error: too few arguments to function  'netif_rx_schedule_prep' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:2491: error: too few arguments to function '__netif_rx_schedule' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c: In function â&#8364;&#732;SkGePoll' :
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:3250: error: â&#8364;&#732;struct net_device'  has no member named  'quota' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:3250: warning: type defaults to â&#8364;&#732;int'  in declaration of  '_y' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:3250: error: â&#8364;&#732;struct net_device'  has no member named  'quota' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:3271: error: â&#8364;&#732;struct net_device'  has no member named  'quota' 
/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.c:3275: error: too few arguments to function  'netif_rx_complete' 
make[1]: *** [/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all/skge.o] Error 1
make: *** [_module_/tmp/Sk98IZjdDLAplMEEfXdkEpHAl/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
+++ Compiler error

-----------------------------------------------------------------
Comments.
----------
Have now corrected the extra "â&#8364;&#8482;" type characters (replaced with [space+'] and ['+space]in last errors section of 'compile the driver' I think that they were numbers [NO, space & '] but not too sure, may repeat tomorrow night or asap. This is caused by my writing them with copy/paste etc using gedit and then opening with Notepad in windows. 

Could do with an application that reads/writes text identical in both systems. Real pain because I have to edit all the "new-line" characters each time. Unfortunately cannot keep both sets of data on screen with dual-booting! Also need to know how to use this text input device to perhaps attach some of text in files maybe to reduce size. Not done much posting to sites to learn howto's

[Apart from text output] Great that's the best so far, nearly at the last fence.
Seems a lot of errors in 'make' section

---

### Post by Belatra on 2008-09-05
Looks like some incompatibilities persist between script and kernel sources.
I would try to update the kernel to the current version 2.6.24-19. At least I got success with that version. As far as you have no Internet access you can download the packages from here
[http://packages.ubuntu.com/hardy/i386/linux-headers-2.6.24-19-generic/download](http://packages.ubuntu.com/hardy/i386/linux-headers-2.6.24-19-generic/download), copy them into temporary folder and then run installation with the command ```
dpkg -i /path/to/package/package_name.deb
``` Two packages should be installed *24-19* and *24-19-generic* I do not remember which one is dependence and which is main. You will be prompted to install main first if you accidentally start with dependence.
Appropriated directories should appear in /usr/src directory
After that remove the link and make new one with new headers' names.
You can also try to ask help from the diver developers pc**UNDERSCORE**connectivity**UNDERSCORE**tech**AT**marvell**DOT**com
The guy named Terry is very friendly and hi-tech literate. I believe you will overcome your problem with his help.

---

### Post by keentolearn on 2008-09-05
Just a quickie, Noticing your reference to i386, does it make any difference that my pc is an Amd Athlon 64 3200+ 2Ghz (skt 939) variety. Are there diff files to D/L for Intel & Athlon pc's Have I been using the wrong type of files??

---

### Post by Belatra on 2008-09-06
Yes, your packages located at
[http://packages.ubuntu.com/hardy/amd64/linux-headers-2.6.24-19-generic/download]("http://packages.ubuntu.com/hardy/amd64/linux-headers-2.6.24-19-generic/download")

---

### Post by keentolearn on 2008-09-06
Thanks for that info Belatra. I have emailed Terry at Marvell and await his reply. Have also D/L the header files. I will try and use the new header files, since if I undrstand you correctly they are the 2 files which appeared in /usr/src and were then used by the install.sh file. Since I was very happy with running that procedure many times I will have a go tomorrow, too late now.

I wanted also to thank you once again for your fantastic assistance to me. I really do appreciate the time and effort you have put in to getting me to understand the steps taken. I very much appreciate that, thanks.

If you don't mind I will keep you in touch with what broadly goes on from hereon in with Terry on this thread. Thanks again.

---

### Post by Belatra on 2008-09-10
I hope **keentolearn** finally you got your problem resolved. Sure you are welcome to ask my help every time you need. I do not have deep knowledge in Linux yet but I try to improve it. At the present time I am building my small home-office server based on Ubuntu 8.04 Sever. I went through some steps but still have a lot to do to get final result.

---

### Post by keentolearn on 2008-09-13
Thanks again for your help Belatra. I have not quite finished with Terry yet but have not made much further progress yet. It may well be that the original driver may be working, don't know until I get reply from email I will write after this.

Maybe that the problem could have something to do with starting up the USB ADSL modem and/or getting WINE to work, wish it was as easy as just downing a nice glass or two!!.

I will leave any prgress detail here for you to follow since it may be helpful perhaps to others following.

---

### Post by keentolearn on 2008-10-14
Hi Belatra,

Hope you see this. Have been doing a lot and not achieving too much. Have managed to contact Terry at MYkn again.

He has managed to supply me with some detailed info on the method and given me a link to the driver which works on Ubuntu Linux. I have copied the info below for youi rperusal. I do not really understand fully what is meant by some of the detail, certianly not enough to be able to implement.  I would really appreciate any comments and help that you could provide at this stage. I am also looking at whether my Win XP driver is as uptodate as it could be. I did some research on hardware drivers and thought that it may be relevant, but will have to wait and see.

I have a copy of that file on my drive already. It is called "Fedora install_v10.70.1.3.tar.bz2" on my drive at the moment so am not too sure why it has the 'fedora ' ref at front end. I have checked and it is the same file which I downloaded from a site which was connected with Fedora Linux version. I do not understand what problems that may hide so have downloaded the file called "Kernel 2.6.x Linux Driver Install Package for Yukon Devices" from Marvel Yukon site.

Sorry for delay in contacting you (house-painting duties etc etc)but until I got something real to get my teeth into it was not worth troubling you. I look forward with greatly resumed interest to see if we can crack this one. I am still also working on getting "Wine" to run the application "Onspeed" - compression type app in broadband ADSL line-link.

I am sure after the world sorted the bank problem we hopefully can solve this tweeny one!

Many thanks again for the time and help you have already given to me to help resolve this issue.

Cheers Keentolearn Pete

-----------------------------------------------------------------
Info supplied by Terry
-----------------------
 Pete, Here is some more detail on installing the Linux driver in Ubuntu using the install package:
 
Important information for using this driver:

1 - The embedded sky2 third party driver should be disabled in the kernel.

2 - It is required that the kernel source files be installed on the system.

3 - If the kernel has been updated a link may need to be added to point the installer to the correct header location.

  If Ubuntu Linux is being used the above information is the same plus please make the following change:

  Ubuntu linux uses dash instead of bash:
Dash = (Debian Almquist shell (dash) is a POSIX-compliant Unix shell, much
smaller than bash. It requires less disk space but is also less feature rich.)
You can just edit the first line in "install.sh" script and change the
offending "sh" to "bash".
- Change from #!/bin/sh" to #!/bin/bash.
- Run "install.sh" again.
 
 And the link to the driver for Linux that works in the v2.6.x kernel:
 
[http://www.marvell.com/drivers/driverDisplay.do?driverId=153](http://www.marvell.com/drivers/driverDisplay.do?driverId=153)

See comments about this file in above text].

---

### Post by keentolearn on 2009-01-06
In order to give this thread an end point, I would like to add that I was not able to solve the above saga of events using the MY88E8053 ethernet adaptors, perhaps another 10 years and who knows what might have been possible.

I am now able to access the intenet and move on (slowly) after having installed a router/wi-fi/hub and cabled access via ethernet cable to PC external port. This proved to be a much easier approach.

Many thanks to those kind enough to help, especially Belatra and to those who popped in to have a read thanks again.

Probably see you soon.

keentolearn

---

