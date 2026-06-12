---
title: "Error compiling 536EP driver"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by Kalidane on 2007-02-14
Need to get the modem running in the next few hours :( 

After 'make clean' I 'make 536' and get the following:

  Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.17-10-generic
make[1]: Entering directory `/home/name/Intel-536/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/kmmcghie/Intel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/name/Intel-536/coredrv/coredrv.o
/home/name/Intel-536/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/name/Intel-536/coredrv/coredrv.c:73: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/name/Intel-536/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/name/Intel-536/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/name/Intel-536/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/name/Intel-536/coredrv/coredrv.c: In function ‘close’:
/home/name/Intel-536/coredrv/coredrv.c:439: warning: implicit declaration of function ‘pm_unregister’
/home/name/Intel-536/coredrv/coredrv.c: In function ‘send_data_to_user’:
/home/name/Intel-536/coredrv/coredrv.c:587: error: ‘struct tty_struct’ has no member named ‘flip’
/home/name/Intel-536/coredrv/coredrv.c:592: error: ‘struct tty_struct’ has no member named ‘flip’
/home/name/Intel-536/coredrv/coredrv.c:593: error: ‘struct tty_struct’ has no member named ‘flip’
/home/name/Intel-536/coredrv/coredrv.c:595: error: ‘struct tty_struct’ has no member named ‘flip’
/home/name/Intel-536/coredrv/coredrv.c:596: error: ‘struct tty_struct’ has no member named ‘flip’
/home/name/Intel-536/coredrv/coredrv.c:597: error: ‘struct tty_struct’ has no member named ‘flip’
/home/name/Intel-536/coredrv/coredrv.c: At top level:
/home/name/Intel-536/coredrv/coredrv.c:665: error: expected ‘)’ before string constant
/home/name/Intel-536/coredrv/coredrv.c: In function ‘hamproc_write’:
/home/name/Intel-536/coredrv/coredrv.c:684: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
/home/name/Intel-536/coredrv/coredrv.c: At top level:
/home/name/Intel-536/coredrv/coredrv.c:880: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/name/Intel-536/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/name/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/name/Intel-536/coredrv'
2.6.17-10-generic
Failed to build driver


Any ideas where to from here?

---

### Post by jimi_tomorrow on 2007-06-05
I have the same chipset on my internal modem, and havent been able to get on line yet either, but for a different reason. 

Sounds to me like you want to make sure you have the requisite supporting software installed before you try to load this driver. Or make sure you have the right version driver for your version of Ubuntu. I have both edgy and feisty on disk, but am still running Xandros v3 until I figure this out.(which also doesn't like my Intel modem.)

From the Ubuntu "Modems supported by the Intel536EP driver" page:
"[COLOR="blue"]Install required Ubuntu packages:
•	Ubuntu 5.04 (Hoary Hedgehog) 
Make sure you have followed the section of this document entitled If compiling from source. 
•	Ubuntu 5.10 (Breezy Badger) 
Make sure you have additionally followed the section entitled Installing GCC 3.4. 
•	Ubuntu 6.06 (Dapper Drake) 
Ubuntu 6.10 (Edgy Eft) 
It's not clear if you need GCC 3.4 for these; it will probably work with the 'normal' gcc you get when following the If compiling from source section."[/COLOR]

Then this follows...
[COLOR="blue"]"Get the driver itself
•	Download the drivers for the modem. 
For Ubuntu 5.04, 5.10 and 6.06, use this link: 
 [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng) 
•	For 6.10, use this instead: 
 [http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz](http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-536EP-2.56.76.0_21_09_2006.tgz) 
•	For 7.04, try this: 
 [http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-2.56.76.0_23_02_2007.tgz) 
•	or this: 
 [http://www.mrgtech.ca/intel_536ep_feisty.tar.gz](http://www.mrgtech.ca/intel_536ep_feisty.tar.gz) 
•	Make sure you know where you've saved this file, which is named Intel-536EP-4.71.tgz or intel-536EP-2.56.76.0_21_09_2006.tgz or intel-536EP-2.56.76.0_23_02_2007.tgz; for the purposes of this document it will be assumed that it is in your home directory (which is /home/<username>, where <username> is your username). 
Compiling the driver
•	First we need to uncompress the downloaded file. Start a terminal window and run the following command: 
•	  tar xzf Intel-536EP-4.71.tgz
 
or (for 6.10) 
  tar xzf intel-536EP-2.56.76.0_21_09_2006.tgz
 
This assumes you saved the file downloaded from Intel in your home directory; otherwise, type cd <directory-where-the-file-is> before typing the tar command above. 
This will create a directory Intel-536 with the source contained in it. Change to this directory by typing 
  cd Intel-536
 
or (for 6.10) 
  cd intel-536EP-2.56.76.0
 
Still in the terminal window, type the following: 
  make clean
 
This should produce output looking like this: 
  Try `uname --help' for more information.
  cd coredrv; make clean
  make[1]: Entering directory `/home/rory/Intel-536/coredrv'
  rm -f *.ko *.o *~ core
  make[1]: Leaving directory `/home/rory/Intel-536/coredrv'
  rm -f *.o *.ko
 
Now type 
  make 536
 
This will result in many lines of output being printed to the terminal window; you can ignore most of them. The final lines should look like this: 
    CC      /home/rory/Intel-536/coredrv/Intel536.mod.o
    LD [M]  /home/rory/Intel-536/coredrv/Intel536.ko
  make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
  make[1]: Leaving directory `/home/rory/Intel-536/coredrv'
 
There should be an Intel536.ko file in the directory now; test this by typing ls -l Intel536.ko; the output should look like 
  -rw-r--r--  1 rory rory 1070520 2005-10-16 21:02 Intel536.ko
 
The file size should be similar, though probably not identical. 
Installing the driver
•	There are two steps to installing the driver. The first is to copy the Intel536.ko file created above to an appropriate directory, and the second is to cause the driver to be loaded at boot time. 
Installing the Intel536.ko file 
Copy the file to the modules directory by this command: 
  sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char
 
You may be prompted for a password; if so, enter your user password. 
Make your system aware of this module with depmod: 
  sudo depmod -a
 
Finally, load the driver with the modprobe command: 
  sudo modprobe Intel536
 
This command should not print a response; if it prints something like this: 
  FATAL: Module Intel536 not found.
 
you have made an error; most likely you have copied the file to the wrong place. If you see a different error message, there may be an error in the module, or your modem, or you may not have a Intel 536-based modem. 
Loading the driver at boot time 
To load the module at boot time, we need to add a line "Intel536" to the file /etc/modules. First make a backup of the file: 
  sudo cp /etc/modules /etc/modules.backup
 
Now add the required line as follows: 
  sudo sh -c "echo Intel536 >> /etc/modules"
 
Using the modem
•	The name of your modem device is /dev/536ep0. You can now use 
sudo pppconfig to set up pon & poff. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a file /etc/udev/rules.d/10-local.rules and put the following lines in it: 
•	  # Intelmodem536ep
•	  KERNEL="536ep0" SYMLINK="modem"
•	 
Now reboot and you can use Kppp to query the modem as this is a quick check if all is well before dialling out. Configure KPP for your ISP connection. These Intel modems are found to be more stable and less finicky that the Smartlink types on Breezy. [/COLOR]"

I've done all this, and the driver loads, and I have a modem listed now, but I can't seem to get a program to dial up the modem to get me on line. There is no Gnomeppp or Kppp on the install CD, and I guess I can't get online and download the packages, and to try to do it at work would be insane!

I found this elsewhere...

"[COLOR="blue"]For Ubuntu, without installing additional software (a.k.a System => Administration => Networking)
The Networking section of System => Administration will let you set up the ppp connection in a graphical interface. You have to know your device name, ISP phone number, username and password to set it up. You can also use the Gnome Modem Monitor and Network Monitor panel applets if you want to stop, start and monitor modem connections without opening the Networking GUI every time. Some people have had a problem with the modem dialing during bootup. This may be related to setting the modem as default route to the internet on the Options tab of Interface properties. 
Note: It has been reported, that connections started with this interface might be very slow, if they work. You can try it, but if this is the case for you, just try one of the other options.[/COLOR] "

I've also heard of people using the intel directions

[COLOR="Blue"]make clean, make 536, make install...[/COLOR]

If you find out how to get on line with this modem, please email me [email]jimi_tomorrow@pa.net[/email] , I'll be you best friend if you do, and if I figure this out before you do, I'll just brag about it!!!

---

### Post by Sepero on 2007-06-12
Kalidane, you're just the type of candidate I'm looking for in my thread, check here:
[http://ubuntuforums.org/showthread.php?t=471503](http://ubuntuforums.org/showthread.php?t=471503)


jimi_tomorrow, check out that thread too. I also cannot connect with those other programs, but I can connect with wvdial. In my binary driver package, I have a sample script for wvdial. Just fill in your PHONE#, USERNAME, and PASSWORD. Then save the file as /etc/wvdial.conf
Here is the script from the package:
```

[Dialer Defaults]
#Modem = /dev/modem
Modem = /dev/536ep0
Baud = 115200
Init = ATZ
New PPPD = yes
Stupid Mode = 1
Auto Reconnect = off
#Carrier Check = no
Dial Attempts = 1

# MODIFY THE FOLLOWING 3 SECTIONS FOR YOUR CONNECTION
Phone = 1234567
Username = ExampleName
Password = ExamplePassword

```

---

### Post by jimi_tomorrow on 2008-01-05
All,
I took a short break from Ubuntu due to the 536EP problem, and was using Xandros, which I purchased, and have really had no problems with.
However, I really, REALLY like the Gnome interface and feel of Ubuntu, and have been monitoring the forums intermittetly in hopes that there would be a driver developed for Ubuntu covering the Intel 536EP chipset, and loe and behold...

[http://ubuntuforums.org/search.php?searchid=34153015](http://ubuntuforums.org/search.php?searchid=34153015)

There is.

The next version of Ubuntu should have it built right in, but it looks like you can go right to the repository now and download the package for it and fire this pig right up. I haven't had time to try it yet, but I manually downloaded the driver packages that were discussed in the posts on the URL I have listed here.

[http://ubuntuforums.org/showthread.php?t=552090&highlight=intel+536ep+driver](http://ubuntuforums.org/showthread.php?t=552090&highlight=intel+536ep+driver)

Go there and drool as I have!!!

I have test drove so many versions of LINUX it's not even funny. Out of all of them, UBUNTU is my favorite.
My computer interests are digital photography editing, video/DVD authoring, Audio Editing and Gaming. Ubuntu is a great platform for them all.

Rock on!

---

### Post by Sepero on 2008-01-07
Hey wow, I was really excited when I first started reading your post jimi, because if Ubuntu included the modem drivers with it that would be great. Though after checking your links, either you or I are confused.

I followed the links you've listed, the first is broken, and the second is by me. I am not an official part of the Ubuntu team. We (Carlos and I) are just a couple guys that are trying to do a little good for society. The Ubuntu team has never officially contacted us once. (Not even to say thanks :)) Though that is fine, for me, I am just doing this for the people.

The first driver is Intel 536EP, produced by myself. The second driver is Intel 537EP, produced with the excellent help of my partner Carlos.

If the official Ubuntu team would like to take over responsibility of producing these drivers, that would be great. Official is almost always better than unofficial.

---

### Post by jimi_tomorrow on 2008-01-07
Oh. 
Well, ... Then you ROCK!!! :):):)
And I suppose the official guys are slackin'!...
I really wish they would take a break from rebuilding the OS, and work more on driver packages. I really think they would get more users interested in Linux, let alone Ubuntu, if people could see a flawless install that recognises all their hardware without having to browse support.(although I have several friends that have cable connections that have never had to "manually tweak" anything using Ubuntu.)
Maybe someday they'll bring cable to my remote location... Maybe the moon really IS made of cheez, and maybe the Hokey Pokey really IS what it's all about!   :)

---

### Post by Sepero on 2008-01-07
Despite the oddness displayed at the end of your post, your appreciation is well received. Take care my friend. :)

---

