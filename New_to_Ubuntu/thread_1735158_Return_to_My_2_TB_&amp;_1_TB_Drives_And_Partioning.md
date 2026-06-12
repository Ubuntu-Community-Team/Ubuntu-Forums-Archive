---
title: "Return to My 2 TB &amp; 1 TB Drives And Partioning For Backing Up"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Glkanter on 2011-04-21
[SIZE=2]Nothing has been done to either of my Ubuntu 10.10 'system' drives since we all last spoke, here:
[/SIZE][INDENT][SIZE=2]http://ubuntuforums.org/showthread.php?t=1731172&page=1[/SIZE]
[/INDENT][SIZE=2] The 1 TB boots and performs fine, the 2 TB does not boot, but all the data is readable.

I have 8 GB of memory. I figure to expand that to the MB's maximum of 16 GB in a year or so, when prices come down. The resources monitor never varies from about '10% in use by programs, 10% in use by cache'. I have never seen the swap memory used.

I have no plans of loading Windows.

I have no plans of loading various flavors of Linux.

I don't know exactly what form of BIOS I have, but this is my motherboard:
[/SIZE][INDENT][FONT=Verdana, Helvetica, sans-serif][SIZE=2]ASUS M4A88TD-V EVO/U Socket AM3 880G ATX AMD
[/SIZE][/FONT][/INDENT][FONT=Verdana, Helvetica, sans-serif][SIZE=2]Here's a link:
[/SIZE][/FONT][INDENT][FONT=Verdana, Helvetica, sans-serif][SIZE=2]http://www.asus.com/Motherboards/AMD_AM3/M4A88TDV_EVOUSB3/[/SIZE][/FONT]
[/INDENT][FONT=Verdana, Helvetica, sans-serif][SIZE=2]
I am, again, requesting guidance on how to use my 1 TB drive as a 'plug and play' backup for the 2 TB drive. As the 2 TB drive is SATA 3.0, which is supported by my MB, my only 'requirement' is that the 2 TB drive is the system drive. It can be the only internal drive, if that is part of the solution.

So, I'm looking for guidance in the form of:
[/SIZE][/FONT][INDENT][FONT=Verdana, Helvetica, sans-serif][SIZE=2]1. What actions to take, and 
2. What tools to use. Please keep in mind that I'm very inexperienced with the command line.[/SIZE][/FONT]
[/INDENT][FONT=Verdana, Helvetica, sans-serif][SIZE=2]
1. My goal is to make a periodic (weekly?) 'identical' backup of the Linux part of the 2 TB drive. That would be 'everything possible', including data. Based on some previous attempts, I think this backup will take a little over an hour.

2. I will copy the data files to my 250 GM drive on a daily basis. I have, let's say, about 175 GB of legacy data files. Probably 75% of that is MP3s.

3. If appropriate, I will copy any changes to the system to the 250 BG drive on a daily basis.

4. In the event of a failure of the 2 TB hard drive, I would remove it, and install the 1 TB drive as the primary drive. I do not need the 1 TB drive in the PC unless it is running the system temporarily.

5. If possible, I would like to continue to use the Linux settings, downloads and preferences I have done the last couple of weeks. On the other hand, if things are just much more straight forward with a completely fresh install, that's fine, too.

I look forward to your solutions, thanks in advance.

Garry
[/SIZE][/FONT]

---

### Post by LowSky on 2011-04-23
1. please use url tags for websites. I and others  hate copy and pasting.
2. What do you mean the 2TB drive doesn't boot? If you set it as the primary drive and it in the first sata port grub will install to it to boot the drive.
3. Ubuntu runs perfectly fine on 2GB of RAM. 4 is superb, 8 is more than you need for most things, and above that is overkill.This is coming from someone with 12GB of RAM.
4. BIOS doesnt matter, just use it to change boot order if you must.
5. I would suggest backup of only the /home folder.  a system install takes less than 30 minutes and most applications can be reinstalled in seconds.
6. what solutions from us are you looking for? you seem to already have tried the software out. all you need to do is implement a plan.

---

### Post by Glkanter on 2011-04-23
Hi, thanks for asking, and thanks for the suggestion.

These links were my previous questions on this forum... Without intending to, I made my 2 TB drive unbootable. It's not the end of the world, as it was a very new install.

But my real goal is to have my 1 TB be a plug & play backup in case the 2 TB fails...

[http://ubuntuforums.org/showthread.php?t=1730367]("http://http://ubuntuforums.org/showthread.php?t=1730367")

[http://http://ubuntuforums.org/showthread.php?t=1731172]("http://http//ubuntuforums.org/showthread.php?t=1731172")

Thanks!

---

