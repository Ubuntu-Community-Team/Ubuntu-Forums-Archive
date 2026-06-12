---
title: "Scanning with Canon MX860 and Simple Scan"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by llmunro on 2010-04-26
Hello all!

I have gotten my  Canon MX860 printer working in under five minutes and without a hitch! Ubuntu automatically detected it and now I'm printing! :D

The scanner, however, I haven't been able to get working.  I've downloaded and installed the Linux scanner drivers for the scanner from Canon Europe, but when I open up Simple Scan, I get a message that no scanner is detected.  If I open up preferences to try to select the scanner, none is listed in the drop down menu.  (Just to rule out the obvious, I should also add that the scanner is plugged in and powered on.)

Thoughts?  

Thanks much.
Best,
Lisa

---

### Post by Jon Monreal on 2010-04-26
Hello,

What version of Ubuntu are you using? Also, are you using the 64-bit version of Ubuntu (as it appears that the Canon scanner drivers don't work under x64)?

Thanks.

---

### Post by llmunro on 2010-04-26
Hi Jon,

Thanks for the help.  I hadn't even considered that the drivers wouldn't work with 64 bit Ubuntu.  I am using the 10.04 RC, but I'm not sure how to check if I'm using the 64 bit or not.  Where might I look?

Thanks much.
Best,
Lisa

---

### Post by Jon Monreal on 2010-04-26
Hello,

If you don't know that you're using 64-bit, you probably aren't, but try going to a terminal, and typing
```
uname -a
```

If it has x86_64 in that text (and it may wrap to the next line) you are using the 64-bit version.

---

### Post by llmunro on 2010-04-26
Here's what I love about Linux: I learn new things every day.

Here's what I got:
Linux lisa-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

So, I think I'm using the 32 bit version.

The scanning thing is the only reason that I still have to boot into Windows.  It would be great to get it working.

Thanks for the help.
Best,
Lisa

---

### Post by Jon Monreal on 2010-04-27
From what I can tell from searching around, it should work.

From what I understand, you can also output .pdf files to a flash drive  from the scanner. Could you use this feature until a fix can be found?  I'll continue looking.

Thanks.

---

### Post by llmunro on 2010-04-27
Hi Jon,

Thanks for looking.  This printer/scanner will output to a flash drive, which I can certainly use in the meantime.  I have never gotten it to work as a scanner.  I tried for a while with Linux Mint, these instructions, and Xsane, but still couldn't get it figured out.

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

Many thanks.

Lisa

---

### Post by llmunro on 2010-04-30
I've been told that I need to enable scanning permissions in order to use the scanner.  If I go to Users and Groups, there's no option to give users (me, really) scanning privileges.  Is there something I have to do here?

Thanks much.
Lisa

---

### Post by Jon Monreal on 2010-04-30
Go to Applications>Accessories>Terminal. In the terminal window, type (or copy+paste)
```
sudo gedit lib/udev/rules.d/50-udev-default.rules
```and press enter, and then enter your password when prompted.

A window with gedit will pop up. Find the line that says
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
```and edit MODE="0664" to be MODE="0666". An easy way to do this would be to press Ctrl+F,  type in the "Search for" box "usb", and press "Find". I've attached a screenshot to highlight this line.

Then simply unplug the USB cord and plug it back in. With any luck, the scanner should work. If it doesn't, we can try something else.

---

### Post by llmunro on 2010-04-30
Hi Jon,

I think perhaps you have hit on the problem, as when I put

sudo gedit lib/udev/rules.d/50-udev-default.rules


and my password in the terminal, the window that came up was completely empty!

:confused:

What could this mean?

Thanks for all of your help!

Best,
Lisa

---

### Post by Jon Monreal on 2010-04-30
My bad
```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```
typed it too fast.

---

### Post by llmunro on 2010-04-30
Hi Jon,

Thanks for all of the help.  

Still no dice!

lisa@lisa-desktop:~$ lsusb
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 04a9:1735 Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

isa@lisa-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x1735 [MX860 series]) at libusb:001:009
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

lisa@lisa-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

lisa@lisa-desktop:~$ sudo chmod 660 /proc/bus/usb/001/009
chmod: cannot access `/proc/bus/usb/001/009': No such file or directory


I swear if I can get this figured out I will never complain about anything ever again! :D  Is there anywhere else to check for permissions?

Thanks for your help!

Best,
Lisa

---

### Post by Jon Monreal on 2010-04-30
Try typing
```
sudo scanimage -L
```
and see if that works.

---

### Post by llmunro on 2010-05-01
Hi Jon,

This is totally baffling.

lisa@lisa-desktop:~$ sudo scanimage -L
[sudo] password for lisa: 

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

I was following these directions

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

which I had no trouble with (ridiculously impressed with myself that I figured out the ./configure, make, and make install!) until I got to the permissions part.  This continues to stump me.

Thanks much!

Best,
Lisa

---

### Post by Jon Monreal on 2010-05-01
Hello Lisa,

That's a lot of work to go through for the entire thing to fail. Sorry to hear compiling from source didn't work.

You've added yourself to the scanners group and logged out and back in, right? If not, type the following in the terminal
```
sudo adduser myusername scanner
```
you'll need to log out and log back in in order for this to take effect.

The thing that gets to me is that you can see sane-find-scanner gives you
```
found USB scanner (vendor=0x04a9 [Canon], product=0x1735 [MX860 series])  at libusb:001:009
```

And, of course, when you used "sudo scanimage -L", you tried running it as root, which suggests this isn't a permissions problem.

Have you unplugged your scanner and plugged it back in yet? That would be a good thing to try.

Perhaps more importantly, did you install both the printer driver and ScanGear, or just the printer driver?

Thanks.

---

### Post by llmunro on 2010-05-01
Hi Jon,

Thanks for not giving up on me! :)  No doubt the problem can be chalked up to user inexperience!

