---
title: "No Wireless - tried many things"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by rhardie on 2008-09-24
I have a Toshiba P15 laptop with built in wireless.  I loaded the ndiswrapper driver installation tool but I need a driver to install.  Not sure how to do this.

My first attempt to install wireless was to install the 8.04 CDROM and download drivers from there but then I was getting some error to install CD into cdrom0 when I already had a CD inserted.

Next, I researched and found the ndiswrapper driver installation too ... now I just need the driver wrapper for the chip set (at least I "believe" that is my next step.)

Here is my set up:

larisa@larisa-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:94:a1:7b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.0.112 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

---

### Post by rhardie on 2008-09-24
I "do" have the Windows CD from Toshiba with the wireless software driver.  Is there a way to put a wrapper around 'that' driver and use it in Linux?

Just a thought.  :-)

---

### Post by Cresho on 2008-09-24
okay....do this first and ill check this message in about 5 minutes.

open add remove, search windows drivers...install windows wiereless drivers.

after install, go to system-administration->windows wireless drivers

install new driver.  now look in your cd and hope your wireless drivers are not as a exe.  you are looking for .inf or ..once you locate windows xp drivers, say open and it will install your windows drivers on linux.  maybee your cd has linux drivers?  explain.

when you successfully install the drivers, ill check back and see what you posted every 10 minutes my email check messages.

---

### Post by rhardie on 2008-09-24
Sources set to CDROM, 3rd party and all other repositories.

Went to Add/Remove and did search on "Windows Drivers".  Answer returned was ndiswrapper installation tool (already loaded).

No actual driver.

The original Toshiba (windows) CD has an Atheros driver as an .EXE file

---

### Post by Cresho on 2008-09-24
atheros drivers are supported in madwifi

ill post in 5 minutes...looking for links and install instructions.  actually it will take less than that

---

