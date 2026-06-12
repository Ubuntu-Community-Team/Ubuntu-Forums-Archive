---
title: "How do I get an Epson scanner going?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by alpinescrambler on 2010-06-23
I'm trying to get an Epson Perfection V300 Photo scanner going.  I've looked over past threads and advice, and I'm getting nowhere.

Anyone have any simplified, step-by-step instructions for a beginner?

This scanner was working fine when I ran my computer on Windows.  The power is on, but it's just not responding.

Thanks!

---

### Post by tacotime on 2010-06-23
> **alpinescrambler said:**
> I'm trying to get an Epson Perfection V300 Photo scanner going.  I've looked over past threads and advice, and I'm getting nowhere.

Anyone have any simplified, step-by-step instructions for a beginner?

This scanner was working fine when I ran my computer on Windows.  The power is on, but it's just not responding.

Thanks!

what happens when you open up simple scan?

applications -> graphics -> simple scan?

---

### Post by SoFl W on 2010-06-23
I was able to get a workforce all-in-one working.  If you check the Epson website it should give you a link to an external website with drivers and packages.
See [this link]("http://ubuntuforums.org/showthread.php?t=1393162") for more info.

The [Epson Linux driver website]("http://avasys.jp/eng/linux_driver/")

---

### Post by Bucky Ball on 2010-06-23
[B]How do I get an Epson scanner going?

[/B]In most cases, with great difficulty!! You're better off getting something that will work out of the box if you intend using Linux. The community doesn't make it that way, hardware manufacturers do. ;)

---

### Post by SoFl W on 2010-06-24
Alpine, was the **[link]("http://avasys.jp/eng/linux_driver/")** able to help you?  I see your drivers are available.

---

### Post by alpinescrambler on 2010-06-24
> **tacotime said:**
> what happens when you open up simple scan?

applications -> graphics -> simple scan?

[B]No scanners detected

[/B]Please check your scanner is connected and powered on

---

### Post by alpinescrambler on 2010-06-24
> **SoFl W said:**
> Alpine, was the **[link]("http://avasys.jp/eng/linux_driver/")** able to help you?  I see your drivers are available.

The odd thing is, the list includes the Perfection V300, but not the Perfection V300 PHOTO.

I'm not sure if that makes a difference.

I don't detect any downloading from that site, either.  Maybe I'm just not downloading it to the right place.

---

### Post by philinux on 2010-06-24
> **alpinescrambler said:**
> I'm trying to get an Epson Perfection V300 Photo scanner going.  I've looked over past threads and advice, and I'm getting nowhere.

Anyone have any simplified, step-by-step instructions for a beginner?

This scanner was working fine when I ran my computer on Windows.  The power is on, but it's just not responding.

Thanks!

I got mine working by following this. [http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/](http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/)

It is specific to my scanner but if you substitute your scanners .bin file it could work.

---

### Post by kaibob on 2010-06-25
About a month ago, I got an Epson Perfection V30 scanner, which is essentially the same scanner as the V300 but without the transparency unit. I downloaded the two software DEB's from the Avasys site. In my case, these were:

> DEB 32bit package [libltdl7] (for Ubuntu 8.10 or later)  	

iscan_2.24.0-4.ltdl7_i386.deb

esci-interpreter-gt-f720_0.0.1-2_i386.deb

I installed these DEB's, rebooted the computer, and the scanner worked fine. The iscan DEB installs the Epson Image Scan program. I'm not sure whether this package is absolutely necessary, but it's a decent program and worth trying. Until you install the esci DEB, I don't think the scanner will work. 

