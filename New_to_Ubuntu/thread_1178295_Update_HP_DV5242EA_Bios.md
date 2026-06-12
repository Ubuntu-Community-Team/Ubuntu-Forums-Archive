---
title: "Update HP DV5242EA Bios"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-06-04
Since I do not have windows installed, what is the method for updating the bios firmware in Ubuntu.

I can install windows if necessary, but would this be an easier way of updating the Bios?

---

### Post by abhiroopb on 2009-06-06
bump!

---

### Post by spcwingo on 2009-06-06
Install unetbootin and gparted.  Insert a USB flash drive and fire up gparted.  Format the flash drive as fat (fat 16).  Now remount the flash drive and start unetbootin.  Choose FreeDOS as distro to install to the flash drive.  When it's done, drop your new bios along with bios flash program on the flash drive.  Reboot; only this time boot from the USB flash drive, then flash as normal.  I just did this same thing to flash the bios on a Dell Inspiron 5100 laptop and it works great.

---

### Post by abhiroopb on 2009-06-06
Thanks for that...seems simple enough...
But what do you mean by:
"drop your new bios along with bios flash program on the flash drive"

When I go to the HP site to download the flash utility. I just get a .exe file: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-54801-1&lc=en&dlc=en&cc=us&lang=en&os=228&product=3223544](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-54801-1&lc=en&dlc=en&cc=us&lang=en&os=228&product=3223544)

Do I put this entire thing onto the pendrive after I have formatted it?

---

### Post by spcwingo on 2009-06-06
> **abhiroopb said:**
> Thanks for that...seems simple enough...
But what do you mean by:
"drop your new bios along with bios flash program on the flash drive"

When I go to the HP site to download the flash utility. I just get a .exe file: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-54801-1&lc=en&dlc=en&cc=us&lang=en&os=228&product=3223544](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-54801-1&lc=en&dlc=en&cc=us&lang=en&os=228&product=3223544)

Do I put this entire thing onto the pendrive after I have formatted it?

Yes, copy/paste sp37159.exe to the root of your flash drive after you have installed FreeDOS with unetbootin.  After booting into FreeDOS it'll drop you into a DOS prompt (A:\>).  Just type:

```
c:
```

followed by enter.  Then type:

```
dir
```

To make sure that is right drive designation where your flash tool is located (sp37159.exe).  If it's there then just type:

```
sp37159
```

and it'll run the bios upgrade...just follow the on screen instructions.

---

### Post by abhiroopb on 2009-06-06
So, I had a problem...

Installed it like you said and I get the following error after selecting "Default" from the Unetbootin page on startup:

[http://www.freedos.org/bugzilla/cgi-bin/show_bug.cgi?id=1918](http://www.freedos.org/bugzilla/cgi-bin/show_bug.cgi?id=1918)

The error specified here is the same as mine, although it says it has been fixed.

I tried formatting the drive to fat16 and fat32, and I tried booting without copying the bios .exe file. Nothing works and I keep getting the "invalid Opcode" error.

Any suggestions?

Thanks for all your help

---

### Post by spcwingo on 2009-06-06
There's only one other way that I know to do this.  Check out this page:

[http://tuxtweaks.com/2009/05/create-a-bootable-usb-drive-ubuntu-freedos/]("http://tuxtweaks.com/2009/05/create-a-bootable-usb-drive-ubuntu-freedos/")

I have tried this method once before and it too works fine.

---

### Post by abhiroopb on 2009-06-06
thanks for the link. I did everything it suggested and then when I load it up it gets stuck on:

-InitDisk

So, instead of using Freedos "ODIN" as suggested in the guide. I downloaded FreeDOS balder and I ran the same commands.

Now i get the following:

-InitDisk
Invalid Opcode ...

So, basically the same error as while using UnetBootin.

Would you suggest changing some boot parameters?

Or any other thoughts on the matter?

I just really need to flash my bios, so any method is fine I guess!

---

### Post by spcwingo on 2009-06-06
The only other way I know of is dependent on if you have access to a windows machine.  Basically, you use the HP USB Disk Storage Format Tool.  It has the option to create a USB DOS startup disk.  It can be downloaded here:

[http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2242_4-201159.html]("http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2242_4-201159.html")

---

### Post by abhiroopb on 2009-06-06
Unfortunately I don't. All i have currently is a Ubuntu and a Mac.

I do have an XP install cd lying at home, so i guess I will have to install that and then do it.

If you think of anything please let me know.

Many thanks!

---

