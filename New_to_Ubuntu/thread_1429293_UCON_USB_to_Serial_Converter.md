---
title: "UCON USB to Serial Converter"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by ctdahle on 2010-03-13
I took my son (7 years old) to a robot workshop at the local college a week ago, and after that, followed up on his request that we get our own robot kit. We looked at several different kits and found that most of them (especially the ones intended for use by kids) are ms windows based.

I ended up with a robot kit called Robo-Box which uses a Logo based programming environment called Logo Blocks, or in the alternative, Logo Cricket. I was able to set up Logo Blocks in WINE, but in order to upload the programming instructions to the robot controller, I need to use an RS232 serial port...naturally my HP-G61 laptop has no RS232 port.

The kit came with a USB to Serial converter identified as a UCON-232S.

I have done a bit of googling around and have found some reference to linux drivers for this converter, but I really don't understand what to do in order to make it work.

I would appreciate any guidance, so would my 7-year old

---

### Post by ctdahle on 2010-03-14
I found this article

[http://www.linux-usb.org/USB-guide/x356.html](http://www.linux-usb.org/USB-guide/x356.html)

which seems to be on target. But I don't understand how to "turn on USB serial converter support"

---

### Post by Bachstelze on 2010-03-14
We need to find out exactly which device you use. Open up a terminal and run the command

```
lsusb
```

then post the results.

---

### Post by ctdahle on 2010-03-14
Thank you,

lsusb returns the following


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by ctdahle on 2010-03-14
Looks like I'm going to have to surrender to MS on this one and put a windows partition back on one of the machines. I can't get either of the robot programming environments to run consistently in WINE, and there is not a lot of support out there anywhere for the particular USB to Serial converter that came with our robot kit.

---

### Post by lkraemer on 2010-03-15
I think we need a little more correct information.

Boot up your computer with the USB to Serial Converter REMOVED!
Open a Terminal Window and type:
```

lsusb

```
Now post the output.

Then Plug in the USB to Serial Converter and wait ~2 minutes.
Open a Terminal Window and type:
```

lsusb

```
Now post that output.  This will tell you if the Device is recognized.
It probably will be recognized.

If it doesn't get detected, Purchase one of these, as they work!

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

This link may be helpful:
[http://ubuntuforums.org/showthread.php?p=8520642#post8520642](http://ubuntuforums.org/showthread.php?p=8520642#post8520642)

lk

---

### Post by ctdahle on 2010-03-20
Thank you Larry, I confirmed, that the usb to serial converter is recognized.

However, the "LogoBlocks" programming environment, via the WINdows Emulator is not able to communicate with the microcontroller, or, for that matter, even get the compiler to consistently load. I could spend a lot of time fiddling with it, but frankly I'm not expecting that I will spend much time probing the limits of the proprietary controller that came with our robot kit. My real desire is to emulate the proprietary controller with an Arduino, and so far I can do that on my Linux machines just fine.

I just set up an old windows machine from the thrift shop for the kids to use for experimenting with the little robot. It's not a very "pure" solution, but it gets the job done.

I'm going to mark this solved.

---

