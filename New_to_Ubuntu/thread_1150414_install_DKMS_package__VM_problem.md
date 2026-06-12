---
title: "install DKMS package?  VM problem"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by nachos99 on 2009-05-06
my sun VirtualBox stopped working after the last kernel update.  when i try to virtualize windows, it gives me the following error msg:

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


just running $sudo /etc/init.d/vboxdrv setup    does not appear to get the VM running windows again.  how do i install the DKMS package?

Thanks in advance for any suggestions.

---

### Post by spcwingo on 2009-05-06
> **nachos99 said:**
> how do i install the DKMS package?

With this command:

```
sudo apt-get install dkms
```

Then try to rebuild the module with the command that you already listed.

---

### Post by nachos99 on 2009-05-06
as suggested, i did

```
sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup

```

after restarting my computer, i can run windows in my virtualBox again.

thank you, spcwingo.

---

### Post by spcwingo on 2009-05-06
No prob.  Glad I could help.

---

### Post by annaa on 2009-05-17
Hi spcwingo,
Maybe you can help?  I get the same error as nachos99 when trying to open vbox, but after vbox 2.2 has failed to install.  The gdeb installer dialog just says "Installation finished, failed to install package 'virtualbox-2.2... Ubunto_hardy_i386.deb" and a blank terminal window.

Apparently it got part way, because trying to open vbox results in the error nachos saw (VERR_VM_DRIVER_NOT_INSTALLED).  "sudo apt-get.." installs the latest DKMS, but "/etc/init.d/vboxdrv setup" results in:

annaa@ubuntu-desktop:~$ /etc/init.d/vboxdrv setup
open: Permission denied
 * Stopping VirtualBox kernel module                                            open: Permission denied
 *  done.
open: Permission denied
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 342: cannot create /var/log/vbox-install.log: Permission denied

open: Permission denied
 * Look at /var/log/vbox-install.log to find out what went wrong
annaa@ubuntu-desktop:~$ 

The vbox-install.log starts with:
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0 ...

followed by yards of "gcc -m32" stuff, incomprehensible to a non-techie of no talent with computer guts.  
I tried running the "make oldconfig && make prepare" in terminal, and get "*** No rule to make target `oldconfig'.  Stop."

Is there any hope for a fix?

Thank you so much for any help you can provide!

---

### Post by spcwingo on 2009-05-17
I believe the reason you're getting errors is you need to add sudo (super user do) in front of the commands.  So instead of:

```
/etc/init.d/vboxdrv setup
```

It should be:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by annaa on 2009-08-08
Hey spcwingo - you rock! Thank you for your kind answer to a dumb question.

---

### Post by faintscrawl on 2009-12-11
.

---

### Post by jrsc109 on 2009-12-14
Hopefully someone can help. I have followed the instructions here, using SUDO, and still hitting problems.

I've attached the log output, so if someone could interpret and make a suggestion, that would be most appreciated.

Thanks in advance.

---

### Post by berlinblue on 2010-12-29
> **nachos99 said:**
> as suggested, i did

```
sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup

```

after restarting my computer, i can run windows in my virtualBox again.

thank you, spcwingo.


Same here.
Thanks very much for providing the solution!
BTW, I got a different error code, still the solution worked perfect!

---

### Post by afjeep on 2011-05-11
I'm having the same problems as the OP but this is what i get when i try to install DKMS. I'm using ubuntu 11.04, is this the issue?  thanks for any help y'all can give.

sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by wildmanne39 on 2011-05-11
> **afjeep said:**
> I'm having the same problems as the OP but this is what i get when i try to install DKMS. I'm using ubuntu 11.04, is this the issue?  thanks for any help y'all can give.

sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Hi, open synaptic packasge manager and put dkms in the search box and see if it is already installed because it looks like it is. Also check and make sure that main, universe,restricted and multiverse repositories are enabled. Under downloadable from the internet make sure the first four boxes are checked. Post back here what you find out, that package is all ready installed. Did you run this command? sudo /etc/init.d/vboxdrv setup:)

---

### Post by afjeep on 2011-05-11
> **wildmanne39 said:**
> Hi, open synaptic packasge manager and put dkms in the search box and see if it is already installed because it looks like it is. Also check and make sure that main, universe,restricted and multiverse repositories are enabled. Under downloadable from the internet make sure the first four boxes are checked. Post back here what you find out, that package is all ready installed. Did you run this command? sudo /etc/init.d/vboxdrv setup:)

yeah, looks like it is installed. all of the mentioned repositories are checked. tried the command you suggested this is what i got 

* Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Bad return status for module build on kernel: 2.6.38-8-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxhost/3.2.12/build/ for more information.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

---

### Post by wildmanne39 on 2011-05-11
> **afjeep said:**
> yeah, looks like it is installed. all of the mentioned repositories are checked. tried the command you suggested this is what i got 

* Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Bad return status for module build on kernel: 2.6.38-8-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxhost/3.2.12/build/ for more information.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

Hi, what does the file /var/lib/dkms/vboxhost/3.2.12/build/ tell you? Ok You need to instal the latest virtualbox by going to virtualbox.org and download the one for your system and for natty.

---

### Post by afjeep on 2011-05-11
> **wildmanne39 said:**
> Hi, what does the file /var/lib/dkms/vboxhost/3.2.12/build/ tell you? Ok You need to instal the latest virtualbox by going to virtualbox.org and download the one for your system and for natty.

fthanks, i'll give that a shot.

---

### Post by wildmanne39 on 2011-05-11
> **afjeep said:**
> fthanks, i'll give that a shot.

your welcome.):P

---

### Post by 14.navneet on 2011-06-30
p, li { white-space: pre-wrap; } **Kernel driver not installed (rc=-1908)**

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000FF]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.



**On the Terminal I found following problem**

sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found


Kindly provide the solution

---

### Post by capncrunch33 on 2012-02-22
worked for me as well thank you!

---

### Post by leMasoud on 2013-02-01
> **afjeep said:**
> yeah, looks like it is installed. all of the mentioned repositories are checked. tried the command you suggested this is what i got 

* Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Bad return status for module build on kernel: 2.6.38-8-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxhost/3.2.12/build/ for more information.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

in another scenario on Ubuntu 12.1 quantal the command 
sudo /etc/init.d/vboxdrv setup
have faced error and guided me to install the latest linux header so i executed the following code!
```
sudo apt-get install linux-headers-3.5.0-23-generic
```
the header version was given by the error message so don't worry ... it worked like a charm!

---

### Post by oldos2er on 2013-02-01
Old thread closed.

---