AVASYS SITE
[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

---

### Post by alpinescrambler on 2010-06-25
> **kaibob said:**
> About a month ago, I got an Epson Perfection V30 scanner, which is essentially the same scanner as the V300 but without the transparency unit. I downloaded the two software DEB's from the Avasys site. In my case, these were:



I installed these DEB's, rebooted the computer, and the scanner worked fine. The iscan DEB installs the Epson Image Scan program. I'm not sure whether this package is absolutely necessary, but it's a decent program and worth trying. Until you install the esci DEB, I don't think the scanner will work. 

AVASYS SITE
[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

Right on.  I think that may be the answer.  Any idea why I'm getting these messages upon installing the drivers?

[B]Error: Dependency is not satisfiable: iscan-data

Error: Dependency is not satisfiable: iscan (>= 2.16.1)[/B] 

(P.S Rebooted and it didn't work.)

So I think I'm just about there.  I just need a way to get these drivers to work.

Any ideas?

---

### Post by SoFl W on 2010-06-25
> **alpinescrambler said:**
> The odd thing is, the list includes the Perfection V300, but not the Perfection V300 PHOTO.
I'm not sure if that makes a difference.
Not sure

> **alpinescrambler said:**
> 
I don't detect any downloading from that site, either.  Maybe I'm just not downloading it to the right place.
Well you got to the scanner selection screen, under that there is "**Questionnaire**" where you select your distribution, and click next.  On the next page is the deb packages.  Right click and save or open them up with the package installer.

---

### Post by alpinescrambler on 2010-06-25
> **SoFl W said:**
> Not sure
 
 
Well you got to the scanner selection screen, under that there is "**Questionnaire**" where you select your distribution, and click next. On the next page is the deb packages. Right click and save or open them up with the package installer.
 
 
Already did that.  Thing is, they weren't downloading or installing.  I tried it again later, and it worked.  Okay.  But upon installation, I got the following error messages:
 
[B]Error: Dependency is not satisfiable: iscan-data

Error: Dependency is not satisfiable: iscan (>= 2.16.1)[/B] 

That is where I am currently.
 
How to make these drivers work.  I assume they are in there somewhere, waiting to be used, but if they are in the right place and whether my computer is configured correctly for them is another question...

---

### Post by kaibob on 2010-06-25
Just this morning Epson uploaded new files. There are now three DEB's that have to be downloaded and installed. For me, these files are:

> iscan-data_1.0.0-2_all.deb

iscan_2.25.0-1.ltdl7_i386.deb

esci-interpreter-gt-f720_0.0.1-2_i386.deb

The install instructions now state:

> There are two packages for installing Image Scan! for Linux: core
package and data package. To install Image Scan! for Linux, install data
package, and then install core package.

So, did you install the new version and, if the new version, did you install all three packages?

The extra package has to do with iscan, so perhaps the esci package was installed properly. You can check this by attempting to do a scan with simple scan or xsane.

I decided to upgrade to the new versions and had to first uninstall the old iscan and esci packages with synaptic. I then installed the new versions in the following order:

> iscan-data_1.0.0-2_all.deb

iscan_2.25.0-1.ltdl7_i386.deb

esci-interpreter-gt-f720_0.0.1-2_i386.deb

After a reboot, everything works fine.

---

### Post by alpinescrambler on 2010-06-25
Hmmm...   I downloaded the old version.  And just the two of them.  I'll have to try this as soon as I get home from work...

---

### Post by SoFl W on 2010-06-25
> **alpinescrambler said:**
> Already did that.  Thing is, they weren't downloading or installing.  I tried it again later, and it worked.  Okay.  But upon installation, I got the following error messages:
 [B]Error: Dependency is not satisfiable: iscan-data
Error: Dependency is not satisfiable: iscan (>= 2.16.1)[/B] 
That is where I am currently.
 How to make these drivers work.  I assume they are in there somewhere, waiting to be used, but if they are in the right place and whether my computer is configured correctly for them is another question...

Sorry I missed this before.  I had this same error, and I believe I tried running them in a different order and it worked. One package needs the other.  That or I downloaded iscan from the package manger.   I was installing to a few machines at the time and the error happened on one machine.

---

### Post by alpinescrambler on 2010-06-26
> **alpinescrambler said:**
> Hmmm...   I downloaded the old version.  And just the two of them.  I'll have to try this as soon as I get home from work...

Downloaded the new ones.  Still getting 

**No scanner detected**

I've checked and re-checked the cables.  I've downloaded three sets of drivers.  This is really aggravating, I must admit.  I bought this scanner just a few weeks before I switched to Linux.  It was just what I needed when I used it in Windows.

---

### Post by philinux on 2010-06-26
> **alpinescrambler said:**
> Downloaded the new ones.  Still getting 

**No scanner detected**

I've checked and re-checked the cables.  I've downloaded three sets of drivers.  This is really aggravating, I must admit.  I bought this scanner just a few weeks before I switched to Linux.  It was just what I needed when I used it in Windows.

Did you try what I suggested in post #8. This got my perfection 2480 going.

---

### Post by alpinescrambler on 2010-06-26
> **philinux said:**
> Did you try what I suggested in post #8. This got my perfection 2480 going.

That I did, thanks.  Nada.  I'm still scratching my head...

---

### Post by philinux on 2010-06-26
> **alpinescrambler said:**
> That I did, thanks.  Nada.  I'm still scratching my head...

Did you get your scanners .bin file of the install disk or elsewhere?

---

### Post by alpinescrambler on 2010-06-26
> **philinux said:**
> Did you get your scanners .bin file of the install disk or elsewhere?

Elsewhere.  How do I get it off the disk, and to the right place?  Or find it, for that matter?

---

### Post by kaibob on 2010-06-26
> **alpinescrambler said:**
> Elsewhere.  How do I get it off the disk, and to the right place?  Or find it, for that matter?


My previous scanner was an Epson 3490, and I had to extract and copy over the firmware file for that scanner to work. The firmware file was named esfw52.bin.

I just checked my hard drive, and what I assume is the firmware file for my Epson V30 is:

/usr/share/esci/esfw8b.bin

I did not install this file, so either it was installed as part of Ubuntu or the DEB files that I got from Avasys installed it.

---

### Post by alpinescrambler on 2010-06-26
> **kaibob said:**
> My previous scanner was an Epson 3490, and I had to extract and copy over the firmware file for that scanner to work. The firmware file was named esfw52.bin.

I just checked my hard drive, and what I assume is the firmware file for my Epson V30 is:

/usr/share/esci/esfw8b.bin

I did not install this file, so either it was installed as part of Ubuntu or the DEB files that I got from Avasys installed it.


Hmmm...  I enter that, and I get:

bash: /usr/share/esci/esfw8b.bin: No such file or directory

---

### Post by alpinescrambler on 2010-06-26
I figured out what I did wrong:

When I followed the instructions below, I entered 

**04b8:0131**

instead of:

**04b8 0131**

I used a colon instead of a space, because that is what I saw when I entered lsusb.

That screwed everything up.  When I went back and did EVERYTHING over again, and the only change I made was that, it WORKED!

THANKS FOR THE HELP, EVERYBODY!

(The instructions I erred on: )


open a terminal and copy and paste the following:
     Code:
     gksudo gedit /etc/sane.d/epson.conf 
then you will see the following:
     Code:
     # epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
**# usb <product ID> <device ID>**
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0 
the line that is in bold letters needs # to be removed from the  beginning of the line and product ID and device ID inserted.
you will need to do      Code:
     lsusb 
to find out the product ID and device ID.

an example of what lsusb looks like, and what #'s you need are:     Code:
     ed@wolfenstein:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 077: ID **03f0:7e04** Hewlett-Packard 
Bus 001 Device 076: ID 0764:0501 Cyber Power System, Inc. 
Bus 001 Device 006: ID 1241:1203 Belkin 
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000 
the #'s in bold are what you need.

close and save.

---

### Post by SoFl W on 2010-06-26
Fantastic, I am glad to see you are up and running.

---

### Post by progone on 2010-09-26
> **SoFl W said:**
> I was able to get a workforce all-in-one working.  If you check the Epson website it should give you a link to an external website with drivers and packages.
See [this link]("http://ubuntuforums.org/showthread.php?t=1393162") for more info.

The [Epson Linux driver website]("http://avasys.jp/eng/linux_driver/")


Following the instructions here [http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/README.html](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/README.html)

at:   /etc/init.d/cupsys restart

I get this error:
-bash: /etc/init.d/cupsys: No such file or directory

---

### Post by skillet-thief on 2010-12-12
I just got my Epson Perfection 4490 working on Maverick AMD64. The only trick was to use the debs indicated as: "deb 64bit package [libltdl7] (for Ubuntu 8.10 or later)". My first try at installation had failed because I used the libltdl3 version (even after installing libltdl3 manually).

I also did not have to do anything with the groups.

---

### Post by FellWanderer on 2012-01-17
Please see my blog.

[http://wilkiecat.wordpress.com/2012/01/17/epson-scanner-on-linux-ubuntu-10-10/](http://wilkiecat.wordpress.com/2012/01/17/epson-scanner-on-linux-ubuntu-10-10/)

---

