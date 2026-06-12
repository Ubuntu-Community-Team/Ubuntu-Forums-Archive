---
title: "Medion Pocket PC"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by spnoe on 2006-11-18
I have recently returned to Ubuntu, after trying some other Distros but find Ubuntu the best for me. I am trying to connect my Pocket PC, so that I can sync my addresses, contacts etc.I have installed mulisync but can not seem to get this working. The PDA says it has a connection. Could any one give me some advice or point me in the right direction.
Help much appreciated. Thanks.
Steve

---

### Post by andreas64 on 2006-11-19
Hi,

what is the operating system of your PocketPC? If it is Windows Mobile 5, there is no way to sync now. The people of multisync are working on this.

Andreas

---

### Post by spnoe on 2006-11-20
Andreas, Thank you for your interest. The operating system for my Medion PDA is Mobile 2003. Have you any other advice?

Thank for taking the time to answer.

Steve

---

### Post by andreh on 2007-03-09
Hello, is mobile 2005 already available ?

Hello, I tried to connect a Mitac Mio P550 to Ubuntu 06.06 Dapper Drake but also I was not able to do this. Did anybody succeed in connnecting a Mitac Mio P350, an Asus N632 or an Qtek g100 to Ubunut and was able to exchange files ?
I think it already goes wrong with the driver which is NOT present. It seems it is only possible for HP IPAQ and for Palm PDA's.
Am I tright ?
If I read the book 
[b]


Ubuntu Hacks
By Bill Childers, Jonathan Oxer, Kyle Rankin
...............................................
Publisher: O'Reilly
Pub Date: June 2006
Print ISBN-10: 0-596-52720-9
Print ISBN-13: 978-0-59-652720-4
Pages: 447
[/b]
they tell me this: ** dmesg**

 1738.233238] usb 1-1: new full speed USB device using ohci_hcd and address 2 [ 1738.796279] ipaq 1-1:1.0: PocketPC PDA converter detected 
[ 1738.803167] **usb 1-1: PocketPC PDA converter now attached to ttyUSB0**

[i]
Unfortunately, this probably won't work with a Pocket PC that's too new. At the time of this writing, SynCE did not yet support the most recent Pocket PC operating system, Windows Mobile 5.0. 
The next thing you'll need to do is install some packages, but before you do so, make sure you've enabled the universe repository in /etc/apt/sources.list. Then, run sudo apt-get update to get the latest packages and install synce, dccm, and some supporting tools: [/i]
USER@ubuntu:~$ sudo apt-get install synce-dccm synce-serial librra0-tools 
            





> 
Hoi, 
Volgens mij wil mijn PocketPC 5 Mip P550 niet praten met ubuntu 06.06.
* Hoe kan ik zien hoe het device heet en waar het zit ? *

als ik dmesg in tik krijg ik
   [quote][4294926.344000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295546.535000] usb 1-1: USB disconnect, address 3
[4295550.957000] usb 1-1: new full speed USB device using uhci_hcd and address 4
maar dan had toch ook al het device genoemd moeten worden ? dus iets als
   > 'usb 4-2: PocketPC PDA converter now attached to ttyUSB0'
In 
"cat /proc/bus/usb/devices"
staat
   > T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=3340 ProdID=a0a1 Rev= 0.00
S:  Manufacturer=Mitac Corporation
S:  Product=Mio DigiWalker USB Sync
S:  SerialNumber=e61dd285-1d1d-0604-0108-00022ac1fc92
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
waarbij 
   > Driver=(none)
me wat ongerust maakt.

Daarna dit commando uitgevoerd:
   > sudo apt-get install librra0 librra0-tools librapi2-tools libsynce0 synce-dccm synce-multisync-plugin synce-serial
met o.a. dit als resultaat:
   > synce-multisync-plugin is already the newest version.
synce-serial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
en nu denk ik dat het hier is mis gegaan:
   > /dev/ttyUSB0
local address: 192.168.131.102
remote address: 192.168.131.201
no dns entry needed
die /dev/ttyUSB0 zie ik nergens, dus niet bij dmesg en ook niet in /dev met :

