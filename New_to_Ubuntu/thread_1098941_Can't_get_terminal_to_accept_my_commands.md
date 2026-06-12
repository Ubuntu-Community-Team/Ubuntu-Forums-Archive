---
title: "Can't get terminal to accept my commands"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by kittyhawk63 on 2009-03-17
I am trying to get Ubuntu 8.10 to locate and run my Linksys Wireless Adapter wpc54g ver.3. I am trying to use a thread I found here in the forum to get the wireless to work. Problem: once I start with the command "sudo" followed by the rest of the command from the instructions I am following, I am asked for my password. I give it and it is accepted. After this...nothing happens but error messages. I am sorry, I have only this computer connected to the Internet using WinXP. I have dual boot. I cannot get to Ubuntu as long as I am on this forum using WinXP. If you need to know exactly what it being said, I will have to reboot into Ubuntu and run terminal and copy down what error I am given and then reboot back into WinXP to come back here and post my reply. It will be time consuming, but, I am willing to give it a go.
Hopefully, you can give me the answer I need without having to reboot these two times.
Thanks for any assistance you can give. 
kittyhawk63

---

### Post by .:Justus:. on 2009-03-17
> **kittyhawk63 said:**
> I am trying to get Ubuntu 8.10 to locate and run my Linksys Wireless Adapter wpc54g ver.3. I am trying to use a thread I found here in the forum to get the wireless to work. Problem: once I start with the command "sudo" followed by the rest of the command from the instructions I am following, I am asked for my password. I give it and it is accepted. After this...nothing happens but error messages. I am sorry, I have only this computer connected to the Internet using WinXP. I have dual boot. I cannot get to Ubuntu as long as I am on this forum using WinXP. If you need to know exactly what it being said, I will have to reboot into Ubuntu and run terminal and copy down what error I am given and then reboot back into WinXP to come back here and post my reply. It will be time consuming, but, I am willing to give it a go.
Hopefully, you can give me the answer I need without having to reboot these two times.
Thanks for any assistance you can give. 
kittyhawk63
Can you tell us what kind of error messages you are receiving?
Do non-sudo commands work?
Basically when you type sudo in front of a command it means you run it as root, which requires a password. If you give it in correctly the command should work without a problem, yet if you get errors it probably has to do with the actual command you put in or something else.
We can only guess whats wrong unless you give us a bit more info.
Sorry but you might have to start copying if you want more feedback.

**If you have a usb stick, go on ubuntu, save the commands/errors(basically copy  everything you typed into the terminal) in a text file and put them on the USB. Then boot back into XP and copy paste them here.**

---

### Post by kittyhawk63 on 2009-03-17
I don't have as USB stick, however, I can save it to a floppy with the same purpose. I will check to make sure that I am typing the commands correctly. I shall return and post my progress. Thanks for your quick response.

---

### Post by kittyhawk63 on 2009-03-17
Well, I am unable to save files from terminal to floppy because Ubuntu will not recognize the floppy drive. I have no CDs I can use. I also cannot get Ubuntu to install ndiswrapper 1.47 which is the one I need. I get an error 2 on trying to install it. I worked with Ubuntu for a few months when I had cable. It recognized my cable broadband without any problem. I now have wireless and no go. When it worked with my cable broadband connection, it was on my desktop. I am now trying to get it to work on my Toshiba laptop. On my desktop, I was using Feisty Fawn 7.04.

---

### Post by adult swim on 2009-03-17
you may need to run ```
sudo modprobe floppy
``` to recognize the drive

---

### Post by RetchingRabbit on 2009-03-17
The other possibility is to mount your windows partition and save the required error message in a tex file there. Then, when you reboot, you can still access the text in question.

---

### Post by kittyhawk63 on 2009-03-17
Thanks for the two last replies. I will try the first suggestion. If that does not work, then the second.

---

### Post by kittyhawk63 on 2009-03-17
Here is the output from terminal. Notice the Error 2 when I type "make."

kittyhawk63@ubuntu:~$ sudo aptitude install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

kittyhawk63@ubuntu:~$ cd ~/ndiswrapper/ndiswrapper-1.47
kittyhawk63@ubuntu:~/ndiswrapper/ndiswrapper-1.47$ make distclean
make -C driver clean
make[1]: Entering directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
       divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
       ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
make -C utils clean
make[1]: Entering directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/utils'
rm -f *~
rm -fr ndiswrapper-1.47 ndiswrapper-1.47.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
       divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
       ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
make -C utils distclean
make[1]: Entering directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/utils'
rm -f .\#*
kittyhawk63@ubuntu:~/ndiswrapper/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
make: *** [all] Error 2
kittyhawk63@ubuntu:~/ndiswrapper/ndiswrapper-1.47$ sudo make install
make -C driver install
make[1]: Entering directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/kittyhawk63/ndiswrapper/ndiswrapper-1.47/driver'
make: *** [install] Error 2
kittyhawk63@ubuntu:~/ndiswrapper/ndiswrapper-1.47$ 


The sudo modprobe floppy did the trick.
kh

---

### Post by adult swim on 2009-03-17
i think i have seen that you need ndiswrapper 1.50 or newer to work with ubuntu 8.10
you can get a newer version here, [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
you could then follow the same tutorial, except everywhere it says ndiswrapper-1.47 you would replace that with ndiswrapper-1.54

---

### Post by kittyhawk63 on 2009-03-18
> **adult swim said:**
> i think i have seen that you need ndiswrapper 1.50 or newer to work with ubuntu 8.10
you can get a newer version here, [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
you could then follow the same tutorial, except everywhere it says ndiswrapper-1.47 you would replace that with ndiswrapper-1.54
OK! I had already downloaded ndiswrapper-1.54. I will give it a try. Back to rebooting into Ubuntu. I will post the results.
kh

---

