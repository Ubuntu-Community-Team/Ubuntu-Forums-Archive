---
title: "Hostap Injection patch on Ubuntu 7.10 (Gutsy Gibson)"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by waraey on 2007-10-20
[http://www.waraey.com/blog/?p=8](http://www.waraey.com/blog/?p=8)

This is a quick tutorial on hot to compile the hostap driver with the aircrack-ng injection patch. Thanks to angus for the old reference material. [http://asndotone.blogspot.com/](http://asndotone.blogspot.com/)

First and foremost you will need to install a few packages you may not already have: "build-essential", "dpkg-dev" and "linux-kernel-devel".

From your home directory create a temp directory that we can work in.

#mkdir hostapinject
#cd hostapinject

you now want to create a sub directory for our new kernel compilation

#mkdir koutput
#cp /boot/config-2.6.22-14-generic ./config-2.6.22-14-generic
#cd koutput
#ln -s ../config-2.6.22-14-generic .config

get the kernel for gutsy gibson. this may take a little while since its a ~60mb file.

#apt-get source linux-image-2.6.22-14-generic

get the modified patch (updated to reflect new kernel), and patch the kernel

#wget -nc [http://www.waraey.com/dl/files/hostap-kernel-2.6.22.patch](http://www.waraey.com/dl/files/hostap-kernel-2.6.22.patch)
#patch -p1 < hostap-kernel-2.6.22.patch

now lets compile the hostap kernel module v0.4.4 Note the v0.4.9 appears newer but is not compliant with the kernel configuration.

#cd linux-source-2.6.22-2.6.22/

we must manuall change version info (bug) so we dont get tainted kernel

#sudo gedit Makefile

change extraversion from "= 9" to "= -14-generic" . This should be the default but it has not been updated yet. Save and exit then:

#make O=../koutput outputmakefile
#make O=../koutput archprepare
#make O=../koutput modules SUBDIRS=scripts
#make O=../koutput modules SUBDIRS=drivers/net/wireless/hostap

hopefully this will succeed without any errors and you should now be ready to backup and install the new drivers.

backup the old files

#cd ..
#mkdir kbackup
#cd kbackup
#sudo cp /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/*.ko ./

now we are safe to install the new patched drivers

#cd ..
#cd koutput/drivers/net/wireless/hostap/
#sudo cp -dpR *.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/

Restart and it should load the new module. If booting freezes, remove the card to boot, then insert it after boot, and check #dmesg | grep hostap for errors.

I am still getting an error about kernel being tainted when loading the module. If figured fixing the vermagic would fix this problem, but it has not. If you have any suggestions let me know. "hostap: no version for "struct_module" found: kernel tainted."

I believe the freezing during boot is due to hostap dependency on ieee80211. If someone knows how to simply add a dependency check to the module let us know, otherwise we are stuck putting the card in after boot.

UPDATE 10/21/2007 !!!!

I have found a way to remove the "kernel tainted" error and fix the dependency problems. After you edit the makefile with"-14-generic" then #make O=../koutput menuconfig . You may need to have all of the latest ncurses configs. Then before you make SUBDIRS=scripts run #make O=../koutput modules . After it gets the essentials and scripts and most all the way through you can control-C out and continue on. This resoves all warnings with dependencies and taintedness.

This does not solve the non-booting problem with the card installed, but I am looking into this issue and will report back.

good luck,
waraey

---

### Post by kasperfish on 2007-11-14
hi i can not get the source for the kernel...

```
kasper@kasper-linux:~$ [COLOR="Red"]apt-get source linux-image-2.6.22-14-generic[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_dapper_free_source_Sources - open (2 No such file or directory)
kasper@kasper-linux:~$ 

```

any idee??
thanks

---

### Post by dlinuxor on 2007-11-22
kasperfish try:

```
$ sudo apt-get install linux-source-2.6.22 
```

you can find the source in /usr/src


Thanx waraey this was very useful to me..

you :guitar:

---

### Post by kevdog on 2007-11-22
Write this up with a little better formatting and submit it to the Tutorials and Tips section.  Its a very excellent tutorial and provides info other people can benefit from!

---

### Post by flyescke on 2008-02-07
Hi i'm getting a lot of errors in dmesg like hostap_cs: Unknown symbol ....
and i have the impression that it's not injecting :)

---

### Post by Reuter2k8 on 2008-02-09
Hi,
thanks for this tutorial. 

I'm getting this error when i'm trying to type this
> make O=../koutput outputmakefile

> scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
*** (missing kernel .config file)
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[3]: *** [silentoldconfig] Fehler 1
make[2]: *** [silentoldconfig] Fehler 2

Didn't i just copy the old config with
> cp /boot/config-2.6.22-14-generic ./config-2.6.22-14-generic?


Now "make oldconfig" should solve this probleme, but in fact it doesn't.
What i have to do next?
For further informations about my system just ask. I'm kinda new to this all but I'll try to follow you.


Greets

---

### Post by yeehawjared on 2008-04-29
any chance we can get this updated for hardy heron 8.04?

---

### Post by 052d on 2008-05-02
> **yeehawjared said:**
> any chance we can get this updated for hardy heron 8.04?

wish to know too

---

### Post by yeehawjared on 2008-05-02
I emailed the author, he's going to write up a hardy heron version soon.  :)

---

### Post by 052d on 2008-05-03
> **yeehawjared said:**
> I emailed the author, he's going to write up a hardy heron version soon.  :)

great!

---

