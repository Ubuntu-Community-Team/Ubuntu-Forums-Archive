---
title: "Is there something wrong with boot in Lucid?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by jackdale on 2010-05-04
I have 10.04 on a 64bit on a Pentium Dual-Core CPUs (2 x 2.6GHz) with 4GB RAM and a 1GB nVIDIA GPU.  My "problem" may not be a problem, so I thought I'd check:

I upgraded from Karmic with only minor problems, easily fixed.  It all runs well and I have got the plymouth to work with the proprietary drivers.  However, the boot time is about 25seconds (from grub to log-in screen).  

When I was testing the beta release, I used Virtual Box on the same machine and gave it one processor with about 1GB RAM.  The boot time on Beta 1 was about 17 seconds (ie which included "power-on" then grub then log-in screen).

25 seconds is still better than Karmic, but I thought it would be faster than the Virtual Box version...  However, from power on to log-in screen is currently 47 seconds (which is only slightly better than the 51 seconds with karmic).

There is one thing that I can think could be causing a delay.  At the end of the plymouth video, right before the log-in screen I get a message about a failure of a "noise floor calibration".

Could this be slowing down the boot time?

---

### Post by cariboo on 2010-05-04
How many times have you rebooted since installing, and how are you timing boot? I've always found os's in vbox, boot faster than from the hard drive, especially Windows. :)

---

### Post by jackdale on 2010-05-05
> **cariboo907 said:**
> How many times have you rebooted since installing, and how are you timing boot? I've always found os's in vbox, boot faster than from the hard drive, especially Windows. :)

Thanks for your reply.
I always shut down the computer after use, so at least once a day.  I upgraded to 10.04 on 1/5/10 and it is now 5/5/10 (in Australia).  On 1/5/10, I shut down and restarted a few times to test the changes to the nVIDIA drivers that let them play the plymouth.

How I measure the boot times (may not be the norm!) with a stop-watch:
1st Measurement: From on-button-press to grub menu (mostly motherboard)
2nd Measurement: From enter @ grub to log-in screen (Mostly Ubuntu)

On 10.04, I get 22sec for the 1st measurement and 25sec for the 2nd.
On VBox, it took only 17 seconds for both (10.04 beta1).

Whilst my machine is by no means a top of the range computer, I would have thought that it would at least be closer to 10second boot than 30seconds (on 2nd measurement).

I noticed that the plymouth video plays for most of the time.  I wondered if the noise floor calibration error perhaps means that the system is waiting until this "calibration" takes place before going to log-in screen and only goes to the log-in screen once the calibration times out.

---

### Post by Kakers on 2010-05-05
> **cariboo907 said:**
> I've always found os's in vbox, boot faster than from the hard drive, especially Windows. :)

Same I've also noticed that virtual boxes seem to boot up much faster.

From experience in the past I've learned it is always best to do a fresh clean install rather than upgrade as sometimes you do get problems, sometimes even underlining ones you can't see. You could try reinstalling the OS and see if that makes a difference but there is no garentee that it will. :(

---

### Post by warfacegod on 2010-05-05
I have a Toshiba Satellite P25-s607 with a P4 2.8 Ghz Hyper Thread CPU, 2 GB RAM (Crucial), and a 7200 RPM WD 250 GB HDD. I've done both upgrade and fresh installs on it and a fresh install generally boots about twice as fast as its equivalent upgrade OS.

At the moment I'm running 9.10 as my main OS and from power on to completely up and running (with login) is about 30 seconds. I could cut that by another 5 seconds if I booted up without Compiz starting. My experiment OS is 10.04 UNE and it boots at around 20 seconds. Neither install is an upgrade.

You might look in Startup Applications to see if anything can be turned off. That's bound to speed up your boot time.

---

### Post by jackdale on 2010-05-05
> **warfacegod said:**
> I have a Toshiba Satellite P25-s607 with a P4 2.8 Ghz Hyper Thread CPU, 2 GB RAM (Crucial), and a 7200 RPM WD 250 GB HDD. I've done both upgrade and fresh installs on it and a fresh install generally boots about twice as fast as its equivalent upgrade OS.

At the moment I'm running 9.10 as my main OS and from power on to completely up and running (with login) is about 30 seconds. I could cut that by another 5 seconds if I booted up without Compiz starting. My experiment OS is 10.04 UNE and it boots at around 20 seconds. Neither install is an upgrade.

You might look in Startup Applications to see if anything can be turned off. That's bound to speed up your boot time.


Thanks for the reply.  Interesting.  I thought that Startup Applications only did its thing after log-in.
I hadn't thought about doing a fresh install...I guess I would have to put my /home folder in a separate partition...but what about installed programs?  They would have to be re-installed wouldn't they?

Thanks again for the reply

---

### Post by warfacegod on 2010-05-05
Yes, installed programs would have to be reinstalled. Make a list, the install process shouldn't take too long. If you have customized settings for your programs and/or desktop (themes and what have you) they are hidden in your /home folder. So make a backup of that and if you do a fresh install put the backup ...well back and your new OS should behave and look like it did in your old one.

I always recommend having a separate /home partition and a small (say 10 - 15 GB) OS partition. That way if anything goes horrifically wrong with the OS, your data and settings are safe. Let me know if you want more advice on how to do this.

---

### Post by oldfred on 2010-05-05
You can with just a couple of commands move reinstall all your programs from one install to another, although I found when going from a very old install I did reinstall some old stuff that I had never removed.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

I installed karmic twice once on my desktop and once on my laptop, so I copied history to a file and converted it to a bash script, I am now updating it in my Lucid "beta" partition for a new install in another partition. I intentionly tried to do as much as possible from command line so I would have it in history.

List history:
history

---

### Post by jackdale on 2010-05-06
Thank you all for your replies.  I just installed the new kernel image, which promptly killed my modifications that let me view the plymouth with the proprietary drivers! :lolflag:

So I'll go and fiddle with that first before partitioning the /home directory.  I'll mark the thread as solved as I think I have enough to go on from here.

Thank you all again for the fantastic support.

:guitar:

---

