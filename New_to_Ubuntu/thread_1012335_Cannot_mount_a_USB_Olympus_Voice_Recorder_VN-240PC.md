---
title: "Cannot mount a USB Olympus Voice Recorder VN-240PC"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Lorin Ricker on 2008-12-15
I've got a digital voice recorder, an Olympus VN-240PC, which looks and attached like any USB device -- except that it does not automount.

I can see it in a list of USB devices, like this (see "Bus 001 Device 006"):

```
$ lsusb
Bus 002 Device 006: ID 0dda:0001 Integrated Circuit Solution, Inc. 
Bus 002 Device 005: ID 058f:6337 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 07b4:020d Olympus Optical Co., Ltd Digital Voice Recorder VN-240PC
Bus 001 Device 005: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 002: ID 03f0:0b17 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```Question is (and similar questions have been asked on this Forum before, but never answered):

How do I mount this device?

If it's a simple USB device (which *should* operate just like a USB memory stick, I'd guess), what **/dev/sd...**, if any, can or should I use?

TIA!
-- Lorin

---

### Post by stoogiebuncho on 2008-12-15
Did you check in the /media folder to see if it was there?

---

### Post by Lorin Ricker on 2008-12-15
> **stoogiebuncho said:**
> Did you check in the /media folder to see if it was there?
Yes, I've checked, and it's not there.  I can account for all mounted devices in /media (such as /media/cdrom, /media/SD4GB (an SD-card), and /media/USB1-8GB (a USB stick)) ...no joy looking for the Olympus voice recorder.  It's really not automounting, to the best that I can see or find...

Other ideas?  TIA!
  -- Lorin

---

### Post by ignacio69 on 2008-12-27
Dear Lorin, as it was posted previously ans is confirmed  by olympus, the VN type of voice recorder does not work as usb mass storage, only the ds and the ws.
I am about to buy a voice recorder and I have searched the net in order to find the proper brand and i think i am going to choose olympus, but not the vn type.
sorry for the news.
however there is a possibility of writing something in the config.sys to make ubuntu to recognice it.
i am not sure how, as i am also new in ubutu, but studying SAMBA (please, not be confused SAMBA has nothing to do with voice recorder devices, it is just an example) someone wrote a line to recognice other devices that are not recogniced automatically.
as you are new in ubuntu, you may have not tried to read the manual page for mount?

here is how:
1.start konsole or terminal (you can do it with ALT+F2) and write terminal
2. once in the konsole, type: man mount
3. read it properly
4. try it.
5. ask in the forum is something is not clear

---

### Post by Lorin Ricker on 2008-12-27
> **ignacio69 said:**
> Dear Lorin, as it was posted previously ans is confirmed  by olympus, the VN type of voice recorder does not work as usb mass storage, only the ds and the ws.
I am about to buy a voice recorder and I have searched the net in order to find the proper brand and i think i am going to choose olympus, but not the vn type.
sorry for the news.

Many thanks for this, ignacio69!  It is good to know what *cannot* work, so as to quit wasting time on the undoable, and to pursue more useful things!  Yes, I too will start shopping for a better Olympus DS or WS type voice recorder.  They're cheap enough, and I'll just give my old VN unit to someone with a Windows system who can use its proprietary download software! :P

I will indeed follow your advice to read the man mount section thoroughly, if not for this purpose, then for something more fruitful in the future!  Again, my thanks for your thorough and helpful response!

P.S.  I found an older thread, perhaps the one you're referring to, here:  [http://ubuntuforums.org/showthread.php?t=611583](http://ubuntuforums.org/showthread.php?t=611583)

