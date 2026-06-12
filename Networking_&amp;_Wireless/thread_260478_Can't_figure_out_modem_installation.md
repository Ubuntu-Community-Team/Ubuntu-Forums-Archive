---
title: "Can't figure out modem installation"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Cryhavoc on 2006-09-18
Hey, I've recently installed Kubuntu Dapper with no problems (and dual booting as well, easy peasy), but I can't for the life of me figure out how to install my modem. 

Now, the thing is, the modem comes with some "linux drivers", but I don't know how to compile them or anything.

I'll put the readme file on here as well. Any help would be appreciated! I want to be able to use kubuntu for my everyday computing, but I can't do that without the internet, and for the moment I'm stuck on 56k, so this is pretty important for me.

Thanks a ton for any help!

```
ReadMe file for the
Intel® 536EP V.92 chipset Linux driver

contents:
1.  License
2.  Release Notes
3.  Installation
4.  File Descriptions
5.  International Users
6.  Beta Tester appreciation
7.  Security issues
8.  Compilation issues
    a. Instructions for Debian Users
    b. Kernel Source
9.  What is the Hamregistry?
10. what's v92 and v44?
11. The Hamregistry tool (for persistance)
12. Known Bugs/Issues
13. Comments, ideas, problems, fixes

-------------------------------------------------------------------------------
1. LICENSE

IMPORTANT - read the file "LICENSE.txt" for the INTEL SOFTWARE LICENSE 
AGREEMENT BEFORE COPYING, INSTALLING OR USING.


also note:
The serial driver open source code located in the directory "serialdrv" 
is work covered under the GNU GENERAL PUBLIC LICENSE (GPL).
The "serialdrv" directory has the GPL in the file "GPL.txt".

-------------------------------------------------------------------------------
2. Release Notes 

      This release supports 2.4.x kernels.

      This release is not compatible with kernels prior to 2.4.

      The 536EP corecode binary was compiled with gcc version 2.96

      v92 support added:  modem on hold AT command set,
      PCM upstream, v44, and quick connect are implemented.			 

      Linux Compatability tests are performed on the latest or previous 
      versions of the following distributions: Mandrake, RedHat, and SuSE

-------------------------------------------------------------------------------
3.  INSTALLATION

Prerequisites:
   1. root access
   2. bash shell to run install scripts
   3. a 536EP modem
   4. KERNEL SOURCE HEADERS FOR THE KERNEL YOU ARE RUNNING
      (found on your distribution's CD)

6 steps to install
   1. login as ROOT 
   2. extract the archive into a directory with "tar -zxvf <archivename>.tgz"
   3. cd into the directory it created.
   4. Type: make clean
   5. Type: make 536ep
   6. Type: make install



The installation script has been designed for the following distributions 
release versions

   mandrake-release
   SuSE-release
   redhat-release
   debian_version (including Corel)
   slackware-version
   conectiva-version
   bluepoint-release
   Unknown distributions install modules and utilities but
   will not install boot scripts!.

Please examine the 536ep-inst script if you have a different distribution.

The driver is split in two.  A serial driver and core driver.
The core driver must be loaded first since the serial driver depends on it.
The serial driver registers itself as character device 
   major number 240, minor number 1.
The serial driver takes one argument right now, which is a number to 
   override the default major number if you need to.


ATTENTION:  if the driver compiles but the script just wont work for you.
   Here are the bare minimum steps to get your modem to work.

   0.  log in as root.
   1.  insmod -f 536epcore.o
   2.  insmod -f 536ep.o
   2a. you can start "hamregistry" at this point if you wish.
   3.  rm /dev/536ep
   4.  mknod /dev/536ep c 240 1   (note "240" is the default, if it does not 
       work see what /proc/devices says 536ep's major number is)
   5.  ln -s /dev/536ep /dev/modem
   6.  start a comm application like minicom and use the modem.
   7.  see section 3 (International Users) for info on setting the correct 
       country settings.


-------------------------------------------------------------------------------
4.  FILE DESCRIPTIONS

536ep-inst installation script to install 536ep modules and supporting files


files copied to /lib/modules/(kernel-version)/misc
   536epcore.o	driver core code module
   536ep.o		pseudo serial driver for 536ep, depends on 536epcore.o

files copied to  /etc/rc.d/...  (path differes per distribution)
   536ep-boot		boot scrip to start and stop 536ep modules

files copied to /usr/sbin
   hamregistry	hamregistry is the "registry" like tool that the modem uses to 
   get and store persistant data such as county info and profile strings.

files copied to /etc
   hamregistry.bin	file that stores the initial persistant data for modem.


-------------------------------------------------------------------------------
5.  INTERNATIONAL USERS

hamregistry will store the last country setting you
set in the modem.

in minicom (or equivalent comm application)
the commmand to change country setting is "AT+GCI="
the command takes a t.35 country code in hexadecimal.
below is a list of currently supported t.35 country codes.
you can also put this "AT" command in the init string of
the comm application you are using.

if you are a CTR-21 country I think you should be able to 
choose a CTR-21 country on the list and be ok.  but 
that's no guarantee.
The same goes for countries that are "USA" compatable.
(this table also exist in the source file wwh_dflt.c that
ships with the 536epcore driver)

country     code     t.35 code
---------------------------
USA         1      B5
KOR         82     61 
ECU         593    35 
BOL         591    14
CHL         56     15 
COL         57     27
PAN         507    85 
PER         51     88 
SAU         966    98 
THA         66     A9 
VNM         84     BC 
SWE         46     A5 
DNK         45     31
FIN         358    3C
NOR         47     82 
ISL         354    52
IRL         353    57 
ISR         972    58
LIE         423    68 
ESP         34     A0
TUR         90     AE
DEU         49     42
AUT         43     0A
CHE         41     A6
CYP         357    2D
GRC         30     46
ITA         39     59
LUX         352    69
NLD         31     7B
GBR         44     B4 
BEL         32     0F
FRA         33     3D
PRT         351    8B
PAK         92     84
JPN         81     00
RUS         7      B8
AUS         61     09
MYS         60     6C
CHN         86     26
HKG         852    50
SGP         65     9C
NZL         64     7E
ARG         54     07
BRA         55     16
MEX         52     73
TWN         886    E3
IND         91     53
PHL         63     89
IDN         62     54
BHS         103    0B 
BRB         104    0E 
BMU         105    12 
GTM         502    49 
HTI         509    4E 
HND         504    4F 
JAM         1      5B 
NIC         505    7F 
PRY         595    87 
PRI         121    8C 
SUR         597    A3 
TTO         117    AC 
URY         598    B7 
VEN         58     BB 
ZWE         263    C4
GUY         592    4D
EST         372    E0
HUN         36     51
SVN         386    E2
ARE         971    B3 
SVK         421    2E
CAN         107    14 
CRI         506    1B 
DOM         110    33 
SLV         503    37 
GMB         220    41 
GIB         350    45 
POL         48     8A
EGY         20     36
CZE         420    2E
ZAF         27     9F
GUF         594    E1


-------------------------------------------------------------------------------
6.  Thanks to the following beta testers for their valuable input and 
    suggestions during the HaM 333 beta test between January 2 - 26, 2001

Dorian S. Araneda
Sean Walbran
Rob Clark
Marvin Stodolsky
Dominique Duval
Roman Krais 
Ulrich Guenther
Marcelino Viana Pinheiro
Thomas S. Iversen
Jospeh Teichman
Michel Bartolone (MED)
Ramon Gonzalez Montoiro
Ryoji Kawagishi
Torsten Vogel
"jandro"
Ian Carr-de Avelon
Helga Weindl
Ed Casas
Bernhard Hoelcker
Alexander "Sasha" Voytov
Albert Woo
Peter Hirschmann

and all of the helpful Linux HaM users
around the world and at www.linmodems.org 

-------------------------------------------------------------------------------
7. Security issues

the 536ep-inst and 536ep-boot file install the files and device nodes as 
root for the owner and group.  
this will cause problems for those who want to user the modem to dialout
using an account other than root.

In SuSE, "dialout" is the group used to install the files and device node.
This way, anyone belonging to the "dialout" group can use the modem to dialout.
(take a look at /etc/group)

I did not want the script to allow full access of the modem to everyone without
"root" knowing.

Edit the 536ep-boot and 536ep-inst scripts to fit your needs.

-------------------------------------------------------------------------------
8. Compile issues
   a. this driver will now compile with the this path:
   /lib/modules/<kernel version>/build/include
   the 2.4.4+ kernels says to copy the /boot/vmlinuz.version.h
   over to the kernel build path.  I have the makefile do this
   if this file exists.  You must install the kernel source
   code anyways.  It should be on your distribution's CD.


-------------------------------------------------------------------------------
9.  What is the Hamregistry?
   The hamregistery is an application that stores data for the 536ep driver onto
   the disk.  hamregistry stores information from the driver that needs to 
   persist from reboot to reboot such as you current country setting.
      The 536ep-inst install script and the 536ep-boot script start this utility 
      automatically for you.
   If this tool is not present when the driver gets used your profile, 
   quickconnect, and current country setting will not be saved but the driver
   should still work fine.	The only step that would need to be done is to
   make sure that the driver is set to the correct country with 
   at+gci= (see section 5)


-------------------------------------------------------------------------------
10. What's v92 and v44?  

   a. modem on hold: (ISP and your ISP dialer must also support this)
      This will allow you to pause your ppp connection to answer an incoming
      call. You will need call waiting, dialer, and ISP support for this to 
      work.  When you are done with the call you can resume your ppp connection
      without having to reconnect.  The AT command set for this feature exist
      in the driver.

   b, pcm upstream: 
      (ISP must also support this, as of version 4.32 I
       dont know any ISP's that do)
      This will allow faster upload speeds.
      to enable: at+pig=0
      to disable: at+pig=1

   c. quickconnect:
      Once you make a call to a v92 modem, your phoneline characteristics are
      stored.  Whenever you make a new v92 connection it will use this data 
      to make the call negotiation  quicker (approx 10 seconds).
      to enable: at+pqc=0  at+pss=0
      to disable: at+pss=2

   d. v44: (ISP must also support this)
      A better compression protocol than v42 which can give you better transfer
      speeds.

-------------------------------------------------------------------------------
11. The Hamregistry tool
   
   The hamregistry tool is used to provide persistance of settings across
   reboots.  The haminst and hamboot scripts automatically setup and start
   the hamregistry background task for the modem to use.
   The hamregistry tool has command line arguments for those who wish to 
   customize persistant settings.  To use these command lines
   you must first stop the driver with "bash hamboot stop".
   Once the driver has been stopped you may run hamregistry with one of these
   arguments to store into the /etc/hamregistry.bin persistance file:
   (supply value for items in < >)
      -mfg <Modem manufactures name>
      -mod <Modem model name>
      -hookflash  <0,1,2>
        hookflash method:  0=(default)without tone  1=with tone  2=reserved
      -v92rptopt  <0,1>
        control v92 reporting:   0=PCM upsteam only       1=(default) all v92
      -gpio_lpohd <0,1>
        Handset Hook detection:  0=not supported          1=(default)supported
      -currentcountry <t.35 code>

   This info is written to the /etc/hamregistry.bin file.
   If hamregistry.bin exists along with the installation files, haminst will
   copy it to /etc/hamregistry.bin when installing the modem.

-------------------------------------------------------------------------------
12. Known Bugs/Issues

   a. If you see this message
      "536ep:rs_open: DSP did not reset. try again or restart computer"
      and you KNOW you have a HaM modem installed
      Disable "PNP OS" in your bios.  There is a problem with the driver and 
      linux PNP.  After a time, Linux PNP will disable the card and the driver
      currently can not reenable itself.
   b. Be aware that the build replaces your 
      /lib/module/<kernver>//build/include/linux/version.h file with 
      /boot/vmlinuz.version.h
      (this is what Linus T. told me to do with a compiler error)
   c. There may be an incompatibility with DevFS. The 536ep device may be located
      in /dev/tts/536ep
      instead of /dev/536ep.  Be aware of this and link /dev/modem to the 536ep
      device that corresponds to your setup.
   e. Incase you are having problems making a ppp connection try using wvidal
      with this information below. execute the script and it will have wvdial
      make the ppp connection

   ------my script----------------------
   #! /bin/sh
   /usr/sbin/pppd -detach lock asyncmap 00000000 \
      defaultroute debug /dev/modem 57600 \
      ipparam ppp0 linkname ppp0 \
      noauth \
      connect "/usr/bin/wvdial --chat bellsouth"

   ------my /etc/wvdial.conf section ---
   [Dialer bellsouth]
   Modem = /dev/modem
   Baud = 57600
   Init1 = ATZ
   Inti2 = ATQ0 V1 E1 S0=0 &C1 &D2
   Dial Command = ATDT
   Phone = 6859500
   Username = myloginname
   Password = mysecretpassword
   #Ask Password = 1
   Stupid Mode = 0
   ------------------


-------------------------------------------------------------------------------
13. Comments, ideas, problems, fixes? please contact:

Linux Voice Band Modems (VBM) of Intel Residential Access Division (RAD)

vbm.linux@intel.com
http://developer.intel.com/design/modems/

To restrict email volume, please email only development related issues that are
needed to fix a bug or improve the driver. General questions on how to use the 
Linux OS will have to be forwarded.

Other resources and information on Linux controllerless modems can be found on 
these usefull sites

http://www.linmodems.org 
	and
http://linmodems.technion.ac.il
```

