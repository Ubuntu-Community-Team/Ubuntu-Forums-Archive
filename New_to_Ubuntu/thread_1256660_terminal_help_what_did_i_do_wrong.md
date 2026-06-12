---
title: "terminal help what did i do wrong?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by gognos on 2009-09-02
Hi guys/girls 

Im trying to understand and work out what im doing wrong

Experience with terminal commands lmited to mainly copy/paste

If someone could point out what i did wrong

What am i trying to do ? update alsa drivers/utiliites so on  to alsa-1.0.20.tar.bz2

what i did

1 typed

>  cat /proc/asound/version into terminal 

result Advanced Linux Sound Architecture Driver Version 1.0.18rc3

So then i tried to follow these instructions to update to version .20

this is what i did

1 typed > 
damien@damien-desktop:~$ sudo apt-get -y install build-essential ncurses-dev gettext xmlto
[sudo] password for damien: into terminal

result

>  Reading package lists... Done
Building dependency tree      
Reading state information... Done
build-essential is already the newest version.
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
gettext is already the newest version.
xmlto is already the newest version.
The following packages were automatically installed and are no longer required:
  mplayer-skins linux-headers-2.6.28-11 smplayer-translations
  linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Side question
I have used sudo apt-get install before however what does the -y mean??

step 2
typed into terminal

> 

cd ~
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2) result 

> damien@damien-desktop:~$ cd ~
damien@damien-desktop:~$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
--2009-09-03 12:07:17--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
           => `alsa-driver-1.0.20.tar.bz2.1'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> SIZE alsa-driver-1.0.20.tar.bz2 ... 2900799
==> PASV ... done.    ==> RETR alsa-driver-1.0.20.tar.bz2 ... done.
Length: 2900799 (2.8M)

100%[======================================>] 2,900,799   13.6K/s   in 60s     

2009-09-03 12:08:31 (46.9 KB/s) - `alsa-driver-1.0.20.tar.bz2.1' saved [2900799]

damien@damien-desktop:~$ wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
--2009-09-03 12:08:31--  [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2)
           => `alsa-lib-1.0.20.tar.bz2.1'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> SIZE alsa-lib-1.0.20.tar.bz2 ... 794728
==> PASV ... done.    ==> RETR alsa-lib-1.0.20.tar.bz2 ... done.
Length: 794728 (776K)

100%[======================================>] 794,728     36.0K/s   in 17s     

2009-09-03 12:08:52 (46.4 KB/s) - `alsa-lib-1.0.20.tar.bz2.1' saved [794728]

damien@damien-desktop:~$ wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)
--2009-09-03 12:08:57--  [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)
           => `alsa-utils-1.0.20.tar.bz2.1'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/utils ... done.
==> SIZE alsa-utils-1.0.20.tar.bz2 ... 1044483
==> PASV ... done.    ==> RETR alsa-utils-1.0.20.tar.bz2 ... done.
Length: 1044483 (1020K)

100%[======================================>] 1,044,483   72.8K/s   in 17s     

2009-09-03 12:09:29 (60.8 KB/s) - `alsa-utils-1.0.20.tar.bz2.1' saved [1044483]


step 3 

typed 

>  sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

result 

