---
title: "Bipac-7000 Adsl Modem"
date: 2004-10-26
forum: Networking &amp; Wireless
---

### Post by fargone on 2004-10-26
I just installed Ubuntu on a second hard drive dual booting with Win98SE.  I had plans to use an online tutorial to learn basic Linux but I cannot get my BIPAC-7000 ADSL Modem to work.  I did have problems at installation with some packages but was fairly clueless as to what was required of me to repair them and, since the system does boot, I figured I could fix them after I get online.  There are Linux drivers available for the BIPAC-7000 from [www.billion.com.tw](www.billion.com.tw) but I couldn't get the file open (downloaded while in Windows) so no help there.  Pain in the deriere switching between Win and Ubuntu so I'd really like to use this site directly in Linux.  I'm a real newbie; I don't even know where to find the command line let alone what to do when I get there.

---

### Post by fargone on 2004-10-27
I've gotten as far as step 1 but cannot figure out what to do with sudo to move on to step 2.   How do you get to the # prompt to change directory?  This modem was also not detected by Win98 but I managed to get it running there in about 15 minutes.   Two days and still no modem in Ubuntu.

[I]This document describes the steps of installing the E2 or Hasbani on the Linux.
Driver Version 062802_REL1.7

First, uncompressing the packaged: USBNET_E2_LINUX_062802_REL1.7.tar.gz
	#tar zxvpf USBNET_E2_LINUX_062802_REL1.7.tar.gz
A directory named e2 will be created under current directory.

Second, Changing directory to the "e2" directory.
	#cd e2

Third, compiling the source code.
	#make

At last, copy the firmware file "CnxE2Fw.bin" to directory "/etc".
	#cp CnxE2Fw.bin /etc/CnxE2Fw.bin


Now, you can install the driver by the command below under current directory:
	#insmod e2.o

If you would like to installing driver anywhere else, Please copy the e2.o to 
the directory: /lib/modules/2.4.xx-xxx/kernel/drivers/usb first.

If the network doesn't up automatically, you must run the following commands to activate the net adapter.
	#ifconfig hsb0 up
	#dhcpcd -n hsb0[/I]

---

### Post by FLeiXiuS on 2004-10-28
This sounds like a PPPoe problem, many others had some of the same concerns. 

Open up a terminal and type
```

pppoeconf

```

---

### Post by fargone on 2004-10-28
Tried #pppoeconf which stated that no ethernet card was detected and I should run #modconf.   #modconf came back with "No command......."

Next I tried the installation instructions for my modem shown in my earlier message.

I clicked on the .zip driver package and an unzipping utility appeared on my screen.  Several mouse clicks later I was in the e2 folder as mentioned in the instruction which was showns as  /./e2   *(Does this mean its in the root directory?)*

I then went in the terminal and typed #cd e2 per the instructions and got:
bash: cd: e2     No such file or directory

UTCWAP

---

### Post by FLeiXiuS on 2004-10-28
Maybe your nic card hasn't been installed on linux.  Try 
```

lspci

``` 

Search for your NIC card and if you find it there then you should be alright.  If not, then lets start there then work our way to PPPoe

---

### Post by fargone on 2004-10-28
Listed:
[I]Host Bridge
PCI Bridge
ISA Bridge
IDE Interface
USB Controller
USB Controller
Host Bridge
Multimedia Audio Controller
Communication Controller (This is a Rockwell 56K modem I no longer use)
VGA Compatible Controller[/I]

I don't see anything about an NIC Card

---

### Post by FLeiXiuS on 2004-10-29
Then begin by googling for your NIC cards drivers for linux.

---

### Post by fargone on 2004-10-30
Thanks for all your help but I'm going to give up on Linux for now.  This is just way over my head.  My wife has handed down a royal decree allowing me to buy a new computer so I'll be sure to purchase as much hardware as possible that is Linux compatible and try again.   I was hoping to pass this one on to my daughter with Linux installed and running to wean her off of Windows but things don't always work out.  Thanks again for your help but it was just a case of trying to teach Calculus to a first grader.

