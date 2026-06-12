---
title: "Wireless troubles on Feisty"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by chocolatedude91 on 2007-05-05
Hello,

I am completely new to Ubuntu (coming from Windows with a 4-year-old Dell Dimension PC and a Linksys Wireless-G card).  I have been impressed with Ubuntu for many reasons, but I cannot seem to get online!  It detects my Internet connection and the hardware itself, but when I try to connect it does not work.  I tried turning off WEP, but that did not work either.  So here is my current configuration:

Wireless-G Linksys card
WEP protection: 5-digit key (ASCII?) as open system
Correctly detects the network, but when I try to connect it gives up after a minute or two.

How can I connect to my wireless network?

Please keep in mind that I am not fully computer-savvy!

Thanks for your help!

---

### Post by Floppyjoe on 2007-05-05
> **chocolatedude91 said:**
> Hello,

I am completely new to Ubuntu (coming from Windows with a 4-year-old Dell Dimension PC and a Linksys Wireless-G card).  I have been impressed with Ubuntu for many reasons, but I cannot seem to get online!  It detects my Internet connection and the hardware itself, but when I try to connect it does not work.  I tried turning off WEP, but that did not work either.  So here is my current configuration:

Wireless-G Linksys card
WEP protection: 5-digit key (ASCII?) as open system
Correctly detects the network, but when I try to connect it gives up after a minute or two.

How can I connect to my wireless network?

Please keep in mind that I am not fully computer-savvy!

Thanks for your help!

You need to first find the chipset for your wireless card:
Open a terminal by clicking on Applications/Accessories/Terminal then;
For a PCI wireless device enter:
```
lspci
```
or for a USB wireless device enter:
```
lsusb
```
This will give you some info about your wireless device's chipset.
Then search the forums for a howto on how to get your specific chipset to work in Ubuntu. Most guides are fairly easy to follow and implement.

The lspci command will give you more info then the lsusb command. If you have a PCI wireless device it will be listed under "network controller".

The lsusb will give you a pciid number and possibly some vague descriptive information.
If you put that pciid into the Ubuntu forums search bar it should turn up something and if not then google it.

---

### Post by chocolatedude91 on 2007-05-06
Thank you for your prompt reply.  Here is the response after lspci:

Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI

Any suggestions?

---

### Post by chocolatedude91 on 2007-05-06
The reason I ask is that my computer is on a different floor from my router, so if I need to plug it in to download a patch or anything, I want to be at least 50% sure it will work.  Since I am new to Ubuntu, any help you give would be greatly appreciated.

---

### Post by chocolatedude91 on 2007-05-06
[Sorry, double post]

---

### Post by chocolatedude91 on 2007-05-07
-bump-

---

### Post by chocolatedude91 on 2007-05-07
Hi, I found several sections of code.  This seemed to be the most promising, so I used it, but it went wrong.  Can anyone help me see where?

apt-get install build-essential
apt-get install linux-headers-`uname -r`
ifconfig ra0 down
rmmod rt2500
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xvzf rt2500-cvs-daily.tar.gz
cd rt2500-cvs-2007050716/Module
make && make install
modprobe rt2500