Anyways,

lisa@lisa-desktop:~$ sudo adduser lisa scanner
[sudo] password for lisa: 
adduser: The group `scanner' does not exist.


Is there a way to create a scanner group that I could then add myself to?

I also don't see anything related to the scanner in Adminstration>Users and Groups>Advanced Settings.  Just about everything under the sun is listed there, but no scanner.

I double checked the /udev/ file that I edited and I think I did it right...there's a screen shot here of the line in question.

I will try your other suggestions as well.

Many thanks.
Best,
Lisa

---

### Post by bwallum on 2010-05-01
Hi

Hope I'm not interrupting the flow but I have a couple of comments.

I have tried to use Simple Scan and had issues with it. It made a 32bit system crash. The scanner was a scsi, not a usb, so this may not be your experience. I loaded Xsane Image Scanner instead and the problem went away.

I also found that I have to start my scanner then the pc to get it all working correctly. You may like to shut down your computer (with the scanner still attached and live), then turn the scanner off and on again after 30 seconds, then restart the pc and use Xsane Image Scanner.

---

### Post by Jon Monreal on 2010-05-01
> **llmunro said:**
> No doubt the problem can be chalked up to user inexperience!

I would say not in this case. You've already tried quite a few different things, 

[Someone over at the Mint forums]("http://forums.linuxmint.com/viewtopic.php?f=90&t=42025&start=0") had the same problem (which was never resolved).

When you typed "sudo scanimage -L", you ran scanimage as root, not your own account, which means that simply giving your account more privileges is not the answer.

I think the pertinent question here might be did you install ScanGear?

The Cannon EU site states
> This driver software allows your computer to interface with  the scanner element of your Canon multifunctional device
It is available as a .deb [here]("http://software.canon-europe.com/products/0010699.asp").

---

### Post by llmunro on 2010-05-01
Thanks much for all of the help! If nothing else, I am learning tons! :)

I reinstalled the .deb of the ScanGear MP.  Is there something else I need to do with it besides install it?

I have unplugged and plugged back in.

The thread over at the Linux Mint forum was actually started by me! :oops:  I was trying to get the darned scanner to work with my Linux Mint laptop.  Same story there: printing but no scanning.  Things got even more confusing when Sane began recognizing the built in webcam as a scanning device.  (Like, what?) This has never been resolved, as I gave up.

I found this thread

[http://ubuntuforums.org/showthread.php?t=1391707](http://ubuntuforums.org/showthread.php?t=1391707)

although I'm not sure I totally understand it completely. 

I blame the scanner! ;)

Best,
Lisa

---

### Post by Jon Monreal on 2010-05-01
If you're using 10.04 and have kept it updated, you will already have the version mentioned in that thread, so that can't offer a solution.

I'll see if I can't dig anything else up.

***EDIT: Type
```
scangearmp
```
in the terminal and press enter, and see if that works for you.

---

### Post by llmunro on 2010-05-02
Jon,

I am literally sitting here in amazement, having now scanned a bunch of pages with the scangearmp command that you suggested!!!!!  It brings up a window that I'd never seen before with all of the scanning options (ADF, duplex, etc.) and scans without a hitch!

I had totally given up!  Thank you so much! :D :D :D

Happy Sunday!!!!  

I'm off to scan a bunch of stuff!

Best,
Lisa

---

### Post by Jon Monreal on 2010-05-02
It's no problem.

That scangearmp is the program you downloaded from Canon (so, for some reason still no simple scan, but at least their program works).

Glad that solved the problem for you.

Regards,
Jon

---

### Post by kahlil88 on 2010-09-06
Forgive me for bumping an old thread, but has anyone gotten the scanner to work on 64-bit?

---

### Post by llmunro on 2011-01-18
I'm resurrecting this ancient thread to report that I upgraded to Ubuntu 10.10 and without doing ABSOLUTELY ANYTHING, the scanner (that refused to scan in 10.04 no matter what I did) now works beautifully with both Simple Scan and XSane.  I have no idea how or why this has happened, but I'm grateful all the same.


As to whether this will work with the 64 bit version, I can't say.

Cheers to all.

Best,
Lisa

---

### Post by msantosnj on 2011-05-21
I had to reply to this thread as I found the answer to using the Canon MX860 to print and scan wirelessly.  Follow the steps below:

                                  
[LIST=1]
[*][FONT=FreeSans, serif][SIZE=2]Get     the Canon drivers from the Canon web site     ([http://software.canon-europe.com/products/0010699.asp](http://software.canon-europe.com/products/0010699.asp)) (both cnijfilter Debian downloads)
[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]Go     to your downloads and extract the package - Right-click and Extract     Here[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]There     should be a deb tar gz file:     cnijfilter-mx860series-3.10-1-i386-deb.tar.gz[/SIZE][/FONT]
[LIST=1]
[*][FONT=FreeSans, serif][SIZE=2]Extract         the package - Right-click and Extract Here[/SIZE][/FONT]
[/LIST]
     
[*][FONT=FreeSans, serif][SIZE=2]There     should be 2 files in the packages directory:     cnijfilter-common_3.10-1_i386.deb,     cnijfilter-mx860series_3.10-1_i386.deb[/SIZE][/FONT]
[LIST=1]
[*][FONT=FreeSans, serif][SIZE=2]Extract         the packages – Right-click and Extract Here[/SIZE][/FONT]
[/LIST]
     
[*][FONT=FreeSans, serif][SIZE=2]In     each of the new directories there should be a usr and DEBIAN     directory. [/SIZE][/FONT]
[LIST=1]
[*][FONT=FreeSans, serif][SIZE=2]In         the DEBIAN directories edit the control file to remove the items         after the line Depends:[/SIZE][/FONT]
[/LIST]
     
[*][FONT=FreeSans, serif][SIZE=2]Now     open a terminal and from the command line rebuild the packages from     the packages directory: 

dpkg-deb -b     cnijfilter-common_3.10-1_i386
dpkg-deb -b     cnijfilter-mx860series_3.10-1_i386
[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]Now     install the packages:

sudo dpkg --force-architecture -i     cnijfilter-common_3.30-1_i386.deb
sudo dpkg --force-architecture     -i cnijfilter-mx870series_3.30-1_i386.deb
[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]Now     make sure the cups items are owned by root: 
sudo chown root:root     /usr/lib/cups/backend/cnij*
sudo chown root:root     /usr/lib/cups/filter/pstocanonij
[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]Go     to System > Administration > Printing and install the printer[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]For     scanning, download the scangearmp* debian file from the same     website.[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]Repeat     steps 2 thru 7, replacing the indicated file names with the ones for     scangearmp*.[/SIZE][/FONT]
[*][FONT=FreeSans, serif][SIZE=2]Go     to Applications, Graphics, Simple Scan and start scanning.[/SIZE][/FONT]
[/LIST]
 
Now if my Ubuntu laptop only showed up when I initiate the scan directly from the printer, I would be in heaven. :popcorn:

---

