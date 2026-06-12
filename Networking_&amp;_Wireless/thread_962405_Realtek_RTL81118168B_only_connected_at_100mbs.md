---
title: "Realtek RTL8111/8168B only connected at 100mb/s"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by cr0wn3r on 2008-10-29
Ive had a good go myself at getting this to connect at 1000 but I'm not having any luck. My own knowledge is a bit too limited to improvise on other fixes I've read here.

The card connects to my switch with no problems, no deliberate driver installs, just out of the box. But at 100mb, not 1000mb.

I have another PC here which connects at 1000 and I'm using the same cat6 cable to test both so I don't think its the switch or cable at fault.

Im using 8.04 hardy, 2.6.24-21-generic

I made a hardware html report, which says:

```
id:	
network
description: 	Ethernet interface
product: 	RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: 	Realtek Semiconductor Co., Ltd.
physical id: 	
0
bus info: 	
pci@0000:03:00.0
logical name: 	
eth0
version: 	02
serial: 	
size: 	100MB/s
capacity: 	1GB/s
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	r8169
driverversion	=	2.2LK
duplex	=	full
ip	=	192.168.0.125
latency	=	0
link	=	yes
module	=	r8169
multicast	=	yes
port	=	twisted pair
speed	=	100MB/s
```

My switch (Netgear GS608 ) confirms it's at 100Mb as the activity light flashes orange. It goes green for gigabit connections.

I found this on the forum and so tried to follow the instructions to sort the correct driver:

```
1 - Downloaded current driver from :
http://www.realtek.com.tw/downloads/...&GetDown=false
2 - Unpacked on the Desktop
3 - $ sudo mv r8168-8.009.00 /usr/src
4 - $ cd /usr/src/r8168-9.004.00
5 - $ sudo make clean modules
6 - $ sudo make install
7 - $ sudo depmod -a
8 - $ sudo insmod ./src/r8168.ko
9 - $ lsmod -a | grep 8186 #just to check it was there
10 - $ cd /etc/modprobe.d
11 - $ sudo touch blacklist-network
12 - $ vi blacklist-network # add "blacklist r8169" to the file
13 - $ sudo update-initramfs -u #to make the change permanent
14 - reboot
15 - ethtool -i eth0 #to see new driver assigned
``` 

But I get this on step#5, which doesnt seem right:

```
# /usr/src/r8168-8.009.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.009.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/usr/src/r8168-8.009.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.009.00/src'
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'. Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.009.00/src'
make: *** [modules] Error 2

```

This seems to give the right result though so maybe the above step is not required?

```
# /usr/src/r8168-8.009.00$ lsmod | grep r8169
r8169                  36868  0 

```

This is where I'm making assumptions because I don't really understand what I'm doing.

Apparently I need to make it use an r1000.ko driver, but where to get this from and how to use it I'm unsure.

lsmod | grep r1000 doesnt return anything.

I'd really appreciate some help.

Thanks.

---

### Post by cr0wn3r on 2008-10-30
Ive been plugging away at this today but havent made any headway.

Ive tried to make the r8169.ko driver but I get all sorts of issues when I try to make clean or make install.

I have all my headers and the paths in the Makefile all go to the right places. But I still get:

```
install: cannot stat `r8169.ko': No such file or directory
```

Can anyone help?

---

### Post by m1r0 on 2008-11-02
problems with cards not working on default install 8.04 x32 and x64:

Realtek: PCI RTL8139c and onboard RTL8111/8168B

any help is appriciated.

---

### Post by evilpar on 2008-11-06
This got latest realtek RTL8111x / 8168x driver to install in ubuntu 8.10:

I've been having the same problems with 8.10 and the new realtek driver r8168-8.009.00 but did get it to install:

The error when do you sudo make clean modules:
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory

If you copy the driver files from r8168-x.xxx.xx into the location /src/ on your hard drive then this step will succeed and you will get the r8168.ko driver file and a bunch of other files. Somewhere after you try to build the driver (no idea where) the os looks for the Makefile in the /src/ directory on the root of the hard drive instead of in the r8168-x.xxx.xx/src/ directory.

Next with sudo make install:

Before you run make install, copy the newly created files from /src/ to r8168-x.xxx.xx/src/ or you will get the error: install: cannot stat `r8168.ko': No such file or directory

Next try sudo depmod -a

Next try  sudo insmod ./src/r8168.ko :
if you get an error that looks like: insmod: error inserting './src/r8168.ko': -1 File exists then you need to try sudo rmmod r8168 and then run the insmod again.

Everything worked at this point, but you just need to watch the errors and do what they imply. If it can't find a file, then you maybe in the wrong directory or the file needs to be where the install program is looking for it etc.

If you still see ubuntu running the r8169 driver then go to your version of:
/lib/modules/2.6.27-7-generic/kernel/drivers/net
find the r8169.ko file and rename it r8169.ko.old

FYI:
I'm not a ubuntu expert, but I don't see any reason why this won't work in 8.04 as well.

---

### Post by yellow99 on 2010-08-26
Don't know if this is still an issue for anyone (hehe, probably for all googlers that are reading my post at this very moment :-) ) but here's a solution.

Download the latest driver on Realtek's website:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

If you're unsure which kernel you are using, try ```
uname -r
```

After downloading, the README is pretty much telling you anything you need to know. Here's a copy of the text, in case you are having a hard time dealing with the .bz2 file.

> <Quick install with proper kernel settings>
        Unpack the tarball :
                # tar vjxf r8168-8.aaa.bb.tar.bz2

        Change to the directory:
                # cd r8168-8.aaa.bb

        If you are running the target kernel, then you should be able to do :

                # ./autorun.sh  (as root or with sudo)

        You can check whether the driver is loaded by using following commands.

                # lsmod | grep r8168
                # ifconfig -a

        If there is a device name, ethX, shown on the monitor, the linux 
        driver is loaded. Then, you can use the following command to activate 
        the ethX.

                # ifconfig ethX up

                ,where X=0,1,2,...


Enjoy!

/Fred

---

