---
title: "Numbers just scrolling by on install?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by LordK on 2011-06-15
Computer - Compaq 2.8Mhz Half Gig ram

Ubuntu 11.4 on CD.
Successful boot from CD
Select "Install" (XP bloated beyond description nothing on here I need nor want- - so long xp)

Hit Enter

Scrolling numbers flying by at light speed! 

And it's been going on for what seems like forever.

Is this a normal install?

Do I just grab the Pop Corn & watch? -_Q  :popcorn:
Thanks in advance.

---

### Post by seawolf167 on 2011-06-15
That isn't normal - can you boot into the LiveCD successfully? i.e. when you put the disk in if you select "Try Ubuntu Without Installing" does the desktop load for you?

You should also re-download and verify that the .iso image is error-free ([how to MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")), and ensure that when you burn the cd you burn it on your slowest writing speed available. Then put it in and try again.

---

### Post by LordK on 2011-06-15
Thanks for the very quick reply.

I think I have found my mistake.

I downloaded the package on a Mac for use on a Windows machine BUT I checked the "Mac" box on download options.

Burned install to a cd & tried to install on the win machine.

I'm now d/l on the painfully slow XP box we'll see how that goes.

Think that was the problem??    -_Q

---

### Post by donkyhotay on 2011-06-15
installation process from the liveCD doesn't look "wierd" with numbers or anything. At the most just a progress bar and thats after it asks you all the setup questions first. Sounds like it may have had problems launching, as mentioned previously can you reach the desktop when you "try ubuntu without installing"?

ninja'd! glad you figured it out, you probably have the PPC version which of couse won't work at all.

---

### Post by seawolf167 on 2011-06-15
To be honest I've never seen the "Mac" checkbox - I've only ever downloaded the .iso file which would be universal across operating systems since it stands-alone (i.e. burn to cd as an iso file).

Just to be sure, do the MD5SUM check after the download to ensure that it is perfect, note that I said earlier, use your slowest write speed even if it is 2x just to ensure that there are no errors. You should be good to go after that - let us know once you boot from the new live cd.

---

### Post by Chronon on 2011-06-15
> **seawolf167 said:**
> To be honest I've never seen the "Mac" checkbox - I've only ever downloaded the .iso file which would be universal across operating systems since it stands-alone (i.e. burn to cd as an iso file).

Just to be sure, do the MD5SUM check after the download to ensure that it is perfect, note that I said earlier, use your slowest write speed even if it is 2x just to ensure that there are no errors. You should be good to go after that - let us know once you boot from the new live cd.
The .iso is aimed at a certain architecture.  The i386 ISO should run on Windows machines or recent Macs.  If you try to execute machine code on the wrong architecture expect random failure.  I don't see any downloads for PPC anymore, so maybe LordK is trying to run an AMD64 ISO on a 32-bit (only) machine.

---

### Post by seawolf167 on 2011-06-15
> **Chronon said:**
> The .iso is aimed at a certain architecture.  The i386 ISO should run on Windows machines or recent Macs.  If you try to execute machine code on the wrong architecture expect random failure.  I don't see any downloads for PPC anymore, so maybe LordK is trying to run an AMD64 ISO on a 32-bit (only) machine.

I knew that much - but why (or where) would there be a "Mac" checkbox and what would the difference be? The physical hardware would be the same (i.e. old[er] 386, 586, 686 architectures), just a different installed OS so as you said, unless the OP is attempting to run the wrong architecture on his machine, it should be fine.

---

### Post by LordK on 2011-06-15
This is frustrating.

I've managed to install 11.04 in what APPEARS to be a dual boot.
Select Ubuntu from the options.
Next screen says. Hit escape now for more options.
If you don't hit escape we're back to the light speed numbers scrolling like a good thing.

Hit escape a new menu presents these options.


[LIST]
[*]*Normal Mode*
[*]*Safe Graphics Mode*
[*]*ACPI work arounds*
[*]*Verbose Mode*
[*]*Demo mode*
[/LIST]
Pick one. Any one. Hit enter.  They're back!!  -_Q
Numbers flying by....just like in the movies. Good thing I'm easily amused.

So rather than trying to figure out exactly what's going on I'm quite prepared to pull out my old standby  "KillDisk" and start with absolutely nothing on that drive. 

Again... what do you think?

I''ve been at this for 6 plus hours now. It should not be this hard.

Thanks

---

### Post by smurphy_it on 2011-06-15
Use the ACPI work-arounds.  Your hardware might be giving you trouble.  Probably need to disable the ACPI and APM features.

This is usually done from the "command line" on boot... Haven't seen 11.04, but imagine it's pretty much the same.

usually you "edit" the boot line, and at the end append "noacpi noapm vga=791"

---

