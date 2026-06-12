---
title: "USB ADSL Modem Manager"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by StevenHarper on 2007-10-21
Hi everyone:

First my apologies for not spotting that my Application was broken in Gutsy 

I understand how much pain it must have caused, and for Future releases I will make sure (and Test) well before release dates.

Anyhow now that thats done with, I can announce that I have fixed the problem and uploaded the new DEB

as always the Wiki is at

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page)

and the Release is at (v5.5)

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

The problem was in the Detection code, a change to how USB devices are detected and listed broke it.

Can we please use this thread as a central point from now on, as the OLD one is closed.

Thanks for sticking with me

Steve

---

### Post by jfrancis on 2007-10-21
Hi Steve,

Thank you for raising awareness of your USB modem manager software.  It looks just the ticket but for some reason it will not work for me.

I have a clean install of Gutsy 7.10 and own a speedtouch 330 modem.  I downloaded your latest version v5.5 but I get the "starting up" message when I hover over the icon and nothing happens from there.

---

### Post by StevenHarper on 2007-10-22
Can you please start the Manager from a console

```
usbadslmodemmanager
```

and tell me what output you get?

also please send me your

```
/var/log/syslog
```

and I can work out whats wrong

Steve

---

### Post by asbani on 2007-10-22
Hi steve, I have installed the 5.5 deb, and ran it good, it goes into my systray and configure it with my username password, but I can't seem to connect via it to the internet. it looks like it stuck in my system tray, i put my mousehover on it and it says "Starting up" all the time. and my both lights on speedtouch330 silver are working. even tho the phone line is not there. but the LINE light is up and working "Not blinking" Thats weird because the phone right now is in the router, I want to connect with usb modem but not router, can you help me please?


"EDIT: I try to right click the system tray icon and then Quit - It doesn't quit, its just staying in there"

---

### Post by StevenHarper on 2007-10-22
Can you try the commands in my last POST

and tell me what you see.

To get rid of the manager open a terminal and enter

```
pkill -9 usbadslmodemmanager
```

Steve

---

### Post by jfrancis on 2007-10-22
Hi Steve,

This is what the terminal output is when I run it for the 1st time:

> 
Root is /usr/share/apps/usbadslmodemmanager
sudo command will be gksudo
about to load path : /usr/share/apps/usbadslmodemmanager/data/langs.xml
xmllangs: XML file succesfully parsed
Language selected is : English
test language is working: The New Firmware has been installed
Please unplug, then re-plug in the Modem
Status Started
checking : ps -ef | grep "pyt[h]on ./USBAdslModemManager.py"
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 382
Traceback (most recent call last):
  File "./USBAdslModemManager.py", line 778, in updateStatus
    self.lastStatusString = self.statusMonitor.updateStatus()
  File "/usr/lib/usbadslmodemmanager/USBAdslModemStatus.py", line 73, in updateStatus
    self.status_modemIdAsInt = float( self.status_modemId);
ValueError: invalid literal for float(): can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permi


THEN I enter the configuration screen and enter my details and save and this is returned in the terminal:

