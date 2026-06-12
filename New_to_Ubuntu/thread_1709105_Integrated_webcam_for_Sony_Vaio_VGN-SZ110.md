---
title: "Integrated webcam for Sony Vaio VGN-SZ110"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by pin0yM1x on 2011-03-17
Hey everyone new guy here with ubuntu 10.10 (for a few days) happy overall, I've just been trying to get this webcam to work the past couple days.

I've followed instructions on numerous websites but two of them I remember:

[http://ubuntuforums.org/showthread.php?p=8930938](http://ubuntuforums.org/showthread.php?p=8930938)
and:
[https://bitbucket.org/ahixon/r5u87x/](https://bitbucket.org/ahixon/r5u87x/)

Screenshot is attached if it helps any.

I've tried cheeze but it freezes up, I have since uninstalled it. Gmail videochat and Skype do not detect the webcam. I really tried to do this on my own.... thanks in advance.

---

### Post by Sina_RJ on 2011-03-17
i think you should check one application if you hadn't yet!
*System*->*Administration*->***Additional Drivers***
i think that'll be a little helpful
tell us about the result

---

### Post by pin0yM1x on 2011-03-18
Thanks for the suggestion Sina_RJ. However, It didn't work.  It only brought up NVIDIA graphics drivers.

---

### Post by no2498 on 2011-03-18
look in your package manager for xawtv and install it
also open a terminal type webcam click enter

try the cam in xawtv

---

### Post by azertyh on 2011-03-18
hello,
try gstreamer-properties [http://forums.linuxmint.com/viewtopic.php?f=42&t=61103&start=0](http://forums.linuxmint.com/viewtopic.php?f=42&t=61103&start=0)

---

### Post by pin0yM1x on 2011-03-18
no2498- Still a no go, this is what I received:
[B]pin0ym1x@pin0ym1x-VGN-SZ110:~$ webcam
reading config file: /home/pin0ym1x/.webcamrc
v4l2: open /dev/video0: Permission denied
v4l2: open /dev/video0: Permission denied
v4l: open /dev/video0: Permission denied
no grabber device available
  
[/B]I tried this also:[B]
pin0ym1x@pin0ym1x-VGN-SZ110:~$ sudo webcam
reading config file: /home/pin0ym1x/.webcamrc
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no grabber device available
  
[/B]Also I installed xawtv.  When I click to open it nothing happens :( .  Thanks for the suggestion though!

---

### Post by pin0yM1x on 2011-03-18
Hello azertyh. I appreciate the help

I got this error message:
Video for Linux 2 (v4l2): Could not open device '/dev/video0' for reading and writing.
I got this for both plugins (Linux 2(v4l2) and Linux (v4l) )

---

### Post by no2498 on 2011-03-19
this is telling me you need to set your Permission for video

Permission denied

and its been way to long for me to tell you how sorry

---

### Post by RBLevin on 2011-03-19
See this thread: [http://ubuntuforums.org/showthread.php?t=40793](http://ubuntuforums.org/showthread.php?t=40793)

---

### Post by pin0yM1x on 2011-03-21
RBLevin- I tried it out and got this:

"/etc/udev/permissions.d/udev.permissions" [New DIRECTORY]
Swap files found:
   Using specified name:
      -- none --
   In directory ~/tmp:
      -- none --
   In directory /var/tmp:
1.    udev.permissions.swo
          owned by: root   dated: Mon Mar 21 23:15:26 2011
         file name: /etc/udev/permissions.d/udev.permissions
          modified: YES
         user name: root   host name: pin0ym1x-VGN-SZ110
        process ID: 5170
2.    udev.permissions.swp
          owned by: root   dated: Sun Mar 20 01:21:29 2011
         file name: /etc/udev/permissions.d/udev.permissions
          modified: YES
         user name: root   host name: pin0ym1x-VGN-SZ110
        process ID: 12438
   In directory /tmp:
      -- none --

Enter number of swap file to use (0 to quit):

---

### Post by Quackers on 2011-03-21
I have a very similar webcam and I got it working following these instructions
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

---

### Post by RBLevin on 2011-03-21
Have you checked your permissions? If not, hit:
**System | Administration | Users and Groups**

Find your login name and select it.

Click the **Advanced Settings** button.

Click the **User Privileges** tab.

Scroll down the list and make sure **Use video devices** is checked.

Accept those settings, and then try the camera.

---

### Post by pin0yM1x on 2011-03-22
> **Quackers said:**
> I have a very similar webcam and I got it working following these instructions
[https://launchpad.net/~r5u87x-loader/+archive/ppa]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa")

Hi Quackers.  Thanks for the suggestion here is where I am currently stuck at:

pin0ym1x@pin0ym1x-VGN-SZ110:~$ sudo /usr/share/r5u87x/r5u87x-download-firmware.sh
This script is going to download and install firmware for Ricoh R5U87x
series cameras. The copyright and license status of this firmware are
unclear.
Do you want to proceed? [y/n] y
Downloading firmware...
cd: 78: can't cd to r5u87x

---

### Post by pin0yM1x on 2011-03-22
> **RBLevin said:**
> Have you checked your permissions? If not, hit:
**System | Administration | Users and Groups**

Find your login name and select it.

Click the **Advanced Settings** button.

Click the **User Privileges** tab.

Scroll down the list and make sure **Use video devices** is checked.

Accept those settings, and then try the camera.

Welcome back RBLevin! Do you really have an RB Levin? Sweet... Anyways, thanks the box wasn't checked.  However the webcam still isn't detected :(

---

### Post by pin0yM1x on 2011-03-22
Thank you to all those who've responded so far.  We are getting close.



Update-

I typed in the command **lsusb** and I can see the webcam listed here:

Bus 001 Device 006: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870

---

### Post by no2498 on 2011-03-22
retry in a terminal gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin try auto

---

### Post by Quackers on 2011-03-22
> **pin0yM1x said:**
> Hi Quackers.  Thanks for the suggestion here is where I am currently stuck at:

pin0ym1x@pin0ym1x-VGN-SZ110:~$ sudo /usr/share/r5u87x/r5u87x-download-firmware.sh
This script is going to download and install firmware for Ricoh R5U87x
series cameras. The copyright and license status of this firmware are
unclear.
Do you want to proceed? [y/n] y
Downloading firmware...
cd: 78: can't cd to r5u87x

At this point you should just type "y" and hit enter.

---

### Post by pin0yM1x on 2011-03-22
Quackers, I did enter y and hit enter as seen above. 

This is what it says afterwards:
cd: 78: can't cd to r5u87x

---

### Post by Quackers on 2011-03-22
Did you run steps 1 to 3 in that guide first?

---

### Post by pin0yM1x on 2011-03-22
> **no2498 said:**
> retry in a terminal gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin try auto

Hello again no2498
I got this for v4l: Video for Linux (v4l): Device "/dev/video0" does not exist

I got this for v4l2: Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

and Finally got this for plugin "custom" : Custom: Cannot identify device '/dev/video0

---

### Post by pin0yM1x on 2011-03-22
> **Quackers said:**
> Did you run steps 1 to 3 in that guide first?


Hi Quackers! 
  Yes I ran steps 1 through 4 actually... this is what it shows at the end of steps 3 and 4:

flipmix1013@pin0ym1x-VGN-SZ110:~**$ sudo apt-get install r5u87x**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
r5u87x is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
flipmix1013@pin0ym1x-VGN-SZ110:~$ **sudo /usr/share/r5u87x/r5u87x-download-firmware.sh**
This script is going to download and install firmware for Ricoh R5U87x
series cameras. The copyright and license status of this firmware are
unclear.
Do you want to proceed? [y/n] y
Downloading firmware...
[COLOR=Red]cd: 78: can't cd to r5u87x


[COLOR=Black]So close... I can feel it! :)[/COLOR]
[/COLOR]

---

### Post by Quackers on 2011-03-22
Try opening Cheese and see if your ugly face peers back at you :-)

---

### Post by pin0yM1x on 2011-03-22
Cheese screenshot:

---

### Post by Quackers on 2011-03-22
Hmm, sadly I'm now at the stage where I don't know what to suggest.
Those 4 instructions I linked you to earlier enabled my camera straight away. I suspect that the methods you tried originally and the latest one are possibly now conflicting with each other. I would like to suggest that you get rid of all of them and after a reboot, start again. Unfortunately, I don't know how to uninstall what you've installed - or even where it all might be.
On the one hand it seems that your camera is recognised (as the screenshot in your first post shows) but if that is the case Cheese should now be showing you your face! As it is not doing that, something is obviously wrong. Sadly, I'm not sure what though.

---

### Post by no2498 on 2011-03-22
do not try Custom use auto

also in a terminal  type dmesg click enter
just read it did it find the cam
after quackes gets back to you try a restart

---

### Post by Quackers on 2011-03-23
Member daniel007 has also found a site which has some info in ricoh cameras. Although it may not help the OP, it may help others who view this thread.

[http://www.arakhne.org/ricoh/index.html](http://www.arakhne.org/ricoh/index.html)

---

### Post by apocamix on 2011-03-25
[FONT=monospace][FONT=Arial]I had the same can't cd to r5u87x message but managed a work around in Ubuntu 10.04 64bit and I hope it helps you.
I tested it with Skype and it works for me.

EDIT: First do what Quackers suggested and follow the directions at [/FONT][/FONT][https://launchpad.net/~r5u87x-loader/+archive/ppa]("https://launchpad.net/%7Er5u87x-loader/+archive/ppa")
This should hopefully resolve step 4 of the guide and manually load the firmware that the script fails to do.
[FONT=monospace][FONT=Arial]     
1) Start by getting the firmware.
    
If you need the 64 bit you can get the rpm from here
    
[/FONT][/FONT][http://download1.rpmfusion.org/nonfree/fedora/releases/14/Everything/x86_64/os/r5u87x-firmware-0.2.0-3.a9b2171d762b.fc14.x86_64.rpm](http://download1.rpmfusion.org/nonfree/fedora/releases/14/Everything/x86_64/os/r5u87x-firmware-0.2.0-3.a9b2171d762b.fc14.x86_64.rpm)
[FONT=monospace][FONT=Arial]     
or 32 bit from here

    [/FONT][/FONT][http://download1.rpmfusion.org/nonfree/fedora/releases/14/Everything/i386/os/r5u87x-firmware-0.2.0-3.a9b2171d762b.fc14.i686.rpm](http://download1.rpmfusion.org/nonfree/fedora/releases/14/Everything/i386/os/r5u87x-firmware-0.2.0-3.a9b2171d762b.fc14.i686.rpm)[FONT=monospace][FONT=Arial]
    
I don't think the correct architecture matters... but it can't hurt :)
    
2) Open a terminal, cd to the directory you downloaded it to and run either of these depending on what you downloaded
    
```

rpm2cpio r5u87x-firmware-0.2.0-3.a9b2171d762b.fc14.x86_64.rpm | cpio -dimv
    
rpm2cpio r5u87x-firmware-0.2.0-3.a9b2171d762b.fc14.i686.rpm | cpio -dimv

```This will extract the contents of the rpm into 3 directories lib sbin and usr
    
Obviously use ```
sudo apt-get install rpm2cpio
``` first if you don't have it.
    
I'm not much of a terminal guy so at this point I opened nautilus (use  whatever file browser you use) as super user ```
sudo nautilus
``` and went into the rpm's newly created lib  folder then opened the firmware directory. There are 17 files called  r5u87x-xxxx-xxxx.fw.
    
Select all of them and copy. Then navigate in nautilus to  /usr/lib/r5u87x/ucode and paste them there.
    
4) Still in nautilus select all the .fw firmware files, right click and  (it might be overkill) set all the permissions to read and write and  allow executing file as program.
    
5) Next load the firmware by terminal ```
sudo /usr/sbin/r5u87x-loader --reload
```6) Cross your fingers, open Cheese or Skype and hope for the best ;)
    
I wasn't documenting my steps as I went but I just did it an hour ago so I'm pretty sure that was the order of events.
    
Let me know how it goes.[/FONT]
[/FONT]

---

### Post by PCNetSpec on 2011-03-25
Taken directly from the ReadMe, after cloning the repository from here:
[https://bitbucket.org/ahixon/r5u87x/overview/](https://bitbucket.org/ahixon/r5u87x/overview/)

[COLOR="blue"]++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++[/COLOR]

[COLOR="Blue"]R5U87x Userspace Tools
Version 0.2.1, 2009/11/22

Introduction
============

This project is an attempt to produce a group of useful usespace tools for
managing cameras based on Ricoh R5U87x chipsets.

You will still need to depend on such kernel drivers like uvcvideo to get the
video stream out of the device.

Supported devices
=================

See docs/model_matrix.txt

Compilation
===========

To compile the tools, it is required you have the following prerequisites
installed:

 * GCC
 * Automake
 * libusb development packages (libusb-dev or similar)
 * GLib 2.0 development packages (libglib2.0-dev or similar)

Quickstart
==========

Ubuntu
	$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
	$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
	$ cd r5u87x
	$ make
	$ sudo make install
	$ sudo r5u87x-loader --reload
	
	The loader will automatically be run on boot when it detects your webcam.
[/COLOR]
[COLOR="Blue"]++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++[/COLOR]

So, as it says:

```
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install
sudo r5u87x-loader --reload
```

hth.

---

### Post by pin0yM1x on 2011-03-31
> **PCNetSpec said:**
> Taken directly from the ReadMe, after cloning the repository from here:
[https://bitbucket.org/ahixon/r5u87x/overview/](https://bitbucket.org/ahixon/r5u87x/overview/)

[COLOR=blue]++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++[/COLOR]

[COLOR=Blue]R5U87x Userspace Tools
Version 0.2.1, 2009/11/22

Introduction
============

This project is an attempt to produce a group of useful usespace tools for
managing cameras based on Ricoh R5U87x chipsets.

You will still need to depend on such kernel drivers like uvcvideo to get the
video stream out of the device.

Supported devices
=================

See docs/model_matrix.txt

Compilation
===========

To compile the tools, it is required you have the following prerequisites
installed:

 * GCC
 * Automake
 * libusb development packages (libusb-dev or similar)
 * GLib 2.0 development packages (libglib2.0-dev or similar)

Quickstart
==========

Ubuntu
    $ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
    $ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
    $ cd r5u87x
    $ make
    $ sudo make install
    $ sudo r5u87x-loader --reload
    
    The loader will automatically be run on boot when it detects your webcam.
[/COLOR]
[COLOR=Blue]++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++[/COLOR]

So, as it says:

```
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone http://bitbucket.org/ahixon/r5u87x/
cd r5u87x
make
sudo make install
sudo r5u87x-loader --reload
```hth.

Thank you PCNetSpec I have already done what is stated above.  This is what I get:
Found camera: 05ca:1830
Camera reports positive microcode state.
Camera reports microcode version 0x0100.
Not doing anything - camera already setup.

Successfully uploaded firmware to device 05ca:1830!
Reloading uvcvideo module...
Finished.


However, my camera still does not work.  Even after reboot.

---

### Post by no2498 on 2011-04-01
install guvcviewer and or xawtv
try you cam in them

---

