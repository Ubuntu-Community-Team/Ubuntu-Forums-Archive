---
title: "The Chain of Errors"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by dmurat on 2009-02-09
well i have a chain of errors.. first of all i tried to install the new/fixed driver of Realtek to be able to use the internet. the instructions were:


```
This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

	- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
	- Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8168.ko (or r8168.o in linux kernel 2.4.x)
```

but when i type "make clean modules", i face such an error

```

dmurat@dmurat-desktop:/usr/src/r8168-8.010.00$ make clean modules
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.010.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/usr/src/r8168-8.010.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.010.00/src'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/usr/src/r8168-8.010.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/src/r8168-8.010.00/src/r8168_n.o
/usr/src/r8168-8.010.00/src/r8168_n.c: In function &#8216;rtl8168_hw_phy_config&#8217;:
/usr/src/r8168-8.010.00/src/r8168_n.c:1398: warning: unused variable &#8216;data&#8217;
/usr/src/r8168-8.010.00/src/r8168_n.c: In function &#8216;rtl8168_down&#8217;:
/usr/src/r8168-8.010.00/src/r8168_n.c:4838: warning: unused variable &#8216;poll_locked&#8217;
/usr/src/r8168-8.010.00/src/r8168_n.c: At top level:
/usr/src/r8168-8.010.00/src/r8168_n.c:2675: warning: &#8216;rtl8168_phy_power_down&#8217; defined but not used
/usr/src/r8168-8.010.00/src/r8168_n.c:4183: warning: &#8216;rtl8168_reinit_task&#8217; defined but not used
  LD [M]  /usr/src/r8168-8.010.00/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/r8168-8.010.00/src/r8168.mod.o
  LD [M]  /usr/src/r8168-8.010.00/src/r8168.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
strip --strip-debug r8168.ko
make[1]: Leaving directory `/usr/src/r8168-8.010.00/src'
```

after a google search, i thought i might need to build the latest kernel. an article i found suggested me to run these commands:

**sudo apt-get install linux-kernel-devel fakeroot build-essential makedumpfile** and **sudo apt-get build-dep linux**

but i face some errors again =((

```
dmurat@dmurat-desktop:~$ sudo apt-get install linux-kernel-devel fakeroot build-essential makedumpfile
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-kernel-devel

```

```
dmurat@dmurat-desktop:~$ sudo apt-get build-dep linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_intrepid_main_source_Sources - open (2 No such file or directory)
```

moreover, i tried to run sudo apt-get dist-upgrade, hoping it might help, but nothing happened.

i really need a help as a beginner =) is there anything i can do? especially for the error i get with [B]sudo apt-get build-dep linux
[/B]
any suggestions would be great. 
thanks.

*BTW im using ubuntu 8.10 atm

---

### Post by LowSky on 2009-02-09
well first off you can run sudo apt-get build-dep linux, without installing linux-kernel-devel, which is why the last error occurs.

secondly when you ran make clean modules you did not as root that command should have been 

sudo make clean modules

---

### Post by LowSky on 2009-02-09
well first off you can run sudo apt-get build-dep linux, without installing linux-kernel-devel, which is why the last error occurs.

secondly when you ran make clean modules you did not as root that command should have been 

sudo make clean modules

---

### Post by dmurat on 2009-02-09
this time, i ran sudo apt-get build-dep linux before the other but still the same error.
and nothing different when i run sudo make clean modules :\

any other suggestion?

---

### Post by dmurat on 2009-02-10
someone help please :\ i want to use my own ubuntu. how can i break this chain?

or, how can i fix
```
dmurat@dmurat-desktop:~$ sudo apt-get build-dep linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_intrepid_main_source_Sources - open (2 No such file or directory)
```

at least?

---

### Post by dmurat on 2009-02-10
well i guess im gonna roll fedora and try once more with linux. i hope i wont switch back to win at last :)

---

