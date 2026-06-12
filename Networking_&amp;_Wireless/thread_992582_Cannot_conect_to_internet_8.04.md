---
title: "Cannot conect to internet 8.04"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by wanted-66 on 2008-11-24
I have installed a Home Server variation put out by PCUser mag- based on Ubuntu 8.04- first time trying Linux
Installed on new machine. Works fine except cannot connect to internet or recognize any hardware to do so.Motherboard P5KPL-CM. Connected to Billion 7404VGP router using Cat 6 cable. Connection fine through other XP computers
Tried sudo :network (or similar)  command in the terminal- get 'not found'
I can get up the configuration box for user name password for internet provider but can never click on the OK button I guess because it cannot see any possible Ethernet connection. Strangely enough can tell me there are updates to download- but cannot download them
Any ideas out there please?:(
Edit :-  has an Atheros R8121 Gigabit Ethernet- do I need to install a driver?
Found this info- but if needed, how do I install it?
[http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg153887.html](http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg153887.html)

---

### Post by Iowan on 2008-11-25
I'm still blissfully ignorant of driver installation.  I found [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") help page, but it's for wireless drivers.  Try a forum search with "Atheros" as a keyword. I found several for "atheros", none for "Atheros R8121".

Let's take a side-trip... From a terminal check (and post, if possible) results of **ifconfig** and **lspci**.  It'd also be helpful if you could post results of **less /etc/network/interfaces**.

---

### Post by wanted-66 on 2008-11-25
Thanks for your reply.I have found a 'Family 81' Linux driver on the Atheros site and downloaded the tar.gz file. Google brings up quite a few references to problems with this ethernet connector and Linux.
I'll try installing it and post back with info if doesn't work.

---

### Post by wanted-66 on 2008-12-02
Can any one give me some more advice please? I'm stuck.I've followed these steps:
1. used mkdir to make /home/username/src/
2. moved tar.gz file to src
3. unzipped using tar zxvf <filename>
4. checked using ls
   seemed to be unzipped to src$ (which is inside src file)with info text files located in src file some of which were instructions which I have followed so far
5. used cd to move to directory
6. used sudo make install

the instructions say:
The binary will be installed as:
  / lib/modules/ <KERNEL VERSION>/kernel/drivers/net/ arl1e
and I checked it and yes it is there exactly.
The next instruction has me stuck-
7. Install the module:
   insmod arl1e <parameter>=<value>
Can someone help as to what directory I should be in to run this, and what goes in parameter and value?
8. next is to run
 ifconfig ethx <IP_address>
then
9. ping <IP_address>
Any advice for a complete newbie would be great.......I'm learning fast!

---

### Post by wanted-66 on 2008-12-03
When I run make install, this is what I get.
Can anyone tell me what I'm doing wrong?
-----------------------------------------------------------------
rebecca@server:~/src/arl1e/src$ make
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/rebecca/src/arl1e/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/rebecca/src/arl1e/src/at_main.o
  CC [M]  /home/rebecca/src/arl1e/src/at_hw.o
  CC [M]  /home/rebecca/src/arl1e/src/at_param.o
  CC [M]  /home/rebecca/src/arl1e/src/at_ethtool.o
  CC [M]  /home/rebecca/src/arl1e/src/kcompat.o
  LD [M]  /home/rebecca/src/arl1e/src/atl1e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rebecca/src/arl1e/src/atl1e.mod.o
  LD [M]  /home/rebecca/src/arl1e/src/atl1e.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rebecca@server:~/src/arl1e/src$ make install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/rebecca/src/arl1e/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
gzip -c ../atl1e.7 > atl1e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.24-16-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.24-16-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/atl1e.ko
install: cannot create directory /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e: Permission denied
make: *** [install] Error 1

---

### Post by spcwingo on 2008-12-03
Try to run as root (sudo make install).

---

### Post by wanted-66 on 2008-12-03
I have given up on the PC User Home Server version- thought I'd try the latest 8.10.
Same problem. I have recorded the entire terminal- I always get to where ' cannot install in catman mode' happens with no problems.
This is on a fresh install.

rebecca@server:~$ mkdir /home/rebecca/src 
rebecca@server:~$ cd /home/rebecca/src 
rebecca@server:~/src$ ls 
rebecca@server:~/src$ ls 
AR81Family-linux-v1.0.1.0.tar.gz 
rebecca@server:~/src$ tar zxvf AR81Family-linux-v1.0.1.0.tar.gz 
atl1e.7 
copying 
ldistrib.txt 
readme 
release_note.txt 
src/ 
src/at.h 
src/at_ethtool.c 
src/at_hw.c 
src/at_hw.h 
src/at_main.c 
src/at_osdep.h 
src/at_param.c 
src/kcompat.c 
src/kcompat.h 
src/kcompat_ethtool.c 
 
gzip: stdin: decompression OK, trailing garbage ignored 
src/Makefile 
src/Module.symvers 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 
rebecca@server:~/src$ cd /~/src/src/ 
bash: cd: /~/src/src/: No such file or directory 
rebecca@server:~/src$ cd /home/rebecca/src/src/ 
rebecca@server:~/src/src$ make 
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/rebecca/src/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic' 
  CC [M]  /home/rebecca/src/src/at_main.o 
  CC [M]  /home/rebecca/src/src/at_hw.o 
  CC [M]  /home/rebecca/src/src/at_param.o 
  CC [M]  /home/rebecca/src/src/at_ethtool.o 
  CC [M]  /home/rebecca/src/src/kcompat.o 
  LD [M]  /home/rebecca/src/src/atl1e.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/rebecca/src/src/atl1e.mod.o 
  LD [M]  /home/rebecca/src/src/atl1e.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' 
rebecca@server:~/src/src$ make install 
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/rebecca/src/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' 
gzip -c ../atl1e.7 > atl1e.7.gz 
# remove all old versions of the driver 
find /lib/modules/2.6.27-7-generic -name atl1e.ko -exec rm -f {} \; || true 
rm: cannot remove `/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e/atl1e.ko': Permission denied 
find /lib/modules/2.6.27-7-generic -name atl1e.ko.gz -exec rm -f {} \; || true 
install -D -m 644 atl1e.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e/atl1e.ko 
install: cannot remove `/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e/atl1e.ko': Permission denied 
make: *** [install] Error 1 
rebecca@server:~/src/src$ sudo make install 
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/rebecca/src/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' 
# remove all old versions of the driver 
find /lib/modules/2.6.27-7-generic -name atl1e.ko -exec rm -f {} \; || true 
find /lib/modules/2.6.27-7-generic -name atl1e.ko.gz -exec rm -f {} \; || true 
install -D -m 644 atl1e.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e/atl1e.ko 
/sbin/depmod -a || true 
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz 
man -c -P'cat > /dev/null' atl1e || true 
man:  
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode 
atl1e. 
rebecca@server:~/src/src$ cd 
rebecca@server:~$ cd /lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e 
rebecca@server:/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e$ sudo insmod./atl1e.ko 
sudo: insmod./atl1e.ko: command not found 
rebecca@server:/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e$ sudo insmod ./atl1e.ko 
insmod: error inserting './atl1e.ko': -1 File exists 
rebecca@server:/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e$ sudo insmod arl1e.ko 
insmod: can't read 'arl1e.ko': No such file or directory 
rebecca@server:/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e$ modprobe arl1e 
FATAL: Module arl1e not found. 
rebecca@server:/lib/modules/2.6.27-7-generic/kernel/drivers/net/atl1e$  

Help!

---

### Post by ge0rdie on 2008-12-04
I have just sorted a similar prob on CentOS 5.2

The driver installed to ...kernel/drivers/net/atl1e/atl1e.ko
"modprobe atl1e" gave me the same BS message

I saw all these other .ko files in the net directory, so I copied atl1e.ko up one level into the ...kernel/drivers/net directory with the others and modprobe seemed to pick it up ok from there.

Hope it works for you too

---

### Post by wanted-66 on 2008-12-07
I found some other instructions at [http://michaelminn.com/linux/eeepc/](http://michaelminn.com/linux/eeepc/) which seemed to work. Be warned- the link here for the download is for wireless only. I installed this OK but of course didn't work for wired, uninstalled and installed wired driver. After I'd successfully connected, Ubuntu updated and I had to install all over again!
Got a lot easier after a few times!
Thanks

---