---

### Post by Deksan on 2005-07-14
Hi,
I managed to get it works so I ll give you some hints on how to do it, it worked for me on ubuntu 5.04 :

1) Get the kernel headers :
apt-cache install build-essential linux-headers-2.6.10-5-386
cd /usr/src/linux-headers-`uname -r`
make oldconfig

2) Compile kernel module for the modem
cd /root
Download from [http://accessrunner.sourceforge.net/](http://accessrunner.sourceforge.net/) the last file :
usbatm-20050216.tar.bz2
Decompress it:
bzip2 -d usbatm-20050216.tar.bz2
tar -xvf usbatm-20050216.tar


We change the configuration of the kernel :
cd /usr/src/linux-headers-`uname -r`
vi .config

Sarch for USB
add
CONFIG_USB_CXACRU=m
CONFIG_USB_ATM=m

Compile the modules
cd /root/drivers/usb/atm
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules_install

You ll have a /usr/src/linux-2.6.10/extras with the two modules 

3) Extract firmware from windows drivers
Download the files  Makefile and cxacru-fw.c from
[http://cvs.sourceforge.net/viewcvs.py/accessrunner/utils/](http://cvs.sourceforge.net/viewcvs.py/accessrunner/utils/)
compile them with the command make
you should get a binary file cxacru-fw
Execute it to get the firmware from the windows drivers :
root@ubuntu:~/drivers # ./cxacru-fw /media/D/WINDOWS/system32/drivers/CnxEtU.sys cxacru-firmware.bin
found firmware in `/media/D/WINDOWS/system32/drivers/CnxEtU.sys' at offset 0x41c0
root@ubuntu:~/drivers # ls -al  cxacru-firmware.bin
-rw-r--r--  1 root root 624192 2005-07-15 01:26 cxacru-firmware.bin
Copy the firmware in the hotplug folder :
cp cxacru-firmware.bin /lib/hotplug/firmware/


Now load the module in the kernel :
insmod /lib/modules/2.6.10-5-386/kernel/drivers/base/firmware_class.ko
insmod /lib/modules/2.6.10/extra/usbatm.ko
insmod /lib/modules/2.6.10/extra/cxacru.ko

You should see :
Jul 15 00:20:21 ubuntu kernel: usbcore: registered new driver cxacru
Jul 15 00:20:36 ubuntu kernel: cxacru 2-1:1.0: ADSL line: attemtping to activate
Jul 15 00:20:41 ubuntu kernel: cxacru 2-1:1.0: ADSL line: channel analysis
Jul 15 00:20:46 ubuntu kernel: cxacru 2-1:1.0: ADSL line: up (2560 Kib/s down | 512 Kib/s up)

5) Establish connection
Now it s up to what connection you need PPPoE or PPPoA

if PPPoA , download from [http://accessrunner.sourceforge.net/debian-scripts/](http://accessrunner.sourceforge.net/debian-scripts/)
the peers-pppoa and put it in /etc/ppp/peers, edit that file especially the user
and the VPC/VCI peers.
Add also your login password in the /etc/ppp/pap-secrets /etc/ppp/chap-secrets
in the form 
login  *  password  *

insmod /lib/modules/2.6.10-5-386/kernel/net/atm/pppoatm.ko
pppd call peers-pppoa



if PPPoE
Install
apt-get install libatm1

also you ll need to download 2 package from the ubuntu 

br2684ctl_20040226-1_i386.deb
atm-tools_2.4.1-16_i386.deb ( I m not sure if that one needed)

then install them with the command dpkg -i xxxxxfilexxxxx.deb

download from [http://accessrunner.sourceforge.net/debian-scripts/](http://accessrunner.sourceforge.net/debian-scripts/)
the peers-pppoe and put it in /etc/ppp/peers, edit that file especially the user.
Add also your login password in the /etc/ppp/pap-secrets /etc/ppp/chap-secrets
in the form 
login  *  password  *

after that modify the /etc/network/interfaces and add :
auto nas0
iface nas0 inet static
        address 192.0.2.1
        netmask 255.255.255.0
        broadcast 192.0.2.255
        gateway 192.0.2.254
        pre-up br2684ctl -b -c 0 -a 0.0.100
        post-down kill $(cat /var/run/$IFACE.pid)
(the 0.0.100 is the form itf.vpi.vci you should set vpi/vci accordingly to what you have see your ISP for this infos.)

Restart the network to get the nas0 match the atm interface
insmod /lib/modules/2.6.10-5-386/kernel/net/atm/br2684.ko
/etc/init.d/networking restart

And finally connect
pppd call  peers-pppoe



I m sorry it s a bit hard and maybe not well organized but it should give you a better
idea of what you need to do.

---

### Post by TiMBuS on 2005-08-08
I know this thread is a little old, but..
Flexius... its a USB modem.. not a NIC card.

More importantly, deksan.

I did exactly what you said, but nothing. Now when it loads linux, it fails to load network interfaces :(

The problem is that after insmod-ing nopthing happens. I have the build modules, but nothing starts. They show up if i use lsmod, but as far as I know, the driver doesnt even start, and doesnt try to connect :(
Are you missing a step? Is there another module or driver I need? I tried installing the red-hat 9.0 driver as well, but it seems to do nothing but sit there and mock me. Ideas?

---

### Post by TiMBuS on 2005-08-08
Dont worry, I'm online in linux now!
happydance.

Just seemed that pppd was being a jerk. Now it just.. works. Weird, but I'm not complaining.

Thanks man!

---

### Post by TiMBuS on 2005-08-09
annnnd its broken again.. uber sad face.

it connected ONCE - now its broken again.. modem lights up so the firmware is going.. I use pppd and call it up, but nothing getd through. pimg google.com returns cant be found, and i cant restart the network even after killall pppd.. this bites.

---

### Post by wpora on 2005-11-26
I follow  Deksan's  instructions but one exception.   I don't include default gateway for nas0 interface so that ppp is the default gateway after ppp is called. 

You can find VPI/VCI by pressing CTRL+P when the BIPAC configuration window is active in Microsoft Window environment.

  
[QUOTE=Deksan]Hi,
I managed to get it works so I ll give you some hints on how to do it, it worked for me on ubuntu 5.04 :

1) Get the kernel headers :
apt-cache install build-essential linux-headers-2.6.10-5-386
cd /usr/src/linux-headers-`uname -r`
make oldconfig

2) Compile kernel module for the modem
cd /root
Download from [http://accessrunner.sourceforge.net/](http://accessrunner.sourceforge.net/) the last file :
usbatm-20050216.tar.bz2
Decompress it:
bzip2 -d usbatm-20050216.tar.bz2
tar -xvf usbatm-20050216.tar


We change the configuration of the kernel :
cd /usr/src/linux-headers-`uname -r`
vi .config

Sarch for USB
add
CONFIG_USB_CXACRU=m
CONFIG_USB_ATM=m

Compile the modules
cd /root/drivers/usb/atm
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=$PWD modules_install

You ll have a /usr/src/linux-2.6.10/extras with the two modules 

3) Extract firmware from windows drivers
Download the files  Makefile and cxacru-fw.c from
[http://cvs.sourceforge.net/viewcvs.py/accessrunner/utils/](http://cvs.sourceforge.net/viewcvs.py/accessrunner/utils/)
compile them with the command make
you should get a binary file cxacru-fw
Execute it to get the firmware from the windows drivers :
root@ubuntu:~/drivers # ./cxacru-fw /media/D/WINDOWS/system32/drivers/CnxEtU.sys cxacru-firmware.bin
found firmware in `/media/D/WINDOWS/system32/drivers/CnxEtU.sys' at offset 0x41c0
root@ubuntu:~/drivers # ls -al  cxacru-firmware.bin
-rw-r--r--  1 root root 624192 2005-07-15 01:26 cxacru-firmware.bin
Copy the firmware in the hotplug folder :
cp cxacru-firmware.bin /lib/hotplug/firmware/


Now load the module in the kernel :
insmod /lib/modules/2.6.10-5-386/kernel/drivers/base/firmware_class.ko
insmod /lib/modules/2.6.10/extra/usbatm.ko
insmod /lib/modules/2.6.10/extra/cxacru.ko

You should see :
Jul 15 00:20:21 ubuntu kernel: usbcore: registered new driver cxacru
Jul 15 00:20:36 ubuntu kernel: cxacru 2-1:1.0: ADSL line: attemtping to activate
Jul 15 00:20:41 ubuntu kernel: cxacru 2-1:1.0: ADSL line: channel analysis
Jul 15 00:20:46 ubuntu kernel: cxacru 2-1:1.0: ADSL line: up (2560 Kib/s down | 512 Kib/s up)

5) Establish connection
Now it s up to what connection you need PPPoE or PPPoA

