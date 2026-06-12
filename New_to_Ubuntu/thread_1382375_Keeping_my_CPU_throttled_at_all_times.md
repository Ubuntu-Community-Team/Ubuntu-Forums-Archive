---
title: "Keeping my CPU throttled at all times?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-15
You know, the options like "OnDemand", "Powersave", "Performance" on the CPU Scaling Monitor.  I want to take the lowest possible option ("800Mhz"), set it to both cores, and have it set at that from the second I turn the computer on to the second I turn it off.  It's the only way to keep this laptop from getting just a smidge to hot with Ubuntu.  I don't care if it slows down or anything, as long as it stays cooler.

Is there somewhere I can go, some file I can edit, to do this?

---

### Post by Hospadar on 2010-01-15
I'm not sure about setting the powersave options (I'm on my windows boot right now) but it might be easiest  to set this in your bios.  Many bios-es have options to over or under-clock the cpu and you may be able to pick the speed you want.

If you can do that, it'd probably be the easiest and most sure way to put a hard limit on the cpu speed that will kick in right away

---

### Post by mister_playboy on 2010-01-16
Taken from another thread:

> **slnkez said:**
> Resurrecting an old thread here, but the easiest way I found on Karmic (9.10) was to install sysfsutils (editing rc.local didn't work, and especially doesn't work when you use concurrent=shell in rc).

sudo apt-get install sysfsutils

edit /etc/sysfs.conf and add to the end:
devices/system/cpu/cpu0/cpufreq/scaling_governor = conservative

Remove /etc/init.d/ondemand so that it doesn't set the cpu frequency to ondemand after a minute or so:

sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak

It's useful to glance through the comments of /etc/sysfs.conf also.  You could do a lot of things with it without having to edit init scripts.

Assuming you have a dual core, add these lines to the end of /etc/sysfs.conf:

devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 800000000
devices/system/cpu/cpu1/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu1/cpufreq/scaling_setspeed = 800000000

---

### Post by warfacegod on 2010-01-16
> **Hospadar said:**
> I'm not sure about setting the powersave options (I'm on my windows boot right now) but it might be easiest  to set this in your bios.  Many bios-es have options to over or under-clock the cpu and you may be able to pick the speed you want.

If you can do that, it'd probably be the easiest and most sure way to put a hard limit on the cpu speed that will kick in right away

I agree with Hospadar, your first option should absolutely be the BIOS. It is the safest way to deal with hardware in the way you want. If your BIOS doesn't support CPU clocking, then modify your sysfs.conf like Mr._PB recommends.

---

### Post by Dreakon on 2010-01-16
> **mister_playboy said:**
> Taken from another thread:



Assuming you have a dual core, add these lines to the end of /etc/sysfs.conf:

devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 800000000
devices/system/cpu/cpu1/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu1/cpufreq/scaling_setspeed = 800000000
How do I edit sysfs.conf?  I don't have the best grasp on Linux commands yet.  When I did get it open with gedit, it said I didn't have permissions to save it...

And I installed that sysfsutils but I don't quite know what its for or how to use it...

---

### Post by warfacegod on 2010-01-16
Another possible solution would be to add the CPU frequency scaling applet to your panel. You will need to add one for each core of your cpu. Set one to cpu0 another to cpu1 and then use them to set the scaling at 100%. You ought to be able to remove them afterwards and have the settings stick.

---

### Post by Dreakon on 2010-01-16
> **warfacegod said:**
> Another possible solution would be to add the CPU frequency scaling applet to your panel. You will need to add one for each core of your cpu. Set one to cpu0 another to cpu1 and then use them to set the scaling at 100%. You ought to be able to remove them afterwards and have the settings stick.
You think they'll stick?  Is there any way to test it without reopening them and probably messing it up?

---

### Post by warfacegod on 2010-01-16
> **Dreakon said:**
> You think they'll stick?  Is there any way to test it without reopening them and probably messing it up?

After you take them off check start up Apps to see if there is an entry or:
Put them back on the panel and check the settings.

---

### Post by Dreakon on 2010-01-16
That's a negatory.  I switched both cores to 800 MHz and removed the applet, restarted, then added them back and they were both on Performance actually... I switched them back to 800 MHz and then they switched themselves to Ondemand, then I switched them back to 800MHz lol.  Kind of makes you want to kick something. ;)

So, whats all this sysfs.conf business?  How do I add those lines to it without permissions?  What's that sysfsutils thing I installed? :)

---

### Post by warfacegod on 2010-01-16
> **Dreakon said:**
> That's a negatory.  I switched both cores to 800 MHz and removed the applet, restarted, then added them back and they were both on Performance actually... I switched them back to 800 MHz and then they switched themselves to Ondemand, then I switched them back to 800MHz lol.  Kind of makes you want to kick something. ;)

