---
title: "Problem using serial or usb  Comm Ports"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by ubume2 on 2009-03-25
I am trying an application through Wine, but suspect Wine is not the problem.  I am trying an application called MixW that uses the sound card to receive and transmit on radio frequencies.  On XP the program runs on Com3. On Ubuntu I get the error message this port does not exist or is used by another application or program. I have tried using a 9 pin serial cable and also a usb to serial connection and get the same error.

I have tried all available ports with the same error message.

I have also tried the linux equivalent called gpsk and still no luck.

Help would be appreciated.

Thank you

---

### Post by PapaNerd on 2009-03-25
I presume you are connecting to either a TNC or directly to the radio.  As a debugging step, you might want to try the "screen" utility to see if you can confirm the connection via the serial port, thus dividing the problem a bit.  73.

---

### Post by ubume2 on 2009-03-25
I am connecting from computer to radio.  I have a CAT cable connected on Com1. It works, but I don't use it on MixW. I have the digital interface connected to Com3.  

I am not sure what you mean by screen utility. lsusb shows the PL2303 is installed.

---

### Post by anewguy on 2009-03-25
I could be wrong here, but I didn't think Wine supported using USB ports (I thought I ran into that a while ago).  I'm not sure if it supports serial ports either.  You may want to go the winehq and check there.

Dave :)

---

### Post by ubume2 on 2009-03-26
> **anewguy said:**
> I could be wrong here, but I didn't think Wine supported using USB ports (I thought I ran into that a while ago).  I'm not sure if it supports serial ports either.  You may want to go the winehq and check there.

Dave :)

I switched around the interfaces and used serial cables only and everything seems to work okay.  You are correct re: Wine not supporting usb ports.

Thanks

---