---

### Post by tatimmer on 2006-09-19
"tomsmodemtips" may help.

a hardware modem is much easier to setup on Linux, no drivers to install.

A soft-modem requires linux kernel headers and maybe the full kernel source code along with gcc.

there is an ubuntu help file on modems too.

---

### Post by zxee on 2006-09-19
Go here: [http://www.linmodems.org/](http://www.linmodems.org/) download the scanModem tool and read the howto. Check the link in my sig too.

---

### Post by Ptero-4 on 2006-09-24
The O.P modem have opensource drivers, hence it should be no problem, but it seems from the readme that the drivers won't work because they're designed for the earlier 2.4.x series kernel.

---

### Post by Matchless on 2006-09-24
Try this

**Modems supported by the Intel536EP driver for Ubuntu Dapper**
This page describes how to install the driver for the Intel 536EP internal modem on Ubuntu Dapper for i386 systems. Some of these are sold as Cnet modems and have Ambient chips on board. The process below is quick easy and works quite well. For other older ubuntu versions you will additionally require gcc 3.4 to also be installed. 
Install required Ubuntu packages
In a terminal type $uname-r, which should give you something like VERSION-XX-ARCH (where ARCH is your kernel flavor, e.g. 386, 686, 686-smp, k7 or k7-smp if you use Intel, powerpc for PPC ...). 
Ubuntu Dapper Drake 6.06 
You will need to install the build-essential and linux-headers-ARCH packages. They are normally on the install CD and can most easily be installed with Synaptic. If you need to download these due to later versions connect to another PC via the network card and download and install with Synaptic.
Download the drivers for the modem here: 
 [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng) 
Save the file, which is named Intel-536EP-4.71.tgz; on your Desktop. 
Compiling the driver
Right click on the file and select “Extract to here” This will create directory Intel-536 with the source on your Desktop. Open a terminal window and type: 
 cd Desktop/Intel-536
 make clean
	This should produce output looking like this: 
 Try `uname --help' for more information.
 cd coredrv; make clean
 make[1]: Entering directory `/home/<username>/Intel-536/coredrv'
 rm -f *.ko *.o *~ core
 make[1]: Leaving directory `/home/<username>/Intel-536/coredrv'
 rm -f *.o *.ko
 make 536
	This will result in many lines of output being printed to the terminal window; you can ignore most of 	them. The final lines should look like this: 
   CC      /home/<username>/Intel-536/coredrv/Intel536.mod.o
   LD [M]  /home/<username>/Intel-536/coredrv/Intel536.ko
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
 make[1]: Leaving directory `/home/<username>/Intel-536/coredrv'
	There should be an Intel536.ko file in the directory now; test this by typing
 ls -l Intel536.ko 
	The output should look like:
 -rw-r--r--  1 <username><username> 1070980 2006-05-06 21:02 Intel536.ko
Your dates and times will be different. If you are using Dapper, the file size (1070980) should be the same. 
Installing the driver
There are two steps to installing the driver. The first is to copy the Intel536.ko file created above to an appropriate directory, and the second is to cause the driver to be loaded at boot time. 
To install the Intel536.ko file, copy the file to the modules directory with this command: 
 sudo cp Intel536.ko /lib/modules/$(uname -r)/kernel/drivers/char
Make your system aware of this module with depmod: 
 sudo depmod -a
Finally, load the driver with the modprobe command: 
 sudo modprobe Intel536
This command should not print a response; if it prints something like this: 
 FATAL: Module Intel536 not found.
you have made an error; most likely you have copied the file to the wrong place. If you see a different error message, there may be an error in the module, or your modem, or you may not have a Intel 536-based modem. 
Loading the driver at boot time 
To load the module at boot time, we need to add a line "Intel536" to the file /etc/modules.
Go to the file /etc/modules and right click, actions, Edit in root and add the following line at the end:
Intel536
Using the modem
The name of your modem device is /dev/536ep0. You can now use sudo pppconfig to set up pon & poff. To use Kppp you will need to create a symlink be able to link the /dev/536ep0 to /dev/modem. Udev rewrites the /dev on each reboot and you thus have to create a new file with kwrite, kate or gedit in /etc/udev/rules.d/10-local.rules and put the following lines in it: 
 	# Intelmodem536ep
 KERNEL="536ep0", SYMLINK="modem"
Now reboot and you can use Kppp to query the modem as this is a quick check if all is well before dialling out. Configure KPP for your ISP connection. These Intel modems are found to be more stable and less finicky that the Smartlink types on Ubuntu.

---

### Post by Gig on 2006-09-26
Hi

I wonder if someone could help me please.

I am trying to install a modem but, I tried the full tutorial, even the one from the manufaturer and I get a message when I run kppp as follows:

kppp: cannot connect to X server

Can anyone recommend what I should do? 

Also, how do I know if the modem is installed - its a Smartlink MSP 2950. I want to login remotely to this server incase my adsl goes down or something and then duplicate this to some other servers I have. Can I use Mgetty to do this, as all my research has indicated?

Thanks in advance for your help.

Gig

---

