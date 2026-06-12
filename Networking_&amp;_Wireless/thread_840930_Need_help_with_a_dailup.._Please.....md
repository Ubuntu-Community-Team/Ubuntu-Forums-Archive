---
title: "Need help with a dailup.. Please...."
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by hussainbtk on 2008-06-25
Hello Dears,

I recently got Toshiba Sattelite X200-21T, but it's designed for window vista :mad: so i decide to move from Vista to Ubuntu :), i have install ubuntu, its working 1000%.. but my problem is that i can't connect to internet, i have also install Gnome-ppp, which is install sucessfully, but when i am connecting to internet i got this error :
```
Failed, Modem not Found
``` << some thing similar to this..

please help me i am new to ubuntu, i have this modem in my Desktop PC : 
[INTEL-V92HAM-453]

and Driver can be find here:
[http://downloadcenter.intel.com/......me=&lang=eng]("http://downloadcenter.intel.com/detail_desc.aspx?agr=&ProductID=1057&DwnldID=5976&strOss=&OSFullName=&lang=eng")

So, please anyone knows, how to install that driver please help me i am really sad.... i really like ubuntu, but this problem making me crazy..

Please help help.............. :confused:

---

### Post by hussainbtk on 2008-06-25
Please, can anyone help me please....

**[COLOR="Red"]PLEASE HELP ME ????? :( :([/COLOR]**

---

### Post by celem on 2008-06-25
This is covered in Ubuntu's documentation. See:
[http://tinyurl.com/6ry76d](http://tinyurl.com/6ry76d)

---

### Post by M3TAL1QU1D on 2008-06-25
I am in the same boat as you, well, kind of. Unfortunatley, you need something a bit different than the standard setup wizards for the driver. you need to find whats called a package for it. Its alot different than windows because you cannot just click, click, click and your off. You should check to see if the company who made the modem has support for linux, if not, then maybe it is possible to find a package for it someone else has made. Or you may just need to find a supported modem....

sorry if it doesnt seem like im much help. like i said, im in the same boat as you being stranded without internet....

---

### Post by hussainbtk on 2008-06-26
Hey celem thanks alot, i got this in ModemData.txt
```

 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_06_21

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0951:1607 Kingston Technology 

USB modems not recognized

For candidate card in slot 05:05.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 05:05.0	1813:4000		Communication controller: Ambient Technologies Inc HaM controllerless modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 05:05.0 ----

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	8086:d605	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 22:        608          0   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   45.714612] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   45.714632] PCI: Setting latency timer of device 0000:00:1b.0 to 64

PCIbus=05:05.0
05:05.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
	Flags: medium devsel, IRQ 10
	Memory at 52001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=256]
	Capabilities: [60] Power Management version 2


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
 ---ALSA bootup diagnostics --- 

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-04: ALC883 Analog : ALC883 Analog : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1
01-00: SAA7134 PCM : SAA7134 PCM : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x52100000 irq 22
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7134[0] at 0x52002000 irq 18
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 05:05.0:
	Modem chipset  detected on
NAME="Communication controller: Ambient Technologies Inc HaM controllerless modem "
CLASS=0780
PCIDEV=1813:4000
SUBSYS=none
IRQ=10
IDENT=AmbientTech

 For candidate modem in:  05:05.0
   0780 Communication controller: Ambient Technologies Inc HaM controllerless modem 
      Primary device ID:  1813:4000
 Support type needed or chipset:	AmbientTech
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read DOCs/InfoGeneral.txt about alternatives.

----------------end Softmodem section --------------

Writing DOCs/Intel.txt

 Vendor=1813 Ambient Tech was acquired by Intel with its HaM (Host assisted Modem) chipsets.
 There is no support under 2.6.n kernels!!
 Intel-v92ham-453.tgz 2.4.n kernels was the FINAL 2.4.n update for HaM modems, available at:
    http://linmodems.technion.ac.il/packages/Intel/ham/ 
    http://developer.intel.com/design/modems/support/drivers.htm
    It is NOT functional when compiled under 2.6.n kernels.
 But under the 2.4.nn kernels, all HaM chipsets were supported,
    with a single EXCEPTION: the odd PCI_ID 1813:4100 modems.  For the explanation, see message:
    http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:9448:200210:fbhcoigfcimgkjdedjad
 ====== end AmbientTech section =======



Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
NAME="Audio device: Intel Corporation 82801G "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=8086:d605
IRQ=22
HDA=8086:27d8
SOFT=8086:27d8.HDA


 High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem, 
 and many are supported by the ALSA audio+modem driver snd-hda-intel
 A modem was not detected on HDA card 8086:27d8.
 If another modem card is present, then most likely 8086:27d8 does not host a modem.
 If another modem card has not been detected, then possibilities are:
	1) A Conexant modem chip is present on 8086:27d8, as Conexant chips
 are frequently not detectable by ALSA diagnostics
	2) The modem may be of the older non-PCI Controller Chipset (hardware) type.
Try detection with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  8086:d605 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.2.tar.gz from:  
	http://linmodems.technion.ac.il/packages/smartlink/

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

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
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,
 linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 15:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html

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
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


```

But where can i find modem driver, please help... 

PleaSE   :confused: :confused: :confused:

---

### Post by hussainbtk on 2008-06-26
Please, can anybody help me please ????

---

### Post by hussainbtk on 2008-07-04
please help, any one, please help

---

### Post by vandorjw on 2008-07-04
Edit: Read your first post again.

Now researching on how to get that to work.
(I had to do the same thing a year back but was unable to....)
Hopefully I am better at it now.

Thanks CC7
-----------------------------------------
I have downloaded the file, and extacted (unziped) the contents.

It looks to me like this thing needs to be compiled.

Lets say that you extracted it to your desktop, and now have a folder there called "Intel-v92ham-453"

Open up the "terminal" /Applications/Accessories/Terminal

then go to that folder on your desktop.
>  cd /home/**********ENTER-YOUR-USERNAME-HERE****/Desktop/Intel-v92ham-453 

Typing "LS" (not capitalized) shows you the folders and other files in this directory. 
for me 
config_check-----hamboot---hamregistry--license.txt--readme.txt
coredrv----------haminst---inc----------makefile-----serialdrv

** Hamboot, hamregistry, hamist are in light green, 
*** coredrv, inc, and serialdrv are in blue with green background 
(not sure, but I think this is just to make it easy to recognize certain file types.

------------------------
make: Nothing to be done for `makefile'.
make: Nothing to be done for `hamboot'. 

I have tried to run them in terminal, and it does nothing, plainly runing them also does nothing.

the ./ also does nothing.
** this is strange....

root@crazy1291-laptop:/home/*******/Desktop/Intel-v92ham-453# ./makefile
-bash: ./makefile: Permission denied
**(I am root?)**

I give up for now...will try some more tomorrow
PS: hopefully someone with more skill than I will help you...

---

### Post by vandorjw on 2008-07-04
> **M3TAL1QU1D said:**
>  ......like i said, im in the same boat as you being stranded without internet....

both of you have internet access somewhere...

and the first guy has the driver package, just doesn't know what to do with it. (and neither do I..*yet*)

I'll have it figured out over this weekend for sure :)

If that is not fast enough...experiment with the files..click them, run commands on them...anything you can think of

Until then hold tight...

---

### Post by hussainbtk on 2008-07-04
> 
Originally Posted by cc7gir
I'll have it figured out over this weekend for sure

Ok, i am waiting for your reply, please do some thing, i am 100% sure you can help me.. :)

Thanks in advance

---

### Post by hussainbtk on 2008-07-04
Hey, I got an error when installing that modem:
> 
mypcname@ubuntu:~/Desktop/Intel-v92ham-453$ sudo make install
bash haminst
running kernel 2.6.24-16-generic
unsupported kernel version.
make: *** [install] Error 1
mypcname@ubuntu:~/Desktop/Intel-v92ham-453$ 


Where i can find a supported kernel? please help..

Let me explain it a little more:

> 
ypcname@ubuntu:~$ cd /home/mypcname/Desktop/Intel-v92ham-453/
mypcname@ubuntu:~/Desktop/Intel-v92ham-453$ sudo make clean

when i wrote: sudo make clean i got this:
> 
[sudo] password for mypcname: 
cd coredrv; make clean
make[1]: Entering directory `/home/mypcname/Desktop/Intel-v92ham-453/coredrv'
rm -f *.o *~ core
make[1]: Leaving directory `/home/mypcname/Desktop/Intel-v92ham-453/coredrv'
cd serialdrv;  make clean
make[1]: Entering directory `/home/mypcname/Desktop/Intel-v92ham-453/serialdrv'
rm -f *.o *~ core
make[1]: Leaving directory `/home/mypcname/Desktop/Intel-v92ham-453/serialdrv'
rm -f *.o
rm -f *.o


When i wrote this: sudo make ham i got this:

> 
o
mypcname@ubuntu:~/Desktop/Intel-v92ham-453$ sudo make ham
   Module precompile check
   Current running kernel is: 2.6.24-16-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
cd coredrv; make \
       "PSTN_DEF=-DTARGET_HAM -DDSP_CODE_800_SERIES -DTARGET_LINUX -DLINUX" \
       ham; 
make[1]: Entering directory `/home/mypcname/Desktop/Intel-v92ham-453/coredrv'
cc -DTARGET_HAM -DDSP_CODE_800_SERIES -DTARGET_LINUX -DLINUX -Wall -O -I /lib/modules/`uname -r`/build/include -I../inc    -c -o coredrv.o coredrv.c
In file included from ../inc/hamcore.h:48,
                 from coredrv.c:33:
../inc/hamdefs.h:49:28: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.24-16-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/preempt.h:11,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/seqlock.h:29,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/time.h:8,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/timex.h:57,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:53,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:79: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:79: error: requested alignment is not a constant
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:200: error: requested alignment is not a constant
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:54,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:35,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:65,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/asm/vm86.h:22:1: warning: "VM_MASK" redefined
In file included from /lib/modules/2.6.24-16-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/preempt.h:11,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/seqlock.h:29,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/time.h:8,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/timex.h:57,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:53,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:29:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:65,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h: In function ‘user_mode’:
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: for each function it appears in.)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: ‘USER_RPL’ undeclared (first use in this function)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h: In function ‘user_mode_vm’:
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:54: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:54: error: ‘USER_RPL’ undeclared (first use in this function)
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:78,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/linux/proportions.h: In function ‘prop_inc_percpu’:
/lib/modules/2.6.24-16-generic/build/include/linux/proportions.h:75: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.24-16-generic/build/include/linux/proportions.h:77: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/timer.h:5,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:87,
                 from coredrv.c:35:
/lib/modules/2.6.24-16-generic/build/include/linux/ktime.h: In function ‘ktime_set’:
/lib/modules/2.6.24-16-generic/build/include/linux/ktime.h:84: warning: comparison is always false due to limited range of data type
coredrv.c: At top level:
coredrv.c:47: warning: data definition has no type or storage class
coredrv.c:47: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:47: warning: parameter names (without types) in function declaration
coredrv.c:48: warning: data definition has no type or storage class
coredrv.c:48: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:48: warning: parameter names (without types) in function declaration
coredrv.c:49: warning: data definition has no type or storage class
coredrv.c:49: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:49: warning: parameter names (without types) in function declaration
coredrv.c:50: warning: data definition has no type or storage class
coredrv.c:50: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:50: warning: parameter names (without types) in function declaration
coredrv.c:51: warning: data definition has no type or storage class
coredrv.c:51: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:51: warning: parameter names (without types) in function declaration
coredrv.c:52: warning: data definition has no type or storage class
coredrv.c:52: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:52: warning: parameter names (without types) in function declaration
coredrv.c:53: warning: data definition has no type or storage class
coredrv.c:53: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:53: warning: parameter names (without types) in function declaration
coredrv.c:54: warning: data definition has no type or storage class
coredrv.c:54: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:54: warning: parameter names (without types) in function declaration
coredrv.c:55: warning: data definition has no type or storage class
coredrv.c:55: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:55: warning: parameter names (without types) in function declaration
coredrv.c:56: warning: data definition has no type or storage class
coredrv.c:56: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:56: warning: parameter names (without types) in function declaration
coredrv.c:57: warning: data definition has no type or storage class
coredrv.c:57: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:57: warning: parameter names (without types) in function declaration
coredrv.c:58: warning: data definition has no type or storage class
coredrv.c:58: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:58: warning: parameter names (without types) in function declaration
coredrv.c:59: warning: data definition has no type or storage class
coredrv.c:59: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:59: warning: parameter names (without types) in function declaration
coredrv.c:60: warning: data definition has no type or storage class
coredrv.c:60: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:60: warning: parameter names (without types) in function declaration
coredrv.c:61: warning: data definition has no type or storage class
coredrv.c:61: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:61: warning: parameter names (without types) in function declaration
coredrv.c:62: warning: data definition has no type or storage class
coredrv.c:62: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:62: warning: parameter names (without types) in function declaration
coredrv.c:63: warning: data definition has no type or storage class
coredrv.c:63: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:63: warning: parameter names (without types) in function declaration
coredrv.c:64: warning: data definition has no type or storage class
coredrv.c:64: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:64: warning: parameter names (without types) in function declaration
coredrv.c:65: warning: data definition has no type or storage class
coredrv.c:65: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:65: warning: parameter names (without types) in function declaration
coredrv.c:66: warning: data definition has no type or storage class
coredrv.c:66: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:66: warning: parameter names (without types) in function declaration
coredrv.c:67: warning: data definition has no type or storage class
coredrv.c:67: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:67: warning: parameter names (without types) in function declaration
coredrv.c:68: warning: data definition has no type or storage class
coredrv.c:68: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:68: warning: parameter names (without types) in function declaration
coredrv.c:69: warning: data definition has no type or storage class
coredrv.c:69: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
coredrv.c:69: warning: parameter names (without types) in function declaration
coredrv.c:123: error: expected ‘)’ before string constant
coredrv.c: In function ‘kcli’:
coredrv.c:317: warning: implicit declaration of function ‘cli’
coredrv.c: In function ‘ksave_flags’:
coredrv.c:322: warning: implicit declaration of function ‘save_flags’
coredrv.c: In function ‘krestore_flags’:
coredrv.c:327: warning: implicit declaration of function ‘restore_flags’
coredrv.c: In function ‘ham_proc_shutdown_wait’:
coredrv.c:375: error: ‘CONFIG_HZ’ undeclared (first use in this function)
coredrv.c: In function ‘kdisable_irq’:
coredrv.c:387: warning: implicit declaration of function ‘disable_irq’
coredrv.c: In function ‘kenable_irq’:
coredrv.c:395: warning: implicit declaration of function ‘enable_irq’
make[1]: *** [coredrv.o] Error 1
make[1]: Leaving directory `/home/mypcname/Desktop/Intel-v92ham-453/coredrv'
make: *** [ham] Error 2


When i wrote, sudo make install i got this:

> 
mypcname@ubuntu:~/Desktop/Intel-v92ham-453$ sudo make install
bash haminst
running kernel 2.6.24-16-generic
unsupported kernel version.
make: *** [install] Error 1
mypcname@ubuntu:~/Desktop/Intel-v92ham-453$ 


Please i have 100% explain my error, so now please can any one help me please :(:confused:

---

### Post by hussainbtk on 2008-07-04
Below is my modem detial:

> 
**Intel® V.92 Modem Chipset Driver for Linux* [INTEL-V92HAM-453.TGZ]**
The Intel-V92ham-453.tgz contains the Intel® V.92 modem chipset driver for Linux (PCI) version 4.53. This driver supports Linux versions 2.4.X kernels - up to 2.4.18. This driver is not compatible with kernel version 2.2.X.

Chip Number: MD5628D-L-B


My Modem Driver support Linux versions 2.4.X kernels or up to 2.4.18, but where can i find the driver..

Please can anyone help me please :S

---

### Post by vandorjw on 2008-07-14
My apologies for my very late response. (and even now, it won't be all that good) :S


First of all, what version of Ubuntu, and what kernal are you using?
To check your kernal Version,

> uname -r

(To be honest with you, I have only been using Linux for about 6 months now, and am still learning.)

I got the same errors as you had. But I don't know what the errors mean.
>  sudo make clean
This already gave me an error. so I didn't even try to continue.

I hope someone with more skill comes and helps.

PS: In the read me, it give the command.
" insmod -f hamcore.o"

Which is something I wouldn't do. (insmod inserts stuff into the kernal, and this could really screw up your install.)

-CC7

---

