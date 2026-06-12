---
title: "Huawei's hsdpa modem Model E220"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by bryan4134 on 2006-09-22
The E220 provides mobile broadband via USB 2.0 and works flawlessly under Windows.  While I can "see" the modem in Device Manager...see attachment.... I am too much of Linux newbie to know how to proceed from here.  I would be interested to hear if anyone has managed to get this neat little 3.6mbps wonder working with Ubuntu.

Any help advice appreciated.

Thanks, Bryan

---

### Post by nickwallingford on 2006-10-15
I, too, would need more help than I've been able to find so far...

[http://the.taoofmac.com/space/Huawei/E220]("http://the.taoofmac.com/space/Huawei/E220") gave me a bit to get started, but I'm still struggling.  

I've had previous similar devices (the PCMCIA card version) working with both Fedora and Ubuntu, but haven't got enough nous to do this on my own!

Any clued up out there?

---

### Post by mips on 2006-10-16
[http://www.linuxforums.org/forum/peripherals-hardware/36506-huawei-ets2077-fixed-wireless-terminal.html](http://www.linuxforums.org/forum/peripherals-hardware/36506-huawei-ets2077-fixed-wireless-terminal.html)
[http://lkml.org/lkml/2005/9/22/57](http://lkml.org/lkml/2005/9/22/57)
[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/p,531/sid,5a67b9d5f06e18bef6647c9e61f3c55c/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/p,531/sid,5a67b9d5f06e18bef6647c9e61f3c55c/)
[http://tuxmobil.org/index.html](http://tuxmobil.org/index.html)
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO.html)
[http://www.google.co.za/search?as_q=Huawei+E220+Linux&num=10&hl=en&client=firefox&rls=Swiftfox%3Aen-US%3Aunofficial&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.co.za/search?as_q=Huawei+E220+Linux&num=10&hl=en&client=firefox&rls=Swiftfox%3Aen-US%3Aunofficial&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=lang_en&as_ft=i&as_filetype=&as_qdr=all&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by bryan4134 on 2006-10-16
Nick - I am still searching for a solution - let me know if you come up with anything...

Bryan

---

### Post by nickwallingford on 2006-10-16
Thanks, mips - I recognise you and some of those links from a year or so ago when I was getting Vodaphone's 3G card working...

Some of the stuff on the pharscape.org page starts to make sense to me, but I'll have to do a bit more reading to phrase meaningful (read: not stupid!) questions...

Nick

---

### Post by nickwallingford on 2006-10-16
The Huawei E220 seems to be being recognised - after plugging it in, I can see (tail /var/log/messages):
usb 4-1: reset full speed USB device using uhci_hcd and address 8
(then more info re: SCSI bulk storage aspect of the modem)

I've then used:
mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1
mknod /dev/ttyUSB2 c 188 2

I *think* the blue flashing light on the vodem indicates it is both recognised and is detecting a 3G network within range (a good thing, as far as that goes...)

But I've not been able to use wvdial to communicate with it - doesn't appear at any of the three device names above.  I've previously used a script (3g.sh) with the PCMCIA card device that Vodaphone uses, and I'm using that but can't find the right device to open to aim the dialling info at.

Hope that isn't too obscurely written!

Nick

---

### Post by nickwallingford on 2006-10-27
I've made some progress - at my most optimistic, I'd even claim it to be in a forward direction (heh, heh...)

The page at [http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726) applies directly to making the Huawei E220 work with Ubuntu.

I downloaded the nozomi-source package (ftp from a link you can find at [http://packages.debian.org/unstable/net/nozomi-source](http://packages.debian.org/unstable/net/nozomi-source))

Unable to compile it initially, getting an error.  Followed that one through to find the answer at [http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,87/sid,705f1f62f6ba056aa36088d9ce00ce9f/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,87/sid,705f1f62f6ba056aa36088d9ce00ce9f/) - and that led to a clean build.

I saw various comments that for whatever reason, it could not be used as 'modprobe -r nozomi', but rather had to be done as 'insmode nozomi.ko' - and it seems to accept that happily.

As this as the first time, I had to create the nodes with 'mknod /dev/noz0 c 241 0' and repeat that 3 more times, making noz1, noz2 and noz3.

By then I had the wvdial.conf file that was linked from the [www.pharscape.org](www.pharscape.org) link above.

And finally, I should be able to use 'wvdial hsdpa' to connect.  But that is where it falls down.  I get the error 'Cannot open /dev/noz0: No such device or address'  I've tried the other three noz? devices as well, but the modem isn't being seen at any of them.

I think I'm close, and I know I've been reasonably methodical and thorough at looking for the info I'm after (If anyone hasn't read  the info that mips has in a sig file as [http://www.catb.org/%7Eesr/faqs/smart-questions.html](http://www.catb.org/%7Eesr/faqs/smart-questions.html), you should!).

I'd appreciate a gentle steer (hell, I'll take an ill mannered tirade - I'm not proud...) as to the next direction I should try, or the next piece of testing that can move me on.  I think I can say I'm at my current limits of expertise/understanding - so I'm ready to learn!

Nick

---

### Post by nickwallingford on 2006-11-17
**OK - PRETTY MUCH DISREGARD MOST ALL OF MY ABOVE POSTINGS AS I BRANCHED OFF THE WRONG TRACKS.  MY HUAWEI E220 USB IS NOW WORKING**.
=======================================================================

The Huawei E220 is a USB 'dongle' for HSDPA connection through (for me, anyway) the Vodaphone network in New Zealand.

When inserted into a Ubuntu OS, it is immediately detected as a SCSI/CDROM type bulk storage device, and the files that are used by Windows appear attached to the filesystem similar to any other USB storage device.

Close any window that might be showing you those files.  Then unmount the device (eject the CDROM icon you'll find on the desktop created when you inserted the device).

All commands I give here are just the commands - you will likely need to put **'sudo'** in front of them so you have the permissions of root to carry them out...

Insert the device and give it a chance to settle down (enjoy watching the lights flash...)

When you insert the device and it gets recognised as a storage device, it will have created /dev/ttyUSB0.  You can see that with:

**ls -la /dev/ttyU***

You will likely only see one entry: ttyUSB0.

To make the modem work, you must first remove the module that is used for usb-storage devices.  You can do that with:

**rmmod usb-storage**

If you are told it is in use, that is an indication you didn't close windows and eject the device first.

This next command may not be absolutely necessary, but it won't hurt anything (heh, heh...):

**rmmod usb-serial**

You are now going to re-insert that module, but giving the specific details of your modem.  First, make sure you have the right details by using:

**lsusb**

You should see an entry similar to this in the output:

**Bus 004 Device 004: ID 12d1:1003  **

The Bus and/or Device number might be different for you, but the important part is the ID.  If yours is not 12d1:1003, you'll need to modify the next command, but I *think* it will be either that or 12d1:1001...

This command will insert the module with the device specific details:

**modprobe usbserial vendor=0x12d1 product=0x1003**

Now, remove the device, wait a bit for things to settle, and then plug it back in.

I *think* you may now have maybe three entries if you do:

ls -la /dev/ttyU*

Basically, what has been done is that you have removed the initial inclination to treat the device only as a bulk storage (removing the module that handles that).  You've also manually caused the recognition of the device (using the modprobe command).  So that when you re-plugged it, it should now be able to work with the *modem* part of the device addressing it as /dev/ttyUSB0, rather than that being the bulk storage device.

Use a text editor such as pico to edit or create if necessary the file to handle the dialling configuration.  My /etc/wvdial.conf file looks like this:

[B]# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
[/B]

I've only put in the relevant sections - the full file can be found at the address below this posting.

You can dial the modem with:

**wvdial hsdpa**

If all is happy, you'll see the messages in the terminal window to show how it is connecting, your IP address, your remote gateway and 2 nameservers the network provides for you.

Do remember the various need for 'sudo' unless you change ownerships/permissions.  In particular, if it looks like you've connected but are not able to connect to any sites, etc, look for a message telling you that /etc/ppp/pap-secrets and /etc/ppp/chap-secrets are not able to be written to - that may well indicate that you for sure need to run the wvdial command as sudo (If you are running it as a normal user, that user would need to have the ability to write to those files for the connection to be able to work...)

I am writing this while standing on the shoulders of the knowledgeable and the helpful.  In particular, see [http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726) - Post 1 in that thread, and Tazz_Tux who wrote and maintains it, has been invaluable.  Go there if for no other reason than to get the latest version of wvdial.conf

Enjoy your Huawei E220 under Ubuntu!

Nick

---

### Post by mips on 2006-11-18
Thanks for the feedback!

Maybe post this as a Howto in the Howto/Tips section.

---

### Post by nickwallingford on 2006-11-18
I've now done that, mips - I was impressed with myself getting it working in spite of my own limitations and the general perception among people I spoke with that it was not possible.

Your help and that of Tazz_tux in another set of forums was for sure what kept me going until I did it.

And like most of these things, I sure learned a lot in the process!

Nick

---

### Post by mips on 2006-11-19
Thx ! I'm sure others will benefit from the info.

---

### Post by bryan4134 on 2006-11-29
Nick - many thanks for this.  I think I now have my machine connecting to the modem (see terminal output below)......

ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately
--> Starting pppd at Wed Nov 29 18:02:45 2006
--> Pid of pppd: 18104
--> Using interface ppp0
--> local  IP address 10.32.129.229
--> remote IP address 203.78.47.18
--> primary   DNS address 10.11.12.13
--> secondary DNS address 10.11.12.14
--> Connect time 0.1 minutes.
--> local  IP address 10.32.129.229
--> remote IP address 203.78.47.18
--> primary   DNS address 202.140.96.51
--> secondary DNS address 202.140.96.52

Right now I am in Shanghai so I will need to wait until I get back to Hong Kong where my carrier is in order to really test the connection to the Internet....

Does the output above look about right?

Thanks, Bryan

---

### Post by bbo on 2006-12-11
> You will likely only see one entry: ttyUSB0.

> To make the modem work, you must first remove the module that is used for usb-storage devices. 

NO !

Use e220 modem activator
[http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)

and
cat /proc/bus/usb/devices
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1003 Rev= 0.00
S:  Manufacturer=HUAWEI Technologies
S:  Product=HUAWEI Mobile
C:* #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=128ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbserial_generic
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

/dev/ttyUSB0 /dev/ttyUSB1 and storage. no kernel patch.

bbo

---

### Post by thet on 2006-12-11
bbo, please give more info on what to do...
i do not speak slovakian... and don't know what do do whith that .out files and how to use the driver...
i know how to compile, but..?

i use ubuntu 6.10 on a laptop with an usb1.1 port

greetings, thet

---

### Post by bbo on 2006-12-12
Standard Kernel debian - no patch.
First connect USB -> only detects modules usb-storage.
cat /proc/bus/usb/devices
 C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
 I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50  ver=usb-storage
 E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
 E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

rmmod usbserial
modprobe usbserial vendor=0x12d1 product=0x1003
huaweiAktBbo-i386.out   = modem activator
detects modules: usb-storage + 2x ttyUSB  ;-)
cat /proc/bus/usb/devices
...
pppd call gprs .. minicom and At commands .... to connect internet. (like standard modem)

---

### Post by daka on 2006-12-18
I wish I lived in New Zealand... I am in Spain and although some of the how-to advice works for me, after one week of convoluted experimentation I finally have my Huawei e220 working in Kubuntu in Spain. The idea of trying to write that How-to is a bit daunting but if anyone else is unable to get the e220 working with the New zealand instructions let me know and I will do it..... It was well worth the effort!!!!!!!!

Daka

---

### Post by thet on 2006-12-18
yea!
bbo and all other informants, thank you.
it worked!
i didn't check that the huaweiAktBbo-i386.out is an executable

here some more infos about my config:
ubuntu 6.10
provider: drei.at (Hutchison 3G Austria)
modem: huawei e220
laptop with usb 1.1 ports

----SKRIPT TO DIAL IN: [EDIT - vendor and product id were wrong]
#/bin/sh
sudo modprobe usbserial vendor=0x12d1 product=0x1003
sudo /PATH/TO/huaweiAktBbo-i386.out
sudo wvdial pin huawei

----wvdial.conf
[Dialer Defaults]
#Phone = *99***1#
Phone = *99#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]
Init1 = AT+CPIN=1234

[Dialer huawei]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = AT
Init3 = AT&FE0V1X1&D2&C1S0=0
ISDN = 0
Modem Type = Analog Modem


-----
(i hope i can reproduce this again...:)

---

### Post by daka on 2006-12-19
This may be most relevant to people trying to configure the Huawei E220 in Linux in Spain.  I tried to follow advice in a number of forums without success but experimented with much of this advice and finally was successful.  Here is my first ever "How_To":

HOW TO Configure the Huawei 220 usb modem in Linux, (IN SPAIN)
__________________________________________________________________

"Spain is different" (..is an advertising slogan they developed years ago to attract tourists to Spain) (Technologically VERY different)

I am a Linux newbie... this is my first "How To".... I tried other advice from various forums without success... by experimenting I came up with this  soultion:

I use a Packard Bell EasyNote laptop with Kubuntu kernel 2.6.15-23-386 

Disable pin by putting card in a phone and disabling (otherwise the nightmare is much worse..,.although it is possible... I eventually disabled the pin and am much happier.

When the Huawei is identified initially as a CD "Connect_Box", right click it and "eject"

Go to System Settings / Network Settings and disable Ethernet and Wireless as these interfere greatly with the Huawei.

(I read in a few places that the long cable doesn't work but this is NOT my experience... I use the long one with an extension of two metres and my connection then, (only then) has a strong and stable signal)

Open a terminal as root

rmmod usb-storage
modprobe usbserial vendor=0x12d1 product=0x1003

remove the Huawei E220 for a few moments

wait a few seconds, maybe 10-20, and re-insert

optionally, you can enter:
ls -la /dev/ttyU* 
and you will probably
find  USB0  USB1  and USB2 .. 
if not, wait a few more moments and try again...
then...

wvdial hsdpa

You should be connected!

Here is my wvdial file:

/etc/wvdial.conf



[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","ac.vodafone.es";

_______________________________________________________



This is what my script looks like when I connect

Password:
root@kp-laptop:/home/daka# rmmod usb-storage
root@kp-laptop:/home/daka# modprobe usbserial vendor=0x12d1 product=0x1003
root@kp-laptop:/home/daka# ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2006-12-19 14:33 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2006-12-19 14:33 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2006-12-19 14:33 /dev/ttyUSB2
root@kp-laptop:/home/daka# wvdial hsdpa
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","ac.vodafone.es";
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Dec 19 14:33:56 2006
--> Pid of pppd: 5550
--> Using interface ppp0
--> local  IP address 62.87.24.143
--> remote IP address 10.64.64.64
--> primary   DNS address 212.73.32.3
--> secondary DNS address 212.73.32.67
                                         
Good Luck... (I hope I haven't made any mistakes in this!!)

Daka





;)

---

### Post by alexmoon on 2006-12-25
Hi, I'm veryvery new to linux generally, and ubuntu in particular. I only sorted out wireless internet a few weeks ago, and then promptly left the country and started using mobile internet. So I've probably missed a basic, very obvious step somewhere - problem is that I'm not sure where.

I followed the instructions given here, as given in the howto from nickwallingford ([http://ubuntuforums.org/showthread.php?t=302464&highlight=huawei+E220](http://ubuntuforums.org/showthread.php?t=302464&highlight=huawei+E220))

As far as I can tell, changing the wvdial.conf bit went ok, but when I type "wvdial hsdpa" I get:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

I suspect that the problem has something to do with nozomi, since I've not really got the hang of compiling programs yet. I got the package from here: [http://packages.debian.org/unstable/net/nozomi-source](http://packages.debian.org/unstable/net/nozomi-source) (from the part that said: "download nozomi-source") and then it came up with a package (nozomi-source_2.1.2_all.deb) that I clicked on and it seemed to have installed itself. 

Are there other bits I was meant to install (compile?)?

I typed this: apt-cache search nozomi
and got this: nozomi-source - source for GlobeTrotter HSDPA kernel driver

I don't know if that means it's compiled or not, though.

Thank you very much for your help, I really hope I haven't done anything too stupid. I've read through "how to install anything on Ubuntu" but it hasn't helped, unfortunately.

---

### Post by thet on 2007-01-03
if you use ubuntu you may download huaweiAktBbo-i386.out (for i386) from [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)

with a wvdial.conf with correct data you may only need to run following commands in terminal:

sudo modprobe usbserial vendor=0x12d1 product=0x1003
sudo huaweiAktBbo-i386.out
wvdial hsdpa


hope that helps

---

### Post by alexmoon on 2007-01-04
I downloaded huaweiAktBbo-i386.out, but when I type "sudo huaweiAktBbo-i386.out" I get something like "no such command found". 

Is there somewhere in particular I'm meant to but huaweiAktBbo-i386.out ? Right now I just put it on my desktop...I don't really know what to do from here.


Another option I've tried out is to install nozomi, but when I typed in "# m-a a-i nozomi" it told me that it had failed. The error messages went like this: (if it helps)

dh_testdir                                                                 &#8593; 
 &#9474; dh_testroot                                                                &#9646; 
 &#9474; dh_clean                                                                   &#9618; 
 &#9474; /usr/bin/make -C /usr/src/modules/nozomi clean                             &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/nozomi'                      &#9618; 
 &#9474; rm -f *.o *.ko *.mod.* .*.o.cmd .*.mod.* .*.ko.cmd                         &#9618; 
 &#9474; rm -f .tmp_versions -rf                                                    &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/nozomi'                       &#9618; 
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     &#9618; 
 &#9474; make[1]: Entering directory `/usr/src/modules/nozomi'                      &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; dh_testroot                                                                &#9618; 
 &#9474; dh_clean                                                                   &#9618; 
 &#9474; /usr/bin/make -C /usr/src/modules/nozomi clean                             &#9618; 
 &#9474; make[2]: Entering directory `/usr/src/modules/nozomi'      
rm -f *.o *.ko *.mod.* .*.o.cmd .*.mod.* .*.ko.cmd                         &#8593; 
 &#9474; rm -f .tmp_versions -rf                                                    &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/nozomi'                       &#9618; 
 &#9474; /usr/bin/gcc-4.1                                                           &#9618; 
 &#9474; for templ in ; do \                                                        &#9646; 
 &#9474;     cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.17-10-generic/g'` ; \   &#9618; 
 &#9474;   done                                                                     &#9618; 
 &#9474; for templ in `ls debian/*.modules.in` ; do \                               &#9618; 
 &#9474;     test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in}         &#9618; 
 &#9474; ${templ%.modules.in}.backup 2>/dev/null || true; \                         &#9618; 
 &#9474;     sed -e 's/##KVERS##/2.6.17-10-generic/g                                &#9618; 
 &#9474; ;s/#KVERS#/2.6.17-10-generic/g ; s/_KVERS_/2.6.17-10-generic/g ;           &#9618; 
 &#9474; s/##KDREV##/2.6.17-10.33/g ; s/#KDREV#/2.6.17-10.33/g ;                    &#9618; 
 &#9474; s/_KDREV_/2.6.17-10.33/g  ' < $templ > ${templ%.modules.in}; \             &#9618; 
 &#9474;   done          
 dh_testdir                                                                 &#8593; 
 &#9474; dh_testroot                                                                &#9618; 
 &#9474; dh_clean -k                                                                &#9618; 
 &#9474; /usr/bin/make -C /usr/src/modules/nozomi                                   &#9618; 
 &#9474; KERNEL_VERSION=2.6.17-10-generic                                           &#9618; 
 &#9474; KERNELDIR=/lib/modules/2.6.17-10-generic/build                             &#9618; 
 &#9474; KDIR=/lib/modules/2.6.17-10-generic/build                                  &#9618; 
 &#9474; make[2]: Entering directory `/usr/src/modules/nozomi'                      &#9618; 
 &#9474; Warning: Compiling for 2.6:                                                &#9646; 
 &#9474; /usr/bin/make -C /lib/modules/2.6.17-10-generic/build                      &#9618; 
 &#9474; SUBDIRS=/usr/src/modules/nozomi modules                                    &#9618; 
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'     &#9618; 
 &#9474;   CC [M]  /usr/src/modules/nozomi/nozomi.o                                 &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c: In function ‘ntty_tty_init’:             &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2170: error: ‘TTY_DRIVER_DYNAMIC_DEV’ 
undeclared (first use in this function)                                    &#8593; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2170: error: (Each undeclared             &#9618; 
 &#9474; identifier is reported only once                                           &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2170: error: for each function it         &#9618; 
 &#9474; appears in.)                                                               &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2171: warning: value computed is not      &#9618; 
 &#9474; used                                                                       &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2171: warning: value computed is not      &#9618; 
 &#9474; used                                                                       &#9618; 
 &#9474; make[4]: *** [/usr/src/modules/nozomi/nozomi.o] Error 1                    &#9618; 
 &#9474; make[3]: *** [_module_/usr/src/modules/nozomi] Error 2                     &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'      &#9618; 
 &#9474; make[2]: *** [default] Error 2                                             &#9646; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/nozomi'                       &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2            
undeclared (first use in this function)                                    &#8593; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2170: error: (Each undeclared             &#9618; 
 &#9474; identifier is reported only once                                           &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2170: error: for each function it         &#9618; 
 &#9474; appears in.)                                                               &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2171: warning: value computed is not      &#9618; 
 &#9474; used                                                                       &#9618; 
 &#9474; /usr/src/modules/nozomi/nozomi.c:2171: warning: value computed is not      &#9618; 
 &#9474; used                                                                       &#9618; 
 &#9474; make[4]: *** [/usr/src/modules/nozomi/nozomi.o] Error 1                    &#9618; 
 &#9474; make[3]: *** [_module_/usr/src/modules/nozomi] Error 2                     &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'      &#9618; 
 &#9474; make[2]: *** [default] Error 2                                             &#9646; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/nozomi'                       &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2            

I'm quite willing to either pursue getting nozomi to work, or try to get it working through huaweiAktBbo-i386.out, which seems (at least theoretically) a bit easier. Unfortunately I'm a bit stuck (again!) for what to try next.

Thanks again for all the help.

---

### Post by thet on 2007-01-08
hi,

try

# to go where huaweiAktBbo-i386.out binary resides
cd Desktop

# you need that just once - to make the binary executable
chmod a+x huaweiAktBbo-i386.out

# ./ says "use file in current directory"
sudo ./huaweiAktBbo-i386.out

---

### Post by alexmoon on 2007-01-09
Thanks thet! (and everyone else who helped.)

I tried that and then dialling in, and it worked. I guess I was missing a couple of the basic bits of knowledge necessary - one more step's filled in, now. Once again very impressed by how patient and willing to help Ubuntu users are.

---

### Post by daka on 2007-01-23
HOW TO Configure the Huawei 220 usb modem in Linux, (IN SPAIN - Vodafone)

(I don't know if these instructions work with other providers)
__________________________________________________________________

I tried to follow the above Forum guidelines but they didn't work for me.  What did work was slightly less work, slightly less complicated so I thought I should put the "How To" in the forum also.



I use a Packard Bell EasyNote laptop with Kubuntu (Dapper) kernel 2.6.15-23-386 and Linux "Mint" (Bea)
(I have also configured this modem with these instructions in Ubuntu Dapper, Ubuntu Edgy, GNU Linex 2006, Linux Mint (Ubuntu based), Knoppix, and Mandriva.

(I read in a few places that the long cable doesn't work but this is NOT my experience... I use the long one with an extension of two metres and my connection then, (only then) has a strong and stable signal)

Create or edit the "wvdial.conf" file in /etc ... (see my wvdial.conf file below)

Disable pin by putting card in a phone and disabling (otherwise the nightmare is much worse..,.although it is possible... I eventually disabled the pin and this made me much happier.

Disable Wifi and Ethernet as these can interfere with Huawei.
Go to System Settings / Network Settings and disable Ethernet and Wireless.

Leave a blank cd in the cdrom (This can prevent the Huawei from being mis-identified as a cdrom or usb storage device)

Remove all usb storage devices

Start up with Huawei plugged in

IF the Huawei is identified initially as a CD "Connect_Box", right click it and "eject".  You MAY need to do this a few times to ensure that it is ejected (until the option to "eject" is no longer there



Open a terminal as root


modprobe usbserial vendor=0x12d1 product=0x1003
wait a few moments ( 5 seconds)

remove (unplug) the Huawei E220 and wait for maybe 2-3 seconds

re-insert huawei.. wait again 10 to 20 seconds before re-inserting
* (look at lights on Huawei and wait until the light changes from green to blue)


(OPTIONALLY, before trying to connect using wvdial you can enter:
ls -la /dev/ttyU* 
and you will probably see...   USB0  USB1  and USB2 .. 

then


wvdial hsdpa

You should be connected!
_________________________________________

Here is my wvdial file:

/etc/wvdial.conf



[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","ac.vodafone.es";

_______________________________________________________



This is what my script looks like when I connect

Password:
root@kp-laptop:/home/daka# rmmod usb-storage
root@kp-laptop:/home/daka# modprobe usbserial vendor=0x12d1 product=0x1003
root@kp-laptop:/home/daka# ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2006-12-19 14:33 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2006-12-19 14:33 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2006-12-19 14:33 /dev/ttyUSB2
root@kp-laptop:/home/daka# wvdial hsdpa
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","ac.vodafone.es";
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Dec 19 14:33:56 2006
--> Pid of pppd: 5550
--> Using interface ppp0
--> local  IP address 62.87.24.143
--> remote IP address 10.64.64.64
--> primary   DNS address 212.73.32.3
--> secondary DNS address 212.73.32.67
                                         
Good Luck... (I hope I haven't made any mistakes in this!!)

I know some people have dificulty configuring the modem in Ubuntu and I don't know why.  Maybe the wvdial prog has to be recent
The distro that gives me the least problems is Linux Mint.  It is Ubuntu Dapper with ALL the Multimedia codecs and other nice stuff!  I really like it!

Daka

---

### Post by mrqwa on 2007-02-06
i have a small problem - i have PPC, so what to do with [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/) ?
how to compile it?
thanks a lot

---

### Post by mrqwa on 2007-02-07
> **mrqwa said:**
> i have a small problem - i have PPC, so what to do with [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/) ?
how to compile it?
thanks a lot

i´ve find solution
if you have a PPC use
**cc [huaweiAktBbo.c]("http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c") -lusb -I. -L. -o huaweiAktBbo-ppc.out**
than
**./huaweiAktBbo-ppc.out**

and i need another help>>
what to do with this?

mrqwa@mrqwa-desktop:~/huawei$ wvdial hsdpa
--> WvDial: Internet dialer version 1.5
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

---

### Post by svenkatesan on 2007-03-05
Hi Folks
Now I can able to get connected with the modem,the problem is how to stop this?
kill wvdial hsdpa?
Anybody have any suggestion?
Thanks

---

### Post by rykel on 2007-04-19
Hi guys,

I am now in Singapore using the same Huawei E220 USB Modem on the M1 Vodafone 3G network in Windows XP.

I will switch to Ubuntu Dapper later and if I can get it to work out of the box, I shall post my experience here.

Cheers!!

---

### Post by rykel on 2007-04-19
hi,

using the original solution, i could not get anything working for my E220 in Singapore.

the problem is that there is NO "ttyUSB-whatever" in /dev. Neither before nor after I have unmounted the 
"cd-rom"...

Next, I ran the huaweiAktBbo.out binary, and it seems to have set up the modem OK...

Now, however, I am using GNOME-PPP... could you please advise me as to how to go about using GNOME-PPP with the modem? (I used "Detect" in the Configuration window, but it says No Modem Found...)

---

### Post by arsya on 2007-06-19
Thanks for the link for modem activator.

I just bought new e220 hsdpa modem. Before, I tried to plug and unplug the modem several times, until I got 3 /dev/ttyUSB*. So, it's really nice that I don't need to do that anymore. Thanks to the modem activator.

---

### Post by schubby on 2007-06-21
I have an option 351GM USB HSDPA modem here n its working fine on Ubuntu. However, I've noticed that the download speed I get in Windows is about 600-700kbps, while in linux I just can't get it past 55kbps...

After tryin all options I could find, I'm starting to wonder if its an issue with the usbserial buffer. Has anyone else using the usbserial module had this issue??

Would like any help on the matter...

Thanks in advance...

---

### Post by rage_ext on 2007-07-07
Here is some good news to everyone who uses Huawei E220 and wants it to work in linux...

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

Just install the packages and read the instructions, and when you run the software call your operator to ask some settings like username, password APN-host and the DNS adress.

Connect and viola you should get online.

---

### Post by kiwigander on 2007-07-16
Agreed, rage_ext, the driver at the Vodafone Betavine Forge has got my system (Edgy) on line through the E220.

It still requires the preliminary steps of ejecting the "CD-ROM Disc" that shows up on the Desktop, then sudo rmmod usb-storage && sudo modprobe usbserial vendor=0x12d1 product=0x1003

(the E220 does not have to be removed and re-plugged)

I wonder whether the entire process could be written into a shell script?

---

### Post by Coruba67 on 2007-07-26
Hi guys,

Had this working perfectly in Australia for quite a while - those were some awesome instructions.  So I put a launcher on the desktop to go and run the commands needed to get me online and this has been working well for a while now.  Recently however it just stopped, not sure why...  I was hoping someone may know how to fix this.  This is what my wvdial.conf file looks like


[Dialer Defaults]
Phone=*99***1#
Username= username
Password = password
Stupid Mode = 1
Dial Command = ATDT
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 460800
Modem = /dev/ttyUSB0
ISDN = 0

This is the output of the terminal when I try connecting

--> WvDial: Internet dialer version 1.56
--> Warning: section [Dialer hsdpa] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jul 27 10:53:50 2007
--> Pid of pppd: 6432
--> Using interface ppp0
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> pppd: &#65533;[08][06][08]P[06][06][08]
--> Disconnecting at Fri Jul 27 10:53:51 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.


and this is the output of the /var/log/messages file

Jul 27 10:54:08 Thommo pppd[6449]: pppd 2.4.4 started by root, uid 0
Jul 27 10:54:08 Thommo pppd[6449]: Using interface ppp0
Jul 27 10:54:08 Thommo pppd[6449]: Connect: ppp0 <--> /dev/ttyUSB0
Jul 27 10:54:08 Thommo pppd[6449]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Jul 27 10:54:08 Thommo pppd[6449]: Warning - secret file /etc/ppp/chap-secrets has world and/or group access
Jul 27 10:54:08 Thommo pppd[6449]: CHAP authentication succeeded
Jul 27 10:54:08 Thommo pppd[6449]: CHAP authentication succeeded
Jul 27 10:54:09 Thommo pppd[6449]: Modem hangup
Jul 27 10:54:09 Thommo pppd[6449]: Connection terminated.
Jul 27 10:54:09 Thommo pppd[6449]: Exit.


Anyone have anyidea whats happening here?  This was working so well too  :(  Thanks heaps for any help in advance.


Cheers

---

### Post by viking777 on 2007-07-29
Hi, I have been wrestling with this problem for months and I have never got it to work yet. I have tried all the instructions above and also installed the connection software that someone provided the link for, but that doesn't work either, the connect button is greyed out. What I do know however is the problem, just not the solution.
I am using the 2.6.22-8 kernel which is supposed to detect the  modem automatically, indeed it does, but it does not configure it properly, and neither do any of the instructions above. The problem is that it only configures and attaches the device to /dev/ttyUSB0. In order for it to work it has to have both /dev/ttyUSB1 and /dev/ttyUSB2 confgured and the device attached to them, until this happens it just will not work, unfortunately I  don't know how to make this happen.
I even tried creating ttyUSB1 and ttyUSB2 manually using mknod. This creates the nodes but the device is not attached to them so it still doesn't work.
Please help me, I have just spent 3 months using only windows because the huawei modem was the only way I had of connecting to the internet - can you imagine how awful that is:shock:

I have found a sort of workround for this (not pretty but at least it gets it working temporarily). Go here:[http://oozie.fm.interia.pl/pro/huawei-e220/index.html](http://oozie.fm.interia.pl/pro/huawei-e220/index.html) and follow the instructions to dowload and install huawei.tar.bz2. CD to the directory where you installed it and type > make generic-install. Replug the modem run > /ls /dev/ttyU* and you should see the three nodes, then use wvdial or whatever to connect. The downside is that you will have to do this every time you shut down or reboot, but at least it works.

---

### Post by viking777 on 2007-07-29
```
huaweiAktBbo: error while loading shared libraries: libusb-0.1.so.4: cannot open shared object file: No such file or directory

```

Sorry thet, that doesn't work either.

And btw ```
sudo apt-get install libusb-0.1.s0.4
``` returns "no such file"

My workround is working though I am posting this reply on the huawei.

---

### Post by svennils on 2007-07-29
After some tinkering and searching the various forums and web pages on the huawei E220, i found my solution to get it to work on ubuntu edgy.
Here is the shell scrip i use to do it:
First, plug in the modem, wait till it settles down. Unmount the disk device if it is automounted.
Then run the shell script as root or with sudo.
        #/bin/sh
        rmmod usb-storage
        sleep 1s
        rmmod option
        sleep 3s 
        rmmod usbserial
        sleep 3s 
        modprobe usbserial vendor=0x12d1 product=0x1003
        sleep 4s
        ls /dev/ttyU*
        sleep 4s
        ls /dev/ttyU*

It does the following:
removes the usb-storage module, which interferes with the usb-serial module
waits 1 second.
removes the option module, which prevents removal of usb-serial
waits 3 seconds
removes usb-serial, which has probably detected the wrong TtyUsb0 by now
waits another 3 seconds
inserts usb-serial with the correct parameters for the huawei. E220
waits again
lists the 3 usb serial ports which now always show up correctly on my laptop
waits
and lists them again.

Then i just run kppp dialer and i'm on the net. 
Works flawlessly, every time, unlike before(got the 3 ports 1 in 25 times of plugging in the modem).
Just wanted to share my solution, in case it helps someone. It ceartinly worked for me,
no drivers added, no system tweaking. Just the right series of commands.
Enjoy.

---

### Post by viking777 on 2007-07-30
Thanks svennils, that works for me too now. I had to modify it slightly (removed the first two lines in fact - these produced an error message for me) but now it works every time and not only on Kubuntu but also on the other varieties of Linux that I use so that is great news for me. Thanks once again.

Just one question though, do you have a way to monitor data usage with the modem? I don't know about yourself but I have a monthly data allowance on my contract and if I exceed this it gets very expensive indeed. The software that runs under windows has a data usage bar that you can refer to but how would I do that in Kubuntu?

---

### Post by craigtyson on 2007-07-30
Im using 6.06LTS and got the E220 working by using the patches from here [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/) (stops the E220 loading the USB Storage module) and also has a status tool which will give you the signal strenght, throuput and amount of data sent

I'm using the wvdial configs posted earlyer.

I loaded DNS cacheing  ([http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)) as Vodafone DNS sucks big time.  and I have a noddy three line script that overwrites /etc/resolv.conf with a DNS setup that works on ip up.

All is well, and apart from a little niggle with browsing:-  DNS lookup does not wake up the e220 once it has gone idle, everything works as expected. 

BTW - The workround is (with dns cacheing) to refresh a loaded web page before opening a new one or ping a known IP for a domain eg google.com


Next question.

How to setup some scripts to auto detect the interface in use when I startup so I can auto start firestarter when using WIFI (eth1) or 3G/E220 (ppp0).  I had thought there was a terminal command I could use but I couldnt find it.  Copying saved configs to /etc/firestarter/config  at ip up dosnt work either (although there is a script to start firestarter, I cannot controll the interface and still have to open  the firestarter GUI and set the interface being used) 

If anyone wants more detail on the setup I am using let me know

Cheers

C

---

### Post by viking777 on 2007-07-31
Thanks for reply craigtyson, I have looked at oozie's stats utility as well, I can get it to install and run OK but cannot make it read any statistics.

However I think I have found my own solution now. Yesterday I installed Firestarter (I have never got this modem working under linux before so I have been using windows and sygate up till now) Anyway, firestarter recognises the connection (network manager doesn't btw) and on the status page is a list of connections along with the amount of data that is being sent and received. This is a good solution since I have effectively killed two birds with one stone, a firewall and a traffic volume monitor.

All I have to do now is to remember to write down the amount of data used at the end of each session and add them up manually to make sure I don't exceed my monthly limit!

---

### Post by cheechong on 2007-08-04
Hi Rykel,

I am Singaporean and am considering subscribing to M1 Vondafone. Have you solve the modem dial-up problem?

--
Chee Chong

---

### Post by viking777 on 2007-08-06
I've recently installed Gutsy (and like it a lot) I just spent some time with the solutions here trying to get the Huawei modem to work and absolutely none of them works if the OS is running when I plug in the modem. However if I plug it in before I start up,it is correctly detected and configured and ready to use, it needs no other scripts or commands or anything, just run wvdial and it connects. Plug it in when you are running though and no amount of 'rmmod-ing' will make it work??

Nearly there then.

---

### Post by rykel on 2007-08-06
> **cheechong said:**
> Hi Rykel,

I am Singaporean and am considering subscribing to M1 Vondafone. Have you solve the modem dial-up problem?

--
Chee Chong

Hi Chee Chong and all,

I have not looked at Ubuntuforums for the past few weeks, but I thought all of you fellow Singaporeans would LOVE this news...

***There is now UNLIMITED Starhub 3G Broadband with NO MINIMUM CONTRACT and the speed of 7.2Mbps!!!***

I have the full story on my blog, check it out: **["Finally, No More M1 Only"]("http://rykel.blogspot.com/2007/08/finally-no-more-m1-only.html")**

btw, do you know if there is any place in Singapore or Malaysia or online where we can purchase the Huawei E270 modem cheaply? Also, is there a compatible but more recent model?

---

### Post by gmanlivid on 2007-08-07
i've got a problem. i tried that but when it comes to editing the wvdial.conf file i get the message that i don't have permission to write to the etc folder and that i'm not an administrator. which shouldn't be cos i'm the one who set up the system......then again that could be the problem.

---

### Post by viking777 on 2007-08-08
> **gmanlivid said:**
> i've got a problem. i tried that but when it comes to editing the wvdial.conf file i get the message that i don't have permission to write to the etc folder and that i'm not an administrator. which shouldn't be cos i'm the one who set up the system......then again that could be the problem.

That is one of Ubuntu's annoying little traits, to get round it you need to open a terminal and type 

```
sudo gedit /etc/wvdial.conf
``` if you are using Gnome or if you are using kde

```
sudo kate /etc/wvdial.conf
```

After about a thousand times of typing stuff like this you will get heartily sick of it and wish you had a root account. This is how to get one in kde, if you are using gnome you will have to look around for similar menus, they do exist but I don't know where they are as I don't use it.

1) Go to System Settings/User Management. Click on the 'Administration Mode' button and enter your password.
2) On the Users tab click the checkbox that says 'Show System Accounts'
3)Find user 'Root' and highlight it.
4)Click the 'Modify' button.
5)In the dialog that opens up click the 'Enable' radio button.
6)Go to the 'Password' tab and enter a good strong password.
7)'OK' out of it and you are nearly done.

You now have 2 choices the easiest and best imho is to open Adept, search for and install 'Krusader' this in turn will also install  'Krusader Root Mode' and this will solve all similar such access problems in the future. The alternative is to right click your desktop, choose 'Create New'/'Link to Application'. Open the application tab and in the 'Command' line type 
```
konqueror --profile filemanagement
```
Then click on the advanced options button and then the 'Run as a different user' radio button. For 'username' type 
```
root
``` then 'OK' out. You now have a desktop shortcut to a root version of konqueror which will again stop these infuriating access problems.

NB Method 2 will only work in KDE if you are using Gnome you will have to adapt it or use method 1.

Edit: Just thought 'krusader' probably doesn't run on Gnome!!
Oh well, if you haven't got KDE you will have to resign youself to typing I suppose - or get KDE - its miles better than Gnome anyway. (IMHO of course!!)

---

### Post by craigtyson on 2007-08-13
> **viking777 said:**
> I've recently installed Gutsy (and like it a lot) I just spent some time with the solutions here trying to get the Huawei modem to work and absolutely none of them works if the OS is running when I plug in the modem. However if I plug it in before I start up,it is correctly detected and configured and ready to use, it needs no other scripts or commands or anything, just run wvdial and it connects. Plug it in when you are running though and no amount of 'rmmod-ing' will make it work??

Nearly there then.

What does lsusb tell you after plugging it in? I find I have to wait about 1-2 mins for "hot plug" to pickup the e220 (should that be a warmish plug then?)

PS whilte my brain is thinking, can you hot plug any other usb devices on your box?

C

---

### Post by kurund on 2007-08-17
I am having Huawei EC325. I have done all the settings as above. I am getting error mentioned below.

> user@ubuntu:/etc# wvdial hsdpa
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Aug 18 05:41:12 2007
--> Pid of pppd: 24641
--> Disconnecting at Sat Aug 18 05:41:12 2007
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

Any Help is highly appreciated.  I am using Ubuntu 7.04(Feisty).

Thanks in advance.

---

### Post by craigtyson on 2007-08-21
> **kurund said:**
> I am having Huawei EC325. I have done all the settings as above. I am getting error mentioned below.



Any Help is highly appreciated.  I am using Ubuntu 7.04(Feisty).

Thanks in advance.

From what I can google there are two possible issues, one is related to the ppp response file.  There is a link to an updated response patch earlier in the thread which may help.

C

---

### Post by victor9098 on 2007-09-15
Hi,

I had the same problems as you on my Huawei's hsdpa modem Model E220. The fix required a bit of messing, but everything works perfect now.

First try: [http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php) bare in mind, the settings are for "3" Ireland.

This is what I did:
Edit your wvdial.conf file via terminal. So just type 'sudo gedit' and try the following settings (you may need to tweak them for your location).

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 =
Area Code =
Phone = *99#
Username = any
Password = any
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 0
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1

I saved that file as 'wvdial.conf', (in 'file system - etc' folder).

Now make sure you have modem is connected, do a restart (I do for good practice). In your network settings make sure you set up a dial up connection via ppp0

Phone Number (as above)
Userame : User
(Next Tab)
Modem: select /dev/modem
(Next Tab)
Click the 1st and 3rd options

Now if you use Firestarter (like me) make sure you set up a ppp0 connection, this is also a good indication to see if your connecting to the internet as the ppp0 will show up on the list.

Restart your computer again (I know, crazy about my restarts)

Start Firestarter. Now try opening Terminal, type wvdial and hit enter! Hopefully you will have a connection. The light on your modem should stop blinking and just stay on (colour varies depending on connection quality). Try to avoid closing the terminal window, that tends to also shut down the connection! I just minimize it.

The above worked for me! Hope it works for you.

---

### Post by pinsky on 2007-09-15
Hy!
i've been trying to get my huawei 220 to work to, but i have a problem at the very begining. When i plug the modem in  the USB, the OS doesn't detect anything. The modem starts blinking, but it isn't eve recodnized as a storage device. I'm using Kubuntu 7.04.

When i plug a normal USB flas memory, it gets detected, and i've tried the modem on windows and it worked. 

I don't have an internet connection on that conmputor since huawei 220 is my only way to connest to the internet so i haven't yet downloaded any NTFS support from the repository. I don't know if that could have perhaps any connection with my problem.

If anyone can help or has the same problem, let me know.

---

### Post by Ashlord on 2007-09-17
Erm, for the Singapore folks out there using M1, here are my settings and they work.

Plug in your modem.
tail -f /var/log/messages and wait until you see your machine detect the USB modem.
'lsmod | grep usb' and kill everything there besides usbcore.
If usbserial or usb_storage exists there, use 'sudo rmmod usbserial', etc.
If it says something about in use by option, just 'sudo rmmod option'.
'lsusb' for device id.

In short, remove every damn thing you see in lsmod | grep usb other than the core.

Then 'modprobe usbserial vendor=0x12d1 product=0x1003'.

Spam 'ls /dev/ttyUSB*' or watch --interval=1 it.
Once you see the devices, the modem is ready.

Fire 'sudo wvdial hsdpa'

Open another window and run 'sudo route add default gw 10.64.64.64'.
Time to surf!!!

xxx@xxxxx:~$ cat /etc/wvdial.conf
[Dialer Defaults]
Phone = *99***16#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
ISDN = 0
Modem Type = Analog Modem



The number to dial seems to be different for various people. I have another friend using the PCMCIA card and his one dials *99***8#. I got my number from the VCMLite profile created in XP Network Connections.

One thing to note, if your set up screws up, make sure you remove the modem and kill all the remnant modules using rmmod.


sudo wvdial hsdpa
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*99***16#
--> Waiting for carrier.
ATDT*99***16#
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Tue Aug 28 02:14:49 2007
--> Pid of pppd: 6638
--> Using interface ppp0
--> local IP address 116.197.224.246
--> remote IP address 10.64.64.64
--> primary DNS address 202.79.127.166
--> secondary DNS address 202.65.247.151

---

### Post by Ashlord on 2007-09-17
> **pinsky said:**
> Hy!
i've been trying to get my huawei 220 to work to, but i have a problem at the very begining. When i plug the modem in  the USB, the OS doesn't detect anything. The modem starts blinking, but it isn't eve recodnized as a storage device. I'm using Kubuntu 7.04.

When i plug a normal USB flas memory, it gets detected, and i've tried the modem on windows and it worked. 

I don't have an internet connection on that conmputor since huawei 220 is my only way to connest to the internet so i haven't yet downloaded any NTFS support from the repository. I don't know if that could have perhaps any connection with my problem.

If anyone can help or has the same problem, let me know.

Hi Pinsky,

My modem behaved the same way as yours before I got it working. When I plug in the modem, it shows only usbserial used by option in lsmod | grep usb and only ttyUSB0 was present.

If I rmmod option, all the rest of the junk appears and gnome picks up the cd drive on the modem.

You may want to give it a try. Usually I just rmmod everything and then modprobe back usbserial and it works fine for me.

---

### Post by carlostdi on 2007-09-18
Please help...
Trying to get huawei e220 working on Ubuntu 7.04, I did this:
Installed huawei.tar.bz2
Then reseted the computer.
when started, He detcted the modem (the light is continuously turned blue, and when oppening firefox don't give me error, just keep trying... and trying... and never get to the page...
listing the USB I get this:
root@cs-laptop:/home/cs# ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2007-09-18 12:56 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2007-09-18 13:56 /dev/ttyUSB1
root@cs-laptop:/home/cs# 
Please can anybody help me... I feel I'm just getting there my can't reach the goal.- I'm a newbie

[http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)

---

### Post by Ashlord on 2007-09-20
What does your netstat -nr show?

---

### Post by Justin2 on 2007-10-01
I've had my Vodafone Huawei E220 working for quite a while already and my solution doesn't involve going anywhere near the terminal / command line.
Basically I use Ubuntu Ultimate 1.4 but it should also work on a standard Ubuntu 7.04 Feisty distro.
You will need to have the Gnome PPP (dial-up program) already installed (already installed as standard on Ubuntu Ultimate 1.4) 
First you must deactivate the sim-card code by using a cellphone. Put the sim-card back in Huwei E220 modem.
Then insert modem in USB slot before boot-up or before turning on your PC. (Important ! )
Then go to Applications > Internet > Gnome PPP.
Enter username and password (anything really).
Select setup button. Press Detect button (to automatically detect modem).
You can also change some settings in the options section, (not totally necessary) like select auto reconnect and selecting stupid mode.
Finally, just under where you entered your name and password, you must enter the dialling number (phone number). For Vodacom South Africa it is:  *99***16#.  If you don't know the number, then  have a look around the program for vodafone in windows (you'll find it somewhere under one of the settings).
Then just press connect.  (Just remember to insert the Modem well before boot-up, preferably before you switch on PC):)

---

### Post by rykel on 2007-10-01
> **Justin2 said:**
> I've had my Vodafone Huawei E220 working for quite a while already and my solution doesn't involve going anywhere near the terminal / command line.
Basically I use Ubuntu Ultimate 1.4 but it should also work on a standard Ubuntu 7.04 Feisty distro.
You will need to have the Gnome PPP (dial-up program) already installed (already installed as standard on Ubuntu Ultimate 1.4) 
First you must deactivate the sim-card code by using a cellphone. Put the sim-card back in Huwei E220 modem.
Then insert modem in USB slot before boot-up or before turning on your PC. (Important ! )
Then go to Applications > Internet > Gnome PPP.
Enter username and password (anything really).
Select setup button. Press Detect button (to automatically detect modem).
You can also change some settings in the options section, (not totally necessary) like select auto reconnect and selecting stupid mode.
Finally, just under where you entered your name and password, you must enter the dialling number (phone number). For Vodacom South Africa it is:  *99***16#.  If you don't know the number, then  have a look around the program for vodafone in windows (you'll find it somewhere under one of the settings).
Then just press connect.  (Just remember to insert the Modem well before boot-up, preferably before you switch on PC):)

i'll try tat in a zippy but would like to add tat the part abt plugging in the modem BEFORE even turning on the PC is applicable to Dapper as well, and is quite an irritant.    :lolflag:

---

### Post by dragon2611 on 2007-10-13
Heres the settings that worked for me on t-mobile UK using debian and wvdial (should work on ubuntu)

/etc/wvdial.conf
```


[Dialer pin]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 =AT+Cpin=12345


[Dialer tmob]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 =AT
Init3 = AT&FE0V1X1&D2&C1S0=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT




```

Replace 12345 with your pincode ;)

Then type

Wvdial pin if youve had the modem discconected this will pass the pin to the modem and let it initallize.

then type wvdial profilename (in my case wvdial tmob) to setup the connection.

I did try putting the numbers in common but i found the problem was the modem wouldn't dial out I think it needs a moment or to settle after taking the pin to find the network.etc so although this script is somewhat crude it seems to work.

Credit goes to whoever wrote it in the first place, I just moved things around a bit to get the pincode command to work :lolflag:

IMO its essential to have a pincode since its such a portable device and could quite easily be misplaced, at least a pincode offers some protection should someone find it.

---

### Post by mips on 2007-10-15
**[SIZE=4][COLOR=Red]Attention!!! Look at this:[/COLOR][/SIZE]**

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)
[https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)


This is a very simple to use gui client for linux. No messing around with wvdial config files etc. Install it and it works !

I do not know wether this works for non-vodafone networks but it is GPL'd and should be customiseable for other carriers if it does not work.

I got this to work on my first try with a Huawei E220 on the South African Vodacom netowrk.

---

### Post by daka on 2007-10-25
GREAT NEWS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I installed software mips referred to...............

 and it is AMAZING.... simple....after months of work and frustration for so many people....

Homage to the tekno-gurus!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Daka

---

### Post by Snille on 2007-10-26
Hi all,
For you who live in Sweden and have bought a "3G Tre" USB modem. 
The same type basically as used by Vodafone.
With the "Tre" as the internet provider.

I'm running Gutsy (7.10 desktop)
I installed the application suggested above, made some changes in the config file, and it works!

Close the Vodafone application,
The config file for the program is located: /home/username/.wvdail/profiles/vmc.cfg

Open the file and use the following config:
```

[connection]
username = *
use_custom_wvdial_profile = no
dns2 = 212.73.32.67
dns1 = 212.73.32.3
staticdns = yes
phone = *99#
connection = 3GPREF
wvdial_profile_name = PAP
password = *
apn = data.tre.se

[sms]
validity = maximum

[preferences]
exit_without_confirmation = no
mua = 
manage_secrets = yes
browser = 

```

Save, start application and connect.
Worked like a charm for me! :)

---

### Post by mizwete on 2007-10-26
> **mips said:**
> **[SIZE=4][COLOR=Red]Attention!!! Look at this:[/COLOR][/SIZE]**

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)
[https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)


This is a very simple to use gui client for linux. No messing around with wvdial config files etc. Install it and it works !

I do not know wether this works for non-vodafone networks but it is GPL'd and should be customiseable for other carriers if it does not work.

I got this to work on my first try with a Huawei E220 on the South African Vodacom netowrk.
Looks good, so good that i dowloaded and installed it !
But, there is a small annoyance... it doesn't work for me.
My E220 modem isn't even recognized at startup.
Kubuntu 7.10, kernel 2.22.14

---

### Post by daka on 2007-10-26
mizwete,

Do you use Gutsy?  If not I suggest you install it soon... it has solved a host of lingering problems for me!

The .deb file to download and install for Gutsy is the following:

  vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb

Make sure you install the correct .deb for your system

I have installed this Vodafone GUI on two laptops... and it has been a piece of cake! ... I was at the beginning of the learning curve about a year ago with Huawei E220 and this is REALLY good news for lots of people.

I'm no tekno-guru, but if you keep having problems find someone competent to advise you how to sort it out.  I suspect it will be fairly easy.

I have noticed that one laptop, the HP Pavilion ZT1185 it seems to (occasionally) still mistakenly recognize the Huawei as a cdrom device.  (This was a problem 2-3 distros ago and it looked solved)... However this does not prevent the program from working as it is intended.

Good luck

Daka

---

### Post by mizwete on 2007-10-27
Hello, yes, I do use Gutsy. I did a full install of Feisty on September 27, then I upgraded to Gutsy in October 12 (release candidate). From october 13 till october 24, I checked and upgraded every day. 
I downloaded and installed the   vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb, installed it on Oct. 21.

My main problem, besides the modem, is that now this notebook HP Compaq nx7300 is back at my father's home, so i can only phone him and have father types commands that I spell to him by phone, in a terminal. Of course, now he isn't able to reach the internet, so I'm currently unable to remotely fix his computer. If only he had sent the modem with the computer, I should have been able to check the installation. It wasn't the case.

Now, if nothing work, I will need to fly to him in december and see by myself. I am not happy about a trans-european 2,500 km x2 only because 150 grams of hardware deprives my family of communications. Yes, I know, it is complicated, sorry. ;-)

By the way ! How could he disable modem's SIMcard PIN' code with his 3G telephone ? I've read that it simplify the installation. His operator is Vodaphone in Portugal. Myself, I live in Belgium.

---

### Post by daka on 2007-10-27
Hi Mizwete

Sorry you have such a complicated situation with the laptop in Portugal etc.

With one laptop when I installed the Vodafone GUI it needed more dependencies installed, maybe three or four programs (dependencies)... so it was broken and needed some work to satisfy these dependencies. but it was easily solved.

also

1) to disable the pin you have to put the sim card in a normal mobile phone and disable it... each phone is different.. your dad can have a store help him if necessary.  The active "pin"  may explain the problems you are having... 

2) better to do a fresh install from cd or dvd than the update method, I think... so when you have the chance..... re-install Gutsy fresh.

3) If the laptop is in Portugal this is a problem especially if your dad doesn't know his way around Linux.  I have friends in Portugal in different places who may help him.  Let me know where he is in Portugal.  Portugal has more linux-gurus per capita than many other countries!

4) Instead of going to Portugal maybe you could have the laptop and modem sent to you, and you send them back once you sort them out... the cost would be less than the airfare.

Probably the best bet is finding a Linux guru in Portugal to help him out.  Let  me know if you want any help with that idea.

I know people in Castelo Branco and Lisboa... and they know people all over Portugal who know Linux quite well.

(What kind of mobile phone does your dad have?  If it is a Nokia 3G model he should be able to easily use that as a modem until the Huawei is sorted.  I use a Nokia N80 and a Nokia 6234, and they are a piece of cake to configure with the usb cable.  Bluetooth is more problematc.  I can help with those instructions if you wish.  I am sure other mobiles work also but Nokia has a reputation of being easy to configure and I have experience with them.

Daka

---

### Post by Nicu Alecu on 2007-10-28
> **daka said:**
> GREAT NEWS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I installed software mips referred to...............

 and it is AMAZING.... simple....after months of work and frustration for so many people....

Homage to the tekno-gurus!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Daka

Well, I installed it too! I finally got to the point where I can chage settings (I'm on Orange, not Vodafone!) but ... it won't connect. Actually it doesn't authenticate properly (understandable, it's another 3G network).
Some info of where to change default connection settings would be great, cause it's not just a simple issue of APN, uname & pass ...

*Later edit:*
Forgot to mention: using E220 on ORANGE network, with Gutsy on a brand new DELL.

---

### Post by daka on 2007-10-28
Nicu

Snille .... see below.... connected with non-vodafone network in Sweden and he gives some config info in his thread... maybe send him a message if you need more help... he is the only person I see who has provided some evidence of experience with non-vodafone config.

- any chance of switching to Vodafone where you live?

- are you running Gutsy?... if not, my advice is to install it asap

daka

---

### Post by mizwete on 2007-10-28
Good evening Daka,
millions of thanks for your answer and your proposition.
1) I've already told my father to disable the PIN code of card. I hope it will be done in a few days.
2) When that will be OK, I'll try again from the beginning. We'll see if it'll be working then.
3) Just in case, but let me hope we won't be obliged to such remedies, my father lives in Algarve, near Faro city, exactly in city of Tavira. 5 km from center of Tavira. Eventualy, he could ride.
4) Thanks to low-cost flight companies, the trip from Belgium to Faro isn't expensive, 200 &#8364; for a 2-way flight bought in september 2007.

I will let you informed about the developements...
Thanks again, you're such a nice gentleman.

Mizwete

---

### Post by Nicu Alecu on 2007-10-29
Thanks for pointing me to Snille, I'll try to contact him.
To answer your questions:
1. I have no intention of switching to Vodafone whatsoever (a lot of reasons for that, network coverage being the most important of all).
2. Yes, I'm on fresh-installed Gusty and (almost) everything is working ok. I said almost cause there are a few things that are stil hanging on Gutsy (like using vmware instead of virtualbox - no usb support on the latter, the relatively big lag between loging in and having access to gnome, and this annoying 3G issue, of course).

_Later (waaay later) edit:_
I got it working using gnome-ppp ... somehow unexpected, but I'm writing this on it.
My guess is that since I managed to deliver the right AT commands using gnome-ppp, it shouldn't be too difficult to do it using the vodafone thingy. I'll test it tommorow, cause right now it's party time (no, I'm not throwing a party in celebration of my E220 finally working, it's just my brother-in-law's birthday :) )

---

### Post by mips on 2007-10-31
> **mizwete said:**
> Looks good, so good that i dowloaded and installed it !
But, there is a small annoyance... it doesn't work for me.
My E220 modem isn't even recognized at startup.
Kubuntu 7.10, kernel 2.22.14

When you plug the E220 into the USB port does it pop up on the desktop as a flash drive with files on it ???

It should at least do this, you could also use the **lsusb** command to list attached usb devices.

It takes about 30-60sec for the modem to settle down once you plugged it in.

---

### Post by mizwete on 2007-11-01
Hello all,
the modem Huawei E220 isn't recognized. NOT EVEN as a disk drive.
lsusb doesn't show ANY device connected to an USB port ( but only a Belkin device... and I swore, nothing but the Huawei is plugged in a USB port).

Even after a        modprobe usbseriel vendor=0x12d1 product=0x1003
no matter how much times the modem is unplugged and plugged again.

In such circumstance, I believe that I should incriminate the modem itself, anyway, it HAS functioned properly (under window XP) a few monthes ago.

Kubuntu 7.10, kernel 2.6.22

Any suggestions ?
I must add that all this doesn't prevent the modem to blink BLUE after it's been plugged 30 or 40 seconds on.

---

### Post by mizwete on 2007-11-04
[COLOR="****Red"]SOLVED ![/COLOR]
Here are the commands needed to "finally" have the Huawei E220 working and connecting 
Open a terminal
sudo -i
modprobe usb-ohci
modprobe usb-uhci
rmmod usb-storage
rmmod usb-serial
lsusb
modprobe usbserial vendor=0x12d1 product=0x1001
modprobe usbserial vendor=0x12d1 product=0x1003
# Unplug the modem
#sleep 20 WAIT 20 seconds
# Plug the modem in

# sleep 30 WAIT 30 seconds for the modem to be recognized
#" Construction of needed tty's"
# HERE ARE THE 3 INSTRUCTIONS I HAD TO TYPE

mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1
mknod /dev/ttyUSB2 c 188 2
# TO CHECK IT IS DONE
ls -la /dev/ttyUSB*-

# NOW WE HAVE 3 tty USB0, USB1 and USB2
# Launch wvdial
wvdial hsdpa

AND IT HAS WORKED

I still don't understand why a brand new kernel 2.6.22-14 hasn't properly made the 3 USB nodes. Now I have to verify if all the commands must be entered at each connection or if once is enough. Just in case, I made a script and mailed it to my father.

Once again, I would like to thank everybody for their support, special thanks to DAKA and MIPS, without you I guess I never would have made it.
Mizwete and his happy father.

---

### Post by cybertrekman on 2007-11-05
I´m completely new to Ubuntu. I was happy that the Gutsy install seemed so effortless on my ThinkPad T60, but setting up some peripherals like the Huawei E220 is driving me crazy, mainly because I have no idea what´s going on. Following the prev. instructions I get:

root@alexander-T60:~# sudo -i
root@alexander-T60:~# modprobe usb-ohci
FATAL: Module usb_ohci not found.
root@alexander-T60:~# modprobe usb-uhci
FATAL: Module usb_uhci not found.
root@alexander-T60:~# rmmod usb-storage
ERROR: Module usb_storage exist in /proc/modules
root@alexander-T60:~# rmmod usb-serial
ERROR: Module usb_serial does not exist in /proc/modules
root@alexander-T60:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 12d1:1003  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
root@alexander-T60:~# modprobe usbserial vendor=0x12d1 product=0x1001
root@alexander-T60:~# modprobe usbserial vendor=0x12d1 product=0x1003

I have no idea what this means and the KPPP dialer won´t light up the connect button so I cannot use the E220 device.

Can someone please lead me through, in baby steps, what I need to do to make the E220 work:confused:

PS: I have a blue flashing light that I presume indicates that it recognises the 3 network in Australia.

---

### Post by mizwete on 2007-11-06
> **cybertrekman said:**
> I´m completely new to Ubuntu. I was happy that the Gutsy install seemed so effortless on my ThinkPad T60, but setting up some peripherals like the Huawei E220 is driving me crazy, mainly because I have no idea what´s going on. Following the prev. instructions I get:

root@alexander-T60:~# sudo -i
root@alexander-T60:~# modprobe usb-ohci
FATAL: Module usb_ohci not found.
root@alexander-T60:~# modprobe usb-uhci
FATAL: Module usb_uhci not found.
root@alexander-T60:~# rmmod usb-storage
ERROR: Module usb_storage exist in /proc/modules
root@alexander-T60:~# rmmod usb-serial
ERROR: Module usb_serial does not exist in /proc/modules
root@alexander-T60:~# lsusb
Bus 005 Device 001: ID 0000:0000  
[COLOR="Red"]**Bus3 Device 004: ID 12d1:1003**[/COLOR]  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
root@alexander-T60:~# modprobe usbserial vendor=0x12d1 product=0x1001
root@alexander-T60:~# modprobe usbserial vendor=0x12d1 product=0x1003

I have no idea what this means and the KPPP dialer won´t light up the connect button so I cannot use the E220 device.

Can someone please lead me through, in baby steps, what I need to do to make the E220 work:confused:

PS: I have a blue flashing light that I presume indicates that it recognises the 3 network in Australia.

[COLOR="Red"]**Bus3 Device 004: ID 12d1:1003**[/COLOR]  THAT line means that the modem IS recognized, at least partially. So... at this stage you need to type:
mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1
mknod /dev/ttyUSB2 c 188 2

The purpose of those 3 instructions is to make kppp, or wvdial, or any other comm. program able to link to the modem.
To verify it, you type:
ls -la /dev/ttyUSB*-
IF you see 3 lines with ".../ttyUSB0..."  "...//ttyUSB1..."  ".../ttyUSB2..."
OR if you got messages such as:
"dev .../ttyUSB0..." already exists
"dev .../ttyUSB1..." already exists
"dev .../ttyUSB2..." already exists    then it is GOOD.
It means that you are ready to connect.

Now all you have to do is to launch A PROPERLY CONFIGURED kppp OR wvdial in a terminal.
For configuring wvdial, you need to EDIT the file named wvdial.conf.
Please, look at previous posts, there are many examples of working files wvdial.conf

When it is done, you only need to type in a command line:
wvdial hsdpa
the connection will last as long as you keep the terminal's window alive.

Here is an example wvdial.conf
# wvdial for Vodacom Data. Created by Tazz_tux
 # Version 1.0
 
 # Change Log:
 #
 # Added support for HSDPA.
 # Added Headers and version control.
 
 [Dialer Defaults]
 Phone = *99***1#
 Username = username
 Password = password
 Stupid Mode = 1
 Dial Command = ATDT
 
 [Dialer hsdpa]
 Modem = /dev/ttyUSB0
 Baud = 460800
 Init2 = ATZ
 Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 
 Look at lines
Username=     insert here your user name
Password=   insert here your password  it may depend of your operator whow I don't know

---

### Post by albaz3245 on 2007-11-07
Thanks Getelman, i'm new to Ubuntu , i'll try your method and then i will report

---

### Post by cybertrekman on 2007-11-08
Thanks Mizwete, but still doesn´t work. I get this now:

alexander@alexander-T60:~$ sudo -i
root@alexander-T60:~# modprobe usb-ohci
FATAL: Module usb_ohci not found.
root@alexander-T60:~# modprobe usb-uhci
FATAL: Module usb_uhci not found.
root@alexander-T60:~# rmmod usb-storage
ERROR: Module usb_storage does not exist in /proc/modules
root@alexander-T60:~# rmmod usb-serial
ERROR: Module usb_serial does not exist in /proc/modules
root@alexander-T60:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 009: ID 12d1:1003  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
root@alexander-T60:~# modprobe usbserial vendor=0x12d1 product=0x1001
root@alexander-T60:~# modprobe usbserial vendor=0x12d1 product=0x1003
root@alexander-T60:~# mknod /dev/ttyUSB0 c 188 0
mknod: `/dev/ttyUSB0': File exists
root@alexander-T60:~# mknod /dev/ttyUSB1 c 188 1
mknod: `/dev/ttyUSB1': File exists
root@alexander-T60:~# mknod /dev/ttyUSB2 c 188 2
mknod: `/dev/ttyUSB2': File exists
root@alexander-T60:~# ls -la /dev/ttyUSB*-
ls: /dev/ttyUSB*-: No such file or directory

I think I´ve got the wvdial.conf changed as you suggested, but still no connection:confused:.

M$ Windoze at least doesn´t require all this commands in a terminal rubbish - sorry just feeling v.frustrated and getting fed up with Ubuntu as I´m also having trouble configuring Cisco VPN and getting citrix to work.

---

### Post by mizwete on 2007-11-09
Maybe you can dowload the attached file:
1) some commands to try and see what you get
2) a little script for connecting
I suggest that you try it in conjunction with the command
tail -f /var/log/messages
entered in another terminal ( Ctrl + Alt + F2 ; login; password )

---

### Post by cybertrekman on 2007-11-10
Thank you so much for trying to help, but it still doesn´t work.


# TEST
# START WITH MODEM UN-PLUGGED
# OPEN A TERMINAL
sudo -i
<- enter password

ls -la /dev/ttyUSB*
***********   WHAT MESSAGES ARE DISPLAYED ?
root@alexander-T60:~# ls -la /dev/ttyUSB*
ls: /dev/ttyUSB*: No such file or directory


lsusb
***********  WHAT MESSAGES ARE DISPLAYED ?mod
root@alexander-T60:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  

# PLUGG THE MODEM IN
tail -f /var/log/messages

mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1
mknod /dev/ttyUSB2 c 188 2

modprobe usbserial vendor=0x12d1 product=0x1003

# UNPLUGG THE MODEM
# WAIT 10 SECONDS
# PLUGG THE MODEM IN

tail -f /var/log/messages

ls -la /dev/ttyUSB*
************* WHAT ARE THE MESSAGES DISPLAYED ?
crw-r--r-- 1 root root 188, 0 2007-11-10 19:01 /dev/ttyUSB0
crw-r--r-- 1 root root 188, 1 2007-11-10 19:02 /dev/ttyUSB1
crw-r--r-- 1 root root 188, 2 2007-11-10 19:03 /dev/ttyUSB2


lsusb
************* WHAT ARE THE MESSAGES DISPLAYED ?
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 12d1:1003  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  

# WE TRY A CONNECTION ?
# THEN WVDIAL
wvdial hsdpa 
************* WHAT ARE THE MESSAGES DISPLAYED ?
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttyUSB0: No such device
WvDial<Err>: Cannot open /dev/ttyUSB0: No such device
WvDial<Err>: Cannot open /dev/ttyUSB0: No such device

-----------------------------------------------------------
# Before launching the script, open a terminal by
Ctrl + Alt + F2
log in
password
(To retreive your graphical display, simply type
Ctrl + Alt + F7)
In the terminal, type 
tail -f /var/log/messages
look at the lines displayed

(I´ve looked at the display but it means nothing to me)

then, go to your graphical display ( Ctrl + Alt + F7)
launch the script below AS ROOT

(Im not sure what this means. I copied and pasted the text into the terminal)

# SCRIPT DE CONNECTION
#!/bin/sh
rmmod option
sleep 4s
rmmod uroot@alexander-T60:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 12d1:1003  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
sbserial
sleep 4s
mknod /dev/ttyUSB0 c 188 0
mknod /dev/ttyUSB1 c 188 1
mknod /dev/ttyUSB2 c 188 2
sleep 1s
modprobe usbserial vendor=0x12d1 product=0x1003
sleep 10s
ls -la /dev/ttyUSB*
sleep 10s
ls -la /dev/ttyUSB*

wvdial hsdpa

(It still displays:)
root@alexander-T60:~# wvdial hsdpa
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttyUSB0: No such device
WvDial<Err>: Cannot open /dev/ttyUSB0: No such device
WvDial<Err>: Cannot open /dev/ttyUSB0: No such device

If I type ´lslsusb´ it displays:
root@alexander-T60:~# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 12d1:1003  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  





At least now when I plug the  the modem in it brings up a box with the data in the modem displayed.

---

### Post by viking777 on 2007-11-10
Have you tried this?

[http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux](http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux)

It works for me and no need to use all this terminal trickery.

NB I haven't read the whole thread here so forgive me if this has already been mentioned.

---

### Post by cybertrekman on 2007-11-10
Thanks but I cant find the application through the normal add/remove button so went to the vodafone website and loaded it from there. It tells me its loaded OK but when i try to open the application the task bar at the bottom shows it trying to open but then it disappears. Looking at the download its designed for Feisty and appears not to work in Gutsy. Curiously its not in the list of installed applications under the add/remove button, but is listed as an application under the internet tab........this really is driving me crazy!!! 
Its almost enough to send me back to Windoze, at least there I can just plug it in and it works.

---

### Post by mips on 2007-11-10
> **cybertrekman said:**
> Thanks but I cant find the application through the normal add/remove button so went to the vodafone website and loaded it from there. It tells me its loaded OK but when i try to open the application the task bar at the bottom shows it trying to open but then it disappears. Looking at the download its designed for Feisty and appears not to work in Gutsy. Curiously its not in the list of installed applications under the add/remove button, but is listed as an application under the internet tab........this really is driving me crazy!!! 
Its almost enough to send me back to Windoze, at least there I can just plug it in and it works.

It does work in Gutsy as I have used it in gutsy, if I recall correctly it migh have about 3 or so dependencies which it tells you about during the installation.

It does not appear under add/remove or synaptic as it is not in the repos. You downloaded a .deb file which you installed. You can however remove it if you want from the cli.

What wrong with the location under Internet ? You can always move it you know.

---

### Post by cybertrekman on 2007-11-11
Thanks to those who have tried to help,

Its nice to know it can work in Gutsy and yes I see there are dependencies, but the web page I was looking at was no help in identying where they could be downloaded.
 
My installed programs list says I have Python v2.5 as nothing else was listed under add/remove programs I assumed this was all I needed. :confused:

You wrote:
You can however remove it if you want from the cli.
What wrong with the location under Internet ? You can always move it you know. 

I have no idea what you mean by these comments. 

Whats a cli and what does it do?

What location are you referring to and why do I need to move whatever it is you are referring to?:confused:

No wonder more people don´t use linux, its too damn hard to make things work, so M$ will continue to make a fortune from people who just want an operating system and peripherals that plug in and work. I share ubuntu´s view of the world but I have no IT training and feel overwhelmed by the skill level that seems to be needed to just do simple tasks. For goodness sake I just want a USB modem to work, how hard should that be.

---

### Post by pkchukiss on 2007-11-11
Hi guys, great thread here; but I'm still wrestling with the settings. Here's what I get when I run wvdial:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Sun Nov 11 20:49:19 2007
WvDial<Notice>: Pid of pppd: 9183
WvDial<*1>: Disconnecting at Sun Nov 11 20:49:19 2007
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 2)


Here's my wvdial.conf:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 =
Area Code =
Phone = *99#
Username = any
Password = any
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 0
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1

:(

My service provider is SingTel Singapore, so the APN name is "internet". As far as I know, they don' authenticate via username and password. At any rate, I'm stumped by this problem. Thanks a lot in advance for your help!

---

### Post by viking777 on 2007-11-12
> **cybertrekman said:**
> Thanks to those who have tried to help,

Its nice to know it can work in Gutsy and yes I see there are dependencies, but the web page I was looking at was no help in identying where they could be downloaded.
 
My installed programs list says I have Python v2.5 as nothing else was listed under add/remove programs I assumed this was all I needed. :confused:

You wrote:
You can however remove it if you want from the cli.
What wrong with the location under Internet ? You can always move it you know. 

I have no idea what you mean by these comments. 

Whats a cli and what does it do?

What location are you referring to and why do I need to move whatever it is you are referring to?:confused:

No wonder more people don´t use linux, its too damn hard to make things work, so M$ will continue to make a fortune from people who just want an operating system and peripherals that plug in and work. I share ubuntu´s view of the world but I have no IT training and feel overwhelmed by the skill level that seems to be needed to just do simple tasks. For goodness sake I just want a USB modem to work, how hard should that be.

A cli is a command line interface - don't go there if you are not comfortable with Linux. I am comfortable with Linux and still detest it!!

As for it 'just working' it took me 9 months of trying before I got mine to work, although now it does 'just work'.

Before I used the vodafone linux driver I used kppp and I too had this ppp message for ages. I find it difficult to remember now but I think I solved it by changing the settings in kppp from Automatic to manual dns and adding a couple of dns servers, although now I am using the vodafone linux driver I no longer need this. 

Another problem is that I really cant comment on your wvdial.conf since the settings for Singapore will not be the same as here in the UK. Are you sure your settings are correct? For instance your username and password are set to'any' whereas mine are both set to 'web'.

I also have a couple of init lines that yours doesn't, this is what it looks like:

[Dialer Defaults]
Phone = *99***16#	
Username = web
Password = web
Stupid Mode = 1
Dial Command = ATDT
Auto DNS = 0
Modem = /dev/ttyUSB0

[Dialer huawei]
Buad = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = at+cops=3,2
INIT8 = AT+CGDCONT=1,"IP","internet"
ISDN = 0
Modem Type = Analog Modem

Maybe you could try incorporating a couple of those and see if they work.

---

### Post by Jeukku77 on 2007-11-13
I quess I'm in trouble.

I'm using usb-disk to boot my computer so I can't remove usb-storage module. Huawei keeps getting recognized as cd-rom drive and I've tried to run huaweiAktBbo-i386.out program which sometimes works (meaning that ttyusb* gets created).

the real problem might be that for some reason device gets resetted after few seconds so ttyUSB devices arent working.

any suggestions?

syslog:
Nov 13 08:41:45 jeukunlaptop kernel: usb 5-1: new full speed USB device using uhci_hcd and address 20
Nov 13 08:41:46 jeukunlaptop kernel: usb 5-1: configuration #1 chosen from 1 choice
Nov 13 08:41:46 jeukunlaptop kernel: scsi23 : SCSI emulation for USB Mass Storage devices
Nov 13 08:41:51 jeukunlaptop kernel: scsi 23:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Nov 13 08:41:51 jeukunlaptop kernel: sr0: scsi-1 drive
Nov 13 08:41:51 jeukunlaptop kernel: sr 23:0:0:0: Attached scsi generic sg2 type 5
Nov 13 08:42:01 jeukunlaptop kernel: usb 5-1: reset full speed USB device using uhci_hcd and address 20
Nov 13 08:42:02 jeukunlaptop kernel: usb 5-1: reset full speed USB device using uhci_hcd and address 20
Nov 13 08:42:02 jeukunlaptop kernel: usb 5-1: USB disconnect, address 20

---

### Post by cybertrekman on 2007-11-13
I changed the KPPP settings to show modem as ttyUSB0 and now I have this:

WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Tue Nov 13 20:31:46 2007
WvDial<Notice>: Pid of pppd: 24203
WvDial<*1>: Disconnecting at Tue Nov 13 20:31:46 2007
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 2)

Any ideas?

---

### Post by CrackersKeenan on 2007-11-13
Hey Coruba, did you have any luck with fixing  this?  I'm getting a similar problem (and I'm also in Australia, trying to connect to my 3 wireless broadband).

---

### Post by viking777 on 2007-11-14
I think the success or otherwise of this device is also kernel dependent. I am using 2-6-22-14 and it seem to work with that. I also installed Linux Mint 3.0 a couple of weeks ago which uses 2-6-20 and it worked 'out of the box' with that using the Gnome ppp tool.

Of course upgrading kernels or installing new os's might bring more problems than it takes away so only you can decide if you want to go down that road.

Did you try the manual DNS hack?
Open kppp
click 'configure'
On the 'Accounts' tab highlight your account entry and click 'edit'
On the 'DNS' tab select the 'Manual' radio button.
Type the DNS server address in the Dns window then click the 'add' button
OK out and try again.

NB according to google the singtel dns servers are 165.21.83.88 and 165.21.100.88 although you could use any local dns server address that you are aware of.

Edit. One more thing that sprang to mind is that while I was trying to get my modem to work another thing I did was to remove the password from the sim card (it is not absolutely essential but it removes one extra complication). You can do this by taking it out of the device and putting it into a mobile phone and using the phone to remove the password or you can use at commands in a kppp terminal. Unfortunately I can't remember the exact command and I have lost the notes I had on it but the command 'at+clck' rings a bell. It is not guaranteed to work but it is another thing to try.

---

### Post by CrackersKeenan on 2007-11-18
Hi All,

I finally got mine working, but I had to connect it to a windows machine to get the card initialised or something.  I did the modprobe commands and pretty much have a standard wvdial.conf.  I'm in Australia (Canberra actually) and am with three mobile broadband.  If anyone else who is with 3 australia is having trouble then try the windows machine approach.

Thanks to everyone for the help.  The is a great online resource!

---

### Post by daka on 2007-11-20
I have been on a long and winding learning curve with the Huawei E220 modem for the last 9 months.  I have used it on three laptops, maybe 20 distros, and I have also figured out how to connect to 3G via my Nokia mobile phone (USB cable).  You get the same connection via mobile phone modem, with much less hassle (if it's a Nokia 3G).  Also sometimes I don't have a connection through the Huawei (I live on a mountain in Spain and the coverage is unpredictable) but I DO if I use the phone.... another mystery for me!.

General advice:

Disable Wifi and Ethernet as these can interfere with Huawei.
Go to System Settings / Network Settings and disable Ethernet and Wireless. Make sure that you select "configure the interface" and that you do NOT have a check in "activate when computer starts"...or else your distro just may ignore you and reset the ethernet and wifi settings.

Disable the pin

To summarize here are the three connection methods I use and I hope they are helpful to someone.

1 -  Huawei E220 using Vodafone Mobile Connect Card software for Linux (GUI)

2 -  Huawei E220 without using Vodafone Mobile Connect card software

3 -  Mobile Phone Modem (USB cable)
-----------------------------------------------------------------------------------------------

1 -  Huawei E220 using Vodafone Mobile Connect Card software for Linux (GUI)

The original link that I found with the Vodafone Mobile Connect card is this one:  [http://ubuntuforums.org/private.php?do=newpm&pmid=402764](http://ubuntuforums.org/private.php?do=newpm&pmid=402764)


Some people have downloaded and configured the vodafone mobile connect-card software making some modifications if their provider is not Vodafone...

Here is the link to download the software.....it is an extremely simple and useful GUI if you can configure it for your provider.  It works perfectly with Vodafone and I have seen people in the forum who claim to have modified the software a bit for other providers ("3" for sure..also Orange and  TMobile UK -see page 4 of this thread).... I suggest you try to find someone who has actually configured the program for your provider.... I am sure there are a few success stories:

Download available from:

[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=9](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=9)

*** This software is as easy and simple as the windows software.... no fiddling with wvdial.conf!!!!!!!!.. plug and play  (if you have Vodafone)
__________________________________________________________________-

2 -  Huawei E220 without using Vodafone Mobile Connect Card software


(Deactivate the pin by putting the card into any phone and going through the process)

You can edit the /etc/wvdial.conf file as follows:

[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","ac.vodafone.es";

plug in Huawei
then in terminal enter ... sudo modprobe -r ehci_hcd    (to recognize modem)
restart computer with modem plugged in ... and....
in terminal, enter...... wvdial hsdpa

you should be happily connected

(you will need to change some of the info from my vodafone to your provider's info.... i.e username / password / "ac.vodafone.es" / and the number to dial)
--------------------------------------------------------------------------------------------------------

3 -  Mobile Phone Modem (USB cable)

(If you are working hard at configuring the Huawei and running into problems I suggest you try to get the coverage temporarily through a mobile phone as modem.... you may be less frustrated during the process)


An easy option, which I revert to if I have any problems with the Huawei, is connecting through my mobile phone (Nokia) via usb cable... 

(Deactivate the pin by putting the card into any phone and going through the process)

you simply have to edit the /etc/wvdial.conf file as follows:

[Dialer nokia]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyACM0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = USB Modem
Init5 = AT+CGDCONT=1,"IP","ac.vodafone.es";

...........then in a terminal enter wvdial nokia.... and you should be connected.... this works with other phones, but I understand that Nokia is most cooperative

I hope this helps someone

Daka

---

### Post by mips on 2007-11-22
If you have manage to use the Vodafone Mobile Connect Card driver for Linux on networks other than vodafone (Orange, 3, Mtn, TMobile etc) could you please post your config file here so others could benefit as well.

It would be nice to get configs for other networks as this software is really user friendly and efficient.

---

### Post by daka on 2007-11-22
Hi

I have only personally connected to Vodafone with this software (Vodafone Connect Card) ... some people  in this thread have indicated that they have had success with "3"... orange and TMobile.... maybe it would help many others if they provided specifics about how they got  the modem  working both with the Huawei on it's own and with the GUI....i.e. wvdial.conf files and also tweaks to the Vodafone Connect Card GUI!!!  

Daka

---

### Post by daka on 2007-11-22
This thread is extremely active.... many people viewing... suggesting that the Huawei E220 is being sold a lot, and many people are trying to configure it, "recreating the wheel".

I am proposing the following to help minimize the frustration and suffering of many people:

Maybe it would help many others who are struggling if we provide one document with all of the wvdial.conf files for the different networks in different countries.. and if  we provided any additional  specifics about how the modem was configured both with the Huawei on it's own if that's how you connect, and with the Vodafone Mobile Connect Card GUI....i.e. wvdial.conf files and also tweaks to the Vodafone Connect Card GUI!!!

If you are willing to send me a personal email with your wvdial.conf file, if you use one, and the name of your country and service provider, along with any other information on how you may have configured the "Vodafone Connect Card Software" for another (non-Vodafone) network/provider I am willing to assemble and keep updating a single document and referring or pointing people to it in the threads.

Thanks

Daka

---

### Post by Loranga on 2007-11-22
Anyone here using 3 Sweden PCMCIA card and have managed it to work?

---

### Post by daka on 2007-11-22
HOW TO install "Vodafone Mobile Connect Card Driver" software


The software has been designed by a Vodafone R and D group .. they are not married to any platform or operating systems... they seem happy to have the software used by people who connect to other service providers too.


***  Also ... in case  you need more help with specific problems that need configuring there is a small expert forum for the Vodafone Mobile Connect Card software at this address:

[https://forge.vodafonebetavine.net/forum/forum.php?forum_id=20](https://forge.vodafonebetavine.net/forum/forum.php?forum_id=20)

***  This software works with the Huawei E220 and also with the PCMCIA modems from what I gather ***

***  Some people are reporting that it works also with service providers other than Vodafone ..  Could they please pass on any information they have about what they  did to get the software working with their provider.... (looks like TMobile, 3 and one other have been mentioned)... sounds like simple fixes, but I have no personal experience as my provider is Vodafone

***  You can send an SMS from your computer
***  You do not have to modify the /etc/wvdial.conf file at all!!!!!
***  You do not have to enter the terminal at all .. after installation a red vodafone icon will be in the applications menu and can be moved to the panel

HOW TO.. install the Vodafone Mobile Connect Card software...

1 -visit:  [https://forge.vodafonebetavine.net/projects/vodafonemobilec](https://forge.vodafonebetavine.net/projects/vodafonemobilec)
        
2 -Download the .deb file  vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb

then

3 -sudo apt-get install python-all

then

There are 3 missing dependencies for the GUI

python-twisted, python-pysqlite2, python-serial

so

4 - sudo apt-get install python-twisted python-pysqlite2 python-serial

then.. go to the folder that has your downloaded "Vodafone Mobile Connect Card driver"

and

5 - dpkg -i vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb

6 - with Huawei plugged in as root enter ..  modprobe -r ehci_hcd   .. and restart


The GUI is self-explanatory.... out of the box... Huawei works really well

You may still get the annoying pop-up when the huawei is incorrectly identified as a usb stick "Connect Box".. but this doesn't affect the modem at all.. you can just get rid of it... eject etc.

I hope I have not missed or messed anything .. I will edit if necessary

Good Luck

Daka

---

### Post by LadZh on 2007-11-24
> **pkchukiss said:**
> Hi guys, great thread here; but I'm still wrestling with the settings. Here's what I get when I run wvdial:

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Sun Nov 11 20:49:19 2007
WvDial<Notice>: Pid of pppd: 9183
WvDial<*1>: Disconnecting at Sun Nov 11 20:49:19 2007
WvDial<*1>: The PPP daemon has died: pppd options error (exit code = 2)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: I guess that's it for now, exiting
WvDial<Notice>: The PPP daemon has died. (exit code = 2)


Here's my wvdial.conf:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 3600000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 =
Area Code =
Phone = *99#
Username = any
Password = any
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 0
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1

:(

My service provider is SingTel Singapore, so the APN name is "internet". As far as I know, they don' authenticate via username and password. At any rate, I'm stumped by this problem. Thanks a lot in advance for your help!

I had exactly the same error message. 
In my case the issue resolution was - I just needed to make sure that the symbolic link 

/etc/ppp/peers/wvdial 

shows to the real existing file wvdial.distrib

I have removed the old wvdial symbolic link and created the new one 

cd /etc/ppp/peers/

rm wvdial

ln -s /etc/ppp/peers/wvdial.distrib wvdial

This has solved the problem for me.

---

### Post by mizwete on 2007-12-01
Hello to all, and once again I would like to express my gratitude to all friends for their help.
We have finally found that a faulty usb cable was responsible for more than a month of errors and headaches.

Now, I confirm, the Huawei E220 works correctly.

Thanks again.

Here is the wvdial.conf Used for connecting in PORTUGAL

[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","internet.vodafone.pt";

---

### Post by karanga on 2007-12-02
Running Ubuntu Gutsy & Vodafone UK HUAWEI E220 USB Modem

Software: Vodafone Mobile Connect card Driver for Linux 1.99.7 [https://forge.vodafonebetavine.net/frs/download.php/58/vodafone-mobile-connect-card-driver-for-linux_1.99.7_all.deb](https://forge.vodafonebetavine.net/frs/download.php/58/vodafone-mobile-connect-card-driver-for-linux_1.99.7_all.deb)

Steps I took to get connected:

Install Dependancies

[B]sudo apt-get install python-all
sudo apt-get install python-twisted python-pysqlite2 python-serial[/B]

install Vodafone Mobile Connect card Driver for Linux 1.99.7 deb


Insert the card and then run the application by navigating to

**Applications - Internet - Vodafone Mobile Connect card for Linux**

Once your card has been detected and the connect button has turned green click 

**Tools - Preferences** within the Vodafone Mobile Connect window

Change the id and password to web as you aren't connecting to Vodafone ES 

id = web
pw = web
APN host =  internet
DNS: 212.73.32.3
        212.73.32.67

With a bit of luck that should be you connected.

I did have to connect the card a couple of times until Vodafone UK appeared and not Vodafone ES. Once setup the card performed as well as it does under Windows and doesn't appear to be as flaky when connecting.

I had also tried the following before running through the steps above so if you can't connect after follwing the steps above try the following:

**sudo modprobe -r ehci_hcp**
restart your computer

make sure you are a member of the dip group

check by typing the following into a terminal session

**groups   **

If you aren't a member of the dip group type the following into a terminal session

**sudo addgroup your_username dip**

I wish other companies were as forward thinking as Vodafone. I'm really impressed with this project.

---

### Post by mohdshakir on 2007-12-06
For those who has not been able to configure their Huawei E220, or simply too lazy to install the Vodafone software, you can try this script that works flawlessly for me. The solution is discussed @ my website [http://www.mohdshakir.net/2007/12/05/huawei-e220-in-gutsy-gibbon-kubuntu](http://www.mohdshakir.net/2007/12/05/huawei-e220-in-gutsy-gibbon-kubuntu), : 

```
#!/bin/bash
 
sudo modprobe -r uhci_hcd
sudo modprobe uhci_hcd
 
echo "Waiting kernel to detect modem device"
 
# Wait till the kernel recognizes our E220
while true; do
 
        # Read log
        tail -n 20 /var/log/messages  > access.history
        sleep 1
        tail -n 20 /var/log/messages  > access.current
 
        LOG=`diff access.history access.current | grep ">" | tr -d ">"`
 
        # Check if it is detected
        if [[ "$LOG" =~ "converter now attached to ttyUSB1" ]]; then
                echo "Modem device detected, dialing..."
                # If it is, get out of the loop immedietly
                break
        fi
done
 
rm access.history access.current
 
# Start dialing
sudo wvdial Celcom3G
```

---

### Post by mizwete on 2007-12-07
For those who had some problems with dns ( domain name server ) in Portugal,

here are some usefull dns address located in Portugal

Portugal

    [COLOR=Blue]* Netvisão (Cable)[/COLOR]
      213.228.128.6
      213.228.128.5



    [COLOR=Blue]* TVTel[/COLOR]
      195.22.0.204
      195.22.0.205

     [COLOR=Blue]* Vodafone[/COLOR]
       212.18.160.133
       212.18.160.134

---

### Post by thenailedone on 2007-12-14
Hi all... anybody have any idea about the required init strings and user name/password for the wvdial.conf file is when trying to access the net with a cellphone via USB using Virgin Mobile in South Africa?

---

### Post by mips on 2007-12-14
> **thenailedone said:**
> Hi all... anybody have any idea about the required init strings and user name/password for the wvdial.conf file is when trying to access the net with a cellphone via USB using Virgin Mobile in South Africa?

[http://mybroadband.co.za/vb/forumdisplay.php?f=127](http://mybroadband.co.za/vb/forumdisplay.php?f=127)

See the stickies ;)

---

### Post by thenailedone on 2007-12-14
> **mips said:**
> [http://mybroadband.co.za/vb/forumdisplay.php?f=127](http://mybroadband.co.za/vb/forumdisplay.php?f=127)

See the stickies ;)

Cool and thanks... I must remember that site... ;)

---

### Post by ChasB on 2008-01-16
Folks

Just to say I have got many modems working using the Vodafone Linux driver. Both the PCMCIA E620 and E220 USB work well on all networks with this software. Using the .deb with 7.10 ..... Oh and it will now allow you to set up the APN and operator directly in the latest version,not just Vodafone, so will work for any operator................. I have used it for local access on various networks.

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/]("https://forge.vodafonebetavine.net/projects/vodafonemobilec/")

Cheers
ChasB

---

### Post by syndrome1987 on 2008-01-17
i work on the troubleshooting team for 3 (UK network) my job specifically deals with the huawei e220 and the ZTE mf622, tomorrow I'm taking home an e220 to test properly on my Ubuntu and fedora systems, to test the possibility of running a Hayes command directly into the modem (which by all means should be possible, but we'll see) anyone with an e220 should also try the same test. 

to give the system the best chance of detecting the modem, insert it before you have booted your system, the Hayes command set or 'at strings'  can be used for daignostics, signal strength, and running extra commands directly into modems, in this case setting an APN (access point name) which is all important, the above technique(the previous post) should work with most modems but the downside is (although i can only speak for three but imagine a similar case with other vendors) this will invalidate your warranty and specifically three re flash the modem with their own set of firmware to deter such techniques, so if anything goes tits up, invariably they often do with the E220, you'll have no chance of getting your money back.

Anyway back to the point, once you have detected the modem run a minicom -o command failing that, download Wvdial or some softwawre along those lines (please bear in mind that i haven't performed this test yet myself so i cant be too specific with the configuration and usage of this kind of software on linux) 

you need to run the command     at+cgdcont=1,"IP","three.co.uk"   but use your networks apn in place of three.co.uk, be sure to retain format and case.

i'll play with a few other bits tomorrow but I'm fairly confident i can put something together
pending what happens, i might be able to write an all purpose configuration and monitoring tool similar to vodafone mobile connect software, perhaps borrowing a bit of their source code, as we detect problems in usage and application for the products for 3, there would be a cahnce 3 would take on the concept and release their own official driver and diagnostic tool based on results produced from my team.

there are two shortcomings running this type of device on linux, one you have little control of what signal the E220 will receive, it might default to an unusable connection i.e - GPRS in most occasions 
and little control of the diagnostics of the device,

give the at a go and tell me what happens and i'll update soon

---

### Post by HarM_triade on 2008-01-18
> **syndrome1987 said:**
> 
i'll play with a few other bits tomorrow but I'm fairly confident i can put something together
pending what happens, i might be able to write an all purpose configuration and monitoring tool similar to vodafone mobile connect software, perhaps borrowing a bit of their source code, as we detect problems in usage and application for the products for 3, there would be a cahnce 3 would take on the concept and release their own official driver and diagnostic tool based on results produced from my team.



I'm trying the same for a 3g Option card. I think I've got it all worked out (connect/disconnect icon, signal strength bar, provider and home/roaming network notification) except for the real time dataflow. After disconnecting I can read /var/log/messages and filter out the data with awk but I can't find where to monitor realtime ..... any idea's?

---

### Post by con on 2008-01-18
In kde knemo is very good at monitoring connections, it can keep daily/monthly statistics as well.

---

### Post by HarM_triade on 2008-01-19
> **con said:**
> In kde knemo is very good at monitoring connections, it can keep daily/monthly statistics as well.

Thanks for that. Just what I needed to point me to "ifconfig" output. Hadn't thought of anything as obvious as that ....... duhhhh!!!
Lack of sleep getting to my brain, methinks. :-)
Now for some sparetime to get this thing working as I want it.
Thanks again.

---

### Post by mustakim on 2008-01-20
Hi.. I made this after I made many research for Huawei modem E220. Better try it. It is easy and save a time. A reason why I develope this installer is to make solution for trouble in configuration of Huawei E220 modem on linux. Read at read me. Execute this tar.gz file first:

tar xzvf huaweiE220.tar.gz

This is my first post to linuxers. Hope this stuff could solve your problems. Thank you for all man that make this command. I'm just took your idea and make it simple way to install. The easiest way is to save our time to get connecting on internet. Get the stuff at here:

[http://www.savefile.com/files/1329895](http://www.savefile.com/files/1329895)

It's suitable for Kernel 2.6 and latest and I has been trying this stuff to opensuse 10-11, sabayon mini, pclos 2007 gnome, mint Daryna, fedora 7-8, mandriva 2007-2008, ubuntu gutsy -hardy and ubuntuME. I has testing to gOS 2.0 too but it doesn't work because it require wvdial installer. Maybe it also compatible with gentoo, slackware and redhat family too and give me a comment about it. Good news, it's very easy with Ubuntu based but I'm not sure about OpenGEU.

FOR MANDRIVA (and its family), IT'S NOT GOING TRUE WITH wvdial hsdpa, so it must be connect by this way:
-After you do this, go to Mandriva Control Centre, Network&Internet,"
-Analog Phone, Manual choice -> choose /dev/ttyUSB0, dont choose any "
provider, just proceed with NEXT, evetually type the following: "
-Connection name: Your-Provider "
-Phone number : *99# "
-Login ID : ppp (can be whatever) "
-Password : ppp (can be whatever) "
-Authentication : CHAP "
-Keep clicking on NEXT and you shall be connected soon ;)

FEDORA USER

Please follow the guide. It's complicated but it will work. Don't run any web browser before restart your computer. Try to put this web adress first and let it run for 1 minutes. Do it twice.It will recognise your IP adress.

[http://202.75.163.27/](http://202.75.163.27/)

 Restart your pc again, and run the IP again before browsing [www.google.com](www.google.com) Good luck 

Additional:
-If you get anything problems with wvdial hsdpa, I suggest you to try KPPP or Kinternet to get connect. (especially to Sabayon and Gentoo user)
- You can change or modify a username, password and phone number at /etc/wvdial.conf if need.
- I am glad if you can comment me about my huawei E220 installer.
-Big thank you to [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/) and [www.kanoistika.sk/bobovsky/archiv/umts/](www.kanoistika.sk/bobovsky/archiv/umts/) because 80 percent from this installer is not my scripts idea. I'm just build the installer only.
- Don't sell my installer!! It is free for everyone

for more info, visit [http://mustakim.blogster.com/huawei-e220-software-installer](http://mustakim.blogster.com/huawei-e220-software-installer)
but today the site in renovation lol..

---

### Post by giruzz on 2008-01-27
I finally managed to have a Working E220 with T-Mobile UK:

These is my configuration:
```
User: t-mobile
Password: one2one
DNS: 4.2.2.1
DNS: 4.2.2.2
APN: general.t-mobile.uk

```

I'm using the default script provided with he Vodafone Mobile Connect Card driver

g.

---

### Post by paulbrab on 2008-01-31
Hi,
I'm a bit of a newbie to this sort of stuff.

I have successfully connected my Hauwei E220 modem to 3 Ireland using a combination of the thread above using the huawei E220-installer.tar file and an article from linux.ie called "Three Ireland USB Modem HOWTO".

Thanks for everyones help.

---

### Post by viper233 on 2008-02-04
Settings using this modem with Vodafone Australia using Ubuntu Gutsy 7.10 kernel 
linux-image-2.6.22-14-generic, 2.6.22-14.47  

The card had been previously installed on a Windows machine, it seems this may improve reliability from previous posts. 

Append this to the end of /etc/wvdial.conf

[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","vfinternet.au";

to connect run
sudo wvdial hsdpa

---

### Post by benc123 on 2008-02-05
If you are trying to use this usb modem on hutchinson three in the uk [here is a guide]("http://jamiedumbill.com/index.php?page=40") with all necessary configs :) :)

---

### Post by pantelis on 2008-02-07
Coz of a little conflict with my Windows Xp in one of my laptops I installed ubuntu 7.10! I only use this particular laptop to join the internet when there is no wireless connectivity!

Anyway! I gotta to thank you guys for helping me, and in just 2 hours I ve managed to make my stupid lil modem work!

I have some notes to make! 

1. Restarts are very useful trust me on that!

2. Somebody asked but didn get an answer, how is it possible to drop the connection pnce it's been connected???

3. Is it anyway to control the traffic???? maybe another application or somethin?

thanks in advance!

Greetings from Greece

p.s. My carrier is WIND. If anybody else from Greece needs help let me know!

---

### Post by gianluca.pettinello on 2008-02-07
The solution you propose allows to surf at max 61.0 kB/s. The attached method allows you to surf at 200 kB/s. I tried and it works perfectly
It is in italian but substantially you have to include the vendor and productid of your hsdpa usb modem in airprime.c which is in the kernel source
Ciao
Gianluca
[ATTACH]58998[/ATTACH]

---

### Post by pieshop1234 on 2008-02-07
Hi, I have now mangaged to get much further with connection. Thanks to all who have posted to help. It seems I'm almost there. 
When I wvdial I get the following messages. As far as I can tell everything is going well until the last few lines. Could anyone help with this. I am using  the uk's 3 network. 

luke@luke-laptop:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1003 
luke@luke-laptop:~$ wvdial 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvModem<*1>: Cannot get information for serial port. 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATDT*99# 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: ATDT*99# 
WvDial Modem<*1>: NO DIALTONE 
WvDial<Err>: No dial tone. 
WvDial<*1>: Disconnecting at Fri Feb  8 18:38:27 2008 
luke@luke-laptop:~$ wvdial hsdpa 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvModem<*1>: Cannot get information for serial port. 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2 
WvDial Modem<*1>: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","three.co.uk" 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATDT*99# 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: CONNECT 
WvDial<*1>: Carrier detected.  Starting PPP immediately. 
WvDial<Notice>: Starting pppd at Fri Feb  8 18:38:38 2008 
WvDial<Notice>: Pid of pppd: 7804 
WvDial<*1>: Using interface ppp0 
WvDial<*1>: Authentication (CHAP) started 
WvDial<*1>: Authentication (CHAP) successful 
WvDial<*1>: local  IP address 10.59.106.41 
WvDial<*1>: remote IP address 10.64.64.64 
WvDial<*1>: primary   DNS address 10.11.12.13 
WvDial<*1>: secondary DNS address 10.11.12.14 
WvDial<*1>: Script /etc/ppp/ip-up run successful 
WvDial<*1>: Default route Ok. 

WvDial<*1>: warning, can't find address for `www.suse.de` 
WvDial<*1>: warning, address lookup does not work 
WvDial<*1>: Nameserver (DNS) failure, the connection may not work. 
WvDial<*1>: Connected... Press Ctrl-C to disconnect 

THANKS IN ADVANCE

---

### Post by alstam on 2008-02-08
I finaly setup the huawei e220 modem but i still can't connect. The signal indicator shows that i have full 3g signal, i can send sms but i ca't connect to the internet. Here is the terminal screen:

> 
alex@alex-laptop:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
Removing stale pidfile /tmp/vmc.pid
2008/02/08 16:44 +0300 [-] Log opened.
2008/02/08 16:44 +0300 [-] twistd 2.5.0 (/usr/bin/python 2.5.1) starting up
2008/02/08 16:44 +0300 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/02/08 16:44 +0300 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/02/08 16:44 +0300 [-] Loaded.
2008/02/08 16:44 +0300 [-] Changing process name to VMCCdfL
2008/02/08 16:44 +0300 [-] Log opened.
2008/02/08 16:44 +0300 [-] twistd 2.5.0 (/home/alex/ 2.5.1) starting up
2008/02/08 16:44 +0300 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/02/08 16:44 +0300 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/02/08 16:44 +0300 [-] Loaded.
2008/02/08 16:44 +0300 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/02/08 16:44 +0300 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8ae07cc>
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE220\r\n\r\nOK\r\n'
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING: CBK = [('E220',), ('OK',)]
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: NEW STATE: idle
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE220\r\n\r\nOK\r\n'
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING: CBK = [('E220',), ('OK',)]
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: NEW STATE: idle
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE220\r\n\r\nOK\r\n'
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter::WAITING: CBK = [('E220',), ('OK',)]
2008/02/08 16:44 +0300 [-] SIMCardConnAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/02/08 16:45 +0300 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE220\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] SIMCardConnAdapter::WAITING: CBK = [('E220',), ('OK',)]
2008/02/08 16:45 +0300 [-] /usr/lib/python2.5/site-packages/vmc/gtk/views/application.py:291: gtk.GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width 588 and height -14
2008/02/08 16:45 +0300 [-] ADAPTING <vmc.common.plugins.huawei_e220.HuaweiE220 object at 0x8cbd80c> to <class 'vmc.common.hardware.huawei.HuaweiE2XXAdapter'>
2008/02/08 16:45 +0300 [-] DAEMONS: DAEMON SignalQualityDaemon started...
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] DAEMONS: executing <bound method SignalQualityDaemon.function of <vmc.common.daemon.SignalQualityDaemon object at 0x8e9fd8c>> every 60 seconds
2008/02/08 16:45 +0300 [-] SIMCardConnAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSQ: 13,99\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('13', '99')]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATZ\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATE0\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: 'ATE0\r\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] GTKBehaviour: LEAVING PreInit AND ENTERING INTO Auth

** (twistd:7173): WARNING **: couldn't read 4 bytes from gnome-keyring socket: Connection reset by peer
2008/02/08 16:45 +0300 [-] Instantiating AuthStateMachine ...
2008/02/08 16:45 +0300 [-] AuthStateMachine: Instantiating get_pin_status mode....
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPIN?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPIN: READY\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('READY',)]
2008/02/08 16:45 +0300 [-] GTKBehaviour: LEAVING Auth AND ENTERING INTO PostInit
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CNMI=2,1,0,0,0\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CMGF=0\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPBR=?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPBR: (1-250),40,20\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('250',)]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCA?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSCA: "002B0033003000390037003100300030003000300030",145\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('002B0033003000390037003100300030003000300030',)]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSCS: "UCS2"\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('UCS2',)]
2008/02/08 16:45 +0300 [-] /usr/lib/python2.5/site-packages/vmc/gtk/controllers/application.py:235: gtk.GtkWarning: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed
2008/02/08 16:45 +0300 [-] GTKBehaviour: LEAVING PostInit AND ENTERING INTO NetReg
2008/02/08 16:45 +0300 [-] Instantiating NetworkRegStateMachine ....
2008/02/08 16:45 +0300 [-] NetworkRegStateMachine: NEW MODE: check_registered
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPBR=1,250\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CME ERROR: not found\r\n'
2008/02/08 16:45 +0300 [-] "HuaweiE2XXAdapter::WAITING: ERROR received '\\r\\n+CME ERROR: not found\\r\\n'"
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS="IRA"\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CREG?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CREG: 0,1\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0', '1')]
2008/02/08 16:45 +0300 [-] NetworkRegStateMachine: NEW MODE: registration_finished
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CMGL=4\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = []
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS="UCS2"\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,0,"GR COSMOTE",2\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,0,"GR COSMOTE",2', None, 'GR COSMOTE', '2')]
2008/02/08 16:45 +0300 [-] GTKBehaviour: LEAVING NetReg AND ENTERING INTO ImDone
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CLCK="SC",2\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CLCK: 0\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0',)]
2008/02/08 16:45 +0300 [-] /usr/lib/python2.5/site-packages/vmc/gtk/controllers/application.py:398: gobject.Warning: unable to set property `text' of type `gchararray' from value of type `PyObject'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT^SYSCFG=2,2,3FFFFFFF,2,4\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CLCK="SC",2\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CLCK: 0\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0',)]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSQ: 13,99\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('13', '99')]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,0,"GR COSMOTE",2\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,0,"GR COSMOTE",2', None, 'GR COSMOTE', '2')]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:68863481,0,0,0,6\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::Huawei E220 NOTIFICATION: '\r\n^BOOT:68863481,0,0,0,6\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,0,"GR COSMOTE",2\r\n\r\nOK\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,0,"GR COSMOTE",2', None, 'GR COSMOTE', '2')]
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvDial<*1>: WvDial: Internet dialer version 1.56

2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvModem<*1>: Cannot get information for serial port.
2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV 
        WvDial<*1>: Initializing modem.

2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvDial<*1>: Sending: ATZ

2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATZ

2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATZ
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0

2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: AT+CGDCONT=1,"IP","internet"

2008/02/08 16:45 +0300 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Modem initialized.
        WvDial<Err>: Configuration does not specify a valid login name.
        WvDial<Err>: Configuration does not specify a valid password.

2008/02/08 16:45 +0300 [-] WVDIAL: pppd closed their stdout!
2008/02/08 16:45 +0300 [-] WVDIAL: pppd closed their stderr.
2008/02/08 16:45 +0300 [-] WVDIAL: quitting
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-5nmp0v9ppY: Connection refused

** (twistd:7173): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:7173): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:7173): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
2008/02/08 16:45 +0300 [-] "Notification <ConnectionNotification at 0x8ebfcec status: disconnected> not in {'rssi': <bound method ApplicationController._change_signal_level of <vmc.gtk.controllers.application.ApplicationController object at 0x8d6acec>>, 'new_conn_mode': <bound method ApplicationController._conn_mode_changed of <vmc.gtk.controllers.application.ApplicationController object at 0x8d6acec>>, 'sms': <bound method ApplicationController._on_sms_received of <vmc.gtk.controllers.application.ApplicationController object at 0x8d6acec>>, 'speed': <bound method ApplicationController._change_net_stats_cb of <vmc.gtk.controllers.application.ApplicationController object at 0x8d6acec>>, 'call': None}"
2008/02/08 16:45 +0300 [-] 'EXIT CODE 1'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:68863481,0,0,0,6\r\n'
2008/02/08 16:45 +0300 [-] HuaweiE2XXAdapter::Huawei E220 NOTIFICATION: '\r\n^BOOT:68863481,0,0,0,6\r\n'




Any ideas???? 

P.S. Sorry for the long post

---

### Post by pip on 2008-02-29
@pieshop1234:

Take a look at your **/etc/peer/ppp/wvdial** file. I replaced mine to only contain this:

```

noauth
name wvdial
usepeerdns
replacedefaultroute
```

Also: you might want to change your APN from "three.co.uk" to "3internet". I'm not sure if it matters, but the windows client sets it to "3internet"

That solved it for me. 

For other people trying to get on the Three network in the UK.
This is how my /etc/wvdial.conf file looks:
```

[Dialer Defaults]
Phone = *99#
Username = three
Password = three
Stupid Mode = 1
Dial Command = ATDT

[Dialer Three]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","3internet"
```

Connect with: "wvdial Three"

Hope that helps.

---

### Post by pip on 2008-02-29
@alstam: Did you set a username and password? 
This:
```
WvDial<Err>: Configuration does not specify a valid login name.
WvDial<Err>: Configuration does not specify a valid password.
```
suggests you didn't. Even if you don have/need a password try setting it to some bogus value.

---

### Post by csamuel on 2008-03-01
> **syndrome1987 said:**
> i'll play with a few other bits tomorrow but I'm fairly confident i can put something together
pending what happens, i might be able to write an all purpose configuration and monitoring tool similar to vodafone mobile connect software, perhaps borrowing a bit of their source code, as we detect problems in usage and application for the products for 3, there would be a cahnce 3 would take on the concept and release their own official driver and diagnostic tool based on results produced from my team.

Please please please please! :-)

As a new Three PAYG Mobile Broadband customer (visiting the UK for a family funeral) I have to say that this would be great - I ended up hacking the scripts in the Vodafone program to call the right number and tracked down the correct APN to get it going.

FWIW with 2.6.24.2 I've found that the Huawei E220 worked out of the box, whereas the ZTE needed the usbserial module loading with the appropriate ID's to get it recognised.

cheers,
Chris

---

### Post by csamuel on 2008-03-01
> **pip said:**
> Also: you might want to change your APN from "three.co.uk" to "3internet". I'm not sure if it matters, but the windows client sets it to "3internet"

Hi there,  FWIW both strings work as APN's for me with Three, with both giving me a private IP address and the usual non-functional DNS servers (10.11.12.13 and 10.11.12.14).

Out of interest - does anyone know if there is there an APN for Three in the UK that gives you a public IP instead ?

cheers,
Chris

---

### Post by mips on 2008-03-01
> **syndrome1987 said:**
> 

i'll play with a few other bits tomorrow but I'm fairly confident i can put something together
pending what happens, i might be able to write an all purpose configuration and monitoring tool similar to vodafone mobile connect software, perhaps borrowing a bit of their source code, as we detect problems in usage and application for the products for 3, there would be a cahnce 3 would take on the concept and release their own official driver and diagnostic tool based on results produced from my team.


Code is GPL'ed so there should be no issue.

Why not join the existing VMC developers and make it a better app instead of writing a new one? Not telling you what to do though if that is what it sounds like.

Anyway for those that want to contibute with suggestions, ideas, code see:
[https://blueprints.launchpad.net/ubuntu/+spec/gprs-connection-out-of-the-box](https://blueprints.launchpad.net/ubuntu/+spec/gprs-connection-out-of-the-box)
[https://launchpad.net/~pmarti](https://launchpad.net/~pmarti)
[https://bugs.launchpad.net/ubuntu/+bug/164369](https://bugs.launchpad.net/ubuntu/+bug/164369)

---

### Post by marksy1984 on 2008-03-05
Hello All,
I just wondered how long this new application might take to develop. It sounds great!

---

### Post by patrickmcduff on 2008-03-12
Mate, I luv ya!

I have been trying to connect my 3 Network USB Modem in Australia for nearly a week! 
I almost had to compromise and install M$ Windows on a Virtual Box.
 
I had to modify my wvdial.conf file just as you suggested. I used the command prompt as follows:
cd /etc
sudo gedit wvdial.conf

I had to use all your commands Verbatim!!!

After that I used KPPP to connect to the internet, I was just wondering how I could the Vodafone_Driver_for _Linux as I would like to use the SMS service.

Cheers

Pat

---

### Post by htan69 on 2008-03-15
Just wanna share my experience with Ubuntu Linux 7.10 (Gutsy Gibbon) and Huawei E220.

Actually, I'm not even a casual user of Linux. My experiences with Linux in the past 5-6 years was limited to installation, used it for couple of week and then ignore it. 

Early this week I install Ubuntu Linux and I guess I fallen in love with its easy of use. Even my wife whom heavy user of Mac like it. But my biggest problem is I can't make my Huawei E220 work on Ubuntu eventhough I tried so many ways explained in this forum as well as Indonesian Ubuntu forum (and user's blog as well).

Finally last night I decided to try the Vodafone software. At first I'm a bit hesitated because I'm not sure it will work with Indonesian ISP (I used 3G services from Indosat).

Anyway, here is the steps I taken.

 - Boot to Windows and download following packages from [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)
[INDENT]- python2.4_2.4.4-6ubuntu4.1_i386
- python2.4-minimal_2.4.4-6ubuntu4.1_i386
- python-all_2.5.1-1ubuntu2_all
- python-crypto_2.0.1+dfsg1-2ubuntu1_i386
- python-pysqlite2_2.3.4-2_i386
- python-serial_2.2-4_all
- python-twisted_2.5.0-2build1_all
- python-twisted-bin_2.5.0-2build1_i386
- python-twisted-conch_0.8.0-1_all
- python-twisted-core_2.5.0-2build1_all
- python-twisted-lore_0.3.0-1_all
- python-twisted-mail_0.4.0-1_all
- python-twisted-names_0.4.0-1_all
- python-twisted-news_0.3.0-1_all
- python-twisted-runner_0.2.0-2_i386
- python-twisted-web2_0.2.0+svn20070403-1_all
- python-twisted-web_0.7.0-1_all
- python-twisted-words_0.5.0-1.1_all
- python-tz_2007d-1_all
- python-zopeinterface_3.3.1-3build2_i386
[/INDENT]

 - Download Vodafone software ((vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb) from [https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)

 - Boot into Linux with Huawei E220 plugged (I used the long cable, lost the short one :()

 - Eject the Huawei (Right click on the Mobile partnet icon and choose Eject)

 - Install all python packages (Simply right click on each file and choose "Open with GDebi Package Installer")

 - Install Vodafone software (same way as installing the python package)

 - Run the Vodafone software (it's in Application ==> internet)

 - Create new profile, enter my username, my password, APN and authentication (must be PAP)

 - Connect ... It's work!!!

After I wrote above steps its looks like pretty straightforward but actually it's not. I'm having problem when installing the python packages because I tried to install the perl-base_5.8.8-7ubuntu3_i386, python2.5_2.5.1-5ubuntu5.1_i386 and python2.5-minimal_2.5.1-5ubuntu5.1_i386 packages as well resulting in dependencies conflict/corrupt and I have to reinstall the Ubuntu from scratch. I experienced this dependencies conflict/corrupt 3 times (yes ... reinstalling Ubuntu 3 times as well) before I managed to get the right package. Above list is the right packages for Ubuntu 7.10 (Gutsy Gibbon) fresh installation.

---

### Post by gercokees on 2008-03-15
Hi,
With a friend of mine we tried this:
[http://ubuntuforums.org/showpost.php?p=1772796&postcount=8](http://ubuntuforums.org/showpost.php?p=1772796&postcount=8)

```

But now we get the following errors:
dennis@dennis-laptop:~$ wvdial hsdpa 0000
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Warn>: Warning: section [Dialer 0000] does not exist in wvdial.conf.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: +CME ERROR: SIM PIN required
WvDial<Err>: Invalid dial command.
WvDial<*1>: Disconnecting at Sat Mar 15 11:09:58 2008
dennis@dennis-laptop:~$ 
```

Any suggestions? This is a Vodafon-nl account...
Thanx in advance...

---

### Post by mips on 2008-03-15
> **gercokees said:**
> Hi,
With a friend of mine we tried this:
[http://ubuntuforums.org/showpost.php?p=1772796&postcount=8](http://ubuntuforums.org/showpost.php?p=1772796&postcount=8)

Any suggestions? This is a Vodafon-nl account...
Thanx in advance...

Yes, use the Vodafone Mobile Connect client, it should work out off the box for you seeing you are with vodafone.

---

### Post by gercokees on 2008-03-15
We tried that, but we could somehow not establish a connection....

---

### Post by wylan on 2008-03-16
My friend just recently signed up for T-mobile UK wireless internet access, and she is wondering if the same steps for the E220 would work for the E170. She is running version 7.10

---

### Post by mips on 2008-03-17
> **gercokees said:**
> We tried that, but we could somehow not establish a connection....

Make sure you have the correct settings for Username, Password, APN & DNS for vodafone NL. The mobile company can provide you with those details.

A google search reveals:

Service:                       APN:                          Username:   Password:  DNS:
Vodafone (normal)       web.vodafone.nl        vodafone     vodafone     -   
Vodafone (business)     office.vodafone.nl     vodafone     vodafone     -

---

### Post by mips on 2008-03-17
> **wylan said:**
> My friend just recently signed up for T-mobile UK wireless internet access, and she is wondering if the same steps for the E220 would work for the E170. She is running version 7.10

You can use the Vodafone Mobile Connect Card Driver Client with the E17x models.
[https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)
Get the .deb file

Setting you will need to specify:

T-Mobile
User: user
Password:mms
DNS: 4.2.2.1
DNS: 4.2.2.2
APN: general.t-mobile.uk 

T-Mobile (One2One
User: t-mobile (or Username)
Password: one2one
DNS: 4.2.2.1
DNS: 4.2.2.2
APN: general.t-mobile.uk

Genrally I see password & usernames simply being password & username so this could always be an option to try.

---

### Post by mips on 2008-03-17
For those of you not sure what settings to use for **APN, Username, Pasword & DNS** fields see the links below:

[http://www.pinstack.com/carrier_settings_apn_gateway.html](http://www.pinstack.com/carrier_settings_apn_gateway.html)
[http://www.unlocks.co.uk/gprs_settings.php](http://www.unlocks.co.uk/gprs_settings.php)
[http://www.modmyifone.com/wiki/index.php?title=Carrier_APN_Settings&diff=3712&oldid=3669#T-Mobile_UK](http://www.modmyifone.com/wiki/index.php?title=Carrier_APN_Settings&diff=3712&oldid=3669#T-Mobile_UK)

---

### Post by iMacUser on 2008-03-17
Thanks htan69 for a very clear and informative posting.  After hours of googling and searching the forums I found your post and.  I just followed your post and successfully installed an E220 on an eee-pc 4G with 1GB of RAM, ubuntu 7.10.  I'm using this modem via 3 UK right now to post my thanks.  Now to try the same steps on my bigger laptop (fujitsu-siemens Amilo Pi1536, also with ubuntu 7.10.

iMacUser  
(linux and ubuntu user for just 2 weeks and enjoying every minute of it)

---

### Post by Wesseli on 2008-03-18
I managed to get huawei e220 modem to work in ubuntu 7.10 with vodafone mobile connect card driver pretty painlessly, got the .deb file from there ->  [https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12) 

Also, I happened to download Mandriva One 2008 and the modem install was even easier! I did not have to download any packages like in Ubuntu 7.10. I am currently typing with the mandriva live cd running, through huawei e220 connection. Mandriva installer asked simple questions and I basicly typed my pin and that was it.

cheers

---

### Post by gercokees on 2008-03-19
thanx everybody.
office.vodafone.nl
did the trick for me!!
(it would be nice to have it in the profile's by default, so all dutch users will have less problems....)
anyhow, thanx for all the work....!!!

---

### Post by pinsky on 2008-03-20
Hy

Got my e220 connected. Detected all ttyUSB0 ttyUSB1 ttyUSB2.

But i still could't connect.

When i start wvdial i get:

> Mar 20 00:56:57 pinsky-desktop pppd[6225]: pppd 2.4.4 started by pinsky, uid 1000
Mar 20 00:56:57 pinsky-desktop pppd[6225]: Using interface ppp0

Mar 20 00:56:57 pinsky-desktop pppd[6225]: Connect: ppp0 <--> /dev/ttyUSB0

Mar 20 00:56:57 pinsky-desktop pppd[6225]: PAP authentication succeeded

Mar 20 00:56:58 pinsky-desktop pppd[6225]: Modem hangup

Mar 20 00:56:58 pinsky-desktop pppd[6225]: Connection terminated.
Mar 20 00:56:58 pinsky-desktop pppd[6225]: Exit.
Mar 20 00:57:26 pinsky-desktop pppd[6228]: pppd 2.4.4 started by pinsky, uid 1000

Mar 20 00:57:26 pinsky-desktop pppd[6228]: Using interface ppp0

Mar 20 00:57:26 pinsky-desktop pppd[6228]: Connect: ppp0 <--> /dev/ttyUSB0

Mar 20 00:57:26 pinsky-desktop pppd[6228]: PAP authentication succeeded

Mar 20 00:57:28 pinsky-desktop pppd[6228]: Modem hangup

Mar 20 00:57:28 pinsky-desktop pppd[6228]: Connection terminated.

Mar 20 00:57:28 pinsky-desktop pppd[6228]: Exit.

Mar 20 00:58:50 pinsky-desktop pppd[6256]: pppd 2.4.4 started by pinsky, uid 1000

Mar 20 00:58:50 pinsky-desktop pppd[6256]: Using interface ppp0

Mar 20 00:58:50 pinsky-desktop pppd[6256]: Connect: ppp0 <--> /dev/ttyUSB0

Mar 20 00:58:50 pinsky-desktop pppd[6256]: PAP authentication succeeded

Mar 20 00:58:51 pinsky-desktop pppd[6256]: Modem hangup

Mar 20 00:58:51 pinsky-desktop pppd[6256]: Connection terminated.

Mar 20 00:58:51 pinsky-desktop pppd[6256]: Exit.   

I also get some error-like messages abut chap, but i don't know where to go to read a log of them. The quoted log is from dmesg.

In addition, i'm supposed to disable chap and other encriptions and use only PAP. I've done it by adding:
refuse-cahp
refuse-mschap
refuse-mschap-v2
refuse-eap

in /etc/ppp/options


Anybody has a solution?

---

### Post by mips on 2008-03-20
> **pinsky said:**
> 
Anybody has a solution?

Use the Vodafone Mobile Connect Card Driver Client
[https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)
Get the .deb file

Why do people still want to use wvdial?

---

### Post by pinsky on 2008-03-20
I have to downlaod all the dependencies for the huawei linux driver manually then, and that could take ages since for every download a do, a have to reboot to windows to connect to the internet.

---

### Post by mips on 2008-03-20
> **pinsky said:**
> I have to downlaod all the dependencies for the huawei linux driver manually then, and that could take ages since for every download a do, a have to reboot to windows to connect to the internet.

There arent that many and I'm sure someone already listed them in this thread.

Edit: I'm sure this can be done with a live cd and then just transferred across. Does anyone think this is plauseable? chroot even comes to mind.

---

### Post by HuBaghdadi on 2008-03-20
My operator isn't Vodafone so I followed this thread: [http://ubuntuforums.org/showthread.php?t=595064&highlight=E220](http://ubuntuforums.org/showthread.php?t=595064&highlight=E220)
It will be more than great if some one hints me how to set the APN...

---

### Post by Ki$$ on 2008-03-23
I have the same problem with my modem. thanks a lot.

---

### Post by philipgm on 2008-04-09
I spoke to vodafone uk for the username, password and APN. They got it wrong and then I found your post so thanks.

BTW, the vodafone software makes this very easy to set up.

Phil

---

### Post by piotrwoj on 2008-05-14
here is program, work ~200 GPRS/UMTS/3G modem:
[http://www.domar.biz.pl/globalumts.tar.gz](http://www.domar.biz.pl/globalumts.tar.gz)
Enjoy :) [DRZWI]("http://www.domar.biz.pl/")

---

### Post by styphon on 2008-05-15
OK, I have been trying for hours, following different tutorials to get my T-Mobile E220 to work with no joy. My wvdial.conf is:
```
[Dialer Defaults]
Phone = *99***1#
Username = user
Password = pass
Stupid Mode = 1
Dial Command = ATDT 

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
```
When I run wvdial.conf hsdpa in a console I get the following:
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu May 15 21:28:15 2008
--> Pid of pppd: 6726
--> Disconnecting at Thu May 15 21:28:15 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)
```

I'm new to Linux and it's processes so any help would be greatly appreciated.

---

### Post by TomasinaServo on 2008-05-22
Hey!

I got the huawei E220 to work, after running the instructions in the first page of this thread and the ones in the [howto thread]("http://ubuntuforums.org/showthread.php?t=595064&highlight=E220") and after that I installed the [vodafone driver]("https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=116").

I needed to download several python packages though.

My provider is three (3) and the profile settings that work are:
Username: three
Password: three

Preferred connection: 3G preferred
Authentication mode: Default
APN host: 3internet

Use static DNS

Primary DNS: 172.31.140.69
Secondary DNS: 172.30.140.69

Enjoy!

---

### Post by salutis on 2008-05-31
There is a simple package I created for my friends. You can try it too.

**Installation WITH working network connection:**
[LIST]
[*] In 'Applications' menu click on 'Accessories' and then 'Terminal'.
[*] Enter these two commands:
```
sudo sh -c "echo deb http://repository.salutis.sk/production ./ >> /etc/apt/sources.list"
sudo sh -c "aptitude update && aptitude install salutis-connect"
```
[*] In 'Applications' menu click on 'Internet' and then 'Salutis Connect'.
[/LIST]

**Installation WITHOUT working network connection:**
[LIST]
[*] Download [this package]("http://repository.salutis.sk/latest/salutis-connect.deb").
[*] Install downloaded package on box without network connection.
[*] In 'Applications' menu click on 'Internet' and then 'Salutis Connect'.
[/LIST]

**Please note:** PIN code MUST be disabled. You can disable it moving your SIM card from Huawei to mobile phone and disable asking for PIN code.

---

### Post by kodiakz on 2008-06-02
Hi,
my connection to 3AU seems to be working, the LED is stable blue But somehow I simple do not have internet access, even I can not ping the dns servers from 3AU.

The ouput of wvdial looks like this:

```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1, "IP", "3netaccess"
AT+CGDCONT=1, "IP", "3netaccess"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jun  2 21:08:17 2008
--> Pid of pppd: 22434
--> Using interface ppp0
--> local  IP address 117.102.144.2
--> remote IP address 10.64.64.64
--> primary   DNS address 202.124.84.2
--> secondary DNS address 202.124.68.130

```

I assume the wvidal.conf is correct:

```

[Dialer hsdpa]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1, "IP", "3netaccess"
Modem Type = Huawei E220
Baud = 466600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Stupid Mode = 1
Username = a
Password = a
Dial Command = ATDT

```

It would be great if someone can help me out!!!

---

### Post by WillemToerien on 2008-06-02
@kodiakz: Okay I've taken at look at your wvdial.conf file, and it doesnt look like the config file I have.

Try this:

Edit your wvdial.conf file to have the following content (take note of the '//' I have inserted, this may vary. The one I use is for South Africa vodacom):
```

[Dialer hsdpa]
Phone = *99***16# //
Username = vodafone //
Password = vodafone //
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","internet"; //

```

And here is what my output looks like:
```

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","internet";
OK
--> Modem initialized.
--> Sending: ATDT*99***16#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jun  2 19:15:57 2008
--> Pid of pppd: 6217
--> Using interface ppp0
--> local  IP address 41.29.14.194
--> remote IP address 10.64.64.64
--> primary   DNS address 196.207.32.83
--> secondary DNS address 196.207.32.69

```

I suggest you disable your pin for now. Dont over complicate things, once you got connected and can browse, then go and find a solution for the pin (if you really need it).

Next, plug in your E220, wait for 2-5 minutes and type ```
ls -la /dev/ttyU*
```. You'll probably see something like this:

```

crw-rw---- 1 root dialout 188, 0 2008-06-02 19:13 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2008-06-02 19:13 /dev/ttyUSB1

```

However, this is not what we want to see, we want to see something like this:

```

crw-rw---- 1 root dialout 188, 0 2008-06-02 19:15 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2008-06-02 19:15 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2008-06-02 19:15 /dev/ttyUSB2
crw-rw---- 1 root dialout 188, 3 2008-06-02 19:15 /dev/ttyUSB3
crw-rw---- 1 root dialout 188, 4 2008-06-02 19:15 /dev/ttyUSB4
crw-rw---- 1 root dialout 188, 5 2008-06-02 19:15 /dev/ttyUSB5

```

So in order to get that result, go and download this file: [huaweiAktBbo-i386.out]("http://www.kanoistika.sk/bobovsky/archiv/umts/") and run it as root. Then unplug your E220 and plug it back again, wait for so 2-5 min, and type in ```
ls -la /dev/ttyU*
```. If you get the result what we want to see, then its good news dude.

Next, go and edit your network settings for the modem.

Connection Type: Serial
Phone Number: *99***16# ( or what ever your number is )
Username: vodafone ( or what ever your username and password are )
Password: vodafone

Modem port: /dev/ttyU0

Then tick all the check boxes in the Options tab.

After that, type in ```
sudo wvdial hsdpa
``` and then go to your network settings and make sure you have your DNS' there.

And thats about what I do to get this working.
Hope this helps.:)