if PPPoA , download from [http://accessrunner.sourceforge.net/debian-scripts/](http://accessrunner.sourceforge.net/debian-scripts/)
the peers-pppoa and put it in /etc/ppp/peers, edit that file especially the user
and the VPC/VCI peers.
Add also your login password in the /etc/ppp/pap-secrets /etc/ppp/chap-secrets
in the form 
login  *  password  *

insmod /lib/modules/2.6.10-5-386/kernel/net/atm/pppoatm.ko
pppd call peers-pppoa



if PPPoE
Install
apt-get install libatm1

also you ll need to download 2 package from the ubuntu 

br2684ctl_20040226-1_i386.deb
atm-tools_2.4.1-16_i386.deb ( I m not sure if that one needed)

then install them with the command dpkg -i xxxxxfilexxxxx.deb

download from [http://accessrunner.sourceforge.net/debian-scripts/](http://accessrunner.sourceforge.net/debian-scripts/)
the peers-pppoe and put it in /etc/ppp/peers, edit that file especially the user.
Add also your login password in the /etc/ppp/pap-secrets /etc/ppp/chap-secrets
in the form 
login  *  password  *

after that modify the /etc/network/interfaces and add :
auto nas0
iface nas0 inet static
        address 192.0.2.1
        netmask 255.255.255.0
        broadcast 192.0.2.255
0x0x        gateway 192.0.2.254
        pre-up br2684ctl -b -c 0 -a 0.0.100
        post-down kill $(cat /var/run/$IFACE.pid)
(the 0.0.100 is the form itf.vpi.vci you should set vpi/vci accordingly to what you have see your ISP for this infos.)

Restart the network to get the nas0 match the atm interface
insmod /lib/modules/2.6.10-5-386/kernel/net/atm/br2684.ko
/etc/init.d/networking restart

And finally connect
pppd call  peers-pppoe



I m sorry it s a bit hard and maybe not well organized but it should give you a better
idea of what you need to do.[/QUOTE]

---

### Post by llandoverysurfer on 2006-08-17
Extract firmware from windows drivers
Download the files Makefile and cxacru-fw.c from
[http://cvs.sourceforge.net/viewcvs.p...srunner/utils/](http://cvs.sourceforge.net/viewcvs.p...srunner/utils/)
 the above link doesnt seem to be working :(  can anyone help??

---

### Post by Deksan on 2007-05-03
Sorry guys was out for a while :( Back to ubuntu 7.04 but not using the modem anymore (bought a router). You should find the needed files there : [http://sourceforge.net/project/showfiles.php?group_id=47406](http://sourceforge.net/project/showfiles.php?group_id=47406)

---

### Post by Meeh on 2007-05-29
Try this website [http://www.siamgeek.com/knowledge/getting-online-in-ubuntu-with-bipac-7000.html]("http://www.siamgeek.com/knowledge/getting-online-in-ubuntu-with-bipac-7000.html"). They have a solution. I don't if it works on other versions... but it works on my Feisty Fawn :D

---

### Post by PachinCam on 2007-08-29
Try this - [http://pachinee.homeunix.org](http://pachinee.homeunix.org)

---