USER@ubuntu:~$ ls -rtl /dev/*SB*
ls: /dev/*SB*: No such file or directory


ls -rtl /dev/*sd*
[b]
Mijn vraag is dus:
Moet ik dit commando 
  sudo synce-serial-config ttyUSB0
wel geven ?
[/b]
Die ttUSB0 is toch niet goed ?


[http://www.ubuntuforums.org/showthread.php?t=136257&page=2](http://www.ubuntuforums.org/showthread.php?t=136257&page=2)
[http://www.ubuntuforums.org/showthread.php?t=136257&page=5](http://www.ubuntuforums.org/showthread.php?t=136257&page=5)
[http://ubuntuforums.org/showthread.php?t=30936&page=9](http://ubuntuforums.org/showthread.php?t=30936&page=9)


> rs@ubuntu:~$ multisync
[plugin_init:915] here
plugin_API_version
short_name
long_name
plugin_init
[sync_connect:48] ----->
[synce_info_from_file:51] unable to open file: /home/USER/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
[sync_connect:48] ----->
[synce_info_from_file:51] unable to open file: /home/USER/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[synce_connect:291] Failed to initialize RAPI
[sync_connect:62] <-----
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
[sync_disconnect:73] ----->
[synce_join_thread:260] synce_join_thread called when no thread is running
[sync_disconnect:79] <-----
[http://www.sjoerdmulder.nl/wordpress/?p=4](http://www.sjoerdmulder.nl/wordpress/?p=4)
[/quote]

---

### Post by andreh on 2007-03-24
Hello,
For Windows Mobile Pocket PC 2003 there should be enough possibilities available. For Mobile 2005 the people are working hard on it.
**It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)

> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
MultiSync is a free modular program to synchronize calendars, addressbooks and other PIM data between programs on your computer and other computers, mobile devices, PDAs or cell phones. MultiSync works on any Gnome platform, such as Linux.

Currently MultiSync has plugins for
Ximian Evolution synchronization, supporting calendar, ToDos and contacts. Multisync also support Evolution 2 
IrMC Mobile Client synchronization (supported by e.g. SonyEricsson T68i/T610/Z600, Siemens S55 phones etc.) via Bluetooth or IR on Linux, or cable connection. [b]
[Windows CE / Pocket PC synchronization](http://www.microsoft.com/windowsmobile/pocketpc/default.mspx). This plugin is part of the SynCE project, and can be downloaded there. 
Opie and Zaurus synchronization. [/b]
SyncML support (supported by e.g. SonyEricsson P800/P900 and many other phones and devices, for example the SyncML server Sync4j). SyncML also allows you to do remote connection of two MultiSync programs via an encrypted connection over the net. 
Palm synchronization. 
LDAP synchronization. 
Backup of your PIM data.
[http://multisync.sourceforge.net/news.php](http://multisync.sourceforge.net/news.php)
> [http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
**Attention Windows Mobile 2005 device owners!**

These devices do not work with SynCE. If you are interested in getting these 
[devices supported by SynCE, please join the SynCE-WindowsMobile5 mailing list](http://sourceforge.net/mailarchive/forum.php?forum=synce-windowsmobile5). Se also bug report 1332550.
[http://synce.sourceforge.net/synce/index2.php](http://synce.sourceforge.net/synce/index2.php)
> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)
> **It's a Windows Mobile 5 device. See [www.synce.org](www.synce.org).** Maart 2007
[http://www.synce.org/index.php/SynCE-Wiki](http://www.synce.org/index.php/SynCE-Wiki)


 

First you must find out what version of Windows your device is running, and visit the corresponding section below: 
For help on finding out what version of Windows your device is running, visit the Discovering your Device's Windows Version page. 
[i]Windows Mobile 2005 
**Windows Mobile 2005 support in SynCE is under development. **
For support and Installation Guides, visit the Windows Mobile 2005 Support page[/i]
[http://www.synce.org/index.php/Installation_Guides](http://www.synce.org/index.php/Installation_Guides)
> [b]STAP 1 
building SynCE with WM5 support from SVN[/b]
Install libsync, librapi2, odccm, synce-gnome 
[http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion)

[b]STAP 2
subversion of usb-rndis-lite and compiled[/b]
[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_(usb-rndis-lite))

[b]STAP 3
Starting A Connection[/b]
"sudo odccm" and then "cd synce-gnome/src" and then "python test.py"
[http://www.synce.org/index.php/Starting_A_Connection](http://www.synce.org/index.php/Starting_A_Connection)
> [http://synce.sourceforge.net/synce/qa.php](http://synce.sourceforge.net/synce/qa.php)

[b]
            Unable to initialize RAPI / Failed to get connection info

Q: I setup everything and connected my PDA but when I try the tools I get a message similar to this in SynCE 0.8 or later:


    *pstatus: Unable to initialize RAPI: An unspecified failure has occurred* [/b] 

Or this message in earlier versions of SynCE:
           [i]ReadConfigFile: stat: No such file or directory
               pstatus: Unable to initialize RAPI: Failure [/i]

If I add -d 4 as parameters to pstatus, I get this a message like this too:
[i]      [synce_info_new:31] unable to open file: /home/david/.synce/active_connection
         [rapi_context_connect:88] Failed to get connection info
[/i]

**A: This means that the PDA has not connected to dccm or that you run the tools and dccm as different users. **Please make sure that:
    1. you are not using an external USB hub
    2. you have installed the patch for the "we're stuffed" bug
    3. you supplied a password to dccm if your device is password-protected
    4. dccm was started before you ran synce-serial-start
    5. that the PPP connection is successful (look in your system logs)
    6. no firewall configuration prevents the PDA from connecting to dccm
    7. you run dccm and the tools as the same user


See * [connect](http://synce.sourceforge.net/synce/start.php) * for more information.
[http://synce.sourceforge.net/synce/qa.php](http://synce.sourceforge.net/synce/qa.php)

---