---

### Post by kodiakz on 2008-06-04
@WillemToerien

Thx for that. I follwed exactly Ur instructions and additionaly I did an "ifdown" for all my other networkInterfaces. Now it runs perfectly!

---

### Post by coldbloodedneo on 2008-06-04
> **salutis said:**
> I created my own package. You can try it.

[LIST]
[*]Relogin as super-user:
```
sudo -s
```
[*]Add new repostiory to '/etc/apt/souces.list':
```
echo deb http://repository.salutis.sk/production ./ >> /etc/apt/sources.list
```
[*]Update database of packages:
```
aptitude update
```
[*]Install package:
```
aptitude install salutis-connect
```
[*]Connect your Huawei E200 device to USB port.
[*]Click on 'Salutis Connect' icon in 'Applications->Internet' menu section and enjoy :)
[/LIST]
this one work like a charm. Thanks salutis

---

### Post by WillemToerien on 2008-06-05
> **kodiakz said:**
> @WillemToerien

Thx for that. I follwed exactly Ur instructions and additionaly I did an "ifdown" for all my other networkInterfaces. Now it runs perfectly!

cool dude. :guitar:

---

### Post by RajaAjmal on 2008-06-11
hi 

i've followed your instruction, but can't alter the wvdial.conf. it says i don't have the permission. can you plaese tell me how to alter the wvdial.conf. i'm new to ubuntu and i'm not too keen to continue with ubuntu the fact that i'm not able to connect to the internet via ubuntu. please help.

