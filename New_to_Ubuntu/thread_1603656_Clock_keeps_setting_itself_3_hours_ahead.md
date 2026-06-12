---
title: "Clock keeps setting itself 3 hours ahead"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by venom104 on 2010-10-23
Whenever I boot into ubuntu my clock changes its time to 3 hours ahead. My windows install on the same machine doesn't do this so I'm assuming nothing is wrong with the system battery. Please assist.

---

### Post by trikster_x on 2010-10-23
Click on the time/date in your panel, expand locations, click on edit and make sure it is set to somewhere in your time zone.  I have this problem whenever I install Ubuntu.  For some reason when the install is finished it sets my time zone to some random place in Europe or Asia.

---

### Post by venom104 on 2010-10-23
> **trikster_x said:**
> Click on the time/date in your panel, expand locations, click on edit and make sure it is set to somewhere in your time zone.  I have this problem whenever I install Ubuntu.  For some reason when the install is finished it sets my time zone to some random place in Europe or Asia.


I've already done that, it didn't help.

---

### Post by GabrielYYZ on 2010-10-23
system > administration > time and date and then, on the bottom, click to make changes, add a NTP server and select "keep synchronized with internet servers" 

also after you set your location, as trikster_x said, click on time settings and then click on "set system time"

---

### Post by mobilediesel on 2010-10-23
Setting the time zone is only part of it. You also have to tell it not to use universal time (UTC) because Windows can't use UTC. That setting should be in the same screen as the time zone setting.

---

### Post by gmargo on 2010-10-23
Edit the file **/etc/default/rcS**.  Look for an entry that says "UTC=yes" or "UTC=no". Toggle the yes/no value and reboot. (This specifies that your hardware clock is set to UTC or local time.)

---

### Post by KawaiDon on 2010-10-23
> **gmargo said:**
> Edit the file **/etc/default/rcS**.  Look for an entry that says "UTC=yes" or "UTC=no". Toggle the yes/no value and reboot. (This specifies that your hardware clock is set to UTC or local time.)
You know, this reply got me thinking about the Ubuntu community.  It was the correct answer, and I appreciate that.  But the way it is presented indicates the underlying reason that Ubuntu isn't used by more people!

To the average new Ubuntu user, it is not possible to simply o to this directory and edit this file.  I am a Linux dummy, so I had to dig up the command line instructions again and use terminal to do a sudo command.

Real Linux users scoff, but what users need is for these things to be put into the GUI - and as far as I can see, it isn't there.

For dual-boot computers, this really is a necessary change from what I can see,  The alternative is for the computer clock to have to be reset every time you boot to a different OS.

<sigh> I like Ubuntu a lot, but this clock issue just underscored the old problem one more time.

---

### Post by perspectoff on 2010-10-23
> **KawaiDon said:**
> You know, this reply got me thinking about the Ubuntu community.  It was the correct answer, and I appreciate that.  But the way it is presented indicates the underlying reason that Ubuntu isn't used by more people!

To the average new Ubuntu user, it is not possible to simply o to this directory and edit this file.  I am a Linux dummy, so I had to dig up the command line instructions again and use terminal to do a sudo command.

Real Linux users scoff, but what users need is for these things to be put into the GUI - and as far as I can see, it isn't there.

For dual-boot computers, this really is a necessary change from what I can see,  The alternative is for the computer clock to have to be reset every time you boot to a different OS.

<sigh> I like Ubuntu a lot, but this clock issue just underscored the old problem one more time.

Unusual solutions for unusual situations. I have never had the problem you describe and I have installed Ubuntu over 500 times. I run 6 OSs from the same computer.

Often the problem comes from a user during the initial installation.

The poor farmer blames his tools.

---

### Post by KawaiDon on 2010-10-23
> **perspectoff said:**
> 
The poor farmer blames his tools.

Yes, and that was so kind and helpful as well.  You are doing such a good job of attracting new users to Ubuntu!

I'm glad it hasn't happened to you before.  It happened on both of the computers I use with both Windows and Ubuntu.  Both were installed as default Ubuntu setups on separate internal hard drives, and both did the same thing.

So, why would all of yours be different?  Maybe because you are enough of an expert to know what to do to prevent it during install.  But another answer would be to give the users a way to change it without having to get back to the command line.

Of course, if you know where suggestions for improvements should be sent, you could also let me know and I might do that, and someone can take the suggestion and add this issue to the clock settings.

DM

---

### Post by Mark Phelps on 2010-10-24
perspectoff:  You have my sympathies ...

I've install Ubuntu and other distros quite a few times, although nowhere near 500, and on all my dual-boot setups, I encounter this very same problem.

So, (1) you're not alone, and (2) I agree that it should be incorporated into the date & time panels so it can be done by checking a box, not by having to drop into a CLI and running a command.

---

### Post by egalvan on 2010-10-24
When Hardy came out, I started installing Ubuntu as a side-line business to my main consulting line.

Over eighty dual installs on Widnows XP machines (mostly Dell, HP, a few IBM), and I NEVER had this problem.

That said, I DID have this issue with a few (four or five?) installs using 7.04 and 7.10.


(an aside.. I started coding software/hardware back in 1970, with a light-weight IBM (1130)...
 then on to VAX`s, PDP`s, Novas, Eclipses, System 360 and System 370.
 The use of UTC (aka Greenwich Mean Time) was universal on hardware...
A manufacturer could set the date/time on the assembly line to UTC,
and it would not matter what the destinaion was...
one less customization step...
software took care of the local translation.
Unix has ALWAYS used UTC on hardware. It makes synchcronizing and networking far easier.
 Again, software takes care of showing the USER the `local` time...
 although many users (especially admins/programmers) still preferd to ^see^ UTC ...)

---

