---
title: "Ndis wrapper trouble"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by snip101 on 2007-07-02
ok i have followed the instructions in this post [http://ubuntuforums.org/showthread.php?t=483548&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=483548&highlight=ndiswrapper)  the part where it says > Check if the ndiswrapper package has been installed correctly
ndiswrapper -v
Should get no errors here

I assume you have the wireless driver for your card??? If you do
cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf <-----Put in file name here

then i get this.

> abcouchey@abcouchey-laptop:~/ndiswrapper/ndiswrapper-1.47$ ndiswrapper -i bcmwl5a.inf
couldn't create /etc/ndiswrapper/bcmwl5a: Permission denied at /usr/sbin/ndiswrapper line 188.


if someone would help me fix this i would appreciate it since i would realy lke to get the wireless card to work with my comp.

my computer has an amd turion64 processor.

i am running the latest version of Ubuntu with the default gui.

my wireless card has been known to work with ndiswrapper and i am using drivers from someone who said that it worked with those drivers on the ndiswrapper site.

my wireless card is the BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

again thanks in advance for the help.

---

### Post by splintercellguy on 2007-07-02
sudo ndiswrapper...?

---

### Post by snip101 on 2007-07-02
that is what the other poster wrote it is about 5 posts down in the middle of a very large one.

---

### Post by splintercellguy on 2007-07-02
So does doing ndiswrapper -i bcmwl5a.inf work?

---

### Post by snip101 on 2007-07-02
i assume it did not since it gave me the error massage in the second quote.

---

### Post by splintercellguy on 2007-07-02
Oops! Meant sudo ndiswrapper -i ...

---

### Post by snip101 on 2007-07-02
wait a minuit i just saw the difference in what you posted let me try that.

---

### Post by snip101 on 2007-07-02
ok i crashed my computer by messing with cpu scailing programs at the same time but as of right now this is where i am 

> abcouchey@abcouchey-laptop:~$ sudo ndiswrapper -i bcmwl5a.inf
Password:
installing bcmwl5a ...
couldn't open bcmwl5a.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
abcouchey@abcouchey-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
abcouchey@abcouchey-laptop:~$ cd ~/Desktop
abcouchey@abcouchey-laptop:~/Desktop$ sudo ndiswrapper -i bcmwl5a.inf
driver bcmwl5a is already installed
abcouchey@abcouchey-laptop:~/Desktop$ sudo ndiswrapper -i bcmwl5.sys
installing bcmwl5.sys ...
couldn't find SourceDisksFiles section - continuing anyway...
couldn't get manufacturer section - installation may be incomplete
abcouchey@abcouchey-laptop:~/Desktop$ ndiswrapper -l
bcmwl5a : invalid driver!
bcmwl5.sys : invalid driver!
abcouchey@abcouchey-laptop:~/Desktop$ 


maby this will help.

---

### Post by kevdog on 2007-07-02
You can only install one driver at a time with ndiswrapper.  If you try to keep installing the same driver without uninstalling previous attempted installs, many times you are going to get strange error messages.

Uninstall all previous drivers.
The easiest way to do this is
cd /etc/ndiswrapper
sudo rm -R *

Then check the contents of the directory
ls
No files or directories should be listed.  If for some reason a file or directory is listed, then you will have to rm or delete this file or directory.

Then change to the directory where you have your wireless driver.  In the directory should be at least a .sys and .inf file.  Then try to reinstall the driver
sudo ndiswrapper -i ****.inf

---

### Post by snip101 on 2007-07-02
ok this is where i am at now

> abcouchey@abcouchey-laptop:/etc/ndiswrapper$ sudo rm -R *
Password:
abcouchey@abcouchey-laptop:/etc/ndiswrapper$ sudo rm -R *
rm: cannot remove `*': No such file or directory
abcouchey@abcouchey-laptop:/etc/ndiswrapper$ cd ~/Desktop
abcouchey@abcouchey-laptop:~/Desktop$ sudo ndiswrapper -i bcmwl5a.inf
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
abcouchey@abcouchey-laptop:~/Desktop$ 
abcouchey@abcouchey-laptop:~/Desktop$ 

now what do i need to do?

i also have a sys file that i think might need to be installed.

---

### Post by kevdog on 2007-07-02
I would consult the previous instructions that you quoted above -- I wrote them!!

Verify the install
ndiswrapper -l

Then procede to install the ndiswrapper module into the kernel.

---

### Post by snip101 on 2007-07-02
this is what i got.

> abcouchey@abcouchey-laptop:~/Desktop$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


i guess i need to disconnect from wired connection and try to get a wireless connection running now.  i will do that in a couple of min i have another program installing also.

---

### Post by snip101 on 2007-07-02
did not work now i do not know what to do.

I rebooted after removing the network cable and i cannot figure out what to do to make it connect to my wireless network.

---

### Post by snip101 on 2007-07-02
ok another problem with it.  now i when i run ndiswrapper -v i get the following message.

> modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9, utils version needed by module: '0'
module details:
modinfo: could not be open ndiswrapper: No such device

You may need to upgrade driver and/or utils to the latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

is the problem that i did not install the bcmwl5.sys file?

---

### Post by kevdog on 2007-07-02
Start over --- reinstall ndiswrapper.  You screwed something up somewhere!!

---

### Post by snip101 on 2007-07-02
how do i remove it i can try again and i will post exactly what i did but i am not certain of how to remove it.

---

### Post by snip101 on 2007-07-02
I have removed it using the package manager i told it to remove the packages completely.

---

### Post by snip101 on 2007-07-02
I need to leave for work now but i will post the results tomorrow when i can.

---

### Post by snip101 on 2007-07-03
So i did everything again but maby i did something wrong.at any rate this is what i did.

> abcouchey@abcouchey-laptop:~$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ cd ~
abcouchey@abcouchey-laptop:~$ mkdir ndiswrapper
mkdir: cannot create directory `ndiswrapper': File exists
abcouchey@abcouchey-laptop:~$ cd ~/Desktop
abcouchey@abcouchey-laptop:~/Desktop$ tar -zxvf ndiswrapper-1.47.tar.gzndiswrapper-1.47/
ndiswrapper-1.47/AUTHORS
ndiswrapper-1.47/ChangeLog
ndiswrapper-1.47/INSTALL
ndiswrapper-1.47/Makefile
ndiswrapper-1.47/README
ndiswrapper-1.47/ndiswrapper.spec
ndiswrapper-1.47/ndiswrapper.8
ndiswrapper-1.47/loadndisdriver.8
ndiswrapper-1.47/utils/
ndiswrapper-1.47/utils/Makefile
ndiswrapper-1.47/utils/ndiswrapper
ndiswrapper-1.47/utils/loadndisdriver.c
ndiswrapper-1.47/utils/ndiswrapper-buginfo
ndiswrapper-1.47/driver/
ndiswrapper-1.47/driver/divdi3.c
ndiswrapper-1.47/driver/hal.c
ndiswrapper-1.47/driver/iw_ndis.c
ndiswrapper-1.47/driver/iw_ndis.h
ndiswrapper-1.47/driver/loader.c
ndiswrapper-1.47/driver/loader.h
ndiswrapper-1.47/driver/longlong.h
ndiswrapper-1.47/driver/Makefile
ndiswrapper-1.47/driver/crt.c
ndiswrapper-1.47/driver/ndis.c
ndiswrapper-1.47/driver/ndis.h
ndiswrapper-1.47/driver/ndiswrapper.h
ndiswrapper-1.47/driver/ntoskernel.c
ndiswrapper-1.47/driver/ntoskernel.h
ndiswrapper-1.47/driver/ntoskernel_io.c
ndiswrapper-1.47/driver/pe_linker.c
ndiswrapper-1.47/driver/pe_linker.h
ndiswrapper-1.47/driver/pnp.c
ndiswrapper-1.47/driver/pnp.h
ndiswrapper-1.47/driver/proc.c
ndiswrapper-1.47/driver/rtl.c
ndiswrapper-1.47/driver/usb.c
ndiswrapper-1.47/driver/usb.h
ndiswrapper-1.47/driver/winnt_types.h
ndiswrapper-1.47/driver/workqueue.c
ndiswrapper-1.47/driver/wrapmem.h
ndiswrapper-1.47/driver/wrapmem.c
ndiswrapper-1.47/driver/wrapper.c
ndiswrapper-1.47/driver/wrapndis.h
ndiswrapper-1.47/driver/wrapndis.c
ndiswrapper-1.47/driver/lin2win.h
ndiswrapper-1.47/driver/win2lin_stubs.S
abcouchey@abcouchey-laptop:~/Desktop$ 
abcouchey@abcouchey-laptop:~/Desktop$ 
abcouchey@abcouchey-laptop:~/Desktop$ cd ndiswrapper-1.47
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ make distclean
make -C driver clean
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o win2lin_stubs.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
make -C utils clean
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
rm -f *~
rm -fr ndiswrapper-1.47 ndiswrapper-1.47.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o win2lin_stubs.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
make -C utils distclean
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
rm -f .\#*
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/abcouchey/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/abcouchey/Desktop/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/usb.o
  AS [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/win2lin_stubs.o
  LD [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/abcouchey/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/abcouchey/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ sudo make install
Password:
make -C driver install
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/abcouchey/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/abcouchey/Desktop/ndiswrapper-1.47/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ 
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ cd ~Desktop
bash: cd: ~Desktop: No such file or directory
abcouchey@abcouchey-laptop:~/Desktop/ndiswrapper-1.47$ cd ~/Desktop
abcouchey@abcouchey-laptop:~/Desktop$ sudo ndiswrapper -i bcmwl5a.inf
driver bcmwl5a is already installed
abcouchey@abcouchey-laptop:~/Desktop$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
abcouchey@abcouchey-laptop:~/Desktop$ 
abcouchey@abcouchey-laptop:~/Desktop$ 
abcouchey@abcouchey-laptop:~/Desktop$ sudo depmod -a
abcouchey@abcouchey-laptop:~/Desktop$ sudo modprobe -i ndiswrapper
abcouchey@abcouchey-laptop:~/Desktop$ sudo ndiswrapper -m
module configuration already contains alias directive

then when i want to do the last 3 commands i could not do them until i opened a terminal in root mode and this is what i go there.

> root@abcouchey-laptop:/home/abcouchey# /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
root@abcouchey-laptop:/home/abcouchey# /etc/iftab
bash: /etc/iftab: Permission denied
root@abcouchey-laptop:/home/abcouchey# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:68:bc:a9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:18
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:b6:31:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:20
root@abcouchey-laptop:/home/abcouchey# 

and it does not work.


I also tried using alien to make a deb package from the tar.gz file i have but that did not work to well.  it gave me the same results.

---

### Post by kevdog on 2007-07-03
Try this

gksu gedit /etc/modprobe.d/blacklist

Go to end of file and add the following:
blacklist bcm43xx

Save file and reboot.  Now do the following and post result:

lshw -C network

---

### Post by snip101 on 2007-07-03
i ran it in the terminal and it said i should run it in super user mode so i opened a super user terminal and re ran it and here are the results.

> Password:
root@abcouchey-laptop:~# lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:68:bc:a9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.109 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:18
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:c0204000-c0205fff irq:3
root@abcouchey-laptop:~#                   

I have also noticed that the wireless network configuration is not an option any more and under hardware configurations there seams to be no interface under the wireless card.

---

### Post by kevdog on 2007-07-03
Ok, now try this:

sudo modprobe -l | grep ndiswrapper

post output

lsmod | grep ndiswrapper

post output

ndiswrapper -v
ndiswrapper -l

---

### Post by kevdog on 2007-07-03
Could you also list the contents of your /etc/iftab file in addition to the above? 


Thanks

---

### Post by snip101 on 2007-07-03
Here you go.

> abcouchey@abcouchey-laptop:~$ sudo modprobe -l | grep ndiswrapper
Password:
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           239608  0 
usbcore               154416  4 ndiswrapper,ehci_hcd,ohci_hcd
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ ndiswrapper -v
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ ndiswrapper -l
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ 
abcouchey@abcouchey-laptop:~$ /etc/iftab
bash: /etc/iftab: Permission denied


I am still working on the /etc/iftab. i have 2 other ideas to try.

---

### Post by snip101 on 2007-07-03
ok i got it.

> # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:36:68:bc:a9 arp 1
eth1 mac 00:14:a5:b6:31:4f arp 1

---

### Post by kevdog on 2007-07-03
To read the file just do the following:

sudo /etc/iftab | more

---

### Post by kevdog on 2007-07-03
This will most likely not solve your problem, but do the following

gksu gedit /etc/iftab

Change eth0 to wlan0

Reboot
Repost lshw -C network

---

### Post by snip101 on 2007-07-03
here you go the first command i entered waited for about 10 sec then it just gave me the line for the next command.  so i did not copy it before rebooting.

> root@abcouchey-laptop:/home/abcouchey# Repost lshw -C networkbash: Repost: command not found
root@abcouchey-laptop:/home/abcouchey# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: wlan0
       version: 10
       serial: 00:16:36:68:bc:a9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.109 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:18
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:c0204000-c0205fff irq:3
root@abcouchey-laptop:/home/abcouchey# 



---

### Post by kevdog on 2007-07-03
What does it say after rebooting with the same command?

---

### Post by snip101 on 2007-07-03
After rebooting i get.

> root@abcouchey-laptop:/home/abcouchey# Reposit lshw -C network
bash: Reposit: command not found
root@abcouchey-laptop:/home/abcouchey# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: wlan0
       version: 10
       serial: 00:16:36:68:bc:a9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.109 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:18
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:c0204000-c0205fff irq:3
root@abcouchey-laptop:/home/abcouchey# 


---

### Post by kevdog on 2007-07-03
You need to uninstall ndiswrapper.  You didnt do it properly last time.  Im going to point you to a link to help you.  Please DO EXACTLY what it says.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

---