> 
Show Config Event!
Saving Configuration
Updating all Labels - lang : English
Making a Auto Start on Login
autostart
cannot remove `/etc/rc2.d/S95usbadslmodem': No such file or directory
Removed RC2 link


I hope this helps.

I see you also want the syslog file.  How do I send you this?  It looks quite big to paste here.

Thanks for you help on this.

---

### Post by StevenHarper on 2007-10-22
Hi Again,

I have found another bug, and fixed it.

The problem was that I was running my test box as root, and the lsusb command used in the modem detection behaves as root, but splurges text to the console, thus confusing the Modem detection.

I HAVE tested the new release 

**Release 0.5.6**
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Please download and report if it works

Thanks

Steve

---

### Post by StevenHarper on 2007-10-22
Arrgg : Its still broken...

I have to make a quick fix : watch this space.

Steve

---

### Post by neophit on 2007-10-22
Take your time... It's not the end of the world. However, it's frustrating to see that something that worked in one previous version of kernel, it doesn't work anymore. Even Microsoft try to make things backward compatible.

---

### Post by StevenHarper on 2007-10-22
Ok Another BUG fixed, I have tested from a full reboot with the firmware removed.

The last problem, was that the terminal I was testing from had gksudo rights.

The new '''release 0.5.7''' is tested from a full reboot.


You can download it at
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Thanks for your patience 

Steve

---

### Post by jfrancis on 2007-10-22
Hi Steve,

Still no joy for me, However I am much closer.  No more "starting up" message, I have a green light showing on the icon, and it looks all ready to go, but when I connect, it will not authenticate me.  I have checked my login details several times and know they are correct.

Here is the terminal:

> 
atom@atom-desktop:~$ usbadslmodemmanager
USB Adsl Modem Manager V0.5.7 (2007/10/22 16:51:00)
Root is /usr/share/apps/usbadslmodemmanager
sudo command will be gksudo
about to load path : /usr/share/apps/usbadslmodemmanager/data/langs.xml
xmllangs: XML file succesfully parsed
Language selected is : English
test language is working: The New Firmware has been installed
Please unplug, then re-plug in the Modem
Status Started
checking : ps -ef | grep "pyt[h]on ./USBAdslModemManager.py"
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Connect pushed
**--------Starting Connecting Stuff--------**
Into kill connection
Making Secrets
Making PPP Script
-------Attempting Auth-------
AuthThread Started
After sleep AuthResponse length is : 0
Auth seems Hung!
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Auth process there: 9208
9209
9210
Into kill connection
Killing Connection : 9208
9209
9210
words: ['9208', '9209', '9210']
killing: 9208

killing: 9209

killing: 9210

Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Change not needed
Auth process there: 9210
Modifying Resolve Conf
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_connected.png
Updating Status!
----------STARTING DETECTION----------
DET : Firmware not Found in dmesg at line 379
DET : Stage 1 Firmware Found in dmesg at line 431
DET : Stage 2 Firmware Found in dmesg at line 432
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 433
DET : ADSL Line is up found in dmesg at line 434 details: (4416 kb/s down | 448 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 434
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(4416 kb/s down | 448 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Into kill connection
Killing Connection : 9210
words: ['9210']
killing: 9210

AuthThread results length :  Plugin rp-pppoe.so loaded.
Timeout waiting for PADO packets
Unable to complete PPPoE Discovery
Terminating on signal 15
atom@atom-desktop:~$ 



Towards the bottom of this long output, you can see what happens when I actually clicked connect.  I bolded the part (I think I found the right part).

---

### Post by StevenHarper on 2007-10-22
Ok Fantastic... we have a modem : this means that for most people 

PPPoA will work...

I can't test PPPoE, but I haven't changed anything...

So I presume that maybe just the libatm is missing

below is a snippit from my troubleshooting wiki

If you using PPPoA and you keep getting can't authenticate, then you need to see whats happening

So setup the manager to use PPPoE then close it

then type (replace 0.38 with your VC and VI settings)

```
br2684ctl -b -c 0 -a 0.38
```

This may give you the error

**br2684ctl: error while loading shared libraries: libatm.so.1: cannot open shared object file: No such file or directory**

if this is the case then you need to get the library

**sudo apt-get install libatm1 **

You will need to be connected on the internet to get this.... 

If your stuck I can get you the file...

Steve

---

### Post by FreewheelinFrank on 2007-10-22
The latest version works for me but I have to type my password every time I restart.

---

### Post by StevenHarper on 2007-10-22
You mean it Asks for Super User?

If this is the case, then yes I know this, the problem is that it needs to scan for the modem as Super User....

At the present time there is no way round this.....

I could make it run as SU, but that seems like a giant hack, maybe I can integrate with the keyring and let you auto-load the keyring on Login... I'm just not sure..

Possibly there is a better way to detect the USB Modem version and Sub Version, but I only know of lsusb, I will keep looking, but I'm not so hopefull.

Steve

---

### Post by neophit on 2007-10-22
Thank you, Mr. Steven. For me it worked. I'm even now in Ubuntu with a Speedtouch modem installed and configured with USBADSLModemManager.

---

### Post by jfrancis on 2007-10-22
> **StevenHarper said:**
> Ok Fantastic... we have a modem : this means that for most people 

PPPoA will work...

I can't test PPPoE, but I haven't changed anything...

So I presume that maybe just the libatm is missing

below is a snippit from my troubleshooting wiki

If you using PPPoA and you keep getting can't authenticate, then you need to see whats happening

So setup the manager to use PPPoE then close it

then type (replace 0.38 with your VC and VI settings)

```
br2684ctl -b -c 0 -a 0.38
```

This may give you the error

**br2684ctl: error while loading shared libraries: libatm.so.1: cannot open shared object file: No such file or directory**

if this is the case then you need to get the library

**sudo apt-get install libatm1 **

You will need to be connected on the internet to get this.... 

If your stuck I can get you the file...

Steve

This is what the terminal returns:

> 
atom@atom-desktop:~$ br2684ctl -b -c 0 -a 0.38
RFC1483/2684 bridge: Interface "nas0" could not be created, reason: Operation not permitted
RFC1483/2684 bridge: Communicating over ATM 0.0.38, encapsulation: LLC
RFC1483/2684 bridge: Fatal: failed to connect on socket


I'm sorry, but I don't know what PPPoE or PPPoA are, but I have tried both.  The latter giving me an error which tells me that is not the type for me (?).

So to recap... with PPPoE, when I hover the mouse over the icon I get this:

> 
Modem Speedtouch 330 V4.00
Line Status:  Synchronized
(4416 kb/s down | 448 kb/s up)


But when I click connect, then I get the authentication problem.  

Thanks for your time on this.  It is appreciated!

---

### Post by StevenHarper on 2007-10-22
Hi,

In the configuration panel there are 5 very important settings

[LIST=1]
[*]Username
[*]Password
[*]VC
[*]VI
[*]AuthType
[/LIST]

All these MUST be correct for the Authentication to be successful

Username: This is provided by your ISP it is usually USER@SUPPLIER
Password: This is provided by your ISP it is case sensitive
VC & VI : these are different for Each country and sometimes ISP [http://www.linux-usb.org/SpeedTouch/faq/index.html#q12](http://www.linux-usb.org/SpeedTouch/faq/index.html#q12)
Auth Type : PPPoE or PPPoA this again is chosen by your ISP

Please check your ISP support to get all these

Steve

---

### Post by Glugglug on 2007-10-22
Thankyou Steven for taking time to solve this.  I'm going to install  7.10 again later so I  will let you know how I get on.

---

### Post by FreewheelinFrank on 2007-10-22
> **StevenHarper said:**
> You mean it Asks for Super User?

If this is the case, then yes I know this, the problem is that it needs to scan for the modem as Super User....

At the present time there is no way round this.....

I could make it run as SU, but that seems like a giant hack, maybe I can integrate with the keyring and let you auto-load the keyring on Login... I'm just not sure..

Possibly there is a better way to detect the USB Modem version and Sub Version, but I only know of lsusb, I will keep looking, but I'm not so hopefull.

Steve

The culprit is lsusb-vw, or it might be  lsusb-wv.

When set to 'Autostart manager on login' and 'Connect as OS boots', there was no prompt for a password with 7.04.

Not a major problem, just a minor annoyance. At least I have a reliable connection.

---

### Post by jfrancis on 2007-10-22
> **StevenHarper said:**
> Hi,

In the configuration panel there are 5 very important settings

[LIST=1]
[*]Username
[*]Password
[*]VC
[*]VI
[*]AuthType
[/LIST]

All these MUST be correct for the Authentication to be successful

Username: This is provided by your ISP it is usually USER@SUPPLIER
Password: This is provided by your ISP it is case sensitive
VC & VI : these are different for Each country and sometimes ISP [http://www.linux-usb.org/SpeedTouch/faq/index.html#q12](http://www.linux-usb.org/SpeedTouch/faq/index.html#q12)
Auth Type : PPPoE or PPPoA this again is chosen by your ISP

Please check your ISP support to get all these

Steve


All double checked and correct.  I manually type these settings every time I connect using a script to connect the adsl modem.  But this is clumsy and so I will persist to seek a solution like you are providing :D

---

### Post by StevenHarper on 2007-10-22
Hold on I just spotted that you got

RFC1483/2684 bridge: Interface "nas0" could not be created, reason: Operation not permitted

Do you have this adaptor already Created?

If so My Code will fail, as my app needs to make it....

If so, please remove it and then try the manager again..

Ta 

Steve

---

### Post by jfrancis on 2007-10-22
> **StevenHarper said:**
> Hold on I just spotted that you got

RFC1483/2684 bridge: Interface "nas0" could not be created, reason: Operation not permitted

Do you have this adaptor already Created?

If so My Code will fail, as my app needs to make it....

If so, please remove it and then try the manager again..

Ta 

Steve

I have no idea!  How would I remove it?  

Cheers o7

---

### Post by Glugglug on 2007-10-22
Just got it running in Gutsy and so far no problems at all.

---

### Post by StevenHarper on 2007-10-22
> **jfrancis said:**
> I have no idea!  How would I remove it?  

Cheers o7

Ok firstly lets see if you do have a nas0 interface

open a Terminal, enter

```
ifconfig
```

post me the result

Steve

---

### Post by jfrancis on 2007-10-22
> **StevenHarper said:**
> Ok firstly lets see if you do have a nas0 interface

open a Terminal, enter

```
ifconfig
```

post me the result

Steve

Does the fact that I am currently online now running this command make any difference?   

Here is the output:

> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21767 (21.2 KB)  TX bytes:21767 (21.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:81.168.125.59  P-t-P:81.168.125.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:179850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:230236802 (219.5 MB)  TX bytes:8665971 (8.2 MB)


---

### Post by StevenHarper on 2007-10-22
> **FreewheelinFrank said:**
> The culprit is lsusb-vw, or it might be  lsusb-wv.

When set to 'Autostart manager on login' and 'Connect as OS boots', there was no prompt for a password with 7.04.

Not a major problem, just a minor annoyance. At least I have a reliable connection.

Yeh if you start the script during boot, it has full Super User rights.... 

Thanks for the feedback : I was worried I wan't going to get it fixed quickly... I only got wind that it was broken last night

Steve

---

### Post by StevenHarper on 2007-10-22
> **jfrancis said:**
> Does the fact that I am currently online now running this command make any difference?   

Here is the output:

Could you send me your current script you use to get online : also include the /etc/ppp/peers/ file

ta

Steve

---

### Post by winh8r on 2007-10-22
original post here was unnecessary.
I have removed version 0.5.7 and reinstalled 0.5.5 and it connected without any problems . Icon displaying in panel is "modem connected" and not "modem connected with ip".
running as user- and was asked for su when connecting-that is not a problem.
still running ok.
hope you get it all just as you want it steve- it is a great advance in ubuntu

---

### Post by asbani on 2007-10-22
EDIT: WORKED after a reboot, NVM this post

---

### Post by asbani on 2007-10-22
EDITED: IT worked after a reboot. so nvm my msg

EDIT: Only one problem tho which is weird, I think it's a bug. since I installed this and there is a window that keep coming in my applications panel and going, it just shows then disappear, and happens every 10 seconds. it says "Starting Administrato....." something like this, is it just me?

also an error came up to me when I started X with my modem plugged in and phone line, when I unplugged usb modem, and I did exit Modem Manager from my system tray and restarted X, the error didn't appear.

so that error & the window that keeps opening every 5secs then disappears within 0.5sec. and also my theme and the look of my gnome got a little broken I think with the modem manager auto-start. so i turned it off then restarted X and things went fine again. here's the error.
[http://shell.lomag.net/~org/Screenshot5.png](http://shell.lomag.net/~org/Screenshot5.png)

---

### Post by plucky on 2007-10-23
Asbani: Nice picture!!!

Steven : I have the same symptoms as asbani. The internet connection works ok.
             If you disconnect and exit the USBADSLMODEMMANAGER then the starting admin         application stops.




p.s Steven keep up the good work, Will keep an eye out on this thread.

Peter
:guitar:

---

### Post by StevenHarper on 2007-10-23
Thanks, for the feedback, I have rushed fixing everything for Gutsy, now its time to smoothen out it all out a bit.

Steve

---

### Post by asbani on 2007-10-23
Thanks plucky and thanks Steve!

well I removed the package for the time being but its truely awesome job from you steve, I'll wait for the next fix maybe, Back to my router right now and can't wait until next fixed version. I just couldn't handle the app that keeps popping and quitting every 5 seconds from my Panel. and the Graphic error msg that I posted in my last msg.

i'll keep checking here aswell for the fix, thanks again.

-Asbani!

---

### Post by StevenHarper on 2007-10-26
> **asbani said:**
> Thanks plucky and thanks Steve!

well I removed the package for the time being but its truely awesome job from you steve, I'll wait for the next fix maybe, Back to my router right now and can't wait until next fixed version. I just couldn't handle the app that keeps popping and quitting every 5 seconds from my Panel. and the Graphic error msg that I posted in my last msg.

i'll keep checking here aswell for the fix, thanks again.

-Asbani!

Its not supposed to popup like that, I will try to replicate that behavior and fix it.

If you could tell me what version of Ubuntu your using and if you have compiz installed or enabled.

A screenshot would also be great

ta

Steve

---

### Post by StevenHarper on 2007-10-26
**Version 0.5.8 is ready**

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

I have stopped the status detection (every 5 seconds) once the Modem is connected....

This should fix the popups you keep seeing

On ubuntu I was seeing the cursor switch to a spinning one every 5 seconds, with 0.5.8 it doesnt do that any more.

Please give feedback

Steve

---

### Post by StevenHarper on 2007-10-26
Do remember if you check the box in preferences : leave modem connected, then you can just shut the Tray icon and the modem stays connected.

---

### Post by asbani on 2007-10-26
Thanks I will try that version right now. and I try to take a screenshot of the window that keeps popping but Its so fast. It like pops Then Exits by itself in a quick 0.005sec, then after 5 seconds it pops again, so hard to take a screenshot of that. but Let me try that version and see if that fixes it

by the way i'm using ubuntu Gutsy 7.10

---

### Post by asbani on 2007-10-26
post deleted. will be Edited soon after the test


EDIT: Working really good so far. I can't say more :) Everything just perfect until now, will report if anything happened. Thanks STEVE <3

---

### Post by jfrancis on 2007-10-27
Yes, this version is working flawlessly for me Steve :)

Thank you very much for this.  It is a fantastic solution to those of us who have yet to purchase a proper adsl modem!

---

### Post by StevenHarper on 2007-10-27
Cheers for the positive feedback....

I hope more people find use for my Package.

Steve

---

### Post by FreewheelinFrank on 2007-10-27
Had the same flashing 'Starting Adminis....' in bottom panel as described- 0.58 has fixed that. Thanks again.

---

### Post by winh8r on 2007-10-28
hi steve,
new version installed and working a treat,runs as smooth as a smooth thing!
Thank you once again for all your efforts and the no doubt countless hours you have spent helping all us speedtouch users to get connected in Ubuntu.
Good luck with your next project!

---

### Post by StevenHarper on 2007-10-28
Which is; if your interested

[http://www.squeezedonkey.com/wiki/linux/index.php?title=EasyCrypt](http://www.squeezedonkey.com/wiki/linux/index.php?title=EasyCrypt)
[http://ubuntuforums.org/showthread.php?p=3652739](http://ubuntuforums.org/showthread.php?p=3652739)

and this one : I am determined to get onto Hardy!

[http://revu.tauware.de/details.py?upid=402](http://revu.tauware.de/details.py?upid=402)


steve

---

### Post by plucky on 2007-10-28
Magnificent Steven

Just installed it on Gutsy , working perfectly. Also managed to install on Xubuntu after resolving the dependancies. That works as well.

Thank again 

Peter

---

### Post by giornata on 2007-10-28
I just did a clean install of Ubuntu 7.10, then installed usbadslmodemmanager_0.5.8_i386.deb. I'm sorry to say it doesn't seem to work.

I've got some stuff from the system log, but I'm inexperienced with Linux and don't really know what to show.

Oct 28 17:08:59 steve-desktop kernel: [  349.512000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:09:10 steve-desktop kernel: [  360.420000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:09:21 steve-desktop kernel: [  371.332000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:09:32 steve-desktop kernel: [  382.260000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:09:43 steve-desktop kernel: [  393.172000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:09:54 steve-desktop kernel: [  404.080000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:10:05 steve-desktop kernel: [  415.000000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:10:16 steve-desktop kernel: [  425.976000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:10:27 steve-desktop kernel: [  436.908000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:10:37 steve-desktop kernel: [  447.816000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:10:48 steve-desktop kernel: [  458.736000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:10:59 steve-desktop kernel: [  469.668000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:11:10 steve-desktop kernel: [  480.580000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:11:18 steve-desktop kernel: [  488.492000] usb 2-2: new full speed USB device using uhci_hcd and address 2
Oct 28 17:11:18 steve-desktop NetworkManager: <debug> [1193591478.833149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00'). 
Oct 28 17:11:18 steve-desktop kernel: [  488.688000] usb 2-2: configuration #1 chosen from 1 choice
Oct 28 17:11:19 steve-desktop kernel: [  489.416000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
Oct 28 17:11:19 steve-desktop kernel: [  489.596000] usbcore: registered new interface driver speedtch
Oct 28 17:11:19 steve-desktop NetworkManager: <debug> [1193591479.772731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if1'). 
Oct 28 17:11:19 steve-desktop firmware_helper[7356]: main: error loading '/lib/firmware/speedtch-1.bin.4.00' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:11:19 steve-desktop NetworkManager: <debug> [1193591479.790482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if2'). 
Oct 28 17:11:19 steve-desktop NetworkManager: <debug> [1193591479.792383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if0'). 
Oct 28 17:11:19 steve-desktop firmware_helper[7372]: main: error loading '/lib/firmware/speedtch-1.bin.4' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:11:19 steve-desktop NetworkManager: <debug> [1193591479.850707] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_usbraw'). 
Oct 28 17:11:19 steve-desktop firmware_helper[7391]: main: error loading '/lib/firmware/speedtch-1.bin' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:11:19 steve-desktop kernel: [  489.736000] speedtch 2-2:1.0: speedtch_find_firmware: no stage 1 firmware found!
Oct 28 17:11:21 steve-desktop kernel: [  491.492000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:11:32 steve-desktop kernel: [  502.328000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:11:43 steve-desktop kernel: [  513.184000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:11:58 steve-desktop kernel: [  527.976000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:12:01 steve-desktop NetworkManager: <debug> [1193591521.214779] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if0'). 
Oct 28 17:12:01 steve-desktop kernel: [  531.076000] usb 2-2: USB disconnect, address 2
Oct 28 17:12:01 steve-desktop NetworkManager: <debug> [1193591521.222427] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if2'). 
Oct 28 17:12:01 steve-desktop NetworkManager: <debug> [1193591521.227704] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if1'). 
Oct 28 17:12:01 steve-desktop NetworkManager: <debug> [1193591521.232207] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00'). 
Oct 28 17:12:01 steve-desktop NetworkManager: <debug> [1193591521.234881] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_usbraw'). 
Oct 28 17:12:04 steve-desktop kernel: [  533.940000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:12:05 steve-desktop kernel: [  535.496000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Oct 28 17:12:05 steve-desktop kernel: [  535.692000] usb 2-2: configuration #1 chosen from 1 choice
Oct 28 17:12:05 steve-desktop NetworkManager: <debug> [1193591525.834794] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00'). 
Oct 28 17:12:05 steve-desktop NetworkManager: <debug> [1193591525.924401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Oct 28 17:12:06 steve-desktop kernel: [  536.308000] usb 2-2: reset full speed USB device using uhci_hcd and address 3
Oct 28 17:12:06 steve-desktop firmware_helper[7545]: main: error loading '/lib/firmware/speedtch-1.bin.4.00' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:12:06 steve-desktop firmware_helper[7548]: main: error loading '/lib/firmware/speedtch-1.bin.4' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:12:06 steve-desktop kernel: [  536.504000] speedtch 2-2:1.0: found stage 1 firmware speedtch-1.bin
Oct 28 17:12:06 steve-desktop firmware_helper[7554]: main: error loading '/lib/firmware/speedtch-2.bin.4.00' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:12:06 steve-desktop firmware_helper[7557]: main: error loading '/lib/firmware/speedtch-2.bin.4' for device '/class/firmware/2-2:1.0' with driver 'speedtch'
Oct 28 17:12:06 steve-desktop NetworkManager: <debug> [1193591526.734245] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if1'). 
Oct 28 17:12:06 steve-desktop NetworkManager: <debug> [1193591526.791663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_if2'). 
Oct 28 17:12:06 steve-desktop kernel: [  536.708000] speedtch 2-2:1.0: found stage 2 firmware speedtch-2.bin
Oct 28 17:12:06 steve-desktop NetworkManager: <debug> [1193591526.872064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6b9_4061_000E50126A00_usbraw'). 
Oct 28 17:12:10 steve-desktop kernel: [  540.164000] usb 6-8: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110
Oct 28 17:12:10 steve-desktop kernel: [  540.512000] usbcore: deregistering interface driver speedtch


Another thing I notice is that when entering username and password into the configuration, data entry hangs for a couple of secs after about 3 characters, then shows another 3 or 4, hangs, etc.

---

### Post by StevenHarper on 2007-10-29
> **giornata said:**
> I just did a clean install of Ubuntu 7.10, then installed usbadslmodemmanager_0.5.8_i386.deb. I'm sorry to say it doesn't seem to work.

I've got some stuff from the system log, but I'm inexperienced with Linux and don't really know what to show.
.

Thanks for the post, could you tell me :

[LIST=1]
[*]Are you using 32bit or 64bit Ubuntu
[*]Which Modem are you using? V0 -> V4.0
[*]Are you using Ubuntu, Kubuntu or Xubuntu
[/LIST]

You can find out the version number by running in a terminal

```
gksudo "lsusb -vvv" | grep -A 1 4061 | tail -1 | awk '{print $2}'
```

Please also post me the results of

```
ls -l /lib/firmware/
```

thanks

Steve

---

### Post by mtn on 2007-10-30
Fantastic, just installed version 5.8 on Feisty and my speedtouch 330 modem worked straight away.

Funny thing was, we (me and flatmates) just got connected to the internet and my flatmate with Vista can't get the modem to work - some compatibility error. I bet him if I could get Ubuntu working with this dodgy bit of hardware (the 330) that he would have to accept Ubuntu is better than Vista - with your .deb it was working a few mins later...hehehe.:guitar::guitar: He is hating it.

---

### Post by StevenHarper on 2007-10-30
> **mtn said:**
> Fantastic, just installed version 5.8 on Feisty and my speedtouch 330 modem worked straight away.

Funny thing was, we (me and flatmates) just got connected to the internet and my flatmate with Vista can't get the modem to work - some compatibility error. I bet him if I could get Ubuntu working with this dodgy bit of hardware (the 330) that he would have to accept Ubuntu is better than Vista - with your .deb it was working a few mins later...hehehe.:guitar::guitar: He is hating it.

It is better than Vista :p

I am very happy you found it so easy, that was my entire aim of the project, it was initialy developed for my Aunt running XUbuntu 6.10, but I found very little 1 click installs for these modems, so decided to polish it up for the public domain.

thanks for the feedback, tell your friend he can stick the Ubuntu 7.10 disk in and split the drive and have both Ubuntu and Vista on (I prefer XP myself) I do still use XP as I use my PC for gaming, so a dual boot system is perfect for anyone.

best of luck converting hiim

Steve

---

### Post by bluetec on 2007-10-31
Had the same flashing 'Starting Adminis....' in bottom panel as described- 
and i installed the 0.58 version but it did NOT fixed that. 

i think it falshes faster than every 5 seconds, maybe for one second, i've got a 32bit 3 GHz intel processor, ubuntu 7.10 and the pain-in-the-*** speedtouch 330

beside even that i have the manager running, i can't log to internet, i'll try the "br2684ctl" trick and i'll give my feedback

Thanks again in advance

---

### Post by vincentstiekema on 2007-11-01
Hi Steven,

Will there also be a 64-bit update of your wonderful tool? The 32 bit version doesnt work on my 64 bit Gutsy :(

Many thanks

---

### Post by StevenHarper on 2007-11-02
> **vincentstiekema said:**
> Hi Steven,

Will there also be a 64-bit update of your wonderful tool? The 32 bit version doesnt work on my 64 bit Gutsy :(

Many thanks

Ah good point.....

Making it now BRB

Steve

---

### Post by StevenHarper on 2007-11-02
Hi there,

the 64 bit version of 0.5.8 is made

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/)

please tell me if it works - as I don't have means to test it at my current location.

Steve

---

### Post by vincentstiekema on 2007-11-02
Great! Will test and report back as soon as I get the chance.

Thanks, 
Vincent

---

### Post by aaapha on 2007-11-02
Nice one, will also have a test ASAP and report back.  Thanks for the assistance!

---

### Post by aaapha on 2007-11-02
Spot on, all connected.  One minor problem, when I set it to not connect at boot, my Gnome went south, took forever to load and the volume control, clock and a couple of other bits refused to load.  So I set the manager to not load at boot at all, but it carried on doing so.  So I set it to connect at boot and it all went fine, only now it's hassling me for my password everytime I boot up.  Only a slight pain, but I would like to be able to choose when I go online or not.

---

### Post by bluetec on 2007-11-02
Wow, it just needed a reboot, now it works 
thanks Steven

---

### Post by StevenHarper on 2007-11-02
I see a few people were waiting for the 64bit version then

Steve

---

### Post by vincentstiekema on 2007-11-02
Hi Steven, just installed the 64 bit version 0.5.8 of your tool under Ubuntu 7.10 and it works flawlessly.

Think more and more people are depending on your tool ... I wouldn't know any other more or less straightforward way to get the ST330 working. Would be silly not to include it in the next Ubuntu release ...

Many thanks for this

---

### Post by aaapha on 2007-11-02
> **vincentstiekema said:**
> Think more and more people are depending on your tool ... I wouldn't know any other more or less straightforward way to get the ST330 working. Would be silly not to include it in the next Ubuntu release ...

Ain't that the truth.  The only alternative I found was an endless bunch of terminal twiddling, not for the beginner such as myself.  Absolutely brilliant.

---

### Post by StevenHarper on 2007-11-02
Sadly the only way it will ever get onto Hardy would be to complicate the application my either 

[LIST=1]
[*]Finding the Drivers binary chucks in the driver off the original speedtouch Driver CD
[*]Offering you to download them
[/LIST]

Both of these are silly, no-one keeps the ancient driver CD and almost every ISP structures the CD differently, secondly how can people download the drivers if they dont have internet.

The promblem is that Speedtouch is owned by Thomson, the drivers are thiers and I have no right to include them in an Ubuntu Distro - I have written to Thomson, but I just get a very standard call centre response.

Ubuntu (rightly) wont include non-free to distribute  software on thier CD's

However lots of people seem to be finding the Package (I have seen over 2gigs of bandwith a month for the DEB file)

Steve

---

### Post by invalidUser on 2007-11-07
Hi all,

I am new and just freshly installed kubuntu 7.10; 64 bit. Installed UAMM 0.5.8-64bit; sadly It cant connect to the internet, by the way, my modem is the green one, rev 0.0, ermm might not work with the rev 0.0 I wonder..

thanks Steve for the nice package

---

### Post by StevenHarper on 2007-11-08
> **invalidUser said:**
> Hi all,

I am new and just freshly installed kubuntu 7.10; 64 bit. Installed UAMM 0.5.8-64bit; sadly It cant connect to the internet, by the way, my modem is the green one, rev 0.0, ermm might not work with the rev 0.0 I wonder..

thanks Steve for the nice package


Hi, the reason why I haven't put 0.5.8 in the Kubuntu download directory is because is doesn't work (yet), I am looking into this - the problem lies if  the lsusb response from Kubuntu, I will have to make separate code for it, as I don't have a ready Kubuntu system to work and test on, this makes the job more difficult.

Steve

---

### Post by warpino on 2007-11-08
Hi everyone,

I'm an absolute newbie with linux, using Ubuntu 7.10. I really enjoy using the bash terminal, but your Modem Manager is simply amazing as it saves people (who is even less expert than I am) a lot of headaches. It works all perfect for me. Just one point: it is a bit annoying to have to insert your password every time the application is started (I think this is due to a sudo command), is it possible to get rid of it?

Thank you very much indeed and best wishes for the project,

w.

---

### Post by ubiubi on 2007-11-30
Hi Steven

I installed version 5.8 and the tray appeared but I had porblems with a conflict of ISP use rname and passwords. I have done a clean install (twice) and both times the manager installs but I get no tray. What can I do to get the tray to appear?

Thanks for all the development work you've done. It looks like a great package! 

Oh, i followed your instructions of typing  usbadslmodemmanager in the terminal and i get an internet connection- YOOHOO!
But, when I close the terminal the tray disapears. OH, well. It's a small price to pay. Any ideas for geting it to work without the terminal?

Logged off and booted up the system and guess what?..... It now works like a dream.

---

### Post by StevenHarper on 2007-12-01
> **ubiubi said:**
> Hi Steven

I installed version 5.8 and the tray appeared but I had porblems with a conflict of ISP use rname and passwords. I have done a clean install (twice) and both times the manager installs but I get no tray. What can I do to get the tray to appear?

Thanks for all the development work you've done. It looks like a great package! 

Oh, i followed your instructions of typing  usbadslmodemmanager in the terminal and i get an internet connection- YOOHOO!
But, when I close the terminal the tray disapears. OH, well. It's a small price to pay. Any ideas for geting it to work without the terminal?

Logged off and booted up the system and guess what?..... It now works like a dream.

Hmmm strange behaviour, Ill try to replicate it : were you using PPoE or PPPoA?

Steve

---

### Post by ubiubi on 2007-12-03
Hi steve

I installed the modem manager by double clicking you package on the desktop. It then installed but I was not invited to unplug the modem, enter details etc and the tray did not appear. I then installed via the terminal (I did not uninstall first because the terminal error message explained it could not find the package when I uninstalled. It then installed corectly in the terminal. Unplug modem message etc. 
I'm using PPPoA

Hope this helps for the future,
Many thanks again, Steve

Mark

---

### Post by ubiubi on 2007-12-06
hi steve

Any idea how to install the same modem in KUBUNTU/HDE
The manager refuses to install giving a file type error

Thanks for any ideas

---

### Post by -RooneY- on 2007-12-09
Hi Steve
I have installed Ubuntu 7.10 . I am not able to set up the internet connection. I use a ADSL Router DL-502T through USB. I used your package but it shows the message "modem not detected". Is it because my modem is not supported ? If not, any other solution ? 

Regards 
Rohil

---

### Post by ftmichael on 2007-12-20
Perhaps this is a silly question, but if I cannot connect to the internet, how am I supposed to download and install GDebi Package Installer or subversion?  And if I have nothing installed and just have a fresh install of Feisty (on a new Dell laptop; they haven't started making them with Gutsy yet), how am I supposed to install usb-adsl-modem-manager from a .deb that I've copied onto my laptop hard drive from a flash stick?

Also, will the most recent version work on Feisty, or should I be using an older version and then upgrading it once I have Gutsy?  Will there be any sort of compatibility error by using the most recent version with Feisty?

Michael

---

### Post by christhemonkey on 2007-12-20
Hasnt GDebi been included by default for a while?

His aim seems to be to get the program onto the live cd so you wouldnt need subversion to get the python script.


I think that is his aim:
>   Aim

The aim of this project is to allow a Gutsy Gibbon user of Ubuntu, KUbuntu or XUbuntu to use a USB ADSL Modem to get onto the Internet.

The Modem should work on Installations and Live CD's

The installation will not require a reboot.

Get this package onto the Gutsy Gibbon Live CD, so USB Modem users can get onto the Internet without anything but the CD and a Modem

Get some kind of Watcher process on USB hotplug, so if a Supported device is detected, then the user is informed and given the option of installing this package 

---

### Post by ftmichael on 2007-12-20
Is it included by default on Feisty?  I don't think it is; I think that was new in Gutsy.  If it is, that would be wonderful.

USB-ADSL-Modem-Manager is not on the Gutsy CD, though.  And the issue here is that after six tries burning a Gutsy CD and having all of them not work, I have given up.  If I can get the modem working under Feisty and upgrade to Gutsy instead of waiting two months for a CD to be shipped to me, that would be much nicer.

I'm getting conflicting messages from the aims; maybe someone can clarify for me.  I keep hearing that the aim is to get this application onto the next CD (was Gutsy, now the aim is Hardy), but then I keep hearing that because the drivers are proprietary, there is no chance that the Ubuntu team will ever allow the application onto their CDs.

Michael

---

### Post by Nikolai D. on 2007-12-26
Hi@all! And Happy new year! :) That's nice to be so welcome here. I'm glad to join the community, maybe some day i can be for help. Thank You Ubuntu! :D More i use Ubuntu (Debian as base says also something), more i like it.

Last view days i've been googlin' for information on solving my problem. Alredy was thinking to buy new modem. Best help i've founded were, Ubuntu forums, agane! 
Tryed out Steve's AdslUsbModemManager - no sucess. I guess, no support for my modem yet. And i still could not figure out how to set up my 'Conexant ADSL USB Modem'. But one day, i've checked my Windoze drivers CD and founded there some linux drivers.
[http://users.fulladsl.be/spb30297/](http://users.fulladsl.be/spb30297/)
Havent figured out yet how to set them up. When i get some results ill inform back here. I'm not that expirienced in linux atm, but have some knowledge.

And offcource. Thank you very much Steven, for all your work. People like u are the ones who make the difference. Keep up the good work, God sees everything.
So, what i tough. Maybe u can add support for this USB Modem in your ModemManager. Maybe it helps someone with same model as mine.

I wish sucess to you pakkage(/project?) and bright future. ;)

Nikolai

---

### Post by Nikolai D. on 2007-12-27
Okay. What can i say. Yesturday i had some time, to explore directorie's and readme's, of my linux usb adsl modem driver, that i've got on the modem drivers cd.
this one: [http://users.fulladsl.be/~spb30297/Linux%20driver/](http://users.fulladsl.be/~spb30297/Linux%20driver/)
 As i see, it's about recompiling the kernel. And that's really not the easyest what can be done. I don't see it like a big enjoyment to compile the kernel when u want it to 'just work'. :)
 Yes, ok, once i've alredy compiled the kernel, folowed some nice HowTo. But, now im not really in the mood for compiling. I mean, i would do it if it is the only way. I would have to. But, is there really no other way? Atleas i haven't found one yet.
 As i see, this (my driver) is also a proprietary one. I got the sorce that i have make/compile myself, to get the driver. So, as i think, there is not mutch of a chance of this driver going to be includded in UsbAdslModemManager or Ubuntu CD.
 Well. Now i have to find maybe some other explanation of setting it up. I'll do my best to look around, forums and google. But it's all time consuming. Maybe someone replays here, atleas with some advice about how i would be able to set my drivers up. :)

p.s. also gotta check here:
[http://ubuntuforums.org/showthread.php?t=354700&highlight=conexant+usb+adsl+modem](http://ubuntuforums.org/showthread.php?t=354700&highlight=conexant+usb+adsl+modem)
and here:
[http://ubuntuforums.org/showthread.php?t=190728&highlight=conexant](http://ubuntuforums.org/showthread.php?t=190728&highlight=conexant)
yet.

Enjoy the holydays guys ;)

Nikolai

---

### Post by Nikolai D. on 2007-12-27
The more i search aroud for solution, the more i get impression that easyer is go and cash out for that another modem that will connect trouth Ethernet. (i guess ill have to call to my provider, maybe modem can be changed)
Tomorrow ill have to check this one to:
[http://rajeshjayaprakash.in/conexant.html](http://rajeshjayaprakash.in/conexant.html)
But now ill betta go to sleep. -.-

p.s. half a day had to fix one persons windose PC with her screen upside down.. another half search for that bloody solution. Cuz otherwise i have to stick to this Windose. Until i solve this connection trouble.

Nikolai

---

### Post by skookem on 2007-12-29
Brilliant! Any plans for a 64-bit version?

many thanks
Neil

---

### Post by Nikolai D. on 2007-12-29
this looks like 64bit:
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/)

Enjoy -.-

Nikolai

---

### Post by supershin on 2008-01-01
Hi, I been using the ubuntu 6.10 live cd with the modem manager and now i've installed 7.04 and i went through the same process as i previously did and i cant connect. 
 After a lot of searching and skimming through posts and webpages and numerous reboots[dual boot with XP] to try the some solutions[like updating to the latest version of modem manger] I realised from  link1 that i need the library libatml. So i downloaded a tar file from link 2. 
 Now when i try to copy paste the extracted folder into the path /var/cache/apt/archive i get told i need root access. So i then searched for out how to get root access but basically i find $sudo passwd root which isn't recommended. 
 So basically how do i copy and paste/install the libatml library to be able to used this modem manager?

link 1  [http://www.squeezedonkey.com/wiki/linux/index.php?title=Troubleshooting](http://www.squeezedonkey.com/wiki/linux/index.php?title=Troubleshooting)
link 2  [http://packages.ubuntu.com/feisty/libs/libatm1](http://packages.ubuntu.com/feisty/libs/libatm1)

---

### Post by supershin on 2008-01-01
Just used gksudo nautilus to copy and paste it but it didnt work. Revisited link 2[above post] and realised i downloaded from list of files and not a deb. *sigh* Will try to copy and paste that file later, too much rebooting is quite frustrating. 
   At least once i get this up and running hopefully i'll be able to find and try out solutions quicker.

---

### Post by Ganimede on 2008-01-02
I'm very new to Ubuntu, using 7.10, and this modem manager was recommended to me as being appropriate for my ADSL connection.  I installed it a few days ago and initially it worked perfectly.  However, 2 or 3 days later it seems to be permanently stuck in 'Starting up' and won't do anything else.  Restarting it doesn't make any difference.  Can you tell me what the issue is and how to fix it?  Preferably in simple terms :)

---

### Post by supershin on 2008-01-03
After some more booting into ubuntu and then XP. I saved a file with the output of two commands: 
sudo ps -ef | grep ppp and usbadslmodemmanager , see attached file. I really have no clue why i can't authenticate, cause the firmware and synchronizing is ok.  :confused:

Forgot to mention i use pppoa.

---

### Post by teeleef on 2008-01-05
Great work Steve,  many years ago I gave up the speedtouch modem and went down the router path.  But this is a relief to all the potential Ubuntu convertees.  

I am letting friends and family trial Linux using an old PC.  The results so far are very positive, 7 out of 7 and n going back!

The commandline really scares most people in my opinion and that can put people off straightaway.  This app makes things easy again. Thank you.

One question mate, on multi-user pc's I would need to grant super-user admin rights to all users in order for Linux to find and run the modem using the lsusb thingy.?

Are there any plans to alter this so that the modem is spotted and loaded on startup perhaps, so that as users log in and out the modem is still connected.

I realise this is a small gripe but as my target newbies tend to be around or over 50 I need to make things as stress free as possible and I am afraid that superuser permissions may open a can of worms?

Still great stuff! :)



Teeleef  UK

---

### Post by JungleBeast on 2008-01-12
Hello there, I'm not sure if this is the right way to ask you for help or not, if it isn't just let me know what is.

I've installed Gutsy Gibbon 7.10 for amd 64 and am using a speedtouch 330 v 4.0

I've installed usbadslmodemmanager_0.5.8-64bit_all.deb 

I'm having trouble connecting to the net though. (Frustratingly and maybe interestingly I did connect once with it - although the computer ran really slowly as did the net. But at least it means that the configuration is correct.)

I've followed your troubleshooter, but am still not there. So here's what I found:

1. on running it in the terminal

```
chris@Esteban-Cortez:~$ usbadslmodemmanager 
USB Adsl Modem Manager V0.5.8 64bit (2008/01/14 13:46:13) 
Root is /usr/share/apps/usbadslmodemmanager 
sudo command will be gksudo 
about to load path : /usr/share/apps/usbadslmodemmanager/data/langs.xml 
xmllangs: XML file succesfully parsed 
Language selected is : English 
test language is working: The New Firmware has been installed 
Please unplug, then re-plug in the Modem 
Status Started 
checking : ps -ef | grep "pyt[h]on ./USBAdslModemManager.py" 
Updating Status! 
----------STARTING DETECTION---------- 
ifconfig returns error ppp0: error fetching interface information: Device not found 
DET : Stage 1 Firmware Found in dmesg at line 346 
DET : Stage 2 Firmware Found in dmesg at line 347 
DET : lsusb response is 4.00 
DET : Modem Found in lsusb -vvv : 4.00 
DET : synchronising found in dmesg at line 387 
DET : ADSL Line is up found in dmesg at line 425 details: (2304 kb/s down | 288 kb/s up) 
ifconfig returns error ppp0: error fetching interface information: Device not found 
----------GENERATED STATUS---------- 
noModem: False 
actual_firmwareOk: True 
actual_modemConnected: True 
actual_syncronizing: False 
self.status_lineUp: True line: 425 
self.status_lineDown: False line: 0 
actual_connected: True 
connection_ip_detail:  
----------Tool Tip----------- 
Modem Speedtouch 330 V4.00 
Line status: Synchronized 
(2304 kb/s down | 288 kb/s up) 
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png 
Updating Status! 
----------STARTING DETECTION---------- 
ifconfig returns error ppp0: error fetching interface information: Device not found 
DET : Stage 1 Firmware Found in dmesg at line 346 
DET : Stage 2 Firmware Found in dmesg at line 347 
DET : lsusb response is 4.00 
DET : Modem Found in lsusb -vvv : 4.00 
DET : synchronising found in dmesg at line 387 
DET : ADSL Line is up found in dmesg at line 425 details: (2304 kb/s down | 288 kb/s up) 
ifconfig returns error ppp0: error fetching interface information: Device not found 
----------GENERATED STATUS---------- 
noModem: False 
actual_firmwareOk: True 
actual_modemConnected: True 
actual_syncronizing: False 
self.status_lineUp: True line: 425 
self.status_lineDown: False line: 0 
actual_connected: True 
connection_ip_detail:  
----------Tool Tip----------- 
Modem Speedtouch 330 V4.00 
Line status: Synchronized 
(2304 kb/s down | 288 kb/s up) 
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png 
Change not needed 
Updating Status! 
----------STARTING DETECTION---------- 
ifconfig returns error ppp0: error fetching interface information: Device not found 
DET : Stage 1 Firmware Found in dmesg at line 346 
DET : Stage 2 Firmware Found in dmesg at line 347 
DET : lsusb response is 4.00 
DET : Modem Found in lsusb -vvv : 4.00 
 

