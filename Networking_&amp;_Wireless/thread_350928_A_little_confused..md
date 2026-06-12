---
title: "A little confused."
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by thorosius on 2007-02-01
Hy!
               I "think" I have a Intel chipset Mercury Modem Model No: AMI-IA92: [http://www.mercury-pc.com/product-spec.php?productid=180]("http://www.mercury-pc.com/product-spec.php?productid=180")because its mentioned on its packing but if you visit the above mentioned url you will see "Ambient" written against Chipset on that webpage. There is another thing: In Device Manager of my WindowsXP modem is shown as "Intel(R) 537 Modem". Now I have been trying to install it in Ubuntu with the this driver: [http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz") with no success. I have run the scanmodem tool but I cant figure out its output. Am I choosing the right driver?

---

### Post by chili555 on 2007-02-01
> I have run the scanmodem tool but I cant figure out its output. Am I choosing the right driver?

If you will post its output here, we will help you figure it out.

---

### Post by thorosius on 2007-02-01
If you are refering to my installation output then its given below:

fahd@fahd-desktop:~/intel-537EP_secure-2.60.80.1$ sudo make clean
cd coredrv; make clean
make[1]: Entering directory `/home/fahd/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o .*.o.cmd *.mod.c *~ core .*.ko.cmd Modules.symvers
rm -rf .tmp_versions
make[1]: Leaving directory `/home/fahd/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko
fahd@fahd-desktop:~/intel-537EP_secure-2.60.80.1$ export MODEM_TYPE=537EP
fahd@fahd-desktop:~/intel-537EP_secure-2.60.80.1$ sudo make 537
   Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.17-10-generic
make[1]: Entering directory `/home/fahd/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/fahd/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/coredrv.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/clmmain.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/rts.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/task.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/uart.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/wwh_dflt.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/locks.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/softserial_io.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/softserial_ioctl.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/softserial.o
  CC [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.o
  LD [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/.537core.lib.cmd for /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/537core.lib
  CC      /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/Intel537.mod.o
  LD [M]  /home/fahd/intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/fahd/intel-537EP_secure-2.60.80.1/coredrv'
fahd@fahd-desktop:~/intel-537EP_secure-2.60.80.1$ sudo make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.17-10-generic
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
install DEBIAN 537 boot script and links
starting module and utilities
FATAL: Error inserting Intel537 (/lib/modules/2.6.17-10-generic/kernel/drivers/char/Intel537.ko): Operation not permitted
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules
done

---

### Post by chili555 on 2007-02-01
I guess I'm a LOT confused. I thought it was the scanmodem tool output you couldn't figure out. That's what we need to see if we are going to determine if you are building the correct driver.

---

### Post by thorosius on 2007-02-01
OK! I don't know the relevant part so Iv posted the whole ModemData.txt.


Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_December_25


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:02.0	e159:0001	8086:0003	Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface

 Modem interrupt assignment and sharing: 
193:        637          0   IO-APIC-level  ehci_hcd:usb5

 --- Bootup diagnositcs for card in PCI slot 02:02.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  02:02.0
   Class 0780: e159:0001 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
      Primary PCI_id  e159:0001
 Support type needed or chipset:	INTEL537
 


 Vendor e159 is Tiger Jet , [http://www.tjnet.com/](http://www.tjnet.com/)
  Controller e159:0001  translates PCI commands to the serial link used by
     the silabs DAA from the si3034, si3044 and si3056 family.
  The e159:0001  with SubSystem 8086:0003 is TJ320 v2.0 
  is the first and still most common of the Intel537 modem family.
  However primary controller chip can have broader uses:  [http://www.tjnet.com/chips/tiger320.htm](http://www.tjnet.com/chips/tiger320.htm)
  Though having its own driver package under 2.4.n. kernels,
  support (if any) from Intel is now included within the Intel-537EP package.

 ====== end Tigerjet section =======
 In 2006, Intel appears to have ceased updates for Linux.
 For the INTEL537 and INTEL536 chipset modems, the most current support is provided at:
       [http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/](http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/)
 But regular support is not available, see:  [http://archives.linmodems.org/24939](http://archives.linmodems.org/24939)
:
 The outdated official Intel support packages can be accessed through:
       [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)
 Read Intel.txt and Modem/YourSystem.txt for follow through guidance.


Writing Intel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-11 00:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by thorosius on 2007-02-01
I don't know if this is helpful, I'v followed the DialupModemHowto at : [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)  for intel537. inserting "537" instead of "537EP" in the step: export MODEM_TYPE=537EP completes the make install command successfully but wvdial doesnt detect any modem ... 

Thanks for all the replies.

---

