---
title: "Ubuntu Jaunty Dialup"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by sufjanfan on 2009-10-10
Hello,
I have recently downloaded Ubuntu Jaunty (9.04) and I am trying to get a dialup connection on it. I have a Gateway laptop with an internal modem (according to scanmodem, an "Intel Corporation 82801/DBL/DBM"). I tried wvdial, but when I attempt to configure it with wvdialconf I get a message stating "Sorry, no modem was detected! Is it in use by another pogram? Did you configure it with setserial?" I tried setserial, but I have no idea how to get it working. I then went in a new direction and used minicom, but that couldn't seem to find the modem either.
 
I don't want to leave Ubuntu, but I don't know what to do. I'm fairly frustrated now. Any help is appreciated.

---

### Post by phidia on 2009-10-10
Did you go to the linmodems website? [http://www.linmodems.org/](http://www.linmodems.org/)
You might want to try minicom as superuser to see if that will do something but you may have an unsupported modem. Most if not all internal modems are controller-less and rely on the OS to work eg windows.
Some can be made to work but you can find an external modem cheaply and it will be much less trouble.
Just be sure you get a controller type external modem-be careful some usb modems are software dependent or controller-less too.

---

### Post by superdav42 on 2009-10-10
I'm 90% sure you have an sl-modem which is actually supported pretty well in Linux. It does take a little manual configuration however. There are basically two drivers for it one is open source and one is closed. Instructions on using the open source one can be found here:
[Sl-modem in Ubuntu]("http://nnucomputerwhiz.com/sl-modem-linux.html")
and the closed sourse installation instructions can be found here:
[https://help.ubuntu.com/community/DialupModemHowto/Smartlink]("https://help.ubuntu.com/community/DialupModemHowto/Smartlink")
I found the open source driver to be easier to use because it's included in the kernel as module snd_intel8x0m and it worked fine for me. Also you don't have to recompile the driver every time you update your kernel.

---

### Post by sufjanfan on 2009-10-10
Thanks. I'll probably just buy an external modem on ebay.

---

### Post by ranch hand on 2009-10-10
An external is better.  I highly suggest a USR modem.  I actually got a USR6510c internal to work on my box under Hardy.

Lucky we have moved to where there is DSL as Jaunty is a nightmare.

Another thing you might try, remembering that it is beta and not out until the 29th, is Karmic.

My modem is still in the box but not hooked to a line and I keep seeing it detected on the verbose bootup.  I think they may have gotten a little better modem support.

That said, if you have a Winmodem I would get the external.  I don't care what  they say, software modems do not perform as well as hardware modems.

You should be able to find your modem by running;
```

lspci

```
You would be surprised the stuff that may be detected by different things in your computer.

---

### Post by Bartender on 2009-10-10
A word of caution - many external modems aren't full hardware.  They're just winmodems inside an enclosure.

If you pick up an old US Robotics serial modem, the Sabrent serial to USB adapters work well in Linux.

I was hoping that new USR 5637 would be a good solution, but have seen several posts with unhappy owners.

---

### Post by ranch hand on 2009-10-10
WOW, I have never used an external, I like the internal.  I have enough stuff plugged in.

I thought that all externals were real modems.  They must be slightly slower than the internal winmodems seeing how they depend on the cpu for processing.  That really suck.

This box came with a connexant internal winmodem (and Vista).  I could get up to 3.6k/s on a real rare good day under Vista.  Usually it was around 3.  The USR5610c that I put in from our old dead box picked it up to 4 and getting rid of Vista and going to Hardy picked it up to a pretty steady 4.4k/s.

Why people put up with winmodems is beyond me.

---

