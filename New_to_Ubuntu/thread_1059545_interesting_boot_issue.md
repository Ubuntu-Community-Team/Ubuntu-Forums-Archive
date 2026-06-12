---
title: "interesting boot issue"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by moveright on 2009-02-03
or maybe it is not interesting.  I installed ubuntu but it does something a bit odd.  when I boot, it brings up the initial ubuntu screen where the 1/5" bar would go back and forth but it only goes about an inch to the right then the system APPEARS to freeze, but alas, it is not frozen.  if I hold down an arrow key, the bar will hit the right side, then go back to the left and become the actual progress bar which loads from left to right, ultimately booting the OS.

any ideas?

weird right?



also, if any of you get a chance, how to I "format" my HDD so that ubuntu is the only thing on it?  I also have kubuntu and windows xp right now, all screwed up.

---

### Post by utnubuuser on 2009-02-04
HI -- Yeah, that's a slightly unusual boot prob.  Occasionally get something similar when running from a USB stick on certain hardware needing proprietary drivers.

Insofar as cleaning your hdd, -- > sudo apt-get install gpartedin terminal. 
 With gParted you can edit your partitions. (resize, delete, etc.).
It's a bit of a chore, but fairly safe.
Usually, instead of upgrading, I make room on my hdd with gParted, install the new release, then delete the old version.  -- You should be able to do this for the other OSs on the hdd.
After resizing/deleting, you might find yourself in a postition of having to re-install grub, - no big deal though.  just google: re-install grub ubuntu.
If you get stuck, send a message

---

### Post by Elfy on 2009-02-04
There are some system logs in the System Admin menu - check messages and syslog - they are both time stamped - so you should be able to see where the issue is.

---

### Post by Ripose on 2009-02-04
> ... system APPEARS to freeze, but alas, it is not frozen.  if I hold down an arrow key, the bar will hit the right side, then go back to the left and become the actual progress bar which loads from left to right, ultimately booting the OS.

any ideas?

weird right?

Not really weird at all. Let me guess,,,you just installed Ubuntu 8.10 right? 64 bit? AMD?

This has become a fairly common issue, there are other threads about it but no solutions yet.

---

### Post by moveright on 2009-02-04
> **Ripose said:**
> Not really weird at all. Let me guess,,,you just installed Ubuntu 8.10 right? 64 bit? AMD?

This has become a fairly common issue, there are other threads about it but no solutions yet.

you got me.  although I didn't install a 64bit version of ubuntu, I just have the 64bit processor.


well if no one on here has made any progress on that, then there is oh, lemme see....  about a -10% I'll make anything happen.  I'll just be patient and wait.  this OS is really pretty cool though, I'm not very used to it but I am able to find things in it quicker than in windows just by naturally looking where I think something would be.

cool, thanks all.

---

### Post by moveright on 2009-02-04
> **forestpixie said:**
> There are some system logs in the System Admin menu - check messages and syslog - they are both time stamped - so you should be able to see where the issue is.

here are the first four lines of my log this morning.  Wonder if it has anything to do with that map file issue.  funny, I figured it was just because I had my partitions all jacked up.

Feb  4 06:02:18 moveright-laptop syslogd 1.5.0#2ubuntu6: restart.
Feb  4 06:02:18 moveright-laptop kernel: Inspecting /boot/System.map-2.6.27-11-generic
Feb  4 06:02:18 moveright-laptop kernel: Cannot find map file.
Feb  4 06:02:18 moveright-laptop kernel: Loaded 68746 symbols from 92 modules.

---

### Post by moveright on 2009-02-04
oh yeah, so knowing about this boot issue, should I be using the 64bit version of ubuntu to fix this?

---

### Post by moveright on 2009-02-05
> **Ripose said:**
> Not really weird at all. Let me guess,,,you just installed Ubuntu 8.10 right? 64 bit? AMD?

This has become a fairly common issue, there are other threads about it but no solutions yet.

so I am guessing there is still no fix for this, I did not see it listed in the official "bugs and workarounds" thread.  it's a shame, it's such a nice OS.  I installed the 64bit version last night, and I get the "aperture beyond 4gb" error which I researched and found that this would be fixed in the jackalope release.  I wonder if this other booting issue I am having (with having to hit a key to make it continue to boot at the progress bar) will be fixed with the new release as well.

---

### Post by Ripose on 2009-02-05
I have posted some info about the _aperture error_ here: [message 82]("http://ubuntuforums.org/showthread.php?p=6678192#post6678192") 

The issue about having to_ repeatedly hit (or hold down) a key to keep the boot startup going_ is quite widespread, it affects Ubuntu, Kubuntu, SuSE, Mint and Debian. I have not found out much about this one yet.

I'll post back when I find out more.:popcorn:

---

### Post by Ripose on 2009-02-06
**FIX:**[SIZE=3] Having to repeatedly hit or hold down ANY key to continue boot and/or shutdown.[/SIZE]\\:D/

Add the following parameters to the kernel line in [COLOR=Navy]/boot/grub/menu.lst [/COLOR]somewhere between the "[COLOR=Red]resume=/dev/sda*[/COLOR]" and "[COLOR=Red]splash=silent[/COLOR]" parameters:

[COLOR=Red]notsc pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

[COLOR=Black]I found the solution on the SuSE forum.[/COLOR]
[/COLOR]

---

### Post by sergiom99 on 2009-05-23
> **Ripose said:**
> 

[COLOR=Red]notsc pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

[/COLOR]

And what does that parameters mean?
How safe is to add that to a laptop?

Edit> read somewhere this can be fixed by adding acpi_osi="Linux" to the grub line. anyone tried it?

---

### Post by Ripose on 2009-05-24
I'm not sure what all those parameters are for, but I will say this:  ALL my problems ended when I switched to Linux Mint and disabled COMPIZ.

---

### Post by sergiom99 on 2009-05-24
I tried adding *acpi_osi="Linux"* to the boot line in GRUB as suggested somewhere, but nothing. Upgraded to the latest BIOS version provided by HP, but nothing again.

---

### Post by sergiom99 on 2009-05-26
*bump*

---

### Post by totoxa on 2009-05-27
Sorry, i make a mistake

---

### Post by sergiom99 on 2009-05-28
Here are my dmesg and syslog when I booted on battery to see if they help someone.
Thanks!

---

### Post by sergiom99 on 2009-06-18
Today I upgraded to
```
$ uname -a
Linux kubuntu 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

But it's still not solved.

---

### Post by sergiom99 on 2009-06-25
I got it fixed by fixing my DSDT with this awesome howto [1] and thanks to 67GTA's kind help.
Take a look and help yourselves, its not difficult at all!
Good luck! 
-Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

