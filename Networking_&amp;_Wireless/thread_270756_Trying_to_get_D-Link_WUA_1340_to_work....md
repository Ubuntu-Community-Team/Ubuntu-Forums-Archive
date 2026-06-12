---
title: "Trying to get D-Link WUA 1340 to work..."
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by LilRayRay on 2006-10-03
Hi all, I am trying to get my dlink WUA 1340 installed using ndiswrapper.  I installed ndiswrapper without any issues, but I am having trouble with the drivers.  I extracted a driver from the Dlink CD but this driver did not work under NDISwrapper.  The tar.gz on the ndiswrapper driver list is broken, so I cant use it.  Does anyone have any idea what I might do to make this work?

---

### Post by LilRayRay on 2006-10-03
Alright, I have been working on this for a bit.  I managed to find windows drivers that were recognized by ndiswrapper.  These unfortunately did not work.  I did on the other hand find native linux drivers, but I cant figure out how to compile them.  I was given some quick instructions, but I kept getting an error when I tried to use the "make" command.

---

### Post by LilRayRay on 2006-10-04
anyone?

---

### Post by midia on 2006-12-22
Hi there,
I got mine working.  Here's how:

- Using Synaptic I installed ndiswrapper 1.5, utils, and common files  onto my Edgy distro from the CD. (not ndiswrapper 1.8 .  I'll tell you why in a bit.)
- I gathered not only the inf file (DrWU71.inf), but all of the driver files into one directory.  Here's the list:
[INDENT]Config.dat
DeviceInst.exe
Dr71WU98.sys
Dr71WU.cat
Dr71WU.inf
Dr71WU.sys[/INDENT]

Note: I got them by installing wine and running wine on the setup.exe file in the D-link Windows CD and copied the files from the Program File directory in the ".wine" directory on my PC.
- I ran ndiswrapper command to install the inf.
[INDENT][COLOR="Red"]sudo ndiswrapper -i Dr71WU.inf [/COLOR][/INDENT]
- To run the module on boot I used this command
[INDENT][COLOR="Red"]sudo ndiswrapper -m[/COLOR][/INDENT]
- I then un-installed ndiswrapper 1.5 and installed ndiswrapper 1.8 from the CD.  For some reason running this command next to create an alias:

[INDENT][COLOR="Red"]sudo modprobe ndiswrapper[/COLOR][/INDENT]

did not work with version 1.5 installed.

- At this juncture I plugged the wireless d-link unit into a USB port and performed a iwconfig to see if wlan0 was present.
Notes: 
Wierdism #1 -  wmaster0 was also present and somehow associated with wlan0.  wlan0 is the actual device.  As long as wmaster0 was there, wlan0 would not allow me to connect to the Internet.  After futzing around, I decided to reboot the computer with the d-link not plugged in.  I plugged the d-link in AFTER the reboot completed.  I ran this command to get it to detect my home network:
[INDENT][COLOR="Red"]sudo iwconfig wlan0 essid "whatever-your-essid-is"[/COLOR][/INDENT]
That connected me to the web.
Wierdism #2 - I check Ubuntu's Network utility ( System>Administration>Networking ).  It said that though wlan0 was present ( and thankfully that wmaster0 was not ), wlan0 was not enabled (!!).  I enabled it and entered my essid ID in the properties dialog box.   
By doing that, it wrote this line
[INDENT]wireless-essid my-home-wireless-ID[/INDENT] 
in the /etc/network/interfaces file under the wlan0 entry that was already there at the end of the file:
[INDENT]auto wlan0
iface wlan0 inet dhcp
wireless-essid my-home-wireless-ID[/INDENT]

The last command I did was this:

[INDENT][COLOR="Red"]sudo dhclient[/COLOR][/INDENT]

to get DHCP working.

Note:  I don't use WPA or any encryption, and I don't broadcast my home wireless network essid.

End of procedures.

Now every time I boot the computer, I stick the d-link device into the usb port after booting onto my desktop completes.  If I reboot with the thing still in its cradle, the light on it stays lit but can't connect to the Internet.  Also, that wmaster0 device returns when I run iwconfig. :-? 

If anyone knows what modifications need to be made to which files for my USB device to work through reboots without me needing to unplug it, I'd like to know.

I hope this helps. 

Take care.

---

### Post by kfinnie on 2006-12-23
I've tried following your instructions, but found no DR71WU.inf file. If you could zip up your driver files for me I would appreciate it.

I grepped the C:\Windows\inf directory for "1340" and found a file called oem15.inf - this file was considered invalid by ndiswrapper.

Also, my Edgy distribution CD does not contain ndiswrapper 1.5 and 1.8. It has 1.1 and 1.8. I have been using 1.1 in place of 1.5 in your instructions.

---

### Post by midia on 2006-12-24
I modified my reply above about sending software files.  I'm not sure that's legal.  Let me tell you exactly where I found the files I listed above:

In Windows XP

C:\Program Files\D-Link\Wireless G WUA-1340\Drivers

In Ubuntu, 
I popped in the wua-1340 CD.
I navigated to the Drivers directory on the disc where there is a setup.exe file.
I opened a terminal window and ran the "[COLOR="Red"]wine setup.exe[/COLOR]" command.
After about a minute, the install program started on my linux box.
After stepping through the installer program, I went to the ".wine" (dot-wine) directory. You'll see it if you do this command [COLOR="Red"]ls -a[/COLOR], or if you select View>>Show Hidden files in Nautilus.

All of the files listed above are in the directory listed below:
[B]
home/your username/.wine/drive_c/Program Files/Drivers[/B]

Good luck.

If you're able to get online, download the most recent ndiswrapper, as root: make uninstall (remove all prior versions completely), make install.  Run ndiswrapper -i to install the win drivers.  NOTE: The Windows drivers come with rt73.inf.  I didn't mention that in my list above.  Don't have it in the directory with the Dr71WU.sys and inf files.  Rather, let ndiswrapper find rt73usb.inf and use that.  rt73usb.inf already part of the Ubuntu build.  Follow my other instructions above to complete the task.
You'll still have to disconnect the device during a reboot, then plug it in when at your desktop.

---

### Post by TripleWithCheese on 2007-01-05
Here is what I did to get the D-Link wua-1340 working with Edgy.  It seems that the rt73usb driver shipped with Edgy is what causes the wmaster0 interface to appear and causes all the headaches so I went and got the rt73 driver from ralinktech.

[http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/ralink/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz)
Unpack this to a safe place using the archive manager 

To build the driver you will need the kernel source package, in a terminal type;

uname -r  

to see what kernel version you have, mine was 2.6.17-10-generic so I went out to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  and searched for linux-source-2.6.17 which brought me to 

[http://packages.ubuntu.com/edgy/devel/linux-source-2.6.17](http://packages.ubuntu.com/edgy/devel/linux-source-2.6.17)

After downloading and installing the source pacakge the actual source files were zipped and sitting in /usr/src as

linux-source-2.6.17.tar.bz2.  

I unpacked the files to /usr/src , you may need to chmod the /src directory before you can unpack the files to it.  

from the terminal again

cd /usr
sudo chmod 777 src

now you can unpack the source files using the archive manager  (double click on the file from in file browser)

you will also need tofrodos, get that here

[http://packages.ubuntu.com/edgy/utils/tofrodos](http://packages.ubuntu.com/edgy/utils/tofrodos)

once that is installed you're ready to go

First we'll kill the current driver

sudo nano /etc/modprobe.d/blacklist

at the bottom of this file add

blacklist rt73usb

save and exit the file

then

sudo modprobe -r rt73usb

your nic should stop working now

next we'll start building the new driver

cd to the directory you unpacked the RT73_Linux_STA_Drv1.0.3.6.tar.gz archive to so we can edit the definitions file make sure you are in the Module directory

cd /*path to files*/RT73_Linux_STA_Drv1.0.3.6/Module

sudo nano rtmp_def.h

page down to the end of this file and you will see a section you will see a section that starts #define RT73_USB_DEVICES 

above the line that reads {USB_DEVICE(0,0)}} /* end marker */
add 
{USB_DEVICE(0x07d1,0x3c04)}, /* D-Link System */       \

save the file and exit

if you're wondering where this came, in a terminal type lsusb -v and look for your nic.  There should be a line that looks like Bus 002 Device 013: ID 07d1:3c04 D-Link System if you would like to try this driver with a card other than the wua-1340 you should be able to add that card's ID to the rtmp_def.h file instead of the ID that I added.

now in the terminal

cp Makefile.6 ./Makefile

make all

when prompted for your source package location give it the directory you unpacked your source files to for me this is

/usr/src/linux-source-2.6.17

assuming that this completes with no errors (warnings are ok) all we need to do now is make the driver available

first make the directory that the driver looks to for config information

sudo mkdir -p /etc/Wireless/RT73STA/ 

then copy the .bin file

sudo cp rt73.bin /etc/Wireless/RT73STA/

now we need to convert the .dat file using tofrodos

sudo chmod 777 rt73sta.dat

sudo fromdos rt73sta.dat

and move it to the directory the driver wants

sudo cp rt73sta.dat /etc/Wireless/RT73STA/

now we move our driver file 

sudo cp rt73.ko /lib/modules/2.6.12-10-386/kernel/drivers/net

fire up the driver

sudo depmod -a

modprobe rt73

and bring up the nic

sudo ifconfig rausb0 inet up

your nic should be up and running

Now you can use iwconfig or the config file (/etc/Wireless/RT73STA/rt73sta.dat) to configure your nic including setting up WEP or WPA.

If everything is working 

sudo nano /etc/modules

after the last entry add

rt73

save and exit

now the module will load when your system boots, since this is a driver solution there is no need to unplug the nic when you shutdown.

---

### Post by midia on 2007-01-05
I rather run from native drivers than ndiswrapper any day, but I haven't the experience setting that up yet.  Too new to Linux/Ubuntu.
Thanks, Triple...!  :D

---

### Post by midia on 2007-01-17
I found these instructions to be spot on.  The d-link will even work through boots:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

---

### Post by kwickone on 2007-04-11
TripleWithCheese you RULE!

I followed your instructions to the 'T' and it worked great.  Now I have wireless and WPA with no ndiswrapper.

Thanks much.

---

### Post by scott_g on 2007-07-11
Hi,

I'm trying to compile the native drivers, but I get this error:

```

scott@scott-ubuntu:/usr/wireless/RT73/Module$ sudo make all
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/wireless/RT73/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/wireless/RT73/Module/rtmp_main.o
/usr/wireless/RT73/Module/rtmp_main.c:66: error: expected &#8216;}&#8217; before &#8216;.&#8217; token
/usr/wireless/RT73/Module/rtmp_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/usr/wireless/RT73/Module/rtmp_main.c:1060: warning: unused variable &#8216;device&#8217;
make[2]: *** [/usr/wireless/RT73/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/usr/wireless/RT73/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

Anyone have any ideas as to where I'm going wrong?

I'm using the 2.6.20 kernel and have downloaded the appropriate source code, and have downloaded the Ralink 1.0.4.0 drivers.  It never asked me for the directory of the source code that I downloaded.

Thanks a lot,
Scott

---

### Post by wakeupgod on 2007-07-20
ralink updated the driver; the new files can be found here:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

that's it

---

### Post by anjael on 2007-08-19
*bows to triplewithcheese*

I followed your instructions and everything FINALLY WORKS with this (almost damned) card.
I have spent 3 days now trying to get the effing thing working.
THANKS YOUZ!!!

---

### Post by Waklevören on 2007-09-08
TripleWithCheese, that was awesome :) It made my Linksys WUSB54GC run like a charm weeks, if not months after I last tried to make it work. I wonder why I didn't find this thread earlier o0 Oh well, it's working now :D Lets just hope the ubuntu devs get this mess fixed for the next release... the rt73 is a widely used chipset and I'm sure it's caused a lot of headaches for ubuntu users around the globe :) I'm wireless, baby! YEAH! :D

Edited sept. 9th:

Well, I guess I was celebrating a bit too early last night.. After rebooting the usb device shows up as a wired connection and does not get me connected anymore. Although if I go to Manual configuration -something- (not given a name) shows up as Wireless connection.. but manual setup of this device does not help... Any Ideas? Btw, I'm running ubuntu feisty..

---

### Post by jakswa on 2007-09-20
I used this wireless network adapter... took me a day and a half of searching, and just about the time i was about to give up (after fiddling for hours with ndiswrapper), I found WICD!

WICD is a network manager, and it takes the place of the "Network-manager" package that comes with ubuntu.

edit:  I'm a noob like you, so don't expect me to know whats up if you run into problems with the way that I did this... (but I would like to know if you did)

I simply:

--uninstalled the Network-manager package  (using System>Administration>synaptic package manager)

--installed the WICD package 
(if you're accessing the internet from a windows computer, just download from sourceforge:  [http://downloads.sourceforge.net/wicd/wicd_1.3.1-all.deb?modtime=1184023948&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.3.1-all.deb?modtime=1184023948&big_mirror=0) )

--ran the WICD package (applications > internet > wicd), and it saw my router, and i clicked 'connect' and POOF!  wireless internet!

I'm talking to you about 5 minutes after i got it working (I'm spreading the word.)

edit:  I'm not sure if uninstalling network manager will disconnect your ubuntu system if you are currently accessing the internet from it (through wired connection, and trying to get wireless to work).  So you might want to make sure you have the necessary file (the WICD .deb) downloaded before uninstalling network manager.

---

### Post by javendo on 2007-10-24
Hello,

I follow your the TripleWithCheese instructions to configure the RT73 module.

The problem is that I am not be able to access the router. The WiFi-1340 flashing light alternate between on and off.

I manage to install the module and this is the return of some commands:

#ifconfig rausb0
rausb0 Link encap:Ethernet HWaddr 00:15:E9:B7:6F:CE
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::215:e9ff:feb7:6fce/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5316 errors:0 dropped:0 overruns:0 frame:0
TX packets:1219 errors:0 dropped:3 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1128019 (1.0 MB) TX bytes:716178 (699.3 KB)

#iwconfig
rausb0 RT73 WLAN ESSID:"dlink"
Mode:Managed Channel=11 Access Point: 00:1B:11:57:BA:11
Bit Rate=54 Mb/s
RTS thrff Fragment thrff

#more /etc/Wireless/RT73STA/rt73sta.dat
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=dlink
NetworkType=Infra
Channel=11
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0
AdhocOfdm=0
FastRoaming=0
RoamThreshold=70

I put rt73* in the places:
/lib/firmware/2.6.22-14-generic/rt73.bin
/lib/modules/2.6.22-14-generic/extra/rt73.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/rt73.ko
/etc/Wireless/RT73STA/rt73.bin
/etc/Wireless/RT73STA/rt73sta.dat

Please, could you help me to fix it.

Thanks in advance.
Alessandro.

---

### Post by javendo on 2007-10-24
Hello

I managed the problem follow this link:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=WUA+1340](http://ubuntuforums.org/showthread.php?t=400236&highlight=WUA+1340)

Regards
Alessandro

---

### Post by queque on 2008-01-10
.

---

### Post by queque on 2008-01-10
.

---

