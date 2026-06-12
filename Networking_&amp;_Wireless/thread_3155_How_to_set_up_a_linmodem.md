---
title: "How to set up a linmodem?"
date: 2004-11-03
forum: Networking &amp; Wireless
---

### Post by Randall on 2004-11-03
Hi Folks,

I have a linmodem with Conexant HSF chipset. lspci shows that this device is detected OK. My problem is: I have no idea what (if anything) I have to do before I can use this modem. My experience to date has been using external modems only. I have configured an ISP using pppconfig and have tried /dev/ttyS0 (and S1 and S2) without success. The docs at linmodems.org are horribly out of date and I have been unable to find any basic setup instructions anywhere. Also, because ubuntu doesn't seem to have "minicom" or anything like it by default, I can't tell if I can even talk to this modem.

After doing "pon", the log in /var/log/messages shows messages being sent when using /dev/ttyS0 (the ATZ command is sent) but no reply from the modem. So I am guessing that something else has to be done to attach a tty to the modem.

Any help would be appreciated.

Cheers,
Randall.

---

### Post by Joeb on 2004-11-03
[QUOTE=Randall]Hi Folks,

I have a linmodem with Conexant HSF chipset. lspci shows that this device is detected OK. My problem is: I have no idea what (if anything) I have to do before I can use this modem. My experience to date has been using external modems only. I have configured an ISP using pppconfig and have tried /dev/ttyS0 (and S1 and S2) without success. The docs at linmodems.org are horribly out of date and I have been unable to find any basic setup instructions anywhere. Also, because ubuntu doesn't seem to have "minicom" or anything like it by default, I can't tell if I can even talk to this modem.

After doing "pon", the log in /var/log/messages shows messages being sent when using /dev/ttyS0 (the ATZ command is sent) but no reply from the modem. So I am guessing that something else has to be done to attach a tty to the modem.

Any help would be appreciated.

Cheers,
Randall.[/QUOTE]


I no longer have any winmodems, but if you're following the docs at linmodems.org, you might be better off trying to run a 2.4 kernel.  The device may be detected, but are you sure the driver is loaded?  It doesn't sound like it.  Assuming you haven't disabled your on-board serial ports, it's highly unlikely that the modem will be ttyS0 or S1 (unless it is set to that in CMOS COM1=ttyS0 COM2 = ttyS1, etc.)


If you don't mind my asking, why did you give up on the external modems?

---

### Post by Randall on 2004-11-03
[QUOTE=Joeb]

If you don't mind my asking, why did you give up on the external modems?[/QUOTE]

This setup is actually for my brother, who is trying to wean himself from Windoze, but is not very computer literate. I was hoping to be able to set up a linux partition on his computer with minimal fuss, hence Ubuntu. Everything has worked perfectly well except this modem and I don't have the time or expertise to change kernels. Judging from the linmodems website, this modem *is* supported- it is just a matter of setup. I just haven't been able to find instructions...

---

### Post by az on 2004-11-03
First:  Many winmodems can be used with linux (Conexant ($) Pctel, SmartLlink (sl-modem) Lucent, others).  Yours, has drivers written by a company called linuxant and you must pay them to get your modem working.  You can get a free version of the driver which will do 14.4KPS ([www.linuxant.com](www.linuxant.com))

