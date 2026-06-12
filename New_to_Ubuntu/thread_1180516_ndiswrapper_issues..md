---
title: "ndiswrapper issues."
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Zilliano on 2009-06-06
Okay, so...
I'm not exactly NEW to Linux, but I'm definitely not good at troubleshooting.

Now, I recently installed Ubuntu 9.04.
Works great.
Now, I have a USR805422 Wireless USB adapter, and it's my only access to internet on this computer.
I got ndiswrapper to load the driver, but...

Well, basically, it has done absolutely nothing.
When I try to scan, I get:
lo:
Interface doesn't support scanning.

eth0:
Interface doesn't support scanning.

pan0:
Interface doesn't support scanning.

Basically, I'm stuck. What am I supposed to do now that I've got the driver installed to the device?

I really need to get this wireless network working.

Any help is appreciated.

---

### Post by coffeeaddict22 on 2009-06-06
At a guess, your problem is ndiswrapper.  Wireless support has improved out of sight; the problem now is that lots of us have ndiswrapper installed, but the kernel now has a driver as well.  Leads to collisions.  Because ndiswrapper keeps scripts in the /home folder, they stay intact during the upgrade.
Can you post back the output of ```
lshw -C network
```

---

### Post by anewguy on 2009-06-06
Indeed, even if the end result is that you still have to use ndiswrapper, there are more modules to be blacklisted now due to increased driver support.

Besides the output requested by coffeeaddict22 above, please also include the following:

lsusb

EDIT:  also include:  sudo ndiswrapper -l <- lower case "L" for "list".


Thanks!
Dave :)

BTW:  ndiswrapper is still a very valid tool, it's just that driver support for wireless has increased in 9.04, so you may be able to use a restricted driver rather than having to use ndiswrapper with the Windows drivers.  If your device is not directly supported by the new drivers, ndiswrapper is still very valid.

---

### Post by Zilliano on 2009-06-07
Hopefully all this will help.


"lshw -C network" comes back as:


 
*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:e0:4d:01:3e:69
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 66:0d:c6:e6:1b:8c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


"lsusb" presents me with:



Bus 001 Device 004: ID 0930:6545 Toshiba Corp. 
Bus 001 Device 003: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


"sudo ndiswrapper -l" gives me:



WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
rsc4usb : driver installed
	device (0BAF:0118 ) present (alternate driver: p54usb)

---

### Post by Zilliano on 2009-06-07
Shamelessly bumping, sorry. I'd love to get this fixed.

---

### Post by anewguy on 2009-06-07
Okay, I found this post in amongst some of what looks like Spanish or Italian or something stuff to me.  I think it explains things - if you need some help please post back.


Jr. Member
**
Non Connesso Non Connesso

Sesso: Maschio
Messaggi: 162

Media messaggi
		



Mostra profilo
	
	
Re: [Risolto] [Wireless] Ndiswrapper su Feisty (USB Adapter U.S. Robotics 5421)
« Risposta #5 inserita: 08 Maggio, 2007, 20:53:00 »
	
Prova a seguire la guida che ti ho postato qua sotto (presa da questo sito [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/))
è un po' difficile, prova a vedere se riesci, se no scrivimi che problemi hai...
Mi raccomando NON mollare!


      USB: US ROBOTICS USR805421 802.11g Wireless USB Adapter
          *
            Chipset:Unknown
          *
            usbid: 0baf:011B
          *
            Driver: Official U.S. Robotics [http://www.usr.com/support/5421/5421-files/5421-na.exe](http://www.usr.com/support/5421/5421-files/5421-na.exe). Unpack it and install driver with USR5421X.inf. This doesn&#8217;t copy the .sys files (.sys files for RNDIS driver are part of Windows, so they are not needed in Windows; however, driver for USR5421 distributes .sys files but they are not installed by .inf file); so copy RNDISMPK.sys and usb8023k.sys files into /etc/ndiswrapper/usr5421x directory as rndismpk.sys and usb8023k.sys respectively).
          *
            Other: Works with snapshot of 2006-02-13.
          *
            Other: With 2.6.16 and later kernels, RNDIS devices are not initialized (when device is plugged in, nothing happens). To get it going, you need to set the variable bConfigurationValue in sysfs. An easy way to do this is to add

BUS==&#8221;usb&#8221;, SYSFS{idProduct}==&#8221;001b&#8221;, SYSFS{idVendor}==&#8221;0baf&#8221;, \

    PROGRAM="/bin/sh -c 'echo 1 > /sys/%p/device/bConfigurationValue'"

to /etc/udev/rules.d/z25_local_rules file and restart udev. Replace idProduct and idVendor as appropriate; for USR5421, &#8216;lsusb&#8217; shows 001b (idProduct) and 0baf (idVendor).
	Registrato
E' sempre l'ora di Open Source!

I think the important thing to note here is besides the .inf file it explains how to get the .sys files which you must have also in order for ndiswrapper to work with your driver.  Basically, you should clear what you've loaded with ndiswrapper first, then copy the .inf and .sys files mentioned above but to your desktop, then use ndiswrapper to install them from your desktop.

Dave :)

---

### Post by Zilliano on 2009-06-08
Sadly, nothing has changed.
In fact, I can't even find the .sys files that article speaks of in the file it links to- which probably woundn't help much anyway, beings that they're for the USR805421, and not the 5422.

I put all the .sys files from the drivers for the 5422 in the directory, though, to no avail.

Maybe it's because I didn't rename them all to lowercase or something, but....
Either way, it's not working.
No changes from the readouts earlier.

Gargh. >.<

---

### Post by Zilliano on 2009-06-08
I seriously hope this isn't going to turn into some giant issue. >.>

---

### Post by cariboo on 2009-06-08
I would suggest using file roller to extract the files from the .exe you downloaded. Just right clcik the .exe file and select open with archive manager. Otherwise just extract the file in windows.

---

### Post by anewguy on 2009-06-08
First, clear anything loaded via ndiswrapper:

sudo ndiswrapper -l <- lower case "L" for "list"

IF anything is returned:

sudo ndiswrapper -e xxxxxx <- the driver name shown above

repeat the 2 steps above until ndiswrapper -l returns a blank list

Now, copy the .inf and the .sys files for your driver to your desktop. I would keep the case the same as what they extract as - look in the inf file and you'll be able to find the sys file name and match it's case.  BTW - the usb device ID in the post I quoted is identical to that for your device, so it should be the same regardless of 21 or 22.

go to a terminal window, change directory to your desktop, and use ndiswrapper to install from there.  Right after the load, be sure to do a list to be sure it shows your driver loaded.

I won't go into the details since I will assume you have read other posts with the detail steps you need to go through - I've written a few in-depth replies myself.

Dave :)

---

### Post by Zilliano on 2009-06-08
Will try that.
Btw, the Device ID is 0baf:0118 for me, and 0baf:011b for the 5421.
Sliiiight difference. >.>

---

### Post by Zilliano on 2009-06-08
Thank God- And you guys as well- It worked.
I still had to use the 5422 drivers like I pointed out, but installing from the desktop, using the COMMAND LINE instead of the Gui did the trick.
I'm up and running. :D

---

### Post by anewguy on 2009-06-08
Sorry about the mix-up on the USB id's - I guess my 54 year old eyes aren't working too well!!  :)

Just glad you got it working!

Dave :)

BTW - you did all the modprobe stuff, ndiswrapper -m, and editing of the modules file (just in case), right?  You'll know if you reboot and it still works.

---

