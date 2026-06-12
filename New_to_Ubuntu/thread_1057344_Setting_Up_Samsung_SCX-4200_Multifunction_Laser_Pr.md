---
title: "Setting Up Samsung SCX-4200 Multifunction Laser Printer &amp; Scanner, Intrepid 32 bit"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by nickpaton on 2009-02-01
I chose this mono laser and scanner combo because it will work on Ubuntu &#8211; and then the fun began!

It turns out that it all works but there's a combination of poor Samsung drivers, changed file locations across different distro versions, and wrong ownership issues.

The following are extracts from a number of threads and posts into a single set of  instructions, which should result in the printer and scanner being set up on a brand new install of 8.10 Intrepid i386 32bit.

_**Splix2 Printer Driver**_

After reading a number of posts, I decided that installing Splix2 printer driver was simplest since it automatically identifies the correct USB printer port.
.
Go to [http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200]("http://www.openprinting.org/show_printer.cgi?recnum=Samsung-SCX-4200")

Download splix2 for 1386 32 bit from [here](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-splix_2.0.0-2lsb3.2_i386.deb) 

Install splix2 by clicking on the .deb.
  
At one point when it pauses, click 'Terminal' to open the terminal window, which will be at 
*general type of mail configuration is wanted.*

Select 1 (no configuration)

Wait for the installation and configuration to finish.


_**Installing the Samsung Unified Printer Driver (SUPD) Part I**_

The  Samsung Unified Linux Driver also installs a printer driver, but it won't be used due to port selection problems.
The part that will be used is the Samsung Unified Driver Configuration (SUDC) program, giving central Desktop access to the printer and scanner settings.

