---
title: "Howto: Linksys WUSB54GSC With SpeedBooster"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by belorix on 2008-02-04
Physical Things you&#8217;ll need:
Linksys WUSB54GSC Wireless Adapter (duh)
Linksys WUSB54GSC Install CD
Ubuntu 7.10 Install CD (only if you need to install the first package in the prerequisite step so you can use the &#8216;make&#8217; command)

Files you&#8217;ll need:
WUSB54GSC.inf (i&#8217;ll include this soon)
usb8023.sys  :::::[Download Usb8023.sys file]("http://www.paulie-pages.com/wp-content/uploads/2008/01/usb8023.sys")
rndismp.sys:::::::[Downlaod Rndismp.sys file]("http://www.paulie-pages.com/wp-content/uploads/2008/01/rndismp.sys")
ndiswrapper package (link to homepage, not the actual files) (i used v1.51)[Ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/")

Prerequisites:

    * Make sure adapter is unplugged
    * First step is to ensure you have the required packages installed on your system (this step may require your Ubuntu CD)
      If you&#8217;ve never used the &#8216;make&#8217; command before, you&#8217;ll probably need to install the package. Type the following in the Terminal:
      sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)

Step 1 - Install NDISWrapper

    * Extract NDISWrapper
    * In a terminal window, navigate into the NDISWrapper folder
    * Type the following:
      sudo make uninstall
      make
      sudo make install
      sudo ndiswrapper -m

Step 2 - Getting the drivers

    * The files usb8023.sys & rndismp.sys should be able to be located in a Windows System directory (i had &#8216;em there) if you have a Windows installation. If not, I&#8217;ve linked to them above. I&#8217;ll continue linking to them as long as they don&#8217;t cause me to use up too much bandwidth. The only way to prevent this is if I find some way to monetarily support this site (hint hint). Supposedly they&#8217;re aso on the wireless adapter&#8217;s install CD.
    * The file WUSB54GSC.inf should be located on the Linksys Install CD. I will be uploading this file as soon as I get the chance.
    * Copy these 3 files into a new folder on your system

Step 3 - Installing the Drivers

    * In a Terminal window, navigate to the folder with the 3 drivers
    * Type the following:
      sudo ndiswrapper -i WUSB54GSC.inf
      sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsc/
      sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsc/

Step 4 - Ensuring the drivers & files are installed correctly

    * Type the following:
      ndiswrapper -l
    * Now, it should read something along the lines of:
      wusb54gsc : driver installed
    * Note: THIS DOESN&#8217;T MEAN THE ADAPTER WILL WORK YET. DO NOT PLUG IT IN YET

Step 5 - Getting it to work in Gutsy (or anything thats Fiesty or beyond)

    * In Fiesty (and thereafter), a safety feature was introduced that limited the power to the USB ports. This was too stop too much power from overpowering and blowing out the device. However, the limit is unfortunately too small for the WUSB54GSC adapter and therefore it doesn&#8217;t get enough power.
    * In a terminal window, type the following:
      sudo nano -w /etc/udev/rules.d/99-custom.rules
    * In the resulting window that opens, type the following on one line:
      BUS==&#8221;usb&#8221;, SYSFS{idProduct}==&#8221;0026&#8243;, SYSFS{idVendor}==&#8221;13b1&#8243;, RUN+=&#8221;/bin/sh -c &#8216;echo 1 > /sys/$devpath/device/bConfigurationValue&#8217;&#8221;
    * Hit Ctrl-O, enter, then Ctrl-X.

Next: Download the Madwifi Package (link to homepage, not the actual files)
[Download MadWifi]("http://sourceforge.net/project/showfiles.php?group_id=82936")

install madwifi by extracting the file to yor desktop. Next go into termianl and go to were the file you extracted and is located and type in make.
Next type sudo make install
This will install madwifi, and now just go into terminal and type:
Sudo modprobe ndiswrapper 
(for more help with installing madwifi please view the read me and install files, they are located within the madwifi package
Congratulations Your USB Adapter for wireless shoudl be running
[SIZE="5"][COLOR="Red"]WARNING:[/COLOR][/SIZE] this may not work for all. 
Im not sure if this follows the how to guide

---

### Post by dicecca112 on 2008-02-04
Hmm I have one of these adapters kicking around, might try this later this week

---

### Post by slats on 2008-02-05
i know this is probably going to sound stupid
but how do i navigate into the NDISWrapper-version in the terminal???

---

### Post by dicecca112 on 2008-02-05
depends where you extracted it.  If you ext it to the Desktop then its
 
cd /home/username/Desktop/ndiswrapper*
 
if you ext it to your home folder just
 
cd ndiswrapper*

---

### Post by slats on 2008-02-05
but what command do i use to access this folder?

edit:
wow im dumb cd is the command
i r stupid!

---

### Post by slats on 2008-02-05
now its saying [sudo] password for slats:

but it wont let me type in my pass

---

### Post by slats on 2008-02-05
again i fixed that but now im getting this when i enter commands
```
slats@Slat-Machine:~$ cd /home/slats/Desktop/ndiswrapper*

slats@Slat-Machine:~/Desktop/ndiswrapper$ sudo make uninstall

[sudo] password for slats:

make: *** No rule to make target `uninstall'.  Stop.

slats@Slat-Machine:~/Desktop/ndiswrapper$ make

make: *** No targets specified and no makefile found.  Stop.

slats@Slat-Machine:~/Desktop/ndiswrapper$ sudo make install

make: *** No rule to make target `install'.  Stop.

slats@Slat-Machine:~/Desktop/ndiswrapper$ sudo ndiswrapper -m

sudo: ndiswrapper: command not found

slats@Slat-Machine:~/Desktop/ndiswrapper$ 


```

---

### Post by slats on 2008-02-05
please i really need help with this

---

### Post by slats on 2008-02-06
bump.

---

### Post by slats on 2008-02-06
i did everything it said and plugged it and i got nothing
the led on the usb device doesnt even blink

is there anything else i could do?

---

### Post by pjhenry1216 on 2008-02-07
I'm actually the owner of the blog that a majority of this was taken from ([http://www.paulie-pages.com](http://www.paulie-pages.com)). Not sure if this will help, but make sure there isn't another folder INSIDE the extracted folder that you need to go into.  Also, if you're going to download the files from the links above, at least visit my blog and what not.

---

### Post by pjhenry1216 on 2008-02-07
Just to let you know, to check to see if there's another folder, when you're in the folder you've been trying the commands, type "ls" (that's a lowercase L).  That lists the contents of the folder.  If it shows only one folder, than that means you need to go into that folder (which you can do with the "cd" command).  if it shows a whole lot of files and what not, I'll have to double check when I get back home (I'm at work on a Windows machine right now, so I really can't mess around with stuff).

---

### Post by fatalbert on 2008-02-12
I have the same card, but the make is failing for me on Dapper 6.06 LTS. Could someone please help?

Thank you

root@zoro:~/ndiswrapper-1.51# uname -a
Linux zoro 2.6.15-29-386 #1 PREEMPT Mon Sep 24 17:18:25 UTC 2007 i686 GNU/Linux

root@zoro:~/ndiswrapper-1.51# sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
cpp is already the newest version.
gcc is already the newest version.
build-essential is already the newest version.
linux-headers-2.6.15-29-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.


root@zoro:/tmp/ndiswrapper-1.51# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

root@zoro:/tmp/ndiswrapper-1.51# make
make -C driver
make[1]: Entering directory `/tmp/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.15-29-386 SUBDIRS=/tmp/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-29-386'
  LD      /tmp/ndiswrapper-1.51/driver/built-in.o
  CC [M]  /tmp/ndiswrapper-1.51/driver/crt.o
In file included from /tmp/ndiswrapper-1.51/driver/crt.c:16:
/tmp/ndiswrapper-1.51/driver/ntoskernel.h:718: error: field ‘lock’ has incomplete type
/tmp/ndiswrapper-1.51/driver/ntoskernel.h: In function ‘raise_irql’:
/tmp/ndiswrapper-1.51/driver/ntoskernel.h:755: warning: implicit declaration of function ‘mutex_lock’
/tmp/ndiswrapper-1.51/driver/ntoskernel.h: In function ‘lower_irql’:
/tmp/ndiswrapper-1.51/driver/ntoskernel.h:777: warning: implicit declaration of function ‘mutex_unlock’
make[3]: *** [/tmp/ndiswrapper-1.51/driver/crt.o] Error 1
make[2]: *** [_module_/tmp/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-29-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/tmp/ndiswrapper-1.51/driver'
make: *** [all] Error 2
root@zoro:/tmp/ndiswrapper-1.51#

---

### Post by fatalbert on 2008-02-13
I gave it another stab and using this link mainly and it worked: 

[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

Now I just need to buy the router and hopefully not run into any issues.

---

### Post by mistered39 on 2008-05-02
Am trying to install into 8.04 and am getting stuck here:

edv@edv-laptop:~/drivers$ sudo ndiswrapper -iWUSB54GSC.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
edv@edv-laptop:~/drivers$ sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsc/
cp: accessing `/etc/ndiswrapper/wusb54gsc/': Not a directory
edv@edv-laptop:~/drivers$ 

Is there something that I put in wrong? Any help would be greatly appreciated.

---