>  damien@damien-desktop:~$ sudo mkdir -p /usr/src/alsa
damien@damien-desktop:~$ cd /usr/src/alsa
damien@damien-desktop:/usr/src/alsa$ sudo cp ~/alsa* 
cp: target `/home/damien/alsa-utils-1.0.20.tar.bz2.1' is not a directory
damien@damien-desktop:/usr/src/alsa$ 
now im presuming it says 20.tar.bz2.1 because its the second apt-get attempt.

however this step seems to of failed saying not a directory 
or has it??

Continued anyway with step 4 

typed 
> sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*Result in terminal showed 

>  damien@damien-desktop:/usr/src/alsa$ sudo tar xjf alsa-driver*
tar: alsa-driver-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
damien@damien-desktop:/usr/src/alsa$ sudo tar xjf alsa-lib*
tar: alsa-lib-1.0.20: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: alsa-lib-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
damien@damien-desktop:/usr/src/alsa$ sudo tar xjf alsa-utils*
tar: alsa-utils-1.0.20: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: alsa-utils-1.0.20.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
damien@damien-desktop:/usr/src/alsa$ 
guess it failed again lol no idea why any reason ?? 

then tried to compile even tho steps prior failed 

typed >  cd alsa-driver*
sudo ./configure
sudo make
sudo make install

result was weird it complied an older version .13 i think 

>  damien@damien-desktop:~$ cd alsa-driver*
damien@damien-desktop:~/alsa-driver-1.0.13$ sudo ./configure
[sudo] password for damien: 
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/damien/alsa-driver-1.0.13
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.28-15-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.28-15-generic
checking for GCC version... ./configure: eval: line 3772: syntax error near unexpected token `)'
./configure: eval: line 3772: `my_compiler_version=4.3.3-5ubuntu4)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
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
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.28-15-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
damien@damien-desktop:~/alsa-driver-1.0.13$ 
Then typed 

>  cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install Result different this time 

>  damien@damien-desktop:~$ cd ../alsa-lib*
bash: cd: ../alsa-lib*: No such file or directory
damien@damien-desktop:~$ sudo ./configure
[sudo] password for damien: 
sudo: ./configure: command not found
damien@damien-desktop:~$ 

Next step 

typed 

[/quote] cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install 

[/quote]

result 

>  

damien@damien-desktop:~$ cd ../alsa-utils*
bash: cd: ../alsa-utils*: No such file or directory
damien@damien-desktop:~$ sudo ./configure
sudo: ./configure: command not found
damien@damien-desktop:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
damien@damien-desktop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
damien@damien-desktop:~$ 
Obviously everything isnt going to plan but continued to cut/paste instructions 

next step 

typed

>  rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils* 

result 

>  damien@damien-desktop:~$ rm -f ~/alsa-driver*
rm: cannot remove `/home/damien/alsa-driver-1.0.13': Is a directory
rm: cannot remove `/home/damien/alsa-driver-1.0.21': Is a directory
damien@damien-desktop:~$ rm -f ~/alsa-lib*
rm: cannot remove `/home/damien/alsa-lib-1.0.13': Is a directory
damien@damien-desktop:~$ rm -f ~/alsa-utils*
rm: cannot remove `/home/damien/alsa-utils-1.0.13': Is a directory
damien@damien-desktop:~$ 
now it is a directory after earlier im told it wasnt ? 

what does this step command translate to ? i mena what does it do 

Continued anyway 

tried 

>  cat /proc/asound/version again 

result 

>  Advanced Linux Sound Architecture Driver Version 1.0.18rc3. Total failure 



Also i tried downloading to desktop and followed generic ibnstructions on adding tar.bz2 files by trying   

>  cd ../
cd ../ alsa-driver-1.0.20.tar.bz2
tar -zxvf ./alsa-driver-1.0.20
./configure
make
sudo checkinstall which didnt work either 

result 

>  damien@damien-desktop:~$  cd ../
damien@damien-desktop:/home$ cd ../ alsa-driver-1.0.20.tar.bz2
damien@damien-desktop:/$ tar -zxvf ./alsa-driver-1.0.20
tar: ./alsa-driver-1.0.20: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
damien@damien-desktop:/$ ./configure
bash: ./configure: No such file or directory
damien@damien-desktop:/$ make
make: *** No targets specified and no makefile found.  Stop.
damien@damien-desktop:/$ sudo checkinstall
No luck either 

is anyone able to look at this information and tell whats gone wrong and explain the steps ive taken a little more so i can learn from my cut/pastes 

Big thanks in advance for any help

---

### Post by gognos on 2009-09-02
Also i just noticed after doing the above i no longer have sound in smplayer which was working perfectly before i tried this any reason as to why? thanks 

Still have sound playing mp3 so on with either movie player or rhythm box smplayer no longer plays music/dvd sound  like it did before i started mucking around

---

### Post by cariboo on 2009-09-02
What's wrong with the drivers that are already installed?

---

### Post by scorp123 on 2009-09-02
> **gognos said:**
>  If someone could point out what i did wrong You never used this simple command to verify if you even caught the right files: ```
ls -al
```

And why blindly continue with following instructions when a step has failed? That's dangerous. You might be deleting things (as you in fact did: "rm" removes files ...) without having the knowledge to fix what you just destroyed afterwards.

---

### Post by gognos on 2009-09-02
hello cariboo907 

Let me say i was lucky enough to have sound work out of the box when doing a clean install of 9.04 ubuntu unlike so many other posts ive read.

however i have  5.1 speakers to which i have only ever been able to use the 2 front and subwoofer with ubuntu. The center and 2 rear have never worked.

i did do a sound test a few days ago forgot how sorry.Its the one where it sends a chime through each speaker to test. the sound came out of every speaker except center with that test.to date i have been unable to get the rear or center speakers working with 9.04.all worked fine with xp. 

thinking i probably needed my motherboard sound drivers i went to the asus web site seeing they just used the alsa drivers but where at version .11 

I ended up getting the .18rc ones loaded thinking hoping it would help getting all my speakers working properly.

Again in a final hope i was going to try the .20 or .21 found on the alsa website in the hope it would improve the situation.

i have tried HDA Nvida alsa mixer changed to 6 channels and no difference 

I have tried the gnome alsa mixer ... no help 

have tried the alsa gui mixer .... no help 

Simply i am just trying to get all my speakers working without a clue of what im doing 

i read the the sound solutions thread [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) 

No help fixing my problem 

Have i broken something doing what i did because now i get no sound using smplayer at all Is another install needed. Is there a system restore type feature in linux like windows? Thanks for your reply

---

### Post by gognos on 2009-09-03
>  You never used this simple command to verify if you even caught the right files:

ls -al  

Yeah i was cuttting and pasting from instructions given by another without knowing what im doing 

So i can better understand where should of the ls -al of gone in what i posted earlier 

>  

And why blindly continue with following instructions when a step has failed? That's dangerous. You might be deleting things (as you in fact did: "rm" removes files ...) without having the knowledge to fix what you just destroyed afterwards. 

i didnt realize that yup obviously removed something lol 

anydata lost on this OS isnt a problem as a i havent moved all my files from xp to here yet and everything backed up on dvd anyway.

ill certainly not continue this practice in future thankyou 

You say the  ls -al command is used to veryify i got the correct file sice i didnt doesnt this mean i recieved it anyway? 

>  damien@damien-desktop:~$ cd ~
damien@damien-desktop:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")
--2009-09-03 12:07:17--  [ftp://ftp.alsa-project.org/pub/drive...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2")
           => `alsa-driver-1.0.20.tar.bz2.1'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> SIZE alsa-driver-1.0.20.tar.bz2 ... 2900799