From various posts in [http://ubuntuforums.org/showthread.php?t=341621]("http://ubuntuforums.org/showthread.php?t=341621")

Download the SUPD from 
 
[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=us&CttFileID=303018&CDCttType=DR&ModelType=N&ModelName=ML-1520&VPath=DR/200707/20070720164730750_UnifiedLinuxDriver.tar.gz]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=us&CttFileID=303018&CDCttType=DR&ModelType=N&ModelName=ML-1520&VPath=DR/200707/20070720164730750_UnifiedLinuxDriver.tar.gz")

into the Home folder.

Decompress by clicking on the tar.gz file (decompressing this way now works with the updated Samsung driver)

This creates a new cdroot directory in the Home folder.


_**Sorting out User Permissions**_

Move to cdroot directory:

```
cd ~/cdroot
```

and correct the ownership issues with 

```
sudo chown -R root:root *
```


_**Installing the SUPD Part II**_

If not already there move to the cdroot directory again:

```
cd ~/cdroot
```

and install the SUPD

```
sudo ./autorun
```

When the Printer wizard appears, select a random port (e.g. dev/mfp4) - it will be removed later.

On the next screen click Manual Select bullet.
Next screen scroll to scx-4200 splix.....(openprinting....) - shortened this down but it's clear which one to pick.
Click Finish to complete.

Dont test the printer since it won't work due to the wrong port selection issue.

The SUPD is now installed with an icon on the Desktop
Close all installation boxes.


_**Getting the Printer to work**_

System > Administration > Printing

Delete SCX-4200 printer if present.

New Printer.
Select SCX-4200 splix2 driver from list.
Complete rest of details.

Run a test print which should give the Ubuntu colour scale page (in black and white).

Go to SUDC, click on SCX-4200 series printer (default) which should be present and run a test print.
This should print a Test Page with a (black and white) colour wheel etc.
Close all open printer boxes.

That completes the printer configuration.


_**Installing the Scanner**_

Go to [http://jacobo.tarrio.org/tech/scx4200]("http://jacobo.tarrio.org/tech/scx4200")

Download the driver permission 'hack' from [here](http://jacobo.tarrio.org/sites/default/files/fix-nopar-scx4200-2.00.95-2008112701.tar.gz) 

and install:

```
tar xfz fix-nopar-scx4200-2.00.95-2008112701.tar.gz
```
Enter
```
cd fix-nopar
```
Enter
```
./check.sh
```

For me this resulted in:

[I]&#8220;The 32-bit library has been found at /usr/lib 
You may replace it with the one in the "i386" directory&#8221;[/I]

Substitute &#8220;/usr/lib&#8221; below with whatever you have above; same for &#8220;i386&#8221;

```
sudo cp /usr/lib/libmfp.so.1.0.1 /usr/lib/oldlibmfp.so.1.0.1
```
Enter
```
sudo cp i386/libmfp.so.1.0.1 /usr/lib/
```
Enter
```
sudo adduser $USER lp
```
Enter


_**Sorting out User Permissions for 8.10 Intrepid**_

Referring to [http://ubuntuforums.org/showpost.php?p=6080732&postcount=168]("http://ubuntuforums.org/showpost.php?p=6080732&postcount=168")

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

ADD THE LINES immediately below

*domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE*:

```
#
# Magic to KEEP /proc/bus/usb working
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb
```

Save and close.
Reboot.

That completes the Scanner configuration.

Many thanks to the numerous Ubuntu forum post contributors, and those who modified the printer drivers and produced great documentation.

---

### Post by steveparbkk on 2009-04-05
I've just set-up a Samsung SCX-4200 on my EeePC with Intrepid installed on it on a network share.  We have an XP box with a Samsung SCX-4200 plugged into it.  The XP box is connected by CAT-5 to our wireless router/modem.  I'm using my EeePC 901 over the wireless interface.  Firstly I had to share the SCX-4200 on the XP box.  Then I followed the instructions in  [ubuntu] Samsung scx 4200 ubuntu 8.04 (post number 1103651). Following these instructions placed an icon on my desktop called Samsung Unified Driver Configurator.  I then added the SMB// path into the Configurator.  I didn't try the scanner yet, but I successfully printed a test page from my EeePC 901 over the wi-fi, which was my objective.

---

### Post by nickpaton on 2009-04-05
Just done the same here, but I cannot find a way to use the scanner as a network scanner - ie plugged into a printer server on the network.

Any ideas?

---

### Post by steveparbkk on 2009-04-27
Sorry, I didn't set the notify status on my post, so I only just discovered your reply.  That XP box and printer/scanner is at my home in the UK and I'm now back in Asia so I can't test the scanner until I am back in the UK.  I'll attempt to do so when next back there but that won't be for several months.

---

### Post by elboeufx on 2009-10-27
Hi--

This worked just great for me on Ubuntu 9.04. But now I've migrated to 9.10, and the scanner part of the printer doesn't work. What would you advise. Should I delete everything and do it all over again, or is it futile because the new build of Ubuntu won't respond the same way? I really need to get this scanner part of the machine working again. Please help.

Thanks,
Elboeufx

---

### Post by nickpaton on 2009-10-28
Many thanks also for trying it on 9,04 and reporting it works - I'll update the title etc to reflect that.

Could you be more specific when you say it doesn't work. Do you mean that you get errors when you carry out the commands?  

If so could you post screens with the errors.

Also was it a brand new 9.10 install or an upgrade?  Note that my instructions refer to a brand new install so that may be the problem.

I'm not sure if I can help you very much but I'll do my best.

---

### Post by elboeufx on 2009-10-28
Hi Nick--

It was, indeed, an upgrade.

There is no error. When I opened Xsane, I used to get an image (as I still do at home when my Epson scanner is attached) that had two choices on it: the built-in camera, and the Samsung SCX-4200. Now, when I open Xsane, there is no "choice," it just goes straight to the camera, as if there is no other scanner attached. When I open the Samsung Unified Driver Configurator, moreover, it only shows the camera under the "scanner" tab, though it shows the SCX-4200 under printers (at home, it shows the Epson under scanners). I'm wondering whether I should de-install everything and then go back through your script again and reinstall it. But then I need directions on how to uninstall (the uninstall option, for instance, under the Samsung Driver Configurator, won't let me proceed because it says I'm "not authorized" to do it.

Thanks for writing back to me.

Cheers,
Tamas

---

### Post by nickpaton on 2009-10-28
Hi Tamas

I'll download a copy of 9.10 and try it for myself and get back to you.  I'm really busy at the moment so it may be some days before I get back.

Nick

---

### Post by elboeufx on 2009-10-28
Nick--

Thanks. Let me know how it goes.

Tamas

---

### Post by binwiederweg on 2010-01-03
Hey you guys,

I know that this post is from long time ago, ... but I'm currently having the same problem on my freshly installed Ubuntu 9.10, 64 bit:

* The printer works out of the box, without any UnifiedLinuxDriver installations. It also works if I install the unified driver from Samsung, so printing is no problem ...
* The scanner doesn't work at all and appears (in xsane and the Samsung configurator) as 'Integrated camera' ... 

Did any of you guys get the scanner to work?

Regards,
Philipp

---

### Post by kedaha on 2010-01-07
> **binwiederweg said:**
> Hey you guys,

I know that this post is from long time ago, ... but I'm currently having the same problem on my freshly installed Ubuntu 9.10, 64 bit:

* The printer works out of the box, without any UnifiedLinuxDriver installations. It also works if I install the unified driver from Samsung, so printing is no problem ...
* The scanner doesn't work at all and appears (in xsane and the Samsung configurator) as 'Integrated camera' ... 

Did any of you guys get the scanner to work?

Regards,
Philipp


Hi,

After enabling Splix2 for the SCX-4200 Laser multifunction printer on Karmic Koala you can enable the Samsung scanner driver by adding the following repository to Synaptic:
(This should work on both 32 and 64-bit systems).

Please consult:

[HTML]http://www-personal.umich.edu/~tjwatt/suldr/index.html[/HTML]

Fresh install (assumes no previous Samsung UnifiedLinux printer installation).
Open a Terminal, cut and paste:
```
sudo gedit /etc/apt/sources.list
```

Add the following line to your sources list:
```
deb http://www-personal.umich.edu/~tjwatt/suldr/ debian extra
```
Save the changed file and exit gedit.
To avoid unknown key errors:
```
wget http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg
```
```
sudo apt-key add suldr.gpg
```
The key may now be deleted from Home.
```
rm suldr.gpg
```
```
sudo apt-get update
```
After doing this, open Synaptic, select and install the following packages:

libstdc+++5
samsungmfp-data
samsungmfp-driver
samsungmfp-scanner

And Xsane works perfectly;)

---

### Post by nejode on 2010-01-15
kedaha, thanks my friend, I've been fighting with this scanner for some time now, and the scanner has won the first 9 rounds!!!, but with this info I could give it a Knock-Out before the fight was over.
Now it works like a charm!

---

### Post by kedaha on 2010-01-20
Splix2 is preferable to the Samsung Unified Linux driver for the printer but the Samsung scanner driver seems OK. Glad to hear you finally beat the thing in round 10! :)

---

### Post by ohmybuntu on 2010-03-28
thanx a million from me, too, this scanner drove me nuts ever since I upgraded to karmic, and now it finally works!

---

### Post by sesemin on 2010-03-29
I followed both instructions and still no luck.

In the instruction on the 1st page everything goes as expected till I start installing the SUPD Part II. I do not have scx-4200 splix in the list!

The other issue is at the end. I do not have /etc/init.d/mountdevusbfs.sh. Why is that?

The instruction on the second page goes with no problem but still XSANE can not detect the Scanner.

---

### Post by gsanse on 2010-03-31
I am also having this problem with SCX-4100. I was able to install the splix open driver and the printer works fine. I installed all the packages recommended by kedaha but xsane does not find the scanner. Anyone can help, I don't know how to troubleshoot this.

---

### Post by yahs on 2010-04-01
gsanse

Hope this helps with your scx-4100

I have been following and contributing to the post
“HOWTO Install Samsung Unified Printer Driver” by Tweedledee
for a couple of years now. 

I have been using a Samsung SCX-4100 for about 6 years on various Ubuntu releases.

It used to be difficult but I have found the installation pretty straight forward recently.

This is what works for me.

I usually do a clean install of each new version of Ubuntu (7.10, 8.04, 8.10, 9.04, 9.10 and recently 10.04 beta – fortunately all with success)

The linux unified driver no longer appears under scx-4100 on the Samsung UK site so I selected scx-4600 and downloaded the file (v 3.00.63).

Extract the file and change to the directory cdroot/Linux 
Open a terminal and run the command sudo ./install.sh 

I usually get a few messages such as

libstdc ++.so.5 not found, install ... done
libstdc ++.so.3 not found, install ... done

It seems Qt library is not installed or X display is not accessible
Custom Qt library will be configured for use with this package.


The Samsung GUI installer then appears and runs.
You are offered the option of adding users to the group lp and disabling parallel printing., both of which I do.

That’s it, I didn't even need a reboot with 10.04

The way ubuntu recognises usb printers seems to have changed since version 9.10.

When I install Ubuntu, no printer is recognised. If you go to system, admin, printing and click new, Ubuntu finds the scx-4100 and offers to install a splix driver for scx 4200. This works for printing but not for scanning.
Installing the unified driver gives you printing and scanning.
The Samsung unified driver sets up printing on Device URI: mfp:/dev/mfp4
The splix driver sets up printing on usb://Samsung/SCX-4200%20Series
Scanner comes up as flatbed scanner scx-4100 series on usb:0 and works perfectly.

---

### Post by spamoften on 2010-04-06
I noted this post seems to be at the top of the google search, so I am cross posting from:
[http://ubuntuforums.org/showthread.php?p=9086046#post9086046](http://ubuntuforums.org/showthread.php?p=9086046#post9086046)


I found there is no need to install any software to get the printer and scanner working in Ubuntu 9.10

Follow the instructions here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2075437.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2075437.html)

sudo echo "usb 0x04e8 0x341b" >> /etc/sane.d/xerox_mfp.conf

then run 

sudo xsane

(start xsane from root, scanner device file has wrong permissions)
the scanner will be recognized and works immediately :-)

It seems the Samsung printer is compatible with the xerox scanner support built into the Ubuntu 9.10 kernel.

Note:  I had in the past tried to get this scanner and printer working using the Samsung unified driver, and I also tried the splix2 option, both without success.  I've been hacking away at this since Ubuntu 7.10 and now it was so easy, thanks Google, and thanks "Linas U" who found this great solution!

Cheers
G

---

### Post by debernardis on 2010-05-02
With 10.04, I'm not having luck either with spamoften's or with yahs's methods. I've edited /etc/sane.d/xerox_mfp.conf but the scanner doesn't get recognized, and also installing the Samsung driver doesn't show the scanner.
Anyone?

EDIT: my fault. I was connecting the SCX-4100 to my notebook through a usb-hub. When I tried to connect directly, everything worked.

---

### Post by Jrrg03 on 2011-03-05
This is for reset Samsung SCX-4600.
[http://www.megaupload.com/?d=KEZPR3LO](http://www.megaupload.com/?d=KEZPR3LO)
This is for reset Samsung SCX-4820.
1. version.
[http://www.megaupload.com/?d=47IOPOR2](http://www.megaupload.com/?d=47IOPOR2)
2. version.
[http://www.megaupload.com/?d=ALFUSZU8](http://www.megaupload.com/?d=ALFUSZU8)

---

### Post by Geremia on 2012-04-04
> **elboeufx said:**
> when I open Xsane, there is no "choice," it just goes straight to the camera, as if there is no other scanner attached. When I open the Samsung Unified Driver Configurator, moreover, it only shows the camera under the "scanner" tabI have the same problem. It's not a permissions issue &#8757; even running xsane as root produces the same problem.

---

