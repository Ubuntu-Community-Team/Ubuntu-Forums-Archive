---
title: "Dell 2407WFP monitor"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by notlob on 2010-01-16
I've just built a new computer and have installed Ubuntu (9.04, then upgraded to 9.10) as a dual boot with Win7.

This worked well and during the 'test' period I was impressed.

I have now adopted the new machine as my main desktop computer and have plugged in my 'normal' monitor, printer, etc. I now find that, although GRUB still works nicely and Windows loads happily and handles the new additions, Ubuntu has a major problem with my 24" monitor - a Dell 2407WFP.

If I swap this monitor out and replace it with the little old 15" TFT I used to set up the system in the first place, Ubuntu loads again! But that's no good as I want to use it with my big monitor...

With the 24" monitor the boot process gets as far as completion of the Ubuntu progress bar but, at that point, the monitor goes into standby and I can see nothing after that. I've left the machine in that state for several minutes and it does not recover.

I've played with Ubuntu's recovery mode (from the GRUB boot menu) but I couldn't achieve anything worthwhile.

Could someone advise how I overcome this problem?

Thanks.

Terry

---

### Post by MarkC502 on 2010-01-16
To start you could plug up the small one and boot up, then unplug it and plug-up the 24" without turning off the power - then adjust the screen resolution to fit the larger monitor. I suspect your problem is that the larger monitor does not support whatever mode your 15" monitor is using. This may not work but will do no harm to try ( I have removed and added monitors while a PC is running for years while working on racks of PC's ) 

Secondly you could try booting with the small monitor then going to the screen resolution settings and change them to as high a resolution your small monitor will take. Also look at the screen refresh rate and set it low as if you currently have it set at say 75hz and your 24" monitor only supports 70hz ( AS AN EXAMPLE ) then you would get the behavior you are describing.


Try those and good luck, I hate when an upgrade breaks stuff.

---

### Post by sandyd on 2010-01-16
ok. try this.

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
that will reset your display config.

---

### Post by notlob on 2010-01-17
Mark

Your suggestions put me on the right track.

I managed to plug in both monitors at the same time - with the same result as before: small one (on VGA connector) worked, big one (on digital connector) didn't.

Big difference was that I could now see (on the 15") what I was doing!

This allowed me to install the ATI driver for my graphics card (it must have been using a generic one before). With that installed I could set up the 24" monitor and I now have it running at 1920x1200. Yay!

Many thanks for the quick response and for pointing me in the right direction.

Terry

---

