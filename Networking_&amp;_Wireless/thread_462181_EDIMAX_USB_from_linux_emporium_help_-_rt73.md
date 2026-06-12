---
title: "EDIMAX USB from linux emporium help - rt73"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by pfwd.tech on 2007-06-02
HI i am having some problems getting my Edimax usb stick to work.  I have followed the manual that the linux emporium sent with the stick but i still dont have wireless

When i put the stick in and open the terminal i get this message.
```
pete@pfwd:~$ 
Message from syslogd@pfwd at Sat Jun  2 17:52:00 2007 ...
pfwd kernel: [  102.933870] Oops: 0002 [1] SMP 

Message from syslogd@pfwd at Sat Jun  2 17:52:00 2007 ...
pfwd kernel: [  102.934165] CR2: 000000000010c000
```

The system crashes out of firefox and i cant open the text editor or restart the system.

Some outputs 
lsmod | grep usbcore
```
usbcore               154416  4 usbhid,ehci_hcd,uhci_hcd

```

gksu gedit /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
```

---

### Post by pfwd.tech on 2007-06-02
Im trying it again. This is what i have got before the restart.

```
pete@pfwd:~$ sudo mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
pete@pfwd:~$ sudo tar xvf /media/cdrom0/le_ralink_install.tar 
install_rt61_rt73.sh
rt61-1.1.0-b1.tar.gz
rt73-cvs-2006123101.tar.gz
set_essid.py
pete@pfwd:~$ ./install_rt61_rt73.sh 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Choose Ralink driver to install:

        1. RT61 - for PCI and PCMCIA cards
        2. RT73 - for USB dongles

        Choose 1 or 2 (q quits) 2