Also, this thread [http://ubuntuforums.org/showthread.php?t=558730](http://ubuntuforums.org/showthread.php?t=558730) and these may help:
[http://www.qbik.ch/usb/devices/showdr.php?id=286](http://www.qbik.ch/usb/devices/showdr.php?id=286)  and  [http://code.google.com/p/odvr/](http://code.google.com/p/odvr/)

---

### Post by ignacio69 on 2009-01-09
Dear Lorin,
at the end I bought a philips Lfh860, it records in mp3 which is propietary software, but it works as a usb mass storage and it is recognized by ubuntu 8.10 inmediately and without problems.

---

### Post by hellomoto on 2009-01-09
hello, 

I have an olympus VN-2100PC voice recorder. I was going to do a HOWTO on this but never got around to it. 

They DO work with ubuntu. But you have to install a little software first called ODVR. Your model is listed as compatible with the software.

It can be downloaded from here:
[http://code.google.com/p/odvr/]("http://code.google.com/p/odvr/")

1. The file is a simple .deb install (click and it will install).
2. After install is complete, plug in your voice recorder.
3. Open a terminal and type: odvr -l
4. To see a list of other commands to manipulate ur files on your voice recorder type: odvr -h

```

-= Options =-
  -h             : This help.
  -v             : Print version.
  -d <folder>    : Download all files in <folder>.
  -e             : Download everything.
  -l             : List all files.
  -x <folder>    : Delete all recordings in <folder>.
  -c             : Delete all recordings.
  -y             : "yes" to all yes/no questions.
  -r             : Reset the DVR. This may fix some sync issues.
  -D             : Enable debug tracing.

```

you now have a working voice recorder... enjoy :)

---

### Post by LyonTamer on 2009-01-14
Thank you! I've been searching all over the internet for that code. :D Thanks so much! It works with my VN-4100pc.

---

### Post by magicfab on 2010-04-12
Hellomoto, thank you for sharing such information. I was able to help someone get their recorder recognized and get files from it. I have since filed a needs-packaging request for odvr:
[https://bugs.edge.launchpad.net/debian/+bug/561575](https://bugs.edge.launchpad.net/debian/+bug/561575)

---

### Post by vayira on 2010-04-13
Using ub9.10 karmic 64bit 
doesn't work with the VN-240PC
unless I use sudo

Any suggestions as to how to avoid that so others users can use the device?
Here is some info...

```

xxx:~$ odvr -l
Failed to open Olympus device: couldn't claim interface

xxx:~$ lsusb
Bus 003 Device 003: ID 07b4:020d Olympus Optical Co., Ltd Digital Voice Recorder VN-240PC

```
**but**
```

xxx:~$ sudo odvr -l
[sudo] password for xx: 
Model: 1100PC
Folder A (5 files):
Slot File     Length       Date          Quality
1    92     00:22:52  4/08/2010 22:51:24 HQ
2    93     00:18:36  4/08/2010 23:16:10 HQ
3    94     00:20:28  4/08/2010 23:37:39 HQ
4    95     00:29:58  4/09/2010 23:59:10 HQ
5    96     00:49:05  4/10/2010  4:25:24 HQ
Folder B (0 files):
Slot File     Length       Date          Quality
Folder C (0 files):
Slot File     Length       Date          Quality


```

shame it only works with XHP quality files

---

### Post by muranyia on 2010-04-15
> **vayira said:**
> Using ub9.10 karmic 64bit 
doesn't work with the VN-240PC
unless I use sudo

Any suggestions as to how to avoid that so others users can use the device?
Here is some info...

```

xxx:~$ odvr -l
Failed to open Olympus device: couldn't claim interface

```

Make sure 41-odvr.rules is copied to /etc/udev/rules.d/

> **vayira said:**
> ```

xxx:~$ lsusb
Bus 003 Device 003: ID 07b4:020d Olympus Optical Co., Ltd Digital Voice Recorder VN-240PC

```
**but**
```

xxx:~$ sudo odvr -l
[sudo] password for xx: 
Model: 1100PC
Folder A (5 files):
Slot File     Length       Date          Quality
1    92     00:22:52  4/08/2010 22:51:24 HQ
2    93     00:18:36  4/08/2010 23:16:10 HQ
3    94     00:20:28  4/08/2010 23:37:39 HQ
4    95     00:29:58  4/09/2010 23:59:10 HQ
5    96     00:49:05  4/10/2010  4:25:24 HQ
Folder B (0 files):
Slot File     Length       Date          Quality
Folder C (0 files):
Slot File     Length       Date          Quality


```

shame it only works with XHP quality files

shame we dont know C programming and cannot integrate the decoder into the project! ;o)
however, it exists, and you can grab it from the project's page Issue #6 Comment #51: [http://code.google.com/p/odvr/issues/detail?id=6#c51](http://code.google.com/p/odvr/issues/detail?id=6#c51)

download both files to a folder and issue 'make' in that folder.

then you can decode your raw files (downloaded with 'odvr -E') by simply issuing 'nasced xyz.raw'

---

### Post by cantillon on 2011-04-12
> **vayira said:**
> Using ub9.10 karmic 64bit 
doesn't work with the VN-240PC
unless I use sudo

Any suggestions as to how to avoid that so others users can use the device?


I have found two ways of solving this:

1. The first (and in my opinion, better) solution is to add your user to the audio group:

```
sudo adduser $USER audio
```

log out and then log back in ubuntu.

2. The other way of fixing this is to edit the 41-odvr.rules file, that you will find in the /etc/udev/rules.d folder. You have to do this:

Open /etc/udev/rules.d/41-odvr.rules as root in gedit (or other text editor):

```
sudo gedit /etc/udev/rules.d/41-odvr.rules
```

The file should look like this:

> SUBSYSTEM=="usb", SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="020d", ACTION=="add", GROUP="audio", MODE="0664"

You have to substitute OWNER="<you_username>" for GROUP="audio", so that the file looks like this:

> SUBSYSTEM=="usb", SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="020d", ACTION=="add", OWNER="<your_username>", MODE="0664"

(Write your username where it says <your_username>)

Save the file and close gedit.

Reload the udev rules by running:

```
sudo udevadm control --reload-rules
```

Unplug and replug your olympus recorder, and that's it.

Keep in mind that if you opt for the second alternative your user is the only one who will be able to use the program.

---

### Post by Lorin Ricker on 2011-04-12
Many thanks, cantillon -- this really helped... so far.  But, after installing odvr, I'm still having to use sudo to overcome the "Failed to open Olympus device: couldn't claim interface" error.  I have done/verified the following:

```

$ id $USER
uid=1111(lorin) gid=1010(rickernet) groups=1010(rickernet),4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),106(fuse),107(lpadmin),110(netdev),114(admin),122(sambashare),1001(lorin)

```confirms that my account does have the "29(audio)" group.  Next, the rules file does exist, and is world-readable:

```

$ ls -l /etc/udev/rules.d/41-odvr.rules 
-rw-r--r-- 1 500 500 118 2008-04-14 16:57 /etc/udev/rules.d/41-odvr.rules

$ cat /etc/udev/rules.d/41-odvr.rules 
SUBSYSTEM=="usb_device", SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="020d", ACTION=="add", GROUP="audio", MODE="0664"

```So, GROUP="audio" should work, no?  I've even reloaded the rules:

```

$ sudo udevadm control --reload-rules

$ odvr -l
Failed to open Olympus device: couldn't claim interface

```Any more ideas as to why I still have to use sudo to get odvr to work?  TIA, and thanks again for your great help so far!...
-- Cheers :D  Lorin

---

### Post by cantillon on 2011-04-12
Hi Lorin,

Try to log out and back in ubuntu after you add your user to the audio group. That might work.

And yes, GROUP="audio" should work. If you go for the first alternative you don't need to modify the rules file.

Cheers

---

### Post by jeid on 2011-05-01
When editing "/etc/udev/rules.d/41-odvr.rules", I also had to rename "usb_device" to "usb" to make it work without sudo.

---