### Post by Cresho on 2008-09-24
1. download [http://madwifi.org/](http://madwifi.org/) madwifi v0.9.4

2.  right click and extract here

3.  cd ~/Desktop/madwifi-0.9.4

```

cd ~/Desktop/madwifi-0.9.4
make clean
make
sudo make install
reboot
```

if it complains about a previous install, hit r and after done, reboot.  let me know when you get to this phase.

Im guessing you do not need development packages but if you do get an error, let me know and ill repost my one hit wonder.

---

### Post by rhardie on 2008-09-24
There seems to be some residual or "junk" from a previous attempt to install the madwifi.

What should I do to clear out the junk and re-do your installation instructions?

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
^[[A^[[A

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.24-19-386/net || mkdir -p //lib/modules/2.6.24-19-386/net
install ath_pci.ko //lib/modules/2.6.24-19-386/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1
larisa@larisa-laptop:~/Desktop/madwifi-0.9.4$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.24-19-386 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.24-19-386/net || mkdir -p //lib/modules/2.6.24-19-386/net
install ath_pci.ko //lib/modules/2.6.24-19-386/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1
larisa@larisa-laptop:~/Desktop/madwifi-0.9.4$ cd ~/Desktop/madwifi-0.9.4
larisa@larisa-laptop:~/Desktop/madwifi-0.9.4$ make clean
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_hal'
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/amrr'
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/onoe'
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c

---

### Post by Cresho on 2008-09-24
just repeat the process.  it asks you what you want to do and you hit r.  enter and it is installed.  post the output here just incase.  I wanna see it.

---

### Post by rhardie on 2008-09-24
larisa@larisa-laptop:~$ cd ~/Desktop/madwifi-0.9.4
larisa@larisa-laptop:~/Desktop/madwifi-0.9.4$ make clean
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath'
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_hal'
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/amrr'
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/onoe'
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/sample'
make[2]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate/minstrel'
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/ath_rate'
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/net80211'
make -C ./tools  clean
make[1]: Entering directory `/home/larisa/Desktop/madwifi-0.9.4/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info core a.out
make[1]: Leaving directory `/home/larisa/Desktop/madwifi-0.9.4/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
larisa@larisa-laptop:~/Desktop/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-386/build SUBDIRS=/home/larisa/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-386'
  CC [M]  /home/larisa/Desktop/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/larisa/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/larisa/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/larisa/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/larisa/Desktop/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/larisa/Desktop/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/larisa/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-386'
make: *** [modules] Error 2
larisa@larisa-laptop:~/Desktop/madwifi-0.9.4$

---

### Post by Cresho on 2008-09-24
okay, lets do this.

fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.

then in terminal you do

```
sudo apt-get update
sudo apt-get upgrade
```

then

```
sudo aptitude remove automake1.4
```

then

```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev cdbs libgnet-dev libxine-dev libxml2-dev libxtst-dev libgnet2.0-0 libgnet-dev
```

copy and paste that in terminal  and hit enter.  no need to type it. :lolflag:

then repeat the wifi instructions. post output and reboot.  ill show you how to use it after.

---

### Post by rhardie on 2008-09-24
OK.  Done.

Now, how to use.  :-)

---

### Post by Cresho on 2008-09-24
in the upper right hand corner, you will see your network adaptor.  it is the same icon as your wired network.  if you right click on it, you have the option to turn on or off the wifi.  if you left click on it, after you enabled your wifi with the right click, you can search for other wifi areas.  it should list them.  I hope you rebooted.

---

### Post by rhardie on 2008-09-24
I went to upper right corner and opened network connection.  Networks is checked and then go to "Edit Wireless Networks".

Does NOT detect any networks in the area.

wireless on/off switch is on but indicator light for wireless Rx/Tx radio is dark indicating no radio enabled.

---

### Post by Cresho on 2008-09-24
when you right click, you have enabled network with a checkmark?  that is fine.  You should see a checkmark for wireless.  If thereis none, then it is not supported.  you will need to hunt down for the drivers of winxp and install the drivers through the windows wireless drivers.  reboot and then try again and see if you have a checkmark to enable the wireless drivers.

post the model of your wifi here.  I can probably find a module for your kernel. or what ever they call it.  This isnt difficult.  the difficult part is finding the right one for your card...if it's supported though.

---

### Post by Cresho on 2008-09-24
doees your laptop have a wifi power button?

---

### Post by rhardie on 2008-09-24
Yes.  There is a sliding switch on the side of the laptop for on/off and an orange LED indicator when the WIFI is broadcasting.

I will hunt down a driver and so far, that has been a challenge.  I have been looking for a driver for the Realtek chipset for Ethernet then it appears I have an Atheros "something or another" for WIFI.

Not certain exactly which of the information to be giving you.  Do they make the WIFI a component of the Ethernet when building laptops?

The closest thing I've found to a Windows Driver is on the Toshiba CD that came with the computer.  I have downloaded the driver but it is an .exe file format.

IF... I understand the concept of "wrappers", then the driver would be "wrapped" inside a Linux module to translate, sort of, so that it would work on my Linux machine.

Not sure if there is a way to put a wrapper on my OEM driver or not.

Thanks for your assistance so far; you've been a big help.

---

### Post by Cresho on 2008-09-24
well, if you have a windows machine, copy the exe file from the cd and place it on your linux and windows  desktop and do this.

you can either rename exe to zip and see if you can extract it this way, ( i have quite a few good successes this way) or



or in linux, try
use command to extract exe content.

[http://upx.sourceforge.net/#download](http://upx.sourceforge.net/#download)
upx.exe -d <exe>

download the upx-3.03-i386_linux.tar.bz2 and right click and extract here.  (i am assuming you are using the 32bit ubuntu)

copy the exe into the upx-3.03-i386_linux folder.  no need to install anything.

cd ~/Desktop/upx-3.03-i386_linux
./upx -d GSCSetup.exe                   change the name of "GSCSetup.exe"  to the exe you are going to use.

in windows use
if this doesnt work, use winrar to open it.  there are many ways of opening the exe.

---

### Post by rhardie on 2008-09-24
Hmmm.  You are full of all kinds of tricks.  You should be working at the FED!

I'll give that a shot.

Thanks.  I'll post my results.

---

### Post by rhardie on 2008-09-24
I converted the .exe file to a .zip file (to duplicate your previous successes) and was able to peek inside.

So far, I have attempted to load a file called net5211.inf (as this file type was suggested) but it comes up as invalid driver.

---

### Post by Cresho on 2008-09-24
did you look in all the folders for .inf?  was that the only one?

give me the output for each of these lines

ndiswrapper -l


give me the device id

lspci -nn

---

### Post by rhardie on 2008-09-24
larisa@larisa-laptop:~$ ndiswrapper -l
net5211 : invalid driver!
larisa@larisa-laptop:~$ 

***********************************

larisa@larisa-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX Go5100] [10de:032d] (rev a1)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)
02:06.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 05)
larisa@larisa-laptop:~$

---

### Post by rhardie on 2008-09-24
Contents of the driver b21425e.ZIP file is:
ar5211.sys
ar52119x.sys
net5211.cat
net5211.inf
Setup.exe
tregapi.dll

I attempted to install the net5211.inf and received the error message that it is not a valid driver.

---

### Post by Cresho on 2008-09-24
> **rhardie said:**
> larisa@larisa-laptop:~$ ndiswrapper -l
net5211 : invalid driver!
larisa@larisa-laptop:~$ 

***********************************

larisa@larisa-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX Go5100] [10de:032d] (rev a1)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)
02:06.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 05)
larisa@larisa-laptop:~$

