---
title: "Printing:  Seems impossible!"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by AVDa on 2010-01-13
Earlier I started a thread about printing and looked through my options to no avail.  Unfortunately, I cannot figure out what to do about printing.  My printer is an HP Deskjet d1420 (1400 series) and it worked great before I updated Ubuntu.  Now it just blinks or has a communication error.  It seems to have something to do with CUPS, but I'm really not sure.  In all honesty, I don't need or want a cups configuration and would prefer to just print directly.  Can't this be done with foomatic or something similar?

Help if you can.  I'm all ears.

Thanks!

---

### Post by ramjet_1953 on 2010-01-13
This has always worked for me with HP printers.

Go into Synaptic package manager and do a search for [COLOR="Blue"]hplip[/COLOR]

Make sure that these packages are installed:

1. hplip
2. hplip-gui
3. hpijs
4. hpijs-ppds
5. hplip-data

When this is done, there should be a [COLOR="Red"]HPLIP Toolbox[/COLOR] item in your System>Preferences Menu.

Make sure your printer is powered and plugged-into your PC.

Open HPLIP Toolbox and see if your printer is recognized.

If not you can configure it using the menus.

Regards,
Roger :)

---

### Post by warfacegod on 2010-01-13
I had a similar problem with my HP 7700 Photosmart last year. Turned that an update disabled the printer.

Go to System> Admin.> Printing> right click printer> check enabled

No problems since. HP generally has excellent linux printer support.

---

### Post by AVDa on 2010-01-14
I'll give both of these a try.  Give me about a half hour if it works and enough time to pull my hair out if it doesn't.  Wish me luck!

---

### Post by AVDa on 2010-01-15
Ok, tried that and nothing worked.  I think that cups and foomatic-rip might be conflicting with one another.  Can they run concurrently and still manage to print?  That might answer why my printer configuration tells me that my printer can't handle a job of large proportions.  Is it possible that they are both trying to print at the same time, thus giving the printer an overload in the file size?  

Well... I'll keep working at it.

Uuuuber-newb signing off.

---

### Post by warfacegod on 2010-01-15
Try disabling one then print. If it doesn't work switch them and try again.

---

### Post by AVDa on 2010-01-17
Tried that to no avail.  Let me dig up some logs and post them.  So things make a bit more sense.

---

### Post by warfacegod on 2010-01-17
I think you may want to reinstall the driver for it. I check the HP site and it brought me here:

