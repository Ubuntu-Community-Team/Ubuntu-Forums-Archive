---
title: "Canon Canoscan LiDE 100"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by spribo on 2009-08-12
I have Ubuntu Jaunty, but my Canon LiDE 100 scanner doesn't work. Sane documentation says it is not supported, but is there a way to make it work by editing, for example, configuration files?
Output from sane-find-scanner:
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x1904 [CanoScan], chip=GL843) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

and from scanimage -L:
scanimage: no SANE devices found.

---

### Post by PureLoneWolf on 2009-08-12
I have the exact same scanner and all attempts to get it working have been fruitless.

I have to run it through XP in Virtualbox PUEL

---

### Post by spribo on 2009-08-12
Well, I am also using VirtualBox Puel, but Win XP is running too slow and crashes all time long!

---

### Post by natacho on 2009-10-07
How do you make it run with virtualbox?
I add it in Settings enable USB enable usb 2.0 and add Canon CanoScan [0603] but my xp does not see it :'(

Thanks

---

### Post by ipernar on 2010-03-11
I made a youtube video where I explained all!!!

[http://www.youtube.com/watch?v=Z3teSzoXpNA](http://www.youtube.com/watch?v=Z3teSzoXpNA)

---

### Post by desertdog on 2010-06-14
This scanner is now supported by sane

> To get this working, here are the steps to take:

1) You need some usb libraries, so, in a terminal type:

sudo apt-get install libusb-dev build-essential libsane-dev

2) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

sudo apt-get install git-core

3) Now use the git that was just installed to get the sane backends using the following command:

git clone git://git.debian.org/sane/sane-backends.git

That downloads the backends and puts them in a folder called sane-backends in your home folder.

4) Change directory into the new sane-backends folder and compile them:

cd sane-backends

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

make <--- this one takes a while

sudo make install

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions.

5) You need to edit a file, but you need to be root to edit it, so:

sudo gedit /lib/udev/rules.d/40-libsane.rules

and add the following 2 lines:

# Canon CanoScan Lide 100
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1904", ENV{libsane_matched}="yes"

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY!
Instructions modified version of Shutter4U's post. 

---

### Post by sarim on 2010-06-29
That is not working for my printer. I fetched the git from debian and compiled. Then add a udev rule.
But in xsane, No device found. :(

---

### Post by desertdog on 2010-06-29
Check file /etc/sane.d/genesys.conf to see if your scanner is listed.

If not, add it with a text editor. Use the format that the other scanners use.

---

### Post by timgayler on 2010-08-01
I'm puzzled. I've followed the very clear instructions above on updating, however I'm getting an error at the make stage saying....


make[1]: *** [sane.ind] Error 1
make[1]: Leaving directory `/home/<username>/sane-backends/doc'
make: *** [all-recursive] Error 1

If anyone has any ideas here on things I could try that would be appeciated

Thanks

---

### Post by soldier1st on 2010-08-03
when you plugged it in did ubuntu prompt to install drivers? i have an lide 20 and it works just fine so yours should be working. also are you running 10.04?

---

### Post by timgayler on 2010-08-04
Yes I'm running 10.04 (all updates having been done). No prompt for drivers, but I wasn't expecting one from previous experience of scanners. No sign of scanner when I probe for it

---

### Post by desertdog on 2010-08-11
> **timgayler said:**
> I'm puzzled. I've followed the very clear instructions above on updating, however I'm getting an error at the make stage saying....


make[1]: *** [sane.ind] Error 1
make[1]: Leaving directory `/home/<username>/sane-backends/doc'
make: *** [all-recursive] Error 1

If anyone has any ideas here on things I could try that would be appeciated

Thanks

It looks like you might have been in the directory ~/sane-backends/doc, when you tried to build. You want to do:
$cd ~/sane-backends
before your ./configure, make, and sudo make install commands.

---

### Post by courtier on 2010-08-23
Thank you Desert Dog. I followed your instructions to the letter and it all worked. Simple Scan works on photo mode but does not work on text mode. Xsane seems to do everything I need.

---

### Post by Tormented Tapir on 2010-10-11
> **timgayler said:**
> I'm puzzled. I've followed the very clear instructions above on updating, however I'm getting an error at the make stage saying....


make[1]: *** [sane.ind] Error 1
make[1]: Leaving directory `/home/<username>/sane-backends/doc'
make: *** [all-recursive] Error 1

If anyone has any ideas here on things I could try that would be appeciated

Thanks

I had the same problem, it seems there's a weird dependency in livetex, a workaround is to set a variable @USE_LATEX_TRUE@STANDARD = sane.ps" as empty in docs/Makefile.in
(ie. delete the string sane.ps). I tried it and it compiles allright.

This is the source of the workaround:  [https://trac.macports.org/ticket/25360](https://trac.macports.org/ticket/25360)

Greets
J

---

### Post by courtier on 2010-10-18
Thank you all for these posts. I followed them and finally have my canon LIDE 100 working with gimp and simple-scan under ubuntu maverik meercat 10.10. Using the gimp I can make all adjustments to gamma, brightness, contrast and dots per inch, in fact it all works.

Truly we are all in this together, and fortunate in having a genuine, and generous BIG SOCIETY.

---

### Post by nethertether on 2011-02-20
[SIZE=3][/SIZE][SIZE=3]I have used the method described in [/SIZE][SIZE=3]desertdog's[/SIZE][SIZE=3] June 14th 2010[/SIZE][SIZE=3] post to successfully retrieve and compile  the sane-backends under Karmic and Lucid, however not under Maverick.

Nevertheless, I did find complete support for the CanoScan LiDE 100 in the newest version of SANE.  It is not available in the canonical sources.  It is from this source.

[http://bobthegnome.blogspot.com/2010/11/using-latest-sane-drivers-in-ubuntu.html](http://bobthegnome.blogspot.com/2010/11/using-latest-sane-drivers-in-ubuntu.html)[/SIZE]

---

### Post by RobertEr on 2011-08-12
The only workable solution I have heard about is using WIndows XP but I am hoping it wills one day work with Ubuntu but I a m not holding my breath because Canon has  always been very uncooperative

---