remove the driver from windows wireless drivers and try it again.  I want to see if the kernel sees your wifi by itself.  make sure the power on wifi is on

---

### Post by rhardie on 2008-09-24
Removed Windows driver from WIFI GUI.

larisa@larisa-laptop:~$ ndiswrapper -l
larisa@larisa-laptop:~$ 

**********************************************************

larisa@larisa-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller [8086:24d6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX Go5100] [10de:032d] (rev a1)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)
02:06.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 05)
larisa@larisa-laptop:~$ clear

---

### Post by Cresho on 2008-09-25
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

i cant find your wifi.  this is your ethernet though

i hope someone can look into this but if not, ill probably spend a little time looking through the devices.  It could be an intel based wifi...not sure though.  I dont see any atheros.  I am certain that your wifi is off!

you need to turn it on!!!!

NOW I KNOW WHAT IS GOING ON!!!!  YOUR OPERATING SYSTEM NEEDS TO EITHER TURN IT ON THROUGH SOFTWARE OR YOU NEED TO PHYSICALLY TURN ON YOUR WIFI WITH THE POWER BUTTON.  IT IS NOT IN THE OUTPUT LIST YOU POSTED!  ITS OFF!

OR maybee the kernel blacklisted it.

---

### Post by Cresho on 2008-09-25
I did a little bit of reading.
[http://www.linux-on-laptops.com/hosted/toshibaP150.html](http://www.linux-on-laptops.com/hosted/toshibaP150.html)

I am now wondering if your ath is blacklisted...maybee.

---

### Post by rhardie on 2008-09-25
I'm going to give this issue only a little bit of time before I decide I've put too much time and effort.  I've been working on this ONE issue for about a week now.  I'm going to hope that 8.10 does WIFI automatically as the v 7.10 did - that was beautiful!

Got a question:  Are you a 12 year old super geek or when God said, "Let there be light", you were there to flip the switch?  A teen ager wouldn't have hung in there this long and a 50 year old would certainly have the patience.

That's a lot of arcane knowledge.  I'm just curious 'cause I have a friend who started college at age 12 and now at age 25 (and an IQ of 187) can programs multi-thousand core linux super computers - and makes me find this stuff out on my own.  I may have to call him on this and let him "command line" it.
  ;-)

I'll check out your latest ideas as that will teach me something else that I know will be important in some aspect of Linux Life.  This already has and a very much appreciate your ideas and consistently hanging in there on this issue.

OK, back on my head.

---

### Post by rhardie on 2008-09-25
By the way:

Guy dies and goes to Hell.  Devil there to meet him with evil, sly look on his face.  Tell poor soul that he'll spend all eternity down there but not to worry 'cause he has three choices.  (Sounds like our Federal Reserve and Congress right about now)

Guy gets three doors; first is man burning and in perpetual agony.  Man slams door in horror and says I couldn't do that.  Devil gives him second door; man sees snakes biting woman who screams in pain and fear.  Man slams door as snakes scare him.

Devil smiles and puts arms around man (Our FED again?) and says not too worry, he has one last selection.

Man opens last door and is knocked over by the most awful smell of sewage.  But he notices people walking around waste-deep in it, smiling and sipping on cups of coffee in fine china.  The man, gaging, says I could do this, I guess.  Devil, with evil laugh, tosses the man in the sewage.  Man is met by nice, friendly guy named Joe, who offers some coffee and nice conversation.