```

and so on... 


2. so running ifconfig i get:

```
chris@Esteban-Cortez:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:89:9E:56   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:18 Base address:0x8000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
wlan0     Link encap:Ethernet  HWaddr 00:11:95:6E:61:40   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:17  
 
 
```

which seems right?


3. my /lib/firmware folder

```

chris@Esteban-Cortez:/lib/firmware$ ls -l 
total 772 
drwxr-xr-x 4 root root   4096 2007-10-16 00:25 2.6.22-14-generic 
-rw-r--r-- 1 root root    935 2008-01-14 13:57 speedtch-1.bin 
-rw-r--r-- 1 root root 775545 2008-01-14 13:57 speedtch-2.bin 
chris@Esteban-Cortez:/lib/firmware$  
 

```

There are other .bin files inside the "2.6.22-14-generic" folder. But I'm not particular confident in linux. Should I delete the whole folder? 




Thank you for any help / insights you can provide, i'll be incredibly grateful! 

Chris

---

### Post by supershin on 2008-01-13
JungleBeast thats the same error i got when i ran it in terminal. Havent ran ifconfig though. As for the firmware folder i think thats firmware for alot of other stuff as well, it seems the only ones used by this app is the speedtch files. 

Hopefully someone can enlighten us and get us online in ubuntu.

---

### Post by graemeackland on 2008-01-14
I have a similar problem running from terminal.  also I get a window saying I need root access to install firmware (regardless of whether I run usbadslmodemmanager as sudo or gksudo or as a user.) 

Also  :oops:  what is a "tray applet"  should I see something on the desktop when the modem manager is running.

(output attached)

Thanks

---

### Post by supershin on 2008-01-14
Hey graemeackland, i also get that need root access to install firmware, i even tried running it with a liveCD. However after that popup i get one saying to unplug and then replug the modem.
A tray applet in one that appears in the panel by right-clicking on it you can usually get more options.

---

### Post by JungleBeast on 2008-01-17
So supershin? have you had any luck? 
I'm completely stuck in my tracks. 
And of course you can't really do much with ubuntu til you get online. 

For the root thing, that's standard. Everyone has it with usbadslmodemmanager . 

Has anyone actually got usbadslmodemmanager working with Gutsy 7.10 on a x64 distribution?

---

### Post by supershin on 2008-01-18
Still no luck JungleBeast, I've given up since i did everything i could think of, i even tried another program called ubudsl. Also tried a liveCD of version 5.10 but I dont know which version of usbadslmodemmanager i used then.

---

### Post by graemeackland on 2008-01-20
> **supershin said:**
> Hey graemeackland, i also get that need root access to install firmware, i even tried running it with a liveCD. However after that popup i get one saying to unplug and then replug the modem.
A tray applet in one that appears in the panel by right-clicking on it you can usually get more options.

OK, I found the "tray applet".  But I seem to be stuck at the same point as you:  "need root access to install firmware" "unplug and replug" then repeat...

---

### Post by kewne on 2008-01-21
Hope this helps... I did this in Ubuntu 7.10 AMD64 connecting PPPoE... Created a little script which consists of 

1.sudo aptitude reinstall br2684ctl libatm1 (this might not be necessary but I found it works around the error of libatm.so.1 not being read or accessed or whatever)
2.sudo br2684ctl -b -c 0 -a 0.35 (this last parameter being the vp.vc you use)
3.sudo usbadslmodemmanager

After that I just fill my account data and hit connect.
Rebooted several times and still working... again I hope this solves many problems... I myself was almost on my way to buy a router :P

btw I'm pretty much a linux n00b here so i'm guessing there is a much more elegant way to do this but this works right now (kinda reminds me of old 56k connections with the long dialing times - mostly because of reinstalling...gonna add sound playing to the script to really act it out xD)

---

### Post by Nikolai D. on 2008-01-28
Hi all. Agane. :)

Ive solved my problem with my usb adsl modem. Just for info. Maybe someone can solve it also this way. So, ive calld my provider, spoke with them, and endly just changed the modem for an adsl router. So now it works on an Ubuntu install and on a Macac OS to. :D Thats it.

Have fun, everyone. And see you around :)

Nikolai

---

### Post by JungleBeast on 2008-02-16
Thanks Kewne, I'm PPPoA but that gave me another good trial of things, just sudo ing and reinstalling. 
Well, I've tried a bunch of other things including blatant attempts at the initial route that usbadslmodemmanager is supposed to do for you. But nothing seems to work.
Which is incredibly frustrating being as it worked once! and then never again!!  

I'm not too sure on the consistency of running 64 bit with this modem. 
1. The 64 bit version of usbadslmodemmanager doesn't seem to be fully configured or supported.
2. My speedtouch seems a bit dodgy anyway as just using windows it seems to manage to corrupt it's own firmware from time to time and need reinstalling. 
(In fact there are a few wierd things with these modems: I'm currently in a house share which uses the modem, and of course i have a spare speedtouch from renting somewhere else, but that old one won't work on this connection, so they might be set so you can ownly use a specific one per location so they can charge you for a new one if you need a 2nd. )
3. The modem clearly wasn't designed to run with a 64 deb linux. (or any computer at all in my opinion!)

So today I'll give up on 64 bit ubuntu and finally go to 32. I'm a newbie and I've been thrashing about with various 64 versions for 2 years now and never getting fully changed over from windows. Despite following many workarounds. 

I'll let you all know if 32 bit does actually fix the problem!!   -fingers crossed.

---

### Post by JungleBeast on 2008-02-17
:grin:  :KS  

Well there we go!  Instant solution to all problems!  
I just reinstalled with the normal 32 bit distrubtion, and following 1 reboot. Lo and behold everything just works perfectly!!!!!!!

Amazing!  I've never had everything just work for me so perfectly before!   

I'm a very happy man!!!

so clearly that was the problem. usbadslmodemmanager (64bit version) does not work in 64 Gutsy 7.10 for me.

---

### Post by why theory? on 2008-02-24
Latest version works good, thanks!

---

### Post by ellalan on 2008-02-25
Hi Steven,
It is a very well done project, congratulations.
You made it so easy even a dumb like me could do it, my PC is very old and has only 10GB with 512MB RAM. I was panicking when I couldn't connect to Internet and your Paper was my Godsend.
I have downloaded the 5.8 version and copied to CD in my laptop, then I extracted in my desktop.
That is it, rest of the procedure was just following the prompts. A big "Thank You" to you for saving my PC and I am going to enjoy UBUNTU.

---

### Post by ubiubi on 2008-02-26
Hi steven

After four months of trouble free use I'vze finally hit a problem. My linux update was rudely interrupted by by small daughter and now I can't get on the net. I have tied removing the manager and reinstalling but when I rub the usbadsl...  command in the console I get about ten lines then uplug and replug modem and then a warning that "we are not alone"!  5 another version is still operating. I don't even get the window where I can reconfigure the modem. Any suggestions?

---

### Post by ubiubi on 2008-02-29
Hi steven

I had to clear my home direcrory and reinstall ubuntu . Do you happen to know which files I should have removed from my home directory in order to reinstall the modem manager successfully.? 

Ps It's a great package (particullarly when I'm not messing up my computer!) Thanks for all your hard work! Well done!

Ubiubi

---

### Post by the.weavster on 2008-03-02
I just wanted to say thanks, I may well have abandoned Ubuntu on day one if somebody hadn't pointed me to your utility. Now everything works great and I can contemplate abandoning Microsoft instead!

Thanks again.:)

---

### Post by one_iota on 2008-03-07
> **the.weavster said:**
> I just wanted to say thanks, I may well have abandoned Ubuntu on day one if somebody hadn't pointed me to your utility. Now everything works great and I can contemplate abandoning Microsoft instead!

Thanks again.:)

I second that! My new laptop would have just been a very expensive DVD player if I had not found the Speedtouch 'drivers' (is that what they're called? LOL) through this forum.

Big thanks to Steven.

---

### Post by keithrennie on 2008-03-07
Congratulations on your adsl effort, which looks like the answer to a maiden's prayer.   A much needed contribution.   But I need help to get mine to work on my Linux laptop.  My 0nly working internet connection is a dualboot desktop running Windows XP.  Details--

:(:(I'm trying to install usbadslmodemmanager_0.5.8_i386 on my laptop which has gutsy and the KDE 3.5.8 desktop enviironment, so that I can connect to my ISP using speedtouch 330.  The laptop sees the modem as a usb device (lsusb and hardware listing) but it is not properly configured and does not connect.  

I downloaded 0.5.8.deb using a dualboot windows XP connection on my desktop, moved the file to my Sony Vaio S460P hard drive and extracted the three files.  But when I ran sudo install in the console, (the modem plugged in to the USB but without live internet connection) it the install process: read package lists, build dependency tree, and read state information.   It then terminated with the error message: "E: Couln't find package."  When I try to install the package using the KDE file manager, it tries to access the internet to download additional packages.   This seems a good old catch-22 -- I need the adsl modem manager to connect to the internet on Kubuntu, but can't install it without a working internet connection.  

 I really need this to work! I'm a bit of a linux newbie, a tinkerer from the old DOS days but persistent and so far have managed to get other  tricky devices like my Palm Tungsten to work as well as the modem for my local USA provider which I cant access from the UK.  

Any suggestions on what to try next would be gratefully received. Is there a particular location where this package is expected to be in order to work properly?  Are there other key libraries that should be installed and if so how can I get a list of them and the repositories to search, using only Windows XP or my boot CD.

---

### Post by keithrennie on 2008-03-07
Sorry to reply to myself but I just found the list of dependencies in the details tab of the installation screen.  I will try to install any missing dependent packages if I can pick them up through my Windows internet connection, then try again.  I'll post the result here, whether or not successful.

---

### Post by whatsup69 on 2008-03-12
Hi Steve,
i have also a problem with the Modem Manager. When I start up my Gutsy Gibbon with root rights I get the USB connection. The problem is to start up as user with restrictet rights because of the command "lsusb -vv". This command needs root rights. Is there a possibility to detect the modem as I do not need root rights. Is it possible to fill in the analyzed (SpeedTouch 300) values without "lsub -vv)
thanx

---

### Post by igo888 on 2008-03-15
Hi. First, I want to thanks Steve and other people who helps newbies like me, you are doing a great work.
I have Ubunu 7.10 64-bit, my modem is ST 330 silver, and I have USB ADSL Modem Manager installed. During instalation, everyting went fine! The line is synchonized and i can see the Speed. My problem is that I can't authenticate. I saw your troubleshooting wiki, but it didn't work for me. "Cannot connect please try again".
I installed the Manager, while I was in LiveCD, and the same error ocurred. Something in nas0 and ppp0. 
Can anyone help me?

EDIT> :----------STARTING DETECTION----------
ifconfig returns error ppp0: error fetching interface information: Device not found
DET : Stage 1 Firmware Found in dmesg at line 294
DET : Stage 2 Firmware Found in dmesg at line 295
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 316
DET : ADSL Line is up found in dmesg at line 331 details: (768 kb/s down | 128 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 331
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Estado da Linha: Sincronizado
(768 kb/s down | 128 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Updating Status!

---

### Post by rajesh18 on 2008-03-20
hi steven,

while connecting USB ADSL Modem Manager, there are 5 impartant settings.
for INDIA what are the VC,VI,authentiction settings?
please let me know.

help me.

---

### Post by rogerdean on 2008-03-23
Hi Steve

I second the query from teeleef and whatsup69 - at every boot my grandmother is prompted for her root password in order to connect. Is there a way around this? Or could something be modified for the next release?

Many thanks for your work
Roger

---

### Post by arturocar on 2008-03-23
Hello, working with the rfc 1483, as in Panama use this technology and many people in this fledgling system we use is discouraged gnu / linux by not having Internet.
And thank you for your time and dedication

---

### Post by Lithium17 on 2008-04-21
Are we going to see a release of this that works with 8.04 anytime soon?

I've tried using older versions, no success.

I've tried the latest versions, no success, because of unsatisfied dependencies. Namely python-gnome2extras.

I've tried satisfying these myself, with no success, every package I install only ends up throwing out more and more dependencies.

This is really irritating and is stopping me enjoying the latest release. If you could help that would be great.

---

### Post by pc-linux on 2008-04-25
> **StevenHarper said:**
> Sadly the only way it will ever get onto Hardy would be to complicate the application my either 

[LIST=1]
[*]Finding the Drivers binary chucks in the driver off the original speedtouch Driver CD
[*]Offering you to download them
[/LIST]

Both of these are silly, no-one keeps the ancient driver CD and almost every ISP structures the CD differently, secondly how can people download the drivers if they dont have internet.

The promblem is that Speedtouch is owned by Thomson, the drivers are thiers and I have no right to include them in an Ubuntu Distro - I have written to Thomson, but I just get a very standard call centre response.

Ubuntu (rightly) wont include non-free to distribute  software on thier CD's

However lots of people seem to be finding the Package (I have seen over 2gigs of bandwith a month for the DEB file)

Steve

It's not your problem Steve.
You do all your best but Ubuntu for decision of Shuttleworth SUCKS!!
Mandriva 2008.0 make Speedtouch 330 rev. 4 usb working out of the box.
I can only say I was planning to install ubuntu on the pc of the daughter of my sister (sorry but english is not my language) but I decided to give mandriva a try. I can't become fool trying to make a stupid modem working.
Many thanks Shuttleworth for you s...t and good luck!
Be free from complicancy use MANDRIVA!!!

---

### Post by thechillum on 2008-04-26
Hello.

I have just tried to use USB ADSL Modem Manager to get online using a Wubi led installation of Ubuntu 8.04.

When I went to install the software, the installation button was greyed out with the message that it was missing a dependency of Python Gnome 2 Extras.

I tried downloading that via my Windows installation and then use it with Ubuntu and I get the message that it is missing a dependency of Python! Python is already installed on this version of Ubuntu.

Thoughts?

I just want to get on the internet via Ubuntu so I can see what it is like.

I have a Speedtouch 330 (Silver coloured) USB ADSL modem.

Thanks.

---

### Post by pc-linux on 2008-04-26
> **thechillum said:**
> Hello.

I have just tried to use USB ADSL Modem Manager to get online using a Wubi led installation of Ubuntu 8.04.

When I went to install the software, the installation button was greyed out with the message that it was missing a dependency of Python Gnome 2 Extras.

I tried downloading that via my Windows installation and then use it with Ubuntu and I get the message that it is missing a dependency of Python! Python is already installed on this version of Ubuntu.

Thoughts?

I just want to get on the internet via Ubuntu so I can see what it is like.

I have a Speedtouch 330 (Silver coloured) USB ADSL modem.

Thanks.

If you want to connect to internet with Speedtouch in linux without pain download and install Mandriva 2008 Spring instead of ubuntu.
It works out of the box.:)

---

### Post by Lithium17 on 2008-04-26
> **thechillum said:**
> Hello.

I have just tried to use USB ADSL Modem Manager to get online using a Wubi led installation of Ubuntu 8.04.

When I went to install the software, the installation button was greyed out with the message that it was missing a dependency of Python Gnome 2 Extras.

I tried downloading that via my Windows installation and then use it with Ubuntu and I get the message that it is missing a dependency of Python! Python is already installed on this version of Ubuntu.

Thoughts?

I just want to get on the internet via Ubuntu so I can see what it is like.

I have a Speedtouch 330 (Silver coloured) USB ADSL modem.

Thanks.

This was my EXACT problem. And currently the only solution I found is a complete pain. The way I did it was instead of fresh installing ubuntu, I installed Ubuntu 7.10, installed the modem manger onto it THEN upgraded to 8.04. which worked.

---

### Post by thechillum on 2008-04-26
PC-Linux: Unfortunately that beats the point of trying Ubuntu!

Lithium17: Yes, that does sound a bit crazy though I might try it.

All this nonsense and hassle with my USB modem  has actually got me thinking about changing providers too. Currently with Tesco 0.5mb for £17.99 whereas I could get O2 Broadband up to 8mb (wireless router supplied) for £12.99!

---

### Post by thechillum on 2008-04-27
Hello.

I tried running Ubuntu 7.10 and running the USB Modem Manager through that installation.

It worked!

I'm going to play about with it a little more, see if I can figure out if I can export certain settings & files to Ubuntu 8.04 and see if that can work.

---

### Post by Lithium17 on 2008-04-27
> **thechillum said:**
> Hello.

I tried running Ubuntu 7.10 and running the USB Modem Manager through that installation.

It worked!

I'm going to play about with it a little more, see if I can figure out if I can export certain settings & files to Ubuntu 8.04 and see if that can work.

All you need to do is, in the Modem Manager's setup page, make sure that "Connect as the OS boots" and "Leave connected on manager exit" are checked.

That way after you upgrade to 8.04 it will still work, and you'll never need to open the manager again.

---

### Post by thechillum on 2008-04-27
Hey guys.

I finally managed to get connected using USB ADSL Modem Manager through my Speedtouch 330 (silver) modem.

Earlier I tried running Wubi with Ubuntu 7.10. That showed that by using USB ADSL Modem Manager, I could get connected to the internet.

Going back to Ubuntu 8.04, I tried installing USB ADSL Modem Manager and got an error about dependencies. The inital one regarded the python-gnome2-extras package and from there a few other dependencies too.

In order to try to get USB ADSL Modem Manager working, I went to download and install all the missing dependencies by downloading via Windows and restart into Ubuntu.

Did this a fair few times and the list of packages I got were all via:

[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages) (it's a big page)

The packages I ended up downloading were:

libgda3-3
libgda3-common
libgdl-1-0
libgdl-1-common
libgdl-gnome-1-0
python-gnome2-extras

You need to install them in order to meet the dependencies of python-gnome2-extras. I don't remember the exact order but essentially, if you can install the package, go ahead and do it. If you come across an error message re a missing dependency, try to install the missing package until all dependencies have been met and you can install python-gnome2-extras.

Once you have installed that, you should be able to install USB ADSL Modem Manager and that (if your set up is anything like mine), allow you to connect to the internet!

Cheers.

---

### Post by Riptr on 2008-04-27
Thank you very much, that fixed the issue with Ubuntu 8.04 head on.

(Now posting from 8.04 with my Speedtouch 330).

---

### Post by thechillum on 2008-04-30
Hello.

Whenever I start up Ubuntu, just after I log onto the system, a pop up saying that "lsusb --v" needs to perform administrative tasks.

I'm just wondering if anyone else has had this?

I tried saying no once and my system effectively froze (as far as I could tell) except my mouse.

To be honest, I can't say for certainty that this is related to the USB ADSL Modem Manager program.

Thoughts?

---

### Post by digitalmusic on 2008-05-01
Hi, I'm a complete newbie to linux and have just done an install of Hardy on a disused laptop which I thought I'd use for surfing.
I have installed Usbadsl modem manager along with its dependenciees and have managed to get connected twice. Now all that happens is the icon shows in tray, but before I get the chance to do anything with it it vanishes. Have tried re-running it through the menu and have reinstalled the package a couple of times, with no effect.
Can anyone please help without being too tecky. Thanks.

---

### Post by djnimrod on 2008-05-07
Hello guys,I'm new here and I have a little problem.I've installed USB ADSL Manager and everything is OK.But a few days ago my internet provider doubled my internet connection from 3mb\s to 6mb\s,the only problem is that in ubuntu(8.04) my download speed is only 490kb\s max,but in windows xp after installing new drivers for the speedtouch 330 modem and a little .reg file that changed the usb connection for BULK to ISOCHRONOUS and the speed went up to 630kb/s.Is there a way to do the same thing in Ubuntu so I can enjoy my full internet speed?Thanx

---

### Post by wolfie2x on 2008-05-08
does modem manager support eagle II chipsets? if not when will it be supported?

I'm having trouble with my Aztech DSL206U (eagle II chipset). pls help if u can..

I followed instructions given here: [ueagle-atm]("https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm")

I get the "modem operational" but it hangs up saying "LCP: timeout sending Config-Requests".

here's my details and output:

DELL INSPIRON 9400 laptop
Ubuntu 8.04 (hardy), GNOME 2.22.1
Linux wolfie-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
Core Duo: Intel T2250 1.73GHz; 1GB RAM.

tail -f /var/log/messages
May  8 08:48:50 wolfie-laptop kernel: [  155.570077] usb 3-1: new full speed USB device using uhci_hcd and address 4
May  8 08:48:51 wolfie-laptop kernel: [  153.798069] usb 3-1: configuration #1 chosen from 1 choice
May  8 08:48:51 wolfie-laptop kernel: [  153.836310] usb 3-1: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9021) Rev (0X500B): Eagle II
May  8 08:48:51 wolfie-laptop kernel: [  155.741191] usb 3-1: reset full speed USB device using uhci_hcd and address 4
May  8 08:48:51 wolfie-laptop kernel: [  154.049298] usb 3-1: [ueagle-atm] using iso mode
May  8 08:48:51 wolfie-laptop kernel: [  155.855458] usb 3-1: [ueagle-atm] (re)booting started
May  8 08:48:53 wolfie-laptop kernel: [  154.772780] usb 3-1: [ueagle-atm] ATU-R firmware version : 44e2ea17
May  8 08:48:53 wolfie-laptop kernel: [  154.775652] usb 3-1: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
May  8 08:48:53 wolfie-laptop kernel: [  154.779705] usb 3-1: [Ueagle-atm] use deprecated cmvs version, please update your firmware
May  8 08:48:53 wolfie-laptop kernel: [  154.805759] usb 3-1: [ueagle-atm] modem started, waiting synchronization...
May  8 08:48:59 wolfie-laptop kernel: [  156.492080] usb 3-1: [ueagle-atm] modem synchronization failed (may be try other cmv/dsp)
May  8 08:48:59 wolfie-laptop kernel: [  156.492095] usb 3-1: [ueagle-atm] (re)booting started
May  8 08:49:00 wolfie-laptop kernel: [  157.186349] usb 3-1: [ueagle-atm] ATU-R firmware version : 44e2ea17
May  8 08:49:00 wolfie-laptop kernel: [  157.189333] usb 3-1: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
May  8 08:49:00 wolfie-laptop kernel: [  158.998031] usb 3-1: [Ueagle-atm] use deprecated cmvs version, please update your firmware
May  8 08:49:00 wolfie-laptop kernel: [  157.223340] usb 3-1: [ueagle-atm] modem started, waiting synchronization...
May  8 08:49:13 wolfie-laptop kernel: [  161.557963] usb 3-1: [ueagle-atm] modem operational
May  8 08:53:12 wolfie-laptop pppd[6660]: Plugin pppoatm.so loaded.
May  8 08:53:12 wolfie-laptop pppd[6669]: pppd 2.4.4 started by wolfie, uid 1000
May  8 08:53:12 wolfie-laptop kernel: [  265.936718] PPP generic driver version 2.4.2
May  8 08:53:12 wolfie-laptop pppd[6669]: Using interface ppp0
May  8 08:53:12 wolfie-laptop pppd[6669]: Connect: ppp0 <--> 8.35
May  8 08:53:42 wolfie-laptop pppd[6669]: LCP: timeout sending Config-Requests 
May  8 08:53:42 wolfie-laptop pppd[6669]: Connection terminated.
May  8 08:53:42 wolfie-laptop pppd[6669]: Modem hangup
May  8 08:54:13 wolfie-laptop pppd[6669]: Using interface ppp0
May  8 08:54:13 wolfie-laptop pppd[6669]: Connect: ppp0 <--> 8.35
May  8 08:54:43 wolfie-laptop pppd[6669]: LCP: timeout sending Config-Requests 
May  8 08:54:43 wolfie-laptop pppd[6669]: Connection terminated.
May  8 08:54:43 wolfie-laptop pppd[6669]: Modem hangup

---

### Post by franzrebs on 2008-05-10
> **thechillum said:**
> Hey guys.

I finally managed to get connected using USB ADSL Modem Manager through my Speedtouch 330 (silver) modem.

Earlier I tried running Wubi with Ubuntu 7.10. That showed that by using USB ADSL Modem Manager, I could get connected to the internet.

Going back to Ubuntu 8.04, I tried installing USB ADSL Modem Manager and got an error about dependencies. The inital one regarded the python-gnome2-extras package and from there a few other dependencies too.

In order to try to get USB ADSL Modem Manager working, I went to download and install all the missing dependencies by downloading via Windows and restart into Ubuntu.

Did this a fair few times and the list of packages I got were all via:

[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages) (it's a big page)

The packages I ended up downloading were:

libgda3-3
libgda3-common
libgdl-1-0
libgdl-1-common
libgdl-gnome-1-0
python-gnome2-extras

You need to install them in order to meet the dependencies of python-gnome2-extras. I don't remember the exact order but essentially, if you can install the package, go ahead and do it. If you come across an error message re a missing dependency, try to install the missing package until all dependencies have been met and you can install python-gnome2-extras.

Once you have installed that, you should be able to install USB ADSL Modem Manager and that (if your set up is anything like mine), allow you to connect to the internet!

Cheers.

Thank you so much! After many hours I finally connected to the internet! :lolflag:

---

### Post by ezze66 on 2008-05-18
Hi.

I recently installed Ubuntu Hardy 8.04 (fresh install) and I have installed all the required dependancies and the USB ADSL Modem Manager as well. Everything works fine but I cant seem to get connected. Gives me an error about my user name or password. I think I entered them correctly: user name : ******@speedy1m
                                   password: *****
the only thing I changed was the pppoa option to pppoe. and the VC and VI numbers to 8 and 35 for my country.

this is what my syslog shows when I try to connect:

 kernel: [   48.462017] speedtch 1-1:1.0: found stage 1 firmware speedtch-1.bin
 kernel: [   48.558518] speedtch 1-1:1.0: found stage 2 firmware speedtch-2.bin

 kernel: [   53.089838] ATM dev 0: ADSL line is synchronising

 kernel: [   68.065183] ATM dev 0: ADSL line is up (1024 kb/s down | 256 kb/s up)
 kernel: [   69.729079] NET: Registered protocol family 10

 RFC1483/2684 bridge: Interface "nas0" created successfully 
 RFC1483/2684 bridge: Communicating over ATM 0.0.35, encapsulation: LLC 
 RFC1483/2684 bridge: Interface configured
 RFC1483/2684 bridge: RFC 1483/2684 bridge daemon started 
 pppd[6226]: Plugin rp-pppoe.so loaded.
 kernel: [  129.461527] PPP generic driver version 2.4.2
 kernel: [  129.536167] NET: Registered protocol family 17
 pppd[6226]: pppd 2.4.4 started by root, uid 0
 pppd[6226]: Timeout waiting for PADO packets
 pppd[6226]: Terminating on signal 15
 pppd[6226]: Exit.
 RFC1483/2684 bridge: Interface "nas0" could not be created, reason: File exists 
 RFC1483/2684 bridge: Communicating over ATM 0.0.35, encapsulation: LLC 
 pppd[6987]: Plugin rp-pppoe.so loaded.
 pppd[6987]: pppd 2.4.4 started by root, uid 0
 RFC1483/2684 bridge: Interface "nas0" could not be created, reason: File exists 
 RFC1483/2684 bridge: Communicating over ATM 0.0.35, encapsulation: LLC 
 pppd[6987]: Timeout waiting for PADO packets
 pppd[6987]: Terminating on signal 15
 pppd[6987]: Exit.



this is when I disconnect and reconnect the modem:

 kernel: [  513.765358] usb 1-1: USB disconnect, address 4

 kernel: [  514.358149] usbcore: deregistering interface driver speedtch

 kernel: [  517.730770] usb 1-1: new full speed USB device using uhci_hcd and address 6
 kernel: [  517.923664] usb 1-1: configuration #1 chosen from 1 choice

 kernel: [  518.633293] usb 1-1: reset full speed USB device using uhci_hcd and address 6

 kernel: [  518.800646] usbcore: registered new interface driver speedtch

 kernel: [  518.827516] speedtch 1-1:1.0: found stage 1 firmware speedtch-1.bin

 kernel: [  518.855733] speedtch 1-1:1.0: found stage 2 firmware speedtch-2.bin

 kernel: [  523.438442] ATM dev 0: ADSL line is synchronising

 kernel: [  538.413787] ATM dev 0: ADSL line is up (1024 kb/s down | 256 kb/s up)

 pppd[9602]: Plugin pppoatm.so loaded.

 pppd[9602]: pppd 2.4.4 started by root, uid 0

 pppd[9602]: Using interface ppp0

 pppd[9602]: Connect: ppp0 <--> 0.35

 pppd[9602]: Terminating on signal 15

 pppd[9602]: Connection terminated.

 pppd[9602]: Modem hangup

 pppd[9602]: Exit.



any ideas of why it wont connect? everything seems ok.

please help

---

### Post by Clark_ElMaSrY on 2008-05-31
At first thanks very much 

ur the man 


then i installed it and worked good at hardy heron but as this bro i have the same problema


> **thechillum said:**
> Hello.

Whenever I start up Ubuntu, just after I log onto the system, a pop up saying that "lsusb --v" needs to perform administrative tasks.

I'm just wondering if anyone else has had this?

I tried saying no once and my system effectively froze (as far as I could tell) except my mouse.

To be honest, I can't say for certainty that this is related to the USB ADSL Modem Manager program.

Thoughts?



any help please iam sick from this message

---

### Post by MichaelSM on 2008-06-18
Hi again. 

I started scouting through these pages on usbadslmodemmanager, which is a brilliant piece of work, to find answers to two questions. Hope someone can help ...

For a start, I'm using LinMint (Gutsy) at the moment and what I think is the latest usbadslmodemmanager. My first question is: Quite randomly it seems, when GDM arcs up, I have to enter my password to run the modem manager...why? It's not a major issue, but if there's something I can do, let me know. Most of the time it's an automatic connection.

Second, and more important. Gutsy's Network Manager doesn't recognise my web connection, and I'm guessing that's why Wine Doors can't function. Is there an input I can do which will 'fool' the Network Manager into reacting to the USB net connection?

Thanks for all the help in the past. There's probably a post I've missed on the last question.

Mike.

---

### Post by Sprax on 2008-07-01
Seems like a great piece of software. However... I can't get it to work. After I start it I get "starting up" and nothing happens.


**usbadslmodemmanager **gives me an error message which I have no idea what it means:

> usbadslmodemmanager
/usr/share/usbadslmodemmanager/USBAdslModemManager.py:14: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
USB Adsl Modem Manager V0.5.1 (2008/07/01 18:02:44)
Setting Path to : /usr/share/usbadslmodemmanager
xmllangs: XML file succesfully parsed
Language selected is : English
The New Firmware has been installed
Please unplug, then re-plug in the Modem
Status Started
checking : ps -ef | grep "pyt[h]on /usr/share/usbadslmodemmanager/USBAdslModemManager.py"
Updating Status!
DET : Stage 1 Firmware Found
DET : Stage 2 Firmware Found
DET : Modem Found : awk: cannot open /proc/bus/usb/devices (No such file or directory)
Traceback (most recent call last):
  File "/usr/share/usbadslmodemmanager/USBAdslModemManager.py", line 704, in updateStatus
    self.lastStatusString = self.statusMonitor.updateStatus()
  File "/usr/share/usbadslmodemmanager/USBAdslModemStatus.py", line 73, in updateStatus
    self.status_modemIdAsInt = float( self.status_modemId);
ValueError: invalid literal for float(): awk: cannot open /proc/bus/usb/devices (No such file or directory)

**dmesg**:

> [  559.657396] usb 1-2: USB disconnect, address 5
[  569.619294] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  569.808847] usb 1-2: configuration #1 chosen from 1 choice
[  190.444124] usb 1-2: reset full speed USB device using uhci_hcd and address 6
[  190.634577] speedtch 1-2:1.0: found stage 1 firmware speedtch-1.bin.4
[  192.174853] speedtch 1-2:1.0: found stage 2 firmware speedtch-2.bin.4
[  588.586695] ATM dev 0: ADSL line is synchronising
[  615.393807] ATM dev 0: ADSL line is up (4640 kb/s down | 512 kb/s up)

I'm running kubuntu / hardy.

---

### Post by georgesIII on 2008-07-10
Hi Steven, have you also tested your package on 8.04 (hardy heron)? I already downloaded your latest version but I would like to know just in case...

---

### Post by Yazan on 2008-07-11
[s]Hey, after I downloaded the latest release, I tried to run it on my Ubuntu....I got this error: error: dependency is not satisfiable: python-gnome-extras
Help is appreciated.[/s]
I read some previous posts, and thanks, it helped me!
Now, I want to know how to run the program through a terminal or a GUI..??

---

