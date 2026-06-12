---
title: "hardware cannot uprade any further"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by 2roombas on 2010-03-31
How dangerous is it to stick with an older unsupported version of ubuntu? I have an older computer here that cannot not upgrade anymore. I could get a new computer, true, but why do that when this one is doing exactly what I need it to do just fine.

---

### Post by halitech on 2010-03-31
usually after a time there are no more security updates so you would be vulnerable to any exploits that were fixed in later versions.

what are the system specs?

---

### Post by undecim on 2010-03-31
It's not entirely dangerous. As long as you are not running any services from it and only visit trusted web sites.

If you browse the web a lot, it wouldn't hurt to learn to compile Firefox so that you can keep it up to date.

---

### Post by NCLI on 2010-03-31
As long as it isn't connected to the internet, you should be fine. If it is, you may have problems...

Why can't you upgrade it?

---

### Post by 2roombas on 2010-03-31
> **NCLI said:**
> Why can't you upgrade it?

I'm OK for now (I use 9.04), but I'm sure eventually that will reach it's EOL.  I'm using an old Dimension 2350 and I've tried repeatedly to upgrade to 9.10 (also to beta 1 10.04) to only get those random freezes, then I just reload trusty 9.04. I sure hope the final 10.04 will fix this, otherwise I think lubuntu might have to be my next OS when it comes out. I'm not a gamer nor do I listen to music and watch tv/movies on this computer (my laptop does all that). This computer is basically email and some web browsing.

---

### Post by NCLI on 2010-03-31
Are you sure it's not just a regression bug? Could be that some of your hardware isn't playing well with the new kernel.

---

### Post by 2roombas on 2010-03-31
> **NCLI said:**
> Are you sure it's not just a regression bug? Could be that some of your hardware isn't playing well with the new kernel.

And how to I check/fix it if that is the case?

---

### Post by NCLI on 2010-03-31
Try reporting a bug. Simply run "ubuntu-bug" in a terminal or the ALT+F2 dialog, then follow the prompts.

This should end with you submitting a bug to Launchpad, Ubuntu's bug-tracker. The developers when then take a look at your report, ask you for more information, and if they conclude it' a regression, they will try to fix it. 

Make sure to run ubuntu-bug in the install you're having problems with.

---

### Post by NCLI on 2010-03-31
Ok, new method:

Run "ubuntu-bug linux" instead. This will start a kernel-specific bug reporting process, which I think is what you need to do.

---

### Post by 2roombas on 2010-03-31
Thank you.. I'll try that.  I'm actually, once again, trying a 9.10 upgrade on this machine. My 9.04 live cd is on the desk in front of me, of course. I've searched this problem and I see the random freezes are  rather common for some people, however no where have I read why that happens. I just thought my computer was too old now, and 9.04 was the end of the line for it. Perhaps not.

---

### Post by halitech on 2010-03-31
According to here ( [http://support.dell.com/support/edocs/SYSTEMS/dim2350/specs.htm](http://support.dell.com/support/edocs/SYSTEMS/dim2350/specs.htm) ) you have decent specs to run any version of Ubuntu. Only limits I see are the mainboard only has 3 PCI slots and the onboard video is an Intel 3D Extreme Graphics card. Have you added a seperate video card or are you using the onboard graphics?

---

### Post by The Real Dave on 2010-03-31
With that hardware, you should be sitting pretty :) If Ubuntu ain't working out well for you, you could try out some other distros, maybe a Debian Stable system. Longer support, similar system if your willing to learn the differences.

But if that is your hardware, any Ubuntu should work fine, Lucid included. I'm running Lucid on less. It could be a bug, or a problem with your hardware. Glitchy programs can often be caused by bad memory. Try running a Memtest overnight and see if anything crops up. Harddrive could be another culprit, so a filesystem check would be good, or a check for bad sectors. 

Sounds more like faulty hardware, or a software bug than anything else to me :)

---

### Post by 2roombas on 2010-03-31
Today via update manager  tried to upgrade once again to 9.10... thenI just immediately upgraded to 10.04.  So far so good!:p

---