So, whats all this sysfs.conf business?  How do I add those lines to it without permissions?  What's that sysfsutils thing I installed? :)

It's a system configuartion file. You don't, you can't change files like that without sudo which gives you temporary permission.

---

### Post by mhgsys on 2010-01-16
to get permission to save the file you're editing; open up a terminal ; 

and typ 

```

gksudo gedit /etc/sysfs.conf

```

---

### Post by Dreakon on 2010-01-16
Well, I added

```
devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 800000000
devices/system/cpu/cpu1/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu1/cpufreq/scaling_setspeed = 800000000
```

To the end of the file.  And I did the trick to keep it from going to Ondemand...

I got rid of the CPU Monitor applet and restarted my computer, but when it turned back on, I added the applet again and it seems they were set at 2.0 GHz...  It wasn't even on Performance or Ondemand... just 2.0 GHz lol.  What a silly thing to do.

:(

---

### Post by Dreakon on 2010-01-17
No ideas why that doesn't seem to be working? :(

---

### Post by gradinaruvasile on 2010-01-17
What does 

ls -al /etc/init.d/ondemand

return?

and

ls -al /etc/rc2.d/*ondemand

?

---

### Post by Dreakon on 2010-01-17
ls -al /etc/init.d/ondemand
ls: cannot access /etc/init.d/ondemand: No such file or directory

ls -al /etc/rc2.d/*ondemand
lrwxrwxrwx 1 root root 18 2010-01-15 10:32 /etc/rc2.d/S99ondemand -> ../init.d/ondemand

I believe the first one is because someone's command that I used earlier in this thread renamed it to ondemand.bak.  The problem isn't that it's turning to Ondemand, because that was solved.  The problem is that when I turn on the computer it's autosetting itself to 2.0GHz rather than 800MHz like I want it to...

---

### Post by warfacegod on 2010-01-17
> **Dreakon said:**
> ls -al /etc/init.d/ondemand
ls: cannot access /etc/init.d/ondemand: No such file or directory

ls -al /etc/rc2.d/*ondemand
lrwxrwxrwx 1 root root 18 2010-01-15 10:32 /etc/rc2.d/S99ondemand -> ../init.d/ondemand

I believe the first one is because someone's command that I used earlier in this thread renamed it to ondemand.bak.  The problem isn't that it's turning to Ondemand, because that was solved.  The problem is that when I turn on the computer it's autosetting itself to 2.0GHz rather than 800MHz like I want it to...

So change the name to just ondemand, .bak is a backup file.

---

### Post by gradinaruvasile on 2010-01-17
> **Dreakon said:**
> ls -al /etc/init.d/ondemand
ls: cannot access /etc/init.d/ondemand: No such file or directory

ls -al /etc/rc2.d/*ondemand
lrwxrwxrwx 1 root root 18 2010-01-15 10:32 /etc/rc2.d/S99ondemand -> ../init.d/ondemand

I believe the first one is because someone's command that I used earlier in this thread renamed it to ondemand.bak.  The problem isn't that it's turning to Ondemand, because that was solved.  The problem is that when I turn on the computer it's autosetting itself to 2.0GHz rather than 800MHz like I want it to...

800 MHz = ondemand. Or it should if you have that stepping...

---

### Post by Dreakon on 2010-01-17
I would like it at 800 MHz at all times, not just when my laptop is under no load... so renaming Ondemand.bak back to Ondemand would not help with that whatsoever.  At least as far as I know, since to my knowledge that makes it so it'll automatically turn into Ondemand a few seconds after reaching the desktop.

**The Goal**
Have both cores of my laptop at 800 MHz from the second I turn the computer on to the second I shut it down at night, and have it stay at 800 MHz no matter what.

The Ondemand setting does not do this as it fluctuates based on how much load the laptop is under.  I want to avoid this setting since extended periods of video watching, gaming or even surfing the web gets the laptop into an uncomfortable temperature.

Thanks for the time and effort spent helping me so far though! :)

---

### Post by happyhamster on 2010-01-17
> devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 800000000
Values should be in kHz. For example, if I run:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

on my system, the output is: 3000000 2000000 (for 3gHz and 2gHz respectively).

---

### Post by mister_playboy on 2010-01-19
> **happyhamster said:**
> Values should be in kHz. For example, if I run:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

on my system, the output is: 3000000 2000000 (for 3gHz and 2gHz respectively).

The examples in the file didn't specific what the units were, and 1870000000 put me at 1.87GHz like I wanted, so I was none the wiser.  ;)

Thanks for the correction.

---

