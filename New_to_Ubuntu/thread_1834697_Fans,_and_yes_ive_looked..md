---
title: "Fans, and yes ive looked."
date: 2011-08-27
forum: New to Ubuntu
---

### Post by DoofyRob on 2011-08-27
I have looked at the threads about loud fans and lm-sensor, but they don seem to be for complete beginners. I am used Ubuntu, but I´m still not familiar with it. ( for some reason my keyboard makes accents like this: &#324;&#472; and i dont know how to make it normal for example.) does anyone have a full step by step newbie walk through of how to quiet fans?

---

### Post by fleamour on 2011-08-28
Fans run at the speed they should, unless dust build up is causing problems.  You do not state whether desktop/tower PC or laptop.

If desktop PC then you can purchase quieter fans from:

[http://www.quietpc.com/](http://www.quietpc.com/)

However you would need to be comfortable with opening up your PC.  You get what you pay for.  Sometimes the PSU (Power Supply Unit) is the noisy culprit, but getting a box to run quieter will usually cost some dollars.  

If a laptop, then there is not an awful lot you can do other than clean the heatsink/fan/airways with some canned air.

I hope this helps...

EDIT [afterthought]:  You may want to check thermal throttling for the fans in BIOS.

---

### Post by LowSky on 2011-08-28
the keyboard accent thing is an entire other issue.
Go to keyboard preferences to fix.

As for fans... if its a desktop, buy quieter ones, or a fan controller.
If its a laptop, it could be a sensor issue, you may need your exact model for more information.

---

### Post by 3rdalbum on 2011-08-28
Set up the BIOS to control them itself. It will control them more efficiently and more safely than any pure software driver could.

I've never understood why Windows PCs come with extra software to control the fans, when the ability to do it is already built into the motherboard. What happens if the software crashes when running the fans slowly, and then you decide to do some gaming? Your computer would crash too due to thermal overload.

---

### Post by Mark Phelps on 2011-08-28
> **DoofyRob said:**
> does anyone have a full step by step newbie walk through of how to quiet fans?

If the fans are loud, they are running fast because your PC is running HOT.  If you simply slow down the fans (using BIOS settings or other software), the heat will only get worse -- and you then risk burning out your PC.

Better approch is to install apps to monitor the temperatures to see what is running hot.  If it's your CPU, there may be ways to throttle it back so that it's not running so fast -- which will cool it down and also slow down the fans.

---

### Post by theozzlives on 2011-08-28
Laptop: Try cleaning with canned air

Desktop/Tower: It's prolly dust, replace your CPU fan and/or Replace your PSU.

Regardless it's prolly dust.

---

### Post by BitJunkie on 2011-08-29
Have a look at this guide: [How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132")

Go to the section titled "How to temporarily set kernel boot options on an installed OS" and use it to add: ```
acpi_osi="Linux"
```

If this helps, you can follow the next section in the guide to add it permanently. 

I have to use this to get my fans working properly on my Toshiba laptop.

---

### Post by goodbye-windows(tm) on 2011-08-29
My PC always ran slower than molasses-I blamed it on windoze for years and years. When I started using ubuntu, the computer still ran slow...although faster than windoze did.

My fan ran full tilt, all the time!!

I finally began to suspect the cooling for the microprocessor was malfunctioning. I took the processor out, expecting to find dust clogged innards in the heat sink. But, it was clean.

I ran sensors with the watch command:

watch sensors -f

I found my processor was running at 160 degrees F, with almost no load on the processor!!! 

I found the problem was a Dell problem, there was no heat sink compound between the processor and the heat sink!!!!!!!!!

I bought some of the good heatsink compound (the silver type) and put the system back together. The processor ran much faster, the processor temp dropped down to 120F with light processor loading and the fan would idle back to slow speed until it needed to cool the processor. I ran the processor at 100 percent for an hour, and never saw a temperature over 145 degrees!!!!

So, I did resolve my issue and ended up with a nice quiet running laptop to boot.

If your processor seems to be sluggish or runs slow, the problem might be in your cooling system-because the fan runs to try to cool the processor!!! 

I love ubuntu-it's good to be having the computer run to serve me rather than to have it running to suit Microsoft::>

Regards,

Art

---