15 minutes go by and the doors burst open to sound of whips cracking and angry commands.

"Coffee break is over!  BACK ON YOUR HEADS!"

(Hey, it's 4:30 AM, what can I say!)  :-)

---

### Post by rhardie on 2008-09-25
Re-read your earlier post - now that I've told a joke and am awake.

Your researched web link describes my wife's laptop exactly.

WIFI switch is definitely ON
Driver from Toshiba re-install CD definitely says Atheros
Don't see any mention of WIFI in the hardware list ( I had been wondering about this and didn't know if laptop Ethernet and WIFI were part of same hardware)

I'm going to give my young genius friend a call, take this to him and see what he does.  I'll let him verbally abuse me for a while for not figuring it out, take some notes on what he does and then I'll post them here - sans verbal abuse part.  ;-)

I really do appreciate your hanging in there consistently.  I've been learning by doing this kind of "brute force" approach.

Never loaded an OS before Linux and would have never learned what I have now on Windows.

---

### Post by Cresho on 2008-09-25
Cool!  thanks for the joke!  I just left my email while I was studying for a test, that's all.

at least we know your hardware does not go on

I have one more trick too!  sometimes you can tell Ubuntu to turn on your wifi.

I'm still thinking the wifi is off completely.  maybe broken>?  you never mentioned if it worked on windows at all either.

You should check to see if you can force bios to turn on wifi all the time.  This way, we can at least get the drivers and all working.  keep your cd, incase madwifi cannot use the wifi, maybee the windows drivers can.

anyway, I'm going back to studying.

---

### Post by rhardie on 2008-09-25
Reading up on Linux Wireless Networking at [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Debian_.2F_Ubuntu](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Debian_.2F_Ubuntu)  to see if I can learn about command line configuration and enabling of wireless.

About what is on the horizon:

[http://www.linuxfoundation.org/en/Linux_Weather_Forecast](http://www.linuxfoundation.org/en/Linux_Weather_Forecast)

Read "short term forcast":  Better support for Atheros in next Kernal release in October.

[http://www.linuxfoundation.org/en/Linux_Weather_Forecast/hardware](http://www.linuxfoundation.org/en/Linux_Weather_Forecast/hardware)

excerpt

  Atheros chipsets

The Atheros 5k chipsets found in many laptops and wireless routers has long lacked a free driver for Linux. OpenBSD has such a driver, but there have been legal concerns about its provenance which prevented it from being merged into the Linux kernel. Those concerns appear to have been resolved after a series of audits by the Software Freedom Law Center, clearing the path for the ath5k driver to be merged. As a result, ath5k was merged for 2.6.25.

Since then, Atheros has adopted a new, more open policy and hired some developers from the community. The company contributed the new "ath9k" driver for 802.11n hardware; that driver has been merged for 2.6.27. Atheros is quickly headed toward top-quality support in the mainline Linux kernel.

Forecast: As noted, ath5k is merged, and ath9k is coming. While the ath5k driver works well for some hardware (including your author's old Thinkpad X31 laptop), other users have not all been so lucky. These drivers can be expected to stabilize over the next development cycle or two.

About NDIS Wrappers (general FYI):

excerpt

 Using ndiswrapper

Windows uses the Network Driver Interface Specification (NDIS) as a standardized method for the operating system to communicate with the NIC driver software from various manufacturers. The Linux ndiswrapper software suite, available from ndiswrapper.sourceforge.net, allows you to run your Windows NIC card's drivers under Linux by creating a software wrapper around the Windows driver to trick it into thinking that it is communicating with Windows and not Linux. The compatibility range is therefore much wider and in cases where you need to recompile your kernel, the project's website has links to RPM packages of standard kernels with ndiswrapper support. Installation instructions on the project's web site are reasonably clear and a proficient Linux user should be able to get their NIC card working within an hour or two on their first try.

ndiswrapper has some limitations too. It only works on hardware architectures supported by Windows, the very useful iwspy command (discussed later) isn't supported and the wrappers add a layer of software complexity that would not exist normally. There is a commercial competitor to ndiswrapper called DriverLoader created by the Linuxant corporation which you may also want to consider.

---

### Post by Cresho on 2008-09-25
very nice reading.  Also, i been getting lots of requests for laptop setup so this is good for me...no more work! time to celebrate.

---

