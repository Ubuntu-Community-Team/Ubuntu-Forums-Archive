---
title: "Serial Communications"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-06-19
So here's something I've never needed to do in the 4 years I've been with linux.  Simple serial communication.

In windows I just open up Putty or Hyper terminal, choose a com port,set my baud rate, and then have a fun time.

How do I do serial communications through bash or another simple program?

---

### Post by jonobr on 2009-06-19
you need to use minicom

Type minicom at the terminal window and hit control a to show how your setp.

Hit z to change config such as speed parity etc.

The trick is finding out what tty your on, but it should be a simple deducation to get it working

---

### Post by jonobr on 2009-06-19
Just to add


I had some screen caps of minicom [in this thread]("http://ubuntuforums.org/showthread.php?t=1179442&highlight=terminal") which may help you

Cheers

---

### Post by CryptiniteDemon on 2009-06-19
Not having any luck.

I have a USB to serial adapter that's on /dev/ttyUSB0,  and another one that does ttyUSB1 and ttyUSB2.  Can't communicate at all though.  It constantly says it's offline.  I have my com settings to 19200,8,N,1 which is what they're supposed to be for my equipment.

---

### Post by jonobr on 2009-06-19
Hello


Im thinking that this maybe a driver issue so, which I may not be able to help you with

Your windows machine willr econgnise the usb connected and load a driver, however your ubuntu may not.

try doing

lsusb  and see what it says back.

You may get a driver for your system if you know the make,
The make sometimes can be found when you look in dmesg , it will tell you the make and model number

So, in short, I dont think its a minicom issue, just that minicom cant use your device.

Is there any way you can use a comm port db9 connected serial?

---

### Post by lkraemer on 2009-06-19
Use Synaptic and install wvdial.

Plug in your USB to Serial Converter.

Open a Terminal Window and copy/paste

```

sudo wvdialconf /etc/wvdial.conf

```

This should locate your USB to Serial Converter and Modem if it is
attached, but by not having it attached you might get error codes,
since it wvdial is trying to communicate with a Modem.  But it should
find your converter.

Once you know 100% what the port is, try minicom.  I haven't used it.

lkraemer

---

### Post by jonobr on 2009-06-19
Hello


minicom is solid, its as good as hypterm, just not gui-fied,
again, the main problem is always with the tty settings
but if your used to hyperterm, you can usually figure out when serial is happening or not by the rubbish displayed on the screen

---

### Post by CryptiniteDemon on 2009-06-19
I figured it out.  I ran minicom like 300 times and one instance of it ended up locking the port for some reason.  I couldn't kill it either.  Weird.  Anyway, restarted and I got it to work fine now.  Also found gtkterm, which is gui.  I like them both.

Thanks for the help.

---

### Post by jonobr on 2009-06-19
Super ):P

---