As with probably all the other winmodems, you will need to compile the driver (make a kernel module)  You will need to get the source (or just your kernel's headers) and unpack it.
You will need to install the packages necessary for compiling stuff

sudo apt-get install build essential
sudo apt-get install linux-headers-2.6-386 kernel-kbuild-2.6-3

Since I am using the default 386 kernel, I got the 386 kernel-headers.  When asked during the configuration of the source for the driver where the kernel-source is, I will tell it to use:
/usr/src/linux-headers-2.6.8.1-3-386

The difference between Ubuntu and debian is that Ubuntu names the packages linux-headers and not kernel-headers.  The Linuxant debian package,for example, tells you to install the kernel-headers-3.6.8-1-386 package (which does not exist in Ubuntu - you must use linux-headers-2.6-386

Linuxant has a debian package for you and I just downloaded it and made it.  You must run sudo hsfconfig if you make a typo and it gives you and error or something.

If you are using another driver, you just follow the three step procedure (like for the pctel modem source)
cd to the directory
./configure
make
sudo make install

Load the module and you are off.  

I know that the sl-modem package also has a deamon.  If you need that driver, install the two packages from Universe and read the docs...  It should compile the modules for you (or even use an included alsa-modem module....)

I hope that this regurgitation of information can help.

---

### Post by Joeb on 2004-11-03
I believe the purpose of the free driver is just to test for compatability.  The full driver is $14.95.  That's not a bad price since it helps them pay the bills and all.  I think you get some help with that, too.   If you're really adventurous and cheap, you can download the last of the free versions of the driver from [http://www.int21.de/conexant/](http://www.int21.de/conexant/)  but there isn't any support or help for installing it.

---

### Post by jamaas on 2004-11-04
I've tried to follow your instructions but get this.  I've even tried changing the instructions to specify the kernel but still no luck :-(.  Any further suggestions?

Thanks 
Jim

=========jamaas@Bossy:~/Downloads/slmodem-2.9.10 $ sudo make install
make -C modem all
make[1]: Entering directory `/home/jamaas/Downloads/slmodem-2.9.10/modem'
make[1]: Leaving directory `/home/jamaas/Downloads/slmodem-2.9.10/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.8.1-3-386/build
make[1]: Entering directory `/home/jamaas/Downloads/slmodem-2.9.10/drivers'
cc -I/lib/modules/2.6.8.1-3-386/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.0-test7
make[2]: Entering directory `/home/jamaas/Downloads/slmodem-2.9.10/drivers'
make modules -C /lib/modules/2.6.8.1-3-386/build SUBDIRS=/home/jamaas/Downloads/slmodem-2.9.10/drivers
make[3]: Entering directory `/lib/modules/2.6.8.1-3-386/build'
make[3]: *** No rule to make target `modules'.  Stop.
make[3]: Leaving directory `/lib/modules/2.6.8.1-3-386/build'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jamaas/Downloads/slmodem-2.9.10/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jamaas/Downloads/slmodem-2.9.10/drivers'
make: *** [drivers] Error 2



[QUOTE=azz]
Since I am using the default 386 kernel, I got the 386 kernel-headers.  When asked during the configuration of the source for the driver where the kernel-source is, I will tell it to use:
/usr/src/linux-headers-2.6.8.1-3-386

The difference between Ubuntu and debian is that Ubuntu names the packages linux-headers and not kernel-headers.  The Linuxant debian package,for example, tells you to install the kernel-headers-3.6.8-1-386 package (which does not exist in Ubuntu - you must use linux-headers-2.6-386
[/QUOTE]

---

### Post by az on 2004-11-04
"I know that the sl-modem package also has a deamon. If you need that driver, install the two packages from Universe and read the docs... It should compile the modules for you (or even use an included alsa-modem module....)"

So I read the docs and it seems to works fine (/usr/share/doc/sl-modem-source/README.Debian)


cd /usr/src
sudo m-a clean slmodem
sudo tar xjvf sl-modem*
sudo module-assistant auto-install sl-modem-source

---

### Post by jamaas on 2004-11-04
Thanks again azz,

It is all getting very close but still getting this error message ! and then it all fails!

Building modules for kernel 2.6.8.1-3-386, using source directory
/usr/src/linux-headers-2.6.8.1-3-386. Please wait...
done.

ERROR: hcfpci driver not active
dpkg: error processing hcfpcimodem (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hcfpcimodem
E: Sub-process /usr/bin/dpkg returned an error code (1)




[QUOTE=azz]"I know that the sl-modem package also has a deamon. If you need that driver, install the two packages from Universe and read the docs... It should compile the modules for you (or even use an included alsa-modem module....)"

So I read the docs and it seems to works fine (/usr/share/doc/sl-modem-source/README.Debian)


cd /usr/src
sudo m-a clean slmodem
sudo tar xjvf sl-modem*
sudo module-assistant auto-install sl-modem-source[/QUOTE]

---

### Post by az on 2004-11-04
Maybe someone who actually has this type of modem can help.  All I can do is run the installation of the packages though.  Since I do not have the hardware, I can no longer help here.

I got rid of my two software modems a while back...

---

### Post by jamaas on 2004-11-04
Thanks a bunch for your help, much appreciated.  

Its oh so close!!  :-)

Jim


[QUOTE=azz]Maybe someone who actually has this type of modem can help.  All I can do is run the installation of the packages though.  Since I do not have the hardware, I can no longer help here.

I got rid of my two software modems a while back...[/QUOTE]

---

### Post by az on 2004-11-04
Are you sure that is the type of modem you have?

A good way to check would be to use the scanmodem script found here:

[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)


This should give you one or more suggestions of possible drivers for your hardware...

---

### Post by jamaas on 2004-11-04
Azz,

I've pursued this a little further, teh Linuaxant people have been throught this and suggest that it is a problem with 
modules-init-tools that it is not finding/loading the module correctly.  Is this a bug, or is there something I can do to tackle this?
Thanks

Jim

[QUOTE=azz]Maybe someone who actually has this type of modem can help.  All I can do is run the installation of the packages though.  Since I do not have the hardware, I can no longer help here.

I got rid of my two software modems a while back...[/QUOTE]

---

### Post by az on 2004-11-04
Can you be more specific?  What did they say.

Another thought:  Would you try the tar version of their driver (just the source, not the deb file)

If I have time at home, I may rip open my Ubuntu computer and try tinkering with these modems...

---

### Post by jamaas on 2004-11-04
this is the feedback after checking all the diagnostic files

perhaps it might help identify the problem?

Jim
=================

this is not the problem because the kernel modules were correctly built.
The problem is with the modprobe tool which is a part of the
'modules-init-tools' package. For an unknown reason, this tool is unable to
load the modem driver even if the right entries were inserted into it's
configuration files.

[QUOTE=azz]Can you be more specific?[/QUOTE]

---

### Post by az on 2004-11-06
Poped my sh*tty connexant modem into my pci slot.  Downloaded the TAR version of the free driver from linuxant

tar -xvzf hsf*
cd hsf*
sudo make install
sudo hsfconfig

pppconfig -------
...

pon test

Worked right away.  No problem.  The computer did not even crash when I did 
sudo hsfconfig uninstall



If I have time, I am going to try my Smartlink AMR modem...

---

### Post by az on 2004-11-06
Removed the Conexant pci modem and stuck in the AMR modem

Installed the sl-modem-source and the sl-modem-daemon packages.

The installation of the package used the alsa module.  I proceeded to make the non-free module anyway.

I will get around to test the alsa module and would encourage it's use wherever possible!


Read the docs.

To get the final modules from sl-modem-source, follow these instructions:

a) First, update the local source directory. If you use
   module-assistant, running "m-a clean sl-modem" should be enough.
   Otherwise, change to /usr/src and extract the driver source executing:
   
   tar jxvf sl-modem.tar.bz2
   
b) Next, build and install the driver using one of the following ways:

 - For already compiled kernel (eg. the currently running) with the
   module-assistant tool:

   module-assistant auto-install sl-modem-source

 - Using the make-kpkg(1) command provided by the kernel-package Debian
   package. This will produce a corresponding sl-modem-modules package for
   the Debian kernel-image package that you are using. This is "the Debian
   way". See the "modules_image" section of the make-kpkg(1) man page. When
   done, you can install the resulting sl-modem-x.y.z*.deb with dpkg.

 - Doing make-kpkg's job by hand, changing to /usr/src/modules/sl-modem and
   executing:

   debian/rules kdist KVERS=`uname -r` KSRC=/usr/src/kernel-headers-`uname -r`

   This assumes that you are building a modules package for the currently
   running kernel (uname -r) and the associated kernel-headers package is
   installed (eg. kernel-headers-2.4.20-bf2.4).

 - Changing to the /usr/src/modules/sl-modem/ directory and building as
   the README file instructs using "make; make install". This will build
   and install a module specific to the system you are building on and is
   not under control of the packaging system.


So I did:
m-a clean sl-modem
module-assistant auto-install sl-modem-source

Modem works fine!

In both cases, /dev/modem is symlinked to the actual device
(hsfconfig or sl-modem-daemon take care of this...)

---

### Post by az on 2004-11-09
For someone who cannot connect to the net, you can probaly download the two sl-modem packages somewhere else and transfer them by floppy:

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)

---

### Post by saBrEwolf on 2004-12-03
[QUOTE=azz]Removed the Conexant pci modem and stuck in the AMR modem

Installed the sl-modem-source and the sl-modem-daemon packages.

The installation of the package used the alsa module.  I proceeded to make the non-free module anyway.

I will get around to test the alsa module and would encourage it's use wherever possible!


Read the docs.

To get the final modules from sl-modem-source, follow these instructions:

a) First, update the local source directory. If you use
   module-assistant, running "m-a clean sl-modem" should be enough.
   Otherwise, change to /usr/src and extract the driver source executing:
   
   tar jxvf sl-modem.tar.bz2
   
b) Next, build and install the driver using one of the following ways:

 - For already compiled kernel (eg. the currently running) with the
   module-assistant tool:

   module-assistant auto-install sl-modem-source

 - Using the make-kpkg(1) command provided by the kernel-package Debian
   package. This will produce a corresponding sl-modem-modules package for
   the Debian kernel-image package that you are using. This is "the Debian
   way". See the "modules_image" section of the make-kpkg(1) man page. When
   done, you can install the resulting sl-modem-x.y.z*.deb with dpkg.

 - Doing make-kpkg's job by hand, changing to /usr/src/modules/sl-modem and
   executing:

   debian/rules kdist KVERS=`uname -r` KSRC=/usr/src/kernel-headers-`uname -r`

   This assumes that you are building a modules package for the currently
   running kernel (uname -r) and the associated kernel-headers package is
   installed (eg. kernel-headers-2.4.20-bf2.4).

 - Changing to the /usr/src/modules/sl-modem/ directory and building as
   the README file instructs using "make; make install". This will build
   and install a module specific to the system you are building on and is
   not under control of the packaging system.


So I did:
m-a clean sl-modem
module-assistant auto-install sl-modem-source

Modem works fine!

In both cases, /dev/modem is symlinked to the actual device
(hsfconfig or sl-modem-daemon take care of this...)[/QUOTE]
 Hi,
I have the slmodem package working with my AMR modem without problems. Apart from this. I have to be root in order to dialout. To keep it simple, how do I change the permission on the device so that I can dialout with any user?

Any help would be greatly appreciated

---

### Post by saBrEwolf on 2004-12-03
Hi,
I have the slmodem package working with my AMR modem without problems. Apart from this. I have to be root in order to dialout. To keep it simple, how do I change the permission on the device so that I can dialout with any user?

Any help would be greatly appreciated

---

### Post by az on 2004-12-03
If you use pon and poff (pppconfig) you should add your user to the dip group and then you should be able to dialout as yourself.  
sudo pppconfig
It's in the advanced options.
You can also probably use the graphical users 'n' groups utility...

---

### Post by saBrEwolf on 2004-12-03
Ok, Thanks azz

---

### Post by saBrEwolf on 2004-12-04
[QUOTE=azz]If you use pon and poff (pppconfig) you should add your user to the dip group and then you should be able to dialout as yourself.  
sudo pppconfig
It's in the advanced options.
You can also probably use the graphical users 'n' groups utility...[/QUOTE]
 Hey again, I've tried using pppconfig.. and it seems to work apart from one thing.
There is an extra line I need to add to the init in /etc/chatscripts/provider and I'm not sure of how to do this.

Any help would be greatly appreciated

---

### Post by saBrEwolf on 2004-12-06
Nevermind, I'll stick to using wvdial and poff

Thanks for the help before anyway azz

---

### Post by az on 2004-12-07
"There is an extra line I need to add to the init in /etc/chatscripts/provider and I'm not sure of how to do this."

Huh?

sudo gedit /etc/chatscripts/provider

or

sudo nano /etc/chatsctipts/provider

---