rt73-cvs-2006123101/
rt73-cvs-2006123101/CVS/
rt73-cvs-2006123101/CVS/Root
rt73-cvs-2006123101/CVS/Entries.Log
rt73-cvs-2006123101/CVS/Entries
rt73-cvs-2006123101/CVS/Repository
rt73-cvs-2006123101/FAQ
rt73-cvs-2006123101/LICENSE
rt73-cvs-2006123101/README
rt73-cvs-2006123101/TESTING
rt73-cvs-2006123101/THANKS
rt73-cvs-2006123101/CHANGELOG
rt73-cvs-2006123101/Module/
rt73-cvs-2006123101/Module/rt_config.h
rt73-cvs-2006123101/Module/rtmp_main.c
rt73-cvs-2006123101/Module/rtusb_io.c
rt73-cvs-2006123101/Module/wpa.h
rt73-cvs-2006123101/Module/load
rt73-cvs-2006123101/Module/rtmp_type.h
rt73-cvs-2006123101/Module/rtmp_tkip.c
rt73-cvs-2006123101/Module/assoc.c
rt73-cvs-2006123101/Module/sanity.c
rt73-cvs-2006123101/Module/oid.h
rt73-cvs-2006123101/Module/rtmp.h
rt73-cvs-2006123101/Module/unload
rt73-cvs-2006123101/Module/iwpriv_usage.txt
rt73-cvs-2006123101/Module/Makefile
rt73-cvs-2006123101/Module/rt73.h
rt73-cvs-2006123101/Module/rtmp_init.c
rt73-cvs-2006123101/Module/auth_rsp.c
rt73-cvs-2006123101/Module/rtusb_data.c
rt73-cvs-2006123101/Module/wpa.c
rt73-cvs-2006123101/Module/rtmp_info.c
rt73-cvs-2006123101/Module/sync.c
rt73-cvs-2006123101/Module/mlme.h
rt73-cvs-2006123101/Module/rt73.bin
rt73-cvs-2006123101/Module/rtmp_def.h
rt73-cvs-2006123101/Module/rt73sta.dat
rt73-cvs-2006123101/Module/mlme.c
rt73-cvs-2006123101/Module/rtmp_wep.c
rt73-cvs-2006123101/Module/ifcfg-rausb0
rt73-cvs-2006123101/Module/md5.c
rt73-cvs-2006123101/Module/md5.h
rt73-cvs-2006123101/Module/connect.c
rt73-cvs-2006123101/Module/auth.c
rt73-cvs-2006123101/Module/rtusb_bulk.c
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtmp_main.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/mlme.o
/home/pete/rt73-cvs-2006123101/Module/mlme.c: In function ‘MlmeAllocateMemory’:
/home/pete/rt73-cvs-2006123101/Module/mlme.c:5870: warning: cast from pointer to integer of different size
/home/pete/rt73-cvs-2006123101/Module/mlme.c:5870: warning: cast from pointer to integer of different size
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/connect.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtusb_bulk.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtusb_io.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/sync.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/assoc.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/auth.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/auth_rsp.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtusb_data.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtmp_init.o
/home/pete/rt73-cvs-2006123101/Module/rtmp_init.c: In function ‘RTMPReadParametersFromFile’:
/home/pete/rt73-cvs-2006123101/Module/rtmp_init.c:2129: warning: cast from pointer to integer of different size
/home/pete/rt73-cvs-2006123101/Module/rtmp_init.c:2129: warning: cast to pointer from integer of different size
/home/pete/rt73-cvs-2006123101/Module/rtmp_init.c:2130: warning: cast from pointer to integer of different size
/home/pete/rt73-cvs-2006123101/Module/rtmp_init.c:2130: warning: cast to pointer from integer of different size
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/sanity.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtmp_wep.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtmp_info.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/rtmp_tkip.o
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/wpa.o
/home/pete/rt73-cvs-2006123101/Module/wpa.c: In function ‘WpaGroupMsg1Action’:
/home/pete/rt73-cvs-2006123101/Module/wpa.c:1320: warning: cast from pointer to integer of different size
/home/pete/rt73-cvs-2006123101/Module/wpa.c:1320: warning: cast to pointer from integer of different size
/home/pete/rt73-cvs-2006123101/Module/wpa.c:1321: warning: cast from pointer to integer of different size
/home/pete/rt73-cvs-2006123101/Module/wpa.c:1321: warning: cast to pointer from integer of different size
  CC [M]  /home/pete/rt73-cvs-2006123101/Module/md5.o
  LD [M]  /home/pete/rt73-cvs-2006123101/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/pete/rt73-cvs-2006123101/Module/rt73.mod.o
  LD [M]  /home/pete/rt73-cvs-2006123101/Module/rt73.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/pete/rt73-cvs-2006123101/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  INSTALL /home/pete/rt73-cvs-2006123101/Module/rt73.ko
cp: cannot create regular file `/lib/modules/2.6.20-16-generic/extra/rt73.ko': Permission denied
  DEPMOD  2.6.20-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
/sbin/depmod -a
FATAL: Could not open /lib/modules/2.6.20-16-generic/modules.dep.temp for writing: Permission denied
make: *** [modules_install] Error
```

---

### Post by avandermade on 2007-06-04
Hi, please run the installer either as root or using the sudo command:

$ sudo ./install_rt61_rt73.sh

Let me know if you still have issues after this.

---

### Post by pfwd.tech on 2007-06-08
Hi i have the rt73 driver working now.  I can access the network/ internet when the Belkin router is at it's default settings (Out of the box) but when i add WEP and a SSID name and reconfigure my wireless it doesn't work.

I have tried adding my key and essid  in quotes and without
Tried the key in lower and upper caps
Changed the ssid name from belkin54g (defaukt) ro blackbox no spaces and lower caps

and added all the above to the interfaces ans it still isn't working.
Any one know whats going on?

---

### Post by qwright on 2007-06-20
With the Linux Emporium driver for the Edimax USB stick, the wireless configuration is held in a file called /etc/Wireless/RT73STA/rt73sta.dat. You can edit this directly  or run the set_essid.py  script.

---