---

### Post by woodbrick on 2008-06-11
[QUOTE=kodiakz;5099227]Hi,
my connection to 3AU seems to be working, the LED is stable blue But somehow I simple do not have internet access, even I can not ping the dns servers from 3AU.

I too am on 3AU. My connection works with this wvdial.conf:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1, "IP", "3netaccess"
Modem Type = Huaweu E220
Baud = 921600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Stupid Mode = true
Username = a
Password = a

The problem I seem to have is that the connection only works on HSDPA (solid green light). If HSDPA is not available, the connection is supposed to drop back to 'normal' 3G UMTS speed (solid blue light). However, my connection speed drops to zero when the green light on my modem changes to blue. Any ideas? (i am very new to Linux. I thought I had won the war when I finally figured out how to connect the E220 modem to internet, but apparently this was just the first battle!)

---

### Post by Norad on 2008-06-13
go here [http://www.vodafonebetavine.net/web/linux_drivers](http://www.vodafonebetavine.net/web/linux_drivers) 

Download debian for i386  drivers, then install by double clicking the downloaded icon should be located in your /home directory (under places),  after install go to applications > internet >vodafone connect device, then phone Vodafone as you will need a username password and something else protacol that they throw in to confuse the issue.

---

### Post by woodbrick on 2008-06-14
The Vodaphone driver did not work for me, I think because I am with Three AU. In fact it crashed my connection completely. I have never been able to get the modem to work through network settings, so I have always just connected through terminal using wvdial. After installing the voda driver, I got an error saying that the software could not access the device (it did recognise it). After that, no matter what I tried, I got this error when trying to run wvdial:
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jun 14 18:32:40 2008
--> Pid of pppd: 9266
--> Disconnecting at Sat Jun 14 18:32:40 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

I ended up doing a clean install, and so far everything is working fine. I would like to know how to set up the network connection, but I am very wary of fixing that which is not broken! Beware three customers with a "working" connection, the vodaphone driver may not be for you! Thanks Norad for trying to help.

---

### Post by salutis on 2008-06-16
> **coldbloodedneo said:**
> this one work like a charm. Thanks salutis

You are welcome! Thanks for feedback.

---

### Post by chmac on 2008-06-17
In case anyone hasn't seen it (I searched the thread and couldn't find a mention) there's an app called USB_ModeSwitch which might help with the Huawei E220 and E169. You can see a detailed walkthrough for the EEE here:
[http://dalelane.co.uk/blog/?p=254](http://dalelane.co.uk/blog/?p=254)
Then the USB_ModeSwitch site itself (I think) is here:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by WillemToerien on 2008-06-18
> **RajaAjmal said:**
> hi 

i've followed your instruction, but can't alter the wvdial.conf. it says i don't have the permission. can you plaese tell me how to alter the wvdial.conf. i'm new to ubuntu and i'm not too keen to continue with ubuntu the fact that i'm not able to connect to the internet via ubuntu. please help.

Go to the terminal and type:
```
sudo gedit /etc/wvdial.conf
```

Also remember that when you run the wvdial hsdpa to add the sudo as well.
```
sudo wvdial hsdpa
```

---

### Post by WillemToerien on 2008-06-18
> **woodbrick said:**
> The Vodaphone driver did not work for me, I think because I am with Three AU. In fact it crashed my connection completely. I have never been able to get the modem to work through network settings, so I have always just connected through terminal using wvdial. After installing the voda driver, I got an error saying that the software could not access the device (it did recognise it). After that, no matter what I tried, I got this error when trying to run wvdial:
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jun 14 18:32:40 2008
--> Pid of pppd: 9266
--> Disconnecting at Sat Jun 14 18:32:40 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

I ended up doing a clean install, and so far everything is working fine. I would like to know how to set up the network connection, but I am very wary of fixing that which is not broken! Beware three customers with a "working" connection, the vodaphone driver may not be for you! Thanks Norad for trying to help.

Have you tried running the vodafone driver as root?
```
sudo vodafone-mobile....
```

---

### Post by woodbrick on 2008-06-22
> **WillemToerien said:**
> Have you tried running the vodafone driver as root?
```
sudo vodafone-mobile....
```
Yes, the application would run, but it was never successful at communicating with the device. I think this is because the E220 comes loaded with some carrier-specific info and my carrier is not vodaphone (I am with 3 mobile Australia). In any case it was not really a major drama, as my install was so new I just re-installed. Alazy solution, I know, but one with gauranteed success! Thanks anyway...

---

### Post by rykel on 2008-06-23
Hi all,

I just have a new problem with the official Vodafone Mobile Connect Card Driver for Linux and Huawei E270 here...

Ever since I installed Hardy Heron and used the VMC 2 Beta 3, IF I took out the device, I **MUST** reboot the PC with it inserted in order to reconnect to the internet again.

This is really lousy because I could easily unplug and plug the Huawei into the same machine running Gutsy with VMC 1.99.19 sometime ago.

I believe this is NOT a VMC problem, but something that Ubuntu developers have done to the way the system hotplugs the USB Huawei device.

Please help?

---

### Post by chmac on 2008-06-23
> **rykel said:**
> Hi all,

I just have a new problem with the official Vodafone Mobile Connect Card Driver for Linux and Huawei E270 here...

Ever since I installed Hardy Heron and used the VMC 2 Beta 3, IF I took out the device, I **MUST** reboot the PC with it inserted in order to reconnect to the internet again.

This is really lousy because I could easily unplug and plug the Huawei into the same machine running Gutsy with VMC 1.99.19 sometime ago.

I believe this is NOT a VMC problem, but something that Ubuntu developers have done to the way the system hotplugs the USB Huawei device.

Please help?

I think you'll get a much better response to this question if you post it as a new thread. This is the archive section of the forum.

---

### Post by bittner on 2008-07-07
For anyone using a **Huawei E169H** modem (USB stick) maybe interesting to know: I got my modem working under KDE without any additional software. (Kubuntu Hardy with kernel 2.6.24-19-generic)

For 3 in Austria (Drei.at) I only needed to create a PPP connection using

[LIST]
[*]APN: drei.at
[*]Dial-in number: *99#
[/LIST]

I get an IP address and the correct IP addresses of the nameservers dns1.drei.at and dns2.drei.at put into /etc/resolv.conf, which I can ping successfully. Also, Skype connects successfully.

The only thing that still doesn't work is surfing the internet, i.e. browsing. I still need to find out how to fix this, but that most probably a minor issue to resolve (any hints?).

Here the German post with detailed setup information that I intend to submit on umtslink.at:
[INDENT][SIZE="1"]Das Huawei H169G blinkt beim Einstecken kurz ein paar Mal grün (gleich wie unter Windows), dann aber bald schon nur mehr blau (interessanterweise gibt es "blau blinken" gar nicht als Möglichkeit laut beiliegendem Beschreibungsheft). Das braucht aber gar nicht zu beunruhigen, es reicht jetzt, eine Einwahlverbindung (PPP), z.B. mit KPPP, anzulegen. Dafür habe ich nur die folgenden Informationen von Drei gebraucht (danke 3Serviceline!).

  APN: drei.at
  Einwahlnummer: *99#

Also:

1. KPPP starten
2. "Konfigurieren..." drücken
3. Zum Reiter "Modem" gehen und neues Modem anlegen:
3.a. "Neu..." drücken, Modem Name "Huawei_E169E", bei "Modem" "/dev/ttyUSB0" auswählen, "OK" drücken.
3.b. Anschließend kann man optional das Modem testen ("Bearbeiten..." drücken, Reiter "Modem" anwählen und "Modem abfragen..." klicken. Nach ein paar Sekunden kommen plausible Ergebnisse - in allen Feldern das Gleiche: "Manufacturer: huawei  Model: E169G  usw."
4. Account anlegen:
4.a. Im KPPP den Reiter "Account" anwählen, "Neu..." klicken, "Manuell anlegen" wählen, dann bei "Name Verbindung" "Drei (Huawei E169G)" eintragen, "Telefonnummer hinzufügen..." klicken und "*99#" eintragen, bei "Autentifizierung" "Mit Script" wählen (bei PAP/CHAP verlangt das KPPP Benutzernamen und Passwort, was wir nicht brauchen), "OK" drücken. - IP, Gateway und DNS bleiben "dynamisch", wie standardmäßig ausgewählt.
5. Dann kann es schon ans Eingemachte gehen: "OK" drücken, um den Konfigurationsdialog zu schließen, Verbindung "Drei (Huawei E169H)" auswählen und "Verbinden" drücken! - Nach wenigen Sekunden schon leuchtet das Licht am Modem/USB-Stick durchgehend grün, blau oder blaugrün, d.h. Hurra, wir haben eine Verbindung mit Drei! - ifconfig zeigt dann eine PPP-Verbindung (ppp0) mit aufrechter IP-Adresse. In /etc/resolv.conf findet man die beiden nameserver, die man erfolgreich anpingen kann.

Hinweise:
- Damit das Ganze klappt, habe ich die Abfrage des PINs ausgeschaltet. Das kann man mit dem 3DataManager unter Windows machen oder aber mit dem "[Vodaphone Mobile Connect](http://vodafonebetavine.net/web/linux_drivers)" Tool aus England (der Name ist wurst, das Tool funktioniert in jedem Land für jeden Provider für diesen Stick).
- Das Verwenden von usb_modeswitch und/oder salutis-connect, wie [woanders im Internet suggeriert](http://samiux.wordpress.com/2008/04/23/huawei-e169g-on-ubuntu-804/) (und scheinbar erfolgreich eingesetzt) hat bei mir nichts bewirkt, ist also nicht notwendig.
[/SIZE][/INDENT]

---

### Post by chmac on 2008-07-07
> **bittner said:**
> For anyone using a **Huawei E169H** modem (USB stick) maybe interesting to know: I got my modem working under KDE without any additional software. (Kubuntu Hardy with kernel 2.6.24-19-generic

In a similar vein, I plugged my Huawei E220 into Ubuntu 8.04 (2.6.24-19-generic) and it "just worked". I had issues with the vodafone software and umtsmon, but gnome-ppp worked fine (with the right init strings). I upgraded to NetworkManager 0.7 and that now handles the connection fairly flawlessly. Happy days. :)

---

