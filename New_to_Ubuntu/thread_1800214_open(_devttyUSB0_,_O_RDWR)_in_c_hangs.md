---
title: "open( /dev/ttyUSB0 , O_RDWR) in c hangs"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Blatm on 2011-07-08
Hi,

I'm on ubuntu 11.04 64bit and I'm fairly inept with computers in general.

I have a device* that returns a signal through a serial cable, which I've connected to my USB port with the use of a converter. /dev/ttyUSB0 appears and is a 0 byte file. I'd like to send commands to the device using a c program. My c code has in it:

```

  printf("0 \n");
  sys = system("stty -F /dev/ttyUSB0 -icanon time 1");
  printf("1 \n");
  FilterPortFD = open("/dev/ttyUSB0",O_RDWR);
  printf("2 \n");

```When I run the code, it prints "0" and "1" but not "2". I have to ^C to kill the program.

*My device is the controller for an [Intelligent Filter Wheel]("http://www.optecinc.com/astronomy/catalog/ifw/ifw.htm") from Optec.

Does anyone know what the problem might be? I'm happy to provide any information I might have forgotten to include while writing this post.

Thanks.

---

### Post by terrykiwi83 on 2011-07-08
I would say the above is not a beginners problem, and you don't seem that inept if you can write c code.

Maybe move your topic to a more suitable forum and not the beginners section?

Just a suggestion

Edit (This is the forum you want) [http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by wep940 on 2011-07-08
I would think you want to do 2 things:

- install libusb-dev (I think that's what it is called - the development lib for USB)

- take out your sys calls and replace them with libusb calls.  This is the preferred way to access a usb device.  The functions are there to open, check the status, read/write, close, etc. a USB device.  I don't remember if there is any docs in the dev lib or if you have to go online.  I could send you a sample, but it's pretty cryptic as it's used to access a non-standard USB camera.

I don't know, but perhaps only the 0 and 1 went out because it's binary?  That would explain a 2 not being accepted.

If you want more info on the libusb calls I can look and see if I can find the more detailed docs.

---