[http://hplipopensource.com/hplip-web/install_wizard/index.html]("http://hplipopensource.com/hplip-web/install_wizard/index.html")

---

### Post by AVDa on 2010-01-18
So... here's the beef in my cups error log:
```

E [18/Jan/2010:18:37:24 -0600] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [18/Jan/2010:18:37:49 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [18/Jan/2010:18:38:52 -0600] [Job 1] No %%BoundingBox: comment in header!
E [18/Jan/2010:18:38:52 -0600] [Job 1] No %%Pages: comment in header!
E [18/Jan/2010:18:39:01 -0600] [CGI] Unable to scan "@LOCAL"!
E [18/Jan/2010:18:48:38 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [18/Jan/2010:18:50:00 -0600] [Job 2] No %%BoundingBox: comment in header!
E [18/Jan/2010:18:50:00 -0600] [Job 2] No %%Pages: comment in header!
E [18/Jan/2010:19:24:37 -0600] Pause-Printer: Unauthorized
E [18/Jan/2010:19:28:50 -0600] Resume-Printer: Unauthorized
E [18/Jan/2010:19:35:10 -0600] [Job 3] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:35:10 -0600] [Job 3] No %%Pages: comment in header!
E [18/Jan/2010:19:36:17 -0600] Pause-Printer: Unauthorized
E [18/Jan/2010:19:36:21 -0600] Resume-Printer: Unauthorized
E [18/Jan/2010:19:36:21 -0600] [Job 3] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:36:21 -0600] [Job 3] No %%Pages: comment in header!
E [18/Jan/2010:19:36:22 -0600] Pause-Printer: Unauthorized
E [18/Jan/2010:19:36:28 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [18/Jan/2010:19:36:28 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [18/Jan/2010:19:40:44 -0600] Resume-Printer: Unauthorized
E [18/Jan/2010:19:40:53 -0600] [Job 3] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:40:53 -0600] [Job 3] No %%Pages: comment in header!
E [18/Jan/2010:19:40:55 -0600] Pause-Printer: Unauthorized
E [18/Jan/2010:19:41:53 -0600] CUPS-Delete-Printer: Unauthorized
E [18/Jan/2010:19:48:05 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:48:05 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [18/Jan/2010:19:48:19 -0600] [Job 4] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:48:19 -0600] [Job 4] No %%Pages: comment in header!
E [18/Jan/2010:19:50:46 -0600] [Job 5] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:50:46 -0600] [Job 5] No %%Pages: comment in header!
E [18/Jan/2010:19:50:57 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:50:57 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:50:57 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:50:57 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:52:56 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:53:04 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:53:04 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [18/Jan/2010:19:53:08 -0600] [Job 6] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:53:08 -0600] [Job 6] No %%Pages: comment in header!
E [18/Jan/2010:19:55:37 -0600] PID 10211 (/usr/lib/cups/filter/foomatic-rip) crashed on signal 9!
E [18/Jan/2010:19:55:38 -0600] PID 10212 (/usr/lib/cups/backend/hp) crashed on signal 9!
E [18/Jan/2010:19:55:38 -0600] [Job 6] No %%BoundingBox: comment in header!
E [18/Jan/2010:19:55:38 -0600] [Job 6] No %%Pages: comment in header!
E [18/Jan/2010:19:56:23 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jan/2010:19:56:23 -0600] cupsdAuthorize: Local authentication certificate not found!


```

That one is for my desktop computer.  Note:  I reinstalled my OS, hoping to be able to print before classes start this week.  No dice... I guess I need to find an authorization certificate of some kind...  Keep in mind that I haven't done this before too...

I'll keep digging and see what I find.

---

### Post by warfacegod on 2010-01-18
Did the link I posted get you anywhere?

---

### Post by AVDa on 2010-01-23
Unfortunately, it didn't help much.  I have been to the link on many occasions and have been unsuccessful.  It might print a test page if I leave it on all night, but that's not exactly satisfactory.  Lost lost lost...  I'll keep trying though.  I'm probably missing some minor detail or something.

For now, I'll be reading this: [http://www.linuxjournal.com/article/6729](http://www.linuxjournal.com/article/6729) and see if there isn't something that can be done.

---

### Post by AVDa on 2010-01-29
Still lost.  I have no idea what to do.  Normally, printing is fairly easy to configure even with the minor details that are involved in it.  The previous version of Ubuntu printed just fine.  It kept bothering me about updates so... I naturally updated and low and behold, no printing.  What I need to do is to start completely over with the printing software, read a *TON* about it and see how it all fits together.  Unfortunately, I don't have a lot of time to do this and hoped to find a simple easy solution at the forums.  For now, I'll try to follow up with the logs produced and see if someone notices something that I am not.  Please just bare with me if you can...  Thanks for the help so far.

-Aaron

-----------------------------------------------------------------------------------------------------------------------------
from printcap:
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
HP-Deskjet-D1400-series|HP Deskjet D1400 series:rm=avd-laptop:rp=HP-Deskjet-D1400-series:

-----------------------------------------------------------------------------------------------------------------------------
From the lpr log file:
```

Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 24 21:41:28 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: Failed to get parent
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 24 21:41:28 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 24 21:41:28 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 24 21:41:28 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 11:18:30 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 11:18:30 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 11:18:30 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 11:18:31 avd-laptop udev-configure-printer: last message repeated 2 times
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 11:18:31 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 11:18:31 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 11:18:31 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 11:18:31 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 11:18:31 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 13:43:37 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 13:43:37 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 13:43:37 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 13:43:37 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 13:43:37 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 15:30:10 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 15:30:10 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 15:30:10 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 15:30:10 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 17:37:21 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 25 17:37:21 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 17:37:21 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 25 17:37:22 avd-laptop udev-configure-printer: Failed to get parent
Jan 25 17:37:22 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 25 17:37:22 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 25 17:37:22 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 07:11:55 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 07:11:55 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 07:11:55 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 07:11:56 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 07:11:56 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 07:11:56 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 07:11:56 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:05:17 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 16:05:17 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:05:17 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:05:17 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 14:12:33 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0
Jan 26 14:12:33 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 14:12:33 avd-laptop udev-configure-printer: Device vendor/product is 03F0:7904
Jan 26 14:12:33 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/usb/lp0
Jan 26 14:12:33 avd-laptop udev-configure-printer: failed to claim interface
Jan 26 14:12:33 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 14:12:33 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 14:12:33 avd-laptop udev-configure-printer: MFG:HP MDL:Deskjet D1400 series SERN:TH75C214PZ04Y5 serial:TH75C214PZ04Y5
Jan 26 14:12:36 avd-laptop udev-configure-printer: SERN fields match
Jan 26 14:12:36 avd-laptop udev-configure-printer: URI match: usb://HP/Deskjet%20D1400%20series?serial=TH75C214PZ04Y5
Jan 26 14:12:36 avd-laptop udev-configure-printer: SERN fields match
Jan 26 14:12:36 avd-laptop udev-configure-printer: URI match: hp:/usb/Deskjet_D1400_series?serial=TH75C214PZ04Y5
Jan 26 14:12:36 avd-laptop udev-configure-printer: Queue ipp://localhost:631/printers/HP-Deskjet-D1400-series has matching device URI
Jan 26 14:12:36 avd-laptop udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/HP-Deskjet-D1400-series
Jan 26 15:16:27 avd-laptop udev-configure-printer: remove /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 15:16:27 avd-laptop udev-configure-printer: Queue ipp://localhost:631/printers/HP-Deskjet-D1400-series has matching device URI
Jan 26 15:16:27 avd-laptop udev-configure-printer: Disabled printer ipp://localhost:631/printers/HP-Deskjet-D1400-series as the corresponding device was unplugged or turned off
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 16:00:54 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 16:00:54 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 16:00:54 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 16:00:54 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 16:00:54 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 21:14:57 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0
Jan 26 21:14:57 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 21:14:57 avd-laptop udev-configure-printer: Device vendor/product is 03F0:7904
Jan 26 21:14:57 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/usb/lp0
Jan 26 21:14:57 avd-laptop udev-configure-printer: failed to claim interface
Jan 26 21:14:57 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 21:14:57 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 21:14:57 avd-laptop udev-configure-printer: MFG:HP MDL:Deskjet D1400 series SERN:TH75C214PZ04Y5 serial:TH75C214PZ04Y5
Jan 26 21:15:01 avd-laptop udev-configure-printer: SERN fields match
Jan 26 21:15:01 avd-laptop udev-configure-printer: URI match: usb://HP/Deskjet%20D1400%20series?serial=TH75C214PZ04Y5
Jan 26 21:15:01 avd-laptop udev-configure-printer: SERN fields match
Jan 26 21:15:01 avd-laptop udev-configure-printer: URI match: hp:/usb/Deskjet_D1400_series?serial=TH75C214PZ04Y5
Jan 26 21:15:01 avd-laptop udev-configure-printer: Queue ipp://localhost:631/printers/HP-Deskjet-D1400-series has matching device URI
Jan 26 21:15:01 avd-laptop udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/HP-Deskjet-D1400-series
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 22:40:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 22:40:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 22:40:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:40:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 22:41:07 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0
Jan 26 22:41:07 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 22:41:07 avd-laptop udev-configure-printer: Device vendor/product is 03F0:7904
Jan 26 22:41:07 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/usb/lp0
Jan 26 22:41:07 avd-laptop udev-configure-printer: failed to claim interface
Jan 26 22:41:07 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 22:41:07 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 22:41:07 avd-laptop udev-configure-printer: MFG:HP MDL:Deskjet D1400 series SERN:TH75C214PZ04Y5 serial:TH75C214PZ04Y5
Jan 26 22:41:11 avd-laptop udev-configure-printer: SERN fields match
Jan 26 22:41:11 avd-laptop udev-configure-printer: URI match: hp:/usb/Deskjet_D1400_series?serial=TH75C214PZ04Y5
Jan 26 22:41:11 avd-laptop udev-configure-printer: SERN fields match
Jan 26 22:41:11 avd-laptop udev-configure-printer: URI match: usb://HP/Deskjet%20D1400%20series?serial=TH75C214PZ04Y5
Jan 26 22:48:54 avd-laptop udev-configure-printer: remove /devices/pci0000:00/0000:00:1d.0/usb6/6-1
Jan 26 22:48:54 avd-laptop udev-configure-printer: Queue ipp://localhost:631/printers/HP-Deskjet-D1400-series has matching device URI
Jan 26 22:48:54 avd-laptop udev-configure-printer: Disabled printer ipp://localhost:631/printers/HP-Deskjet-D1400-series as the corresponding device was unplugged or turned off
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 23:44:49 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 26 23:44:49 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 26 23:44:49 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 26 23:44:49 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 26 23:44:49 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 05:55:38 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 05:55:38 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 05:55:38 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 08:33:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 08:33:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 08:33:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 08:33:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 08:33:44 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 13:43:50 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 13:43:50 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 13:43:50 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 13:43:51 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 13:43:51 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 13:43:51 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 13:43:51 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 15:03:36 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 15:03:36 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 15:03:36 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 27 15:03:36 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 16:30:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 27 16:30:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 27 16:30:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 27 16:30:02 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 27 16:30:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 08:06:39 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 08:06:39 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 08:06:39 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 08:06:39 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 08:06:39 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 15:08:46 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 15:08:46 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 15:08:46 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 15:08:46 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 15:08:46 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 19:20:02 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 19:20:02 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 19:20:02 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 19:20:02 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 19:20:02 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 21:12:05 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 21:12:05 avd-laptop udev-configure-printer: last message repeated 2 times
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 28 21:12:05 avd-laptop udev-configure-printer: Failed to get parent
Jan 28 21:12:05 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 28 21:12:05 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 28 21:12:05 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 29 06:32:44 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 29 06:32:44 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 29 06:32:44 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 06:32:45 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 29 06:32:45 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 06:32:45 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 06:32:45 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.0/usb3
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb7/7-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb8/8-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2
Jan 29 12:07:34 avd-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb6/6-2
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 147E:1000
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.1/usb4
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-2
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 0BDA:0158
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb7
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent
Jan 29 12:07:34 avd-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Jan 29 12:07:34 avd-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 29 12:07:34 avd-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 29 12:07:34 avd-laptop udev-configure-printer: Failed to get parent

```

Device uri: hp:/usb/Deskjet_D1400_series?serial=TH75C214PZ04Y5

-------------------------------------------------------------------------------------------------------------------------------

It's so odd.  The printer activates and draws in paper, but prints one line every 20-30 seconds.  That's not one line of text, it's one line of.... pixies, or dots?  Anyway, that's about the best way to describe it.

Then, when I change from cups to hpijs again, I get this error: There was an error during the CUPS operation: 'client-error-document-format-not-supported'. 

_-----------------------------------------------------------------------------------------------------------------------------

lpstat: 
avd@avd-laptop:~$ lpstat -p 
printer HP-Deskjet-D1400-series is idle.  enabled since Fri 29 Jan 2010 12:50:39 PM PST

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 03f0:7904 Hewlett-Packard 
Bus 006 Device 002: ID 147e:1000 Upek 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

-------------------------------------------------------------------------------------------------------------------------------

If you have any suggestions, just say the word.

---

### Post by AVDa on 2010-01-31
How embarrassing.  After working for what seemed like an eternity, I finally found the "communication error".  For some reason, the ink in the cartridge leaked onto the outer circuitry and was causing the printer to act up.  Anyway, it took about a month to find this problem because it was virtually invisible unless one inspected the cartridge very closely and made a point to look through the transparent printed circuit tape to see the condition of the cartridge.  I cleaned and checked every little part.  Either it was that, or the printer is possessed and stops at random.  I will go with the former which also includes my ignorance and lack of attention to detail.  Apologies for wasting any of your time, and I really appreciate the help.  I did learn that it is very important to rule out all potential issues before whining about errors and asking for assistance.

Thanks again,

-Aaron

note: I don't know how to mark this as solved, but if someone could do so, that would be great!

---

### Post by steveneddy on 2010-01-31
to the OP:

the next time you need to post long lines of code, please wrap it in the ```
 code 
``` tags.

It makes it easier to read and the readers of the thread don't have to scroll through long lines of code unnecessarily.

---

### Post by AVDa on 2010-02-02
Thanks, Steven.  I'll be sure to do that from now on.

---------------------------------------------------------------

All taken care of in this thread.  Suggestions are always welcome.

-Aaron

---

