---
title: "Laptop doesn't recognise webcam"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Malt Frisky on 2010-06-05
I've been having this problem for sometime.

I've got a Sony Vaio VGN-FZ21Z and I've been trying to configure the in built webcam with Ubuntu and so far have had no joy.

Can anyone help me out with this?

Jonny

---

### Post by gordintoronto on 2010-06-05
Have you used Synaptic to install Cheese? When you run it, what happens?

If you open Accessories/Terminal and enter the command:
lsusb
how is your webcam identified?

What did you do to "configure the webcam"? What happened?

---

### Post by Malt Frisky on 2010-06-06
> **gordintoronto said:**
> Have you used Synaptic to install Cheese? When you run it, what happens?

If you open Accessories/Terminal and enter the command:
lsusb
how is your webcam identified?

What did you do to "configure the webcam"? What happened?

I've installed the following from Synaptic

Cheese
Cheese-common
libcheese-gtk18
libcheese-gtk-dev

I then open from applications and then the program goes grey.

When I type in the following the command 'Isusb' in terminal these stats show.

Bus 007 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 007 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 007 Device 003: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 007 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Still no joy, it just seems that Ubuntu doesn't know it's there?

Any other solutions.

Jonny

---

### Post by no2498 on 2010-06-06
wxcam may be in Synaptic if not read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by gordintoronto on 2010-06-06
Ubuntu certainly knows it's there. This line is your webcam:
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]

Google shows this page about using this camera in Debian or Ubuntu:
[http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/) 

but I'm not sure how current it is.

---

### Post by no2498 on 2010-06-07
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


hope it come on

if yes try the cam in cheese

hope this helps

---

### Post by Malt Frisky on 2010-06-11
> **no2498 said:**
> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


hope it come on

if yes try the cam in cheese

hope this helps

I've tried the gstreamer line.

Okay, put in the gstreamer-properties line at this come up in the terminal

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

Mutimedia System Selector 

Tested the line v4l

Video for Linux (v4l): Device "/dev/video0" does not exist.

And v4l2

Video for Linux 2 (v4l2): Cannot identify device "/dev/video0".

Still no joy.

---

### Post by z3uSS on 2010-06-12
same problem here ... i have an VGN-FZ31M and have the same issue with camera ... funny part is that when i tried the notebook edition it worked fine ... but with desktop edition camera is unavailable ...

some help anyone ?

---

### Post by z3uSS on 2010-06-14
ok ... problem solved for me :)

here is what i did : 

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x](http://bitbucket.org/ahixon/r5u87x)
$ cd r5u87x
$ sudo make
$ sudo make install
$ sudo r5u87x-loader --reload
        
The loader will automatically be run on boot when it detects your webcam.

hope it work's for you too

---

### Post by fordowner on 2010-06-16
I also have a Ricoh camera operating on my Sony Vaio laptop which Ubuntu apparently does not recognize. 

I put the command suggested in the terminal but just got "command not found responses to the lines.  

Cheese also just turns grey.  

I am also getting the same messages when i open the gstreamer.

---

### Post by fordowner on 2010-06-16
[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)   these files got my ricoh webcam on my Sony Vaio  to work.  first i downloaded the i386 firmware file then the i386 file.  

Though I was trying to set it up so i could do webchat with people on msn messenger  the "aMSN" file.  Unfortunately now i got a message saying MSN has changed their protocals and thus aMSN no longer has access to providing a camera to MSN people.   So I can see them but they can't see me.   Guess I need to look for a way to be able to do video chat with people using MSN in Honduras.

---

### Post by sandy8925 on 2010-06-21
you could probably try pidgin or empathy. i think you can do video chat over msn with those.

---

### Post by fordowner on 2010-06-21
Thanks, but it looks like they still don't support video in msn messenger

---

### Post by rmp73 on 2010-08-19
> **z3uSS said:**
> ok ... problem solved for me :)

here is what i did : 

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x](http://bitbucket.org/ahixon/r5u87x)
$ cd r5u87x
$ sudo make
$ sudo make install
$ sudo r5u87x-loader --reload
        
The loader will automatically be run on boot when it detects your webcam.

hope it work's for you too

I've a Vaio VGN-FZ11Z, so a little older perhaps.  The lsusb entry for my webcam reads: 

Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

Running 10.04 this solution works like a dream (for Skype) following a system reboot, (prior to the reboot the webcam image was upside-down).

BUT - Cheese is another story!  The programme loads and recognizes the camera (little green LED next to camera is lit) but the Cheese window is completely black... Any ideas?

---