==> PASV ... done.    ==> RETR alsa-driver-1.0.20.tar.bz2 ... done.
Length: 2900799 (2.8M)

100%[======================================>] 2,900,799   13.6K/s   in 60s     

2009-09-03 12:08:31 (46.9 KB/s) - `alsa-driver-1.0.20.tar.bz2.1' saved [2900799]

damien@damien-desktop:~$ wget [ftp://ftp.alsa-project.org/pub/lib/a...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2")
--2009-09-03 12:08:31--  [ftp://ftp.alsa-project.org/pub/lib/a...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2")
           => `alsa-lib-1.0.20.tar.bz2.1'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> SIZE alsa-lib-1.0.20.tar.bz2 ... 794728
==> PASV ... done.    ==> RETR alsa-lib-1.0.20.tar.bz2 ... done.
Length: 794728 (776K)

100%[======================================>] 794,728     36.0K/s   in 17s     

2009-09-03 12:08:52 (46.4 KB/s) - `alsa-lib-1.0.20.tar.bz2.1' saved [794728]

damien@damien-desktop:~$ wget [ftp://ftp.alsa-project.org/pub/utils...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2")
--2009-09-03 12:08:57--  [ftp://ftp.alsa-project.org/pub/utils...1.0.20.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2")
           => `alsa-utils-1.0.20.tar.bz2.1'
Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/utils ... done.
==> SIZE alsa-utils-1.0.20.tar.bz2 ... 1044483
==> PASV ... done.    ==> RETR alsa-utils-1.0.20.tar.bz2 ... done.
Length: 1044483 (1020K)

100%[======================================>] 1,044,483   72.8K/s   in 17s     

2009-09-03 12:09:29 (60.8 KB/s) - `alsa-utils-1.0.20.tar.bz2.1' saved [1044483] 			 		 

anything else i typed thats out of place?

---

### Post by gognos on 2009-09-03
Also scorp123 >  (as you in fact did: "rm" removes files ...) Fair enough rm removes files ill certanily remember that one however looking at the results 

>  damien@damien-desktop:~$ rm -f ~/alsa-driver*
rm: cannot remove `/home/damien/alsa-driver-1.0.13': Is a directory
rm: cannot remove `/home/damien/alsa-driver-1.0.21': Is a directory
damien@damien-desktop:~$ rm -f ~/alsa-lib*
rm: cannot remove `/home/damien/alsa-lib-1.0.13': Is a directory
damien@damien-desktop:~$ rm -f ~/alsa-utils*
rm: cannot remove `/home/damien/alsa-utils-1.0.13': Is a directory
damien@damien-desktop:~$  Doesnt it state cannot remove so therefore didnt ?? is there a reversal process i can do or another clean install needed?

---

### Post by nothingspecial on 2009-09-03
You need the -r flag to remove a directory, rm itself will only remove single files.

```
rm -r *directory_you_want_to_remove*
```

---

### Post by nothingspecial on 2009-09-03
Try [COLOR="Magenta"][this]("http://ubuntuforums.org/showthread.php?p=6589810")[/COLOR]

---

