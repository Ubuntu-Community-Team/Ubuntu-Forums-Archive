---
title: "Sometimes Nothing Happens When I Turn On My Computer"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by mulluysavage on 2010-04-23
This started happening a few weeks ago - the machine would make it through various stages in the startup:

Sometimes, it would freeze on the GRUB screen.

Sometimes, it would make it through the BIOS splash screen  but not to the GRUB screen.

Sometimes, there would just be a blank screen, no blinking cursor, no nothing. I could tell that a signal was coming from my video card from the indicator on my monitor.

Then for a week or so it was totally fine and went back to booting 9.04 flawlwessly. But tonight, it just did the blank screen persistently.

After powering down the power supply and back up again, it went through the BIOS but then hit a black screen.

Then I tried to boot from a Live CD - but it said 'system disk error -enter a system disk and hit enter.'

When I was about to give up, I tried powering down the power supply again and booting from CD - and voila - here I am, running 9.04 on Live CD, afraid to shut it off :)

My Guesses:

Something intermittently wrong with the BIOS

Something intermittently wrong with GRUB

Something intermittently wrong with my CD ROM

Something wrong with the processor itself (I took the heatsink off at one point and then put it back on without heat conducting paste - how bad is that?)

Any ideas?

---

### Post by nhasian on 2010-04-23
it is possible that you are describing a problem caused my overheating.  When you enter your bios does it show you fan speeds or cpu temperatures?  thermal paste does help heat transfer to the heat sink.  if/when you can get ubuntu running again, check the temperatures for the video cards, hard disk, cpu, etc.  you can get info on your hard disk by going to system-> administration-> Disk utility

also from a terminal you can get cpu temperature info with the command:

```
sensors
```

if you have a desktop open up the side panel and use a can of air to blow out the dust from inside the case, power supply, fans, etc.

---

### Post by mulluysavage on 2010-04-23
The one thing that makes me think it's not overheating is I tried turning my computer off for 30 minutes and still had the same problems, and I'm running it now for the last hour on the live cd.

---

### Post by mulluysavage on 2010-04-23
Could it be a weak CMOS battery? Is that the same as the clock battery?

---

### Post by nhasian on 2010-04-23
can you give us your temperatures then?  for comparisons my laptop has an intel dual core 2.4Ghz CPUs and i never turn my laptop off.  right now my CPUs are at 48C and 54C.  my nvidia GPU is at 65C (yeah i know it runs a little on the warm side, known problem with the 8x00 GPUs) and my hard disks are 39C and 56C.

---

### Post by nhasian on 2010-04-23
> **mulluysavage said:**
> Could it be a weak CMOS battery? Is that the same as the clock battery?

you could take your cmos battery out and your computer would still boot provided it auto-detects the hard disks.  all the cmos battery does is save your bios settings and date/time.

---

### Post by mulluysavage on 2010-04-23
> **nhasian said:**
> can you give us your temperatures then?  for comparisons my laptop has an intel dual core 2.4Ghz CPUs and i never turn my laptop off.  right now my CPUs are at 48C and 54C.  my nvidia GPU is at 65C (yeah i know it runs a little on the warm side, known problem with the 8x00 GPUs) and my hard disks are 39C and 56C.

I can't seem to install sensors (because I'm on livecd?) is there another way to get at it?

---

### Post by mkvnmtr on 2010-04-23
I was having problems with freezing and of course blamed Ubuntu. There was no overheating. One day last week it finally got to where it would not start. I replaced the power supply I think you call it in English. And it works fine. I decided to reinstall and it works even better. 
Looks like you have some hardware problems. You might start with cleaning the dust out of the machine. I think that was the problem with my power supply.

---

### Post by mmalone21 on 2010-04-23
Yes, it could be a weak CMOS battery. Yes, CMOS battery runs the system clock.

---

### Post by mulluysavage on 2010-04-28
New DVD RW drive.

New CMOS battery.

Re-loaded GRUB 

***

On attempt to boot from HD: "NON-SYSTEM DISK ERROR. INSERT SYSTEM DISK AND PRESS ENTER" (not verbatim)

Will not boot Ubuntu 9.10 Live CD

Will boot Parted Magic

Will boot Xubuntu 8.04 LTS


I'm thinking something is up with my boot sector - like, it's physically messed up. I'm thinking about cloning my OS partition to a new HD and installing GRUB there and trying that. 

Totally puzzled by the fact that it won't boot the 9.10 live cd, which it did before, and I installed from. I don't know, maybe it's scratched.

---

### Post by nhasian on 2010-05-01
> **mulluysavage said:**
> 
Will not boot Ubuntu 9.10 Live CD

Will boot Parted Magic

Will boot Xubuntu 8.04 LTS

i can suggest three things to try:

1) on another computer boot from the new Ubuntu 10.04 LiveCD and create a bootable usb-thumbdrive from system-> administration-> Startup Disc Creator.

2) if you are unable to install the Ubuntu 10.04 LiveCD (either via optical or usb) then use the Alternate cd instead:

[32bit alternate CD]("http://releases.ubuntu.com/lucid/ubuntu-10.04-alternate-i386.iso") 
[URL="http://releases.ubuntu.com/lucid/ubuntu-10.04-alternate-amd64.iso"]
64bit alternate CD[/URL]

3) run the memory test from the livecd on your computer overnight and see if it hangs.

---

