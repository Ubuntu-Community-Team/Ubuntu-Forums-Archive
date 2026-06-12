---
title: "Is Oracle VM virtualbox OK for using USB"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by ex-para on 2010-12-17
Is Oracle VM virtualbox OK for using USB as I have not seen Puel mentioned. I need it on 10.04 Lucy.

---

### Post by MoebusNet on 2010-12-17
I was using the latest VBox (Oracle) version on Hardy before I upgraded to Lucid; it ran well for me. USB, CD all worked. YMMV.

---

### Post by K.J. on 2010-12-17
Yes, although I would recommend getting the latest version from the virtualbox site and not use the ones in the repositories. I'm fairly certain there's a PPA with the latest version as well.

---

### Post by hwychld on 2010-12-17
Definitely install the .deb file from Oracle's site.  There are two versions, and open source one (OSE) and a PUEL one.  The OSE version does not support USB.  I think (but not 100% sure) the version in the repositories is the OSE version.

---

### Post by Vaphell on 2010-12-17
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
goto 'Debian based distributions' part, there are repos listed and some instructions

---

### Post by ex-para on 2010-12-21
Thanks for the replies. I have downloaded Oracle VM Virtualbox correct deb file for 10.04 Lucid from the the correct site but I simply can't get the USB to work. I have added a memory stick details and it is ticked and should work. When I right click the USB icon it shows the details of the stick but when I left click it says no USB devices attached. Elsewhere I get the message  State: Unavailable. Any ideas please.

---

### Post by migs73 on 2010-12-21
> **ex-para said:**
> Thanks for the replies. I have downloaded Oracle VM Virtualbox correct deb file for 10.04 Lucid from the the correct site but I simply can't get the USB to work. I have added a memory stick details and it is ticked and should work. When I right click the USB icon it shows the details of the stick but when I left click it says no USB devices attached. Elsewhere I get the message  State: Unavailable. Any ideas please.

Tyr clicking System>Administraion>Users and Groups then click on Manage Groups. Scroll down the list of groups to Vboxusers, select it, click on Properties and then check the box for your name, click OK (put in your password) then try Virtual box again. 

Mike :)

---

### Post by ex-para on 2010-12-21
Thanks for the reply, I followed your instructions then booted virtualbox and put the stick in but with no success as USB is still not working.

---

### Post by migs73 on 2010-12-21
> **ex-para said:**
> Thanks for the replies. I have downloaded Oracle VM Virtualbox correct deb file for 10.04 Lucid from the the correct site but I simply can't get the USB to work. I have added a memory stick details and it is ticked and should work. When I right click the USB icon it shows the details of the stick but when I left click it says no USB devices attached. Elsewhere I get the message  State: Unavailable. Any ideas please.

Does this mean you set up a filter? I can't rmember how to d this as I am on my works machine a teh moment, I'll post back in a bit, once I get my buntu machine booted

---

### Post by ImDougy on 2010-12-21
it never works the first time 4 me but after i restart the virtual machine it works

---

### Post by JKyleOKC on 2010-12-21
After you add yourself to the vboxusers group, you have to log out and log back in for the change to take effect.

You can check all of your group membership from the command line; here's what my setup shows (with "me" as my user name):

```
~$ grep me /etc/group
adm:x:4:me
dialout:x:20:me
cdrom:x:24:me
plugdev:x:46:me
lpadmin:x:105:me
admin:x:118:me
me:x:1000:
sambashare:x:121:me
vboxusers:x:122:me

```

If you don't have "plugdev" in your list, add yourself to that group also -- it's the one for USB access! And the numbers for the last two above may be different on your system. These groups were created after my initial system installation and picked up the next unused number in sequence...

I'm using vbox, from the Oracle site, on this system and everything is working well. However it did take some fiddling at first to get USB working properly.

---

### Post by migs73 on 2010-12-21
Okay on my Ubuntu  machine now. When you set up a filter, just leave it generic (don't fill in any device details), as this means only this device can be used (if you make a mistake inputting details, it won't work at all). If you need a filter (you have a USB device on the host you do not want mounted in Vbox) try to be as generic as possible.

I don't have any details set in my filter as I want any USB device to be available to my guest.

See Below

---

### Post by gradinaruvasile on 2010-12-21
You dont need any filters. If it is set up right, it will show your usb devices that are attached to your system if you right-click on the usb icon on the bottom bar. Each device should have a checkbox near it. This is if you have the version from the VirtualBox site that has this usb thing implemented.
Even if you cant give the devices to the VM, they should show up (greyed out if you dont have the necessary permissions).
You should rebuild the VirtualBox modules first:

service vboxdrv setup

as root/with sudo.

---

### Post by migs73 on 2010-12-21
> **gradinaruvasile said:**
> You dont need any filters.

Mine wouldn't allow me to check any devices (although shown) until after I had set a filter. That wasn't the case on my older (9.10) set up, no filters needed on that.

---

### Post by wep940 on 2010-12-21
I've used virtualbox off and on for about the last 3 years or so, and each time needed to add a generic filter to get USB devices to work.  It at least used to even be in the docs for virtualbox.

---

### Post by spillage2 on 2010-12-21
I can remember ever setting any filters. plug in my usb device and click "devices" (top left) and tick the box to enable it.

only issue i have ever had is restoring an iphone as during the restore it will disconnect the usb connection and not auto connect...(sure this is down to a setting on my part).

---

### Post by ex-para on 2010-12-22
I got the USB working thanks to all the replies, but there is no end to my problems as now when I try to install some software from an installation disc the disc is not picked up. I had this problem when installing XP on the virtualbox but was able to overcome this using the boot sequence but I don't think same thing will apply in this case so once again any help will be appreciated.

---

### Post by JKyleOKC on 2010-12-22
I've had the most success doing installation from ISO files rather than from actual CD or DVD disks. To install from a CD, I first (in my Xubuntu host) put the CD in the drive, then use the command "dd if=/dev/sr0 of=$HOME/xxx.iso" to create the ISO file in my home directory (where "sr0" is the device name of my CD drive and "xxx" is the name I want to use on the ISO file). The next step is to add the newly created ISO file to the Virtual Device Manager's list of CD drives, in vbox. Finally, in vbox, I use the "Devices" menu or the settings page for the VM to attach the ISO as its CD drive, set the boot sequence (in the VM settings) to use the CD first, and start the VM. This always seems to work; trying to use the actual CD, with its drive attached to the VM, often fails because the host system takes too long to discover that the CD is present.

Hope this helps! Having the ISO file on the host also makes it easy to process updates that insist on having the CD available, as well.

---

### Post by ex-para on 2010-12-22
nks again, I searched through Linux questions and found this 
 
Registered: Dec 2009
Distribution: Debian Sid, Arch Linux
Posts: 1,121

Rep: Reputation: 161Reputation: 161
	
In the bottom panel of the VM you have a little CD icon. Do a right-click on it and choose the line that begins with "host drive". Now insert your CD into your hosts drive and install your software.
I would recommend to have a look at the really good manual.
__________________
Registered Linux User #501265
-------------------------------------------------------------------------------------
And it worked so that seems to be that, I can't find a solved button but again thanks for every ones help.

-------------------------------------------------------------------------------------


-------------------------------------------------------------------------------------

---

### Post by JKyleOKC on 2010-12-22
That works, too. As for the "solved" button, look at the top of the page for "Thread Tools." That menu will have the link. Click it and you're done.

---

