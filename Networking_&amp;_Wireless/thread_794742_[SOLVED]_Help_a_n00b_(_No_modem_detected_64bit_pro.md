---
title: "[SOLVED] Help a n00b :( No modem detected 64bit problem"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by sober on 2008-05-14
Hi! I'm a total newbie in ubuntu, and right now i have almost anything i need... but the modem. I use mostly wireless but i have a long trip coming up and for 2 o 3 months i'll need to use dial-up.

The problem is that i don't have the drivers... and i was looking all day long and i got to a website called "linuxant" , since my modem's a conexant. It made me download some files for installing my PCI modem. Then i had to open a terminal and run some commands that led me to a website where i wrote as my username "/root" and as a password a loong code that appeared in the terminal. 

After all that.. the page told me it was going to install the driver, but i got only errors (404 and such) and it was impossible to install it. Then, a friend of mine came with a screwdriver, started poking one of my usb ports and my laptop turned off.... i lost all websites and cookies, well that's not the point but leads to the question.

I used software for diagnosis, (softmodem) and i got this:


 There are no blacklisted modem drivers in /etc/modprobe*  files 
USB modems not recognized
For candidate card in slot 00:10.1, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:10.1	10de:026c	103c:30b7	Audio device: nVidia Corporation MCP51 High Definition Audio 

 Modem interrupt assignment and sharing: 
 10:     338646      65229    XT-PIC-XT        HDA Intel, eth0
 --- Bootup diagnostics for card in PCI slot 00:10.1 ----
[   33.503714] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   33.503850] PCI: Setting latency timer of device 0000:00:10.1 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:10.1 has a High Definition Audio Card

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are:


The /proc/asound/pcm file reports:
-----------------------
00-01: Conexant Digital : Conexant Digital : playback 1
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb0000000 irq 10
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:10.1:
	Modem chipset  detected on
CLASS="Class 0403: 10de:026c"
NAME="Audio device: nVidia Corporation MCP51 High Definition Audio "
SUBSYS=103c:30b7
PCIDEV=10de:026c
IRQ=10
HDA=10de:026c
SOFT=10de:026c.HDA
CodecArchived=14f12bfa
ArchivedChip=0x14f12bfa
CodecClass=14f1
IDENT=hsfmodem

 For candidate modem in:  00:10.1
   Class 0403: 10de:026c Audio device: nVidia Corporation MCP51 High Definition Audio 
      Primary device ID:  10de:026c
    Subsystem PCI_id  103c:30b7 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x14f12bfa, a Conexant type using hsfmodem software.
                        
      

Support type needed or chipset:	hsfmodem


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.07full_k2.6.24_16_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. When compiling ALSA drivers, the utility "patch" will also be needed.



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 313600 2007-10-04 15:48 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1 wmaster0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


The problem is that i went to [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php) and downloaded as sugessted, but when i tried to install, i got the error that since my system is 64bit, i couldn't install the driver.

How can i fix my modem? And make it work? I tried the use the GNOME PPP for dialup.

My laptop's an HP Pavillion dv6000, AMD Turion 64x2 processor. 1 gb ram, i only have ubuntu, no partitions, no windows.

I hope someone can help me, setting up my dial-up is the only thing that keeps my ubuntu from being perfect.

THANKS IN ADVANCE!

---

### Post by Ayuthia on 2008-05-14
I have not even tried to see if my modem works on my dv6338se.  So I am not going to be too much use for you.  I did look at [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) and it looks like you will need to compile it on your own.  Take a look at the Generic packages with source and you will find this link: [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.68.00.10x86_64full/hsfmodem-7.68.00.10x86_64full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.68.00.10x86_64full/hsfmodem-7.68.00.10x86_64full.tar.gz)

They also say that if you are using 8.04 and have an HDA modem, you will also need to install [alsa-driver-linuxant]("http://www.linuxant.com/alsa-driver").

Hope that helps.  By the way, if you do go this route, you will also need to make sure that you have build-essential and linux-headers-`uname-r` installed prior to compiling.

---