### Post by quadproc on 2010-05-01
> **mulluysavage said:**
> This started happening a few weeks ago - the machine would make it through various stages in the startup:
(problem summary elided)
Something wrong with the processor itself (I took the heatsink off at one point and then put it back on without heat conducting paste - how bad is that?)

Any ideas?
The thermal compound might be an issue but it's really not possible to say without doing some measurements on the hardware.  Overheating a processor could cause permanent damage but I think that the damage would not heal itself, as seems to be your case.

The problem really sounds like a bad connection.  It could be in a connector, in a circuit board, in a soldered joint, etc.  Often mechanical connection problems can be affected by temperature, shock, vibration, and so forth.  I don't know if this is practical for your circumstances but you might use something insulated such as a plastic knife to gently push on parts of the system while it is running.  If you can find a sensitive spot then close physical inspection may reveal a problem.

Good luck!

quadproc

---

### Post by nhasian on 2010-05-01
that doesn't sound like a good idea [-X

> **quadproc said:**
> use something insulated such as a plastic knife to gently push on parts of the system while it is running.  If you can find a sensitive spot then close physical inspection may reveal a problem.

---

### Post by lkraemer on 2010-05-01
Here is what I would suggest!
Is the Drive IDE, and is WIN installed?

Listen for the startup beeps, and make sure you are still getting the
normal number of beeps.

First thing I'd do if it were mine is to blow the dirt out of the case
and power supply to clean it up a bit.  Just don't blow high pressure air
on your fans so they turn at warp one!  Then I'd carefully remove and
reseat the Memory, Video Card, and other Cards that are installed while
you are properly grounded to the case.  At this point I'd power up again
and see what happens.  Keep the case open to allow you to verify that all
fans are turning up to speed.  If any have been making a squeal or slowing
down sound, I'd replace them.  Check your CPU Fan too.  And, don't forget
the fan located inside your power supply.

You could have a Power Supply that is about to give out, or it could be 
producing low/high voltage.  Have you noticed any other symptoms?  You
can check the voltages with a meter when the problem happens.

It could be a card that is going bad, memory, or the hard drive, so I'd
get it to boot a Linux LiveCD and run a Memory test for at least 24 hours.
You can turn the monitor off and turn it back on at intervals to see how
the test is progressing.  From there you can run the Hard Drive
Diagnostics from the Manufacture to see what those Diagnostics tell you.
Just don't run any of the Diagnostics that WRITE to the Drive, because that
will destroy your data.  You might also want to carefully unplug the data cable
from the Motherboard to the Hard drive, ONE END AT A TIME, and replug them in.
I've seen one cable that caused me lots of problems with a Grub 18 Error.
If you can locate Spinrite by Gibson Research you can also run a test on
your drive with that software.  But, it will cost more than a replacement drive.

By now you should have located what is causing the problem, or at least 
narrowed it down to a suspect part.

lk

---

### Post by chappajar on 2010-05-01
> **mulluysavage said:**
> I can't seem to install sensors (because **I'm on livecd?**) is there another way to get at it?

> **mulluysavage said:**
> New DVD RW drive.

New CMOS battery.

Re-loaded GRUB 

***

On attempt to boot from HD: &quot;NON-SYSTEM DISK ERROR. INSERT SYSTEM DISK AND PRESS ENTER&quot; (not verbatim)

Will not boot Ubuntu 9.10 Live CD

Will boot Parted Magic

Will boot Xubuntu 8.04 LTS


I'm thinking something is up with my boot sector - like, it's physically messed up. I'm thinking about cloning my OS partition to a new HD and installing GRUB there and trying that. 

Totally puzzled by the fact that it won't boot the 9.10 live cd, which it did before, and I installed from. I don't know, maybe it's scratched.

I recently had what I think is a similar problem. 

 Was installing Ubuntu onto a relative's laptop, but the following CDs refused to boot:
- 10+ copies of the 9.10 LiveCD(a variety of CD brands, burnt from several different computers, some DVD disks, most burnt at slowest possible speed)
- several Win XP install disks (despite having successfully used the same disks on the same laptop in the past)
- a 9.04 LiveCD
- an 8.10 LiveCD

Note that all these disks boot just fine on other computers 

The following disks **would** boot: 
- a DSL LiveCD 
- a GParted LiveCD 
- one lone copy of 9.10, but during install would crash with disk(CD) read errors. 

Based on this I had to conclude my problem was the optical drive; there really was no other logical explanation.  My solution was to download and burn an [Ubuntu Minimal Install CD]("https://help.ubuntu.com/community/Installation/MinimalCD") that is only about 20 MB and downloads the rest of the install data from the net as it installs.

The small size of the image decreases your chances of burning something that your optical drive doesn't like.  I used the Minimal CD to install Ubuntu without any extra packages at all (because it crashed when I tried to add any extras above a bare-bones install) and successfully installed Ubuntu that booted into a shell command line when I turned the computer on.
I then ran $ **sudo apt-get install ubuntu-desktop** from the shell, to install everything you usually get from the install process.  The result is an Ubuntu install identical to a ''standard'' install from a LiveCD.

Sorry, may have wandered off topic slightly there, but my point is (at least part of your problem) it's your optical drive not liking your disks (you're running Ubuntu from a LiveCD, not from an install on your hard disk, if I read your quote above correctly) (I notice that you got a new drive - was that before or after the problems started?)

---