<my username>@<my computer>:~$ apt-get install build-essential
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 
<my username>@<my computer>:~$ apt-get install linux-headers-`uname -r`
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 
<my username>@<my computer>:~$ ifconfig ra0 down
SIOCSIFFLAGS: Permission denied
<my username>@<my computer>:~$ rmmod rt2500
ERROR: Module rt2500 is in use
<my username>@<my computer>:~$ wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
--18:39:58--  [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
           => `rt2500- cvs-daily.tar.gz.5'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK 
Length: 251,718 (246K) [application/x-tar]

100%[====================================>] 251,718      311.38K/s             

18:39:59 (310.28 KB/s) - `rt2500-cvs-daily.tar.gz.5' saved [251718/251718] 

<my username>@<my computer>:~$ tar -xvzf rt2500-cvs-daily.tar.gz
rt2500-cvs-2007050716/
rt2500-cvs-2007050716/FAQ
rt2500-cvs-2007050716/THANKS
rt2500-cvs-2007050716/CHANGELOG
rt2500-cvs-2007050716/CVS/
rt2500-cvs-2007050716/CVS/Root 
rt2500-cvs-2007050716/CVS/Repository
rt2500-cvs-2007050716/CVS/Entries.Log
rt2500-cvs-2007050716/CVS/Entries
rt2500-cvs-2007050716/LICENSE
rt2500-cvs-2007050716/Utilitys/
rt2500-cvs-2007050716/Utilitys/CVS/ 
rt2500-cvs-2007050716/Utilitys/CVS/Root
rt2500-cvs-2007050716/Utilitys/CVS/Repository
rt2500-cvs-2007050716/Utilitys/CVS/Entries.Log
rt2500-cvs-2007050716/Utilitys/CVS/Entries
rt2500-cvs-2007050716/Utilitys/ico/ 
rt2500-cvs-2007050716/Utilitys/ico/CVS/
rt2500-cvs-2007050716/Utilitys/ico/CVS/Root
rt2500-cvs-2007050716/Utilitys/ico/CVS/Repository
rt2500-cvs-2007050716/Utilitys/ico/CVS/Entries
rt2500-cvs-2007050716/Module/ 
rt2500-cvs-2007050716/Module/auth.c
rt2500-cvs-2007050716/Module/rt2x00debug.h
rt2500-cvs-2007050716/Module/md5.c
rt2500-cvs-2007050716/Module/ifcfg-ra0
rt2500-cvs-2007050716/Module/rt2560.h
rt2500-cvs-2007050716/Module/rtmp_main.c 
rt2500-cvs-2007050716/Module/2.6.x/
rt2500-cvs-2007050716/Module/2.6.x/CVS/
rt2500-cvs-2007050716/Module/2.6.x/CVS/Root
rt2500-cvs-2007050716/Module/2.6.x/CVS/Repository
rt2500-cvs-2007050716/Module/2.6.x/CVS/Entries 
rt2500-cvs-2007050716/Module/rt_config.h
rt2500-cvs-2007050716/Module/assoc.c
rt2500-cvs-2007050716/Module/CVS/
rt2500-cvs-2007050716/Module/CVS/Root
rt2500-cvs-2007050716/Module/CVS/Repository
rt2500-cvs-2007050716/Module/CVS/Entries.Log 
rt2500-cvs-2007050716/Module/CVS/Entries
rt2500-cvs-2007050716/Module/wpa.c
rt2500-cvs-2007050716/Module/docs/
rt2500-cvs-2007050716/Module/docs/CVS/
rt2500-cvs-2007050716/Module/docs/CVS/Root
rt2500-cvs-2007050716/Module/docs/CVS/Repository 
rt2500-cvs-2007050716/Module/docs/CVS/Entries
rt2500-cvs-2007050716/Module/sync.c
rt2500-cvs-2007050716/Module/rtmp_data.c
rt2500-cvs-2007050716/Module/rtmp_info.c
rt2500-cvs-2007050716/Module/iwpriv_usage.txt 
rt2500-cvs-2007050716/Module/mlme.h
rt2500-cvs-2007050716/Module/connect.c
rt2500-cvs-2007050716/Module/rtmp_tkip.c
rt2500-cvs-2007050716/Module/auth_rsp.c
rt2500-cvs-2007050716/Module/oid.h
rt2500-cvs-2007050716/Module/rtmp_init.c 
rt2500-cvs-2007050716/Module/TESTING
rt2500-cvs-2007050716/Module/2.4.x/
rt2500-cvs-2007050716/Module/2.4.x/CVS/
rt2500-cvs-2007050716/Module/2.4.x/CVS/Root
rt2500-cvs-2007050716/Module/2.4.x/CVS/Repository 
rt2500-cvs-2007050716/Module/2.4.x/CVS/Entries
rt2500-cvs-2007050716/Module/RT2500STA.dat
rt2500-cvs-2007050716/Module/rtmp.h
rt2500-cvs-2007050716/Module/mlme.c
rt2500-cvs-2007050716/Module/md5.h
rt2500-cvs-2007050716/Module/wpa.h 
rt2500-cvs-2007050716/Module/eeprom.c
rt2500-cvs-2007050716/Module/rtmp_wep.c
rt2500-cvs-2007050716/Module/README
rt2500-cvs-2007050716/Module/rtmp_def.h
rt2500-cvs-2007050716/Module/Makefile
rt2500-cvs-2007050716/Module/rtmp_type.h 
rt2500-cvs-2007050716/Module/sanity.c
<my username>@<my computer>:~$ cd rt2500-cvs-2007050716/Module
<my username>@<my computer>:~/rt2500-cvs-2007050716/Module$ make && make install
make[1]: Entering directory `/usr/src/linux- headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
2.6 module install
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/<my username>/rt2500-cvs-2007050716/Module  modules_install 
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
mkdir: cannot create directory `/lib/modules/2.6.20-15-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux- headers-2.6.20-15-generic'
make: *** [modules_install] Error 2
<my username>@<my computer>:~/rt2500-cvs-2007050716/Module$ modprobe rt2500


After that I tried a different code, but got another error.
me@mycomputer:~$ tar -zxf rt2570-1.1.0-bl.tar.gz
tar: rt2570-1.1.0-bl.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Handssolow on 2007-05-07
Check out the Forum and you will find that the RT2500 chipset doesn't work too well with Feisty, well certainly not using Network Manager. I'm waiting for the 2x00 driver update that will put an end  to me having to input my essid and wep key in the terminal every time I bootup.

Wireless things seemed better with Edgy.

---

### Post by chocolatedude91 on 2007-05-07
Thanks Handssolow,

At this point I am perfectly willing to do anything to get online.  How do you put in the essid and wep key into the terminal?  I tried following one site's instructions, but it didn't seem to improve my situation.  How did you pull it off?

Thanks!

---

### Post by Handssolow on 2007-05-07
I'm not an expert.

I'd check in the terminal for the result of ifconfig to see if your wireless is recognised, mine is ra0 yours might be wlan0.
Next I'd check  iwconfig to see what settings have been recognised.

---

### Post by cheetaux on 2007-05-07
I am using the RT2500 chipset  (RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)) in a Linksys card using Fiesty with no problem (I'm also running it on an old Dell Dimension 4100).

There were a few things, however, that I had to do (which I learned about from the forums):

(1) Configure the wireless router for WPA security rather than WEP.  WPA is more secure and I couldn't get my wireless working in Ubuntu without switching to WPA.

(2) Remove network manager:

sudo apt-get remove --purge network-manager network-manager-gnome

(3)  Edit the /etc/network/interfaces file and add the following to the end.

iface ra0 inet dhcp
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid "PUT YOUR NETWORK ESSID HERE"
pre-up iwpriv ra0 set WPAPSK="PUT YOUR WPA KEY HERE"
auto ra0

After rebooting, your wireless should be working.

Hope this helps

---

### Post by chocolatedude91 on 2007-05-08
Thank you Cheetaux,

Unfortunately, my router does not support WPA encryption, only WEP.   Do you have instructions on how to do WEP, despite its problems?

Right now, I am network manager-less (after deleting it) and I do not know how to proceed.  I tried other things in the mean time, including some from an Italian UbuntuForums site (although I didn't understand it!).

I would appreciate your help.  I have a Dimension 4700.

---

### Post by cheetaux on 2007-05-08
Unfortunately, I don't know how to get it to work using WEP.  :(  I tried initially to get it working using WEP since that was the default configuration of my router but was unsuccessful.  Someone here should know the answer, however.

Good luck.

---

### Post by chocolatedude91 on 2007-05-08
Do you think that a different Network Manager-like program from the Feisty repositories could solve the problem, or is it a system issue?

Thanks.

---

### Post by chocolatedude91 on 2007-05-09
-bump

---

### Post by WhiteHorse on 2007-05-12
You need to add sudo before all of your commands. That's why you get "Permission denied"

---