### Post by sober on 2008-05-15
Thanks a lot, i downloaded the file, and i followed the instructions on "http://www.linuxant.com/drivers/hsf/install.php", (method C since the file is a gz) . I unzipped, them makefiled and the next step was to type "hsfconfig" . But when i tried, i got the error message, "command not found". 

What am i doing wrong? Sorry but all this is new for me, i have only used windows in the past (i used gnome for c programming with emacs but that's it).

Any help will be greatly appreciated

---

### Post by Ayuthia on 2008-05-15
> **sober said:**
> Thanks a lot, i downloaded the file, and i followed the instructions on "http://www.linuxant.com/drivers/hsf/install.php", (method C since the file is a gz) . I unzipped, them makefiled and the next step was to type "hsfconfig" . But when i tried, i got the error message, "command not found". 

What am i doing wrong? Sorry but all this is new for me, i have only used windows in the past (i used gnome for c programming with emacs but that's it).

Any help will be greatly appreciated
How did you build it?  Here is how I did mine:
```
sudo make clean install
sudo hsfconfig
```

I did test it out (the free version) and was able to connect at 14.4.  By the way, I have the same modem hardware as you (Nvidia MCP51).

---

### Post by sober on 2008-05-16
Thanks a lot! That way i was able to install it, but during installation, it asked me for the linux source build directory that matches my running kernel. I don't know what that is, so i just pressed enter. (it seems that it is lib/modules/2.6.24-16-generic/build by default), So it started building modules, but at the end i got the following warning:

> 
Warning: no device detected by hsf driver - HDA modems may require reboot
Note: HDA support not compiled in the driver


So i rebooted, but nothing happened. It still doesn't detect my modem...and worse, while installing, the terminal warned me that there may be some problems with the audio if i proceeded, and indeed, after the installation i didn't have any audio driver, and worse, the modem is still undetected! :( 

After the error came out, i was suggested to install the ALSA driver from [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) (i used the DEB package) but it couldn't be installed! Weird thing is, while installing, it produces a sound, like the login sound. 

The relevant events that happen during the alsa installation are (messages i get from the terminal during install):

> No pre-built modules for: Ubuntu - 8.04 linux 2.6.24-16-generic x86_64 SMP

Building modules... 
Warning: Module snd_hda_intel is in use

Waning: no device detected by hsf driver - HDA modems may require reboot

Removing hsf driver from /lib/modules/2.6.24-16 generic
ERROR: Build failed. Please review the build log 

Then it tries again and when it overrides the kernel modules :

> 
dpkg: error processing alsa-driver-linuxant (--install): subprocess post-installation script returned error exit status 2.


Failed to install the package alsa-driver-linuxant_1.0.16.1-1_all.deb


What am i doing wrong? I really don't know a lot about all this package installation thing... so maybe i'm doing something wrong, i built it as Ayuthia and i thought it had installed the drivers but for the errors i described earlier, it seems it didn't... :( it's weird that i can hear the login sound but at the end of the install process i get nothing...

:( please help!

---

### Post by Ayuthia on 2008-05-16
> **sober said:**
> Thanks a lot! That way i was able to install it, but during installation, it asked me for the linux source build directory that matches my running kernel. I don't know what that is, so i just pressed enter. (it seems that it is lib/modules/2.6.24-16-generic/build by default), So it started building modules, but at the end i got the following warning:



So i rebooted, but nothing happened. It still doesn't detect my modem...and worse, while installing, the terminal warned me that there may be some problems with the audio if i proceeded, and indeed, after the installation i didn't have any audio driver, and worse, the modem is still undetected! :( 

After the error came out, i was suggested to install the ALSA driver from [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) (i used the DEB package) but it couldn't be installed! Weird thing is, while installing, it produces a sound, like the login sound. 

The relevant events that happen during the alsa installation are (messages i get from the terminal during install):



Then it tries again and when it overrides the kernel modules :



What am i doing wrong? I really don't know a lot about all this package installation thing... so maybe i'm doing something wrong, i built it as Ayuthia and i thought it had installed the drivers but for the errors i described earlier, it seems it didn't... :( it's weird that i can hear the login sound but at the end of the install process i get nothing...

:( please help!

Well, there is supposed to be a log in /tmp that starts with alsa-driver-linuxant.  However, if you have rebooted after doing the attempted install, the file disappears (since it lives in /tmp).

Since the error lists that it is a post-installation script that failed, you should be able to run it again by:
```
sudo dpkg-reconfigure alsa-driver-linuxant
```It will create the error message again.  This time go to the /tmp directory and see if you can find a log for alsa-driver-linuxant.  If you can, attach the log to your post.

---

### Post by sober on 2008-05-17
Okay, here's the logfile, thanks

> rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-16-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-16-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver version... 1.0.16
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... yes
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... yes
checking for nested class_device... yes
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for PnP suspend/resume... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
copying file alsa-kernel/core/info.c
/usr/lib/alsa-driver-linuxant/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make: *** [include/sndversions.h] Error 2

---

### Post by Ayuthia on 2008-05-17
> **sober said:**
> make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
copying file alsa-kernel/core/info.c
/usr/lib/alsa-driver-linuxant/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
If you did not know, this is the error.  I think that patch-alsa is trying to patch info.c.  The problem is that there is no patch for it(I think).  I am not for sure if I am going to be able to figure this one out.  I am currently backtracking this to see what called this script and see what it passed.

The only thing that differs between you and me is that you are using 2.6.24-16 and I am using 2.6.24-17 (I am using the proposed changes from hardy-proposed).  The other thing that I did differently is that I installed this before compiling.

---

### Post by sober on 2008-05-17
> **Ayuthia said:**
> If you did not know, this is the error.  I think that patch-alsa is trying to patch info.c.  The problem is that there is no patch for it(I think).  I am not for sure if I am going to be able to figure this one out.  I am currently backtracking this to see what called this script and see what it passed.

The only thing that differs between you and me is that you are using 2.6.24-16 and I am using 2.6.24-17 (I am using the proposed changes from hardy-proposed).  The other thing that I did differently is that I installed this before compiling.

Thanks... then maybe if i change to 24-17? ... and how do i do that? I really know almost nothing about this... i'm just learning (the hard way, it seems), so i'll just try to keep up with your suggestions... Maybe if i do every step that you did we can figure out where's the problem...

And while (hopefully) we find an answer, is any way to restore the audio drivers back the way they were before i started messing with the modem drivers? :confused: Thanks again..

---

### Post by Ayuthia on 2008-05-17
> **sober said:**
> Thanks... then maybe if i change to 24-17? ... and how do i do that? I really know almost nothing about this... i'm just learning (the hard way, it seems), so i'll just try to keep up with your suggestions... Maybe if i do every step that you did we can figure out where's the problem...

And while (hopefully) we find an answer, is any way to restore the audio drivers back the way they were before i started messing with the modem drivers? :confused: Thanks again..
I am not for sure if you want to use the hardy-proposed repositories or not.  They are the pre-releases.  They are relatively safe, but they are not the actual release so there could be occasional problems.

There is a way to revert them back, but I am not 100% sure if it will work or not because I have never tried it.  It would be a matter of reinstalling one of the linux*2.6.24-16* packages, but I am not for sure which.

Are you having sound problems?  I was thinking that the alsa-driver-linuxant has not installed anything yet because it could not build the module.

The other bit of good news is that your sound should come back on the next update.  If I recall correctly, every kernel update will require us to recompile our modem driver.

---

### Post by sober on 2008-05-17
HOLY NOOB LUCK....

I was beginning to consider switching again to windows, when i decided to entirely delete alsa... (sudo apt-get -y remove alsa-base alsa-oss oss-compat), then i ran again the package installer for alsa driver linuxant, and this time it installed!!! Then audio came back and i was able to dial :D! So it's problem solved :D:D:D :popcorn:

Thanks a lot for all the help Ayuthia :D i probably couldn't have gotten to that "decision" without all the posting here. Thanks a lot! :p

---

