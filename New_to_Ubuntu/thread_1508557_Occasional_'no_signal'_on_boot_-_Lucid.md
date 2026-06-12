---
title: "Occasional 'no signal' on boot - Lucid"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Orographic on 2010-06-13
Hi all,

Still a relative beginner with Ubuntu with about eighteen months of use.

Every now and then, maybe only every thirty to fifty boots, I get a 'no signal' on my monitor with the monitor light staying orange instead of green and then I have to do a forced shutdown. Its the only problem I have with Ubuntu.

I've had the same problem with a DVI connection or D-SUB. 

My system is a Core i3 540 with on chip GPU, 4 Gig of Ram and a H55 USB3 Gigabtye motherboard with a BenQ 2200HD 21.5" monitor.  

Maybe its that the kernel doesn't fully support Core i3 yet?

Do I need to edit grub with the nomodeset command after quite splash or is there another way?

I just have to hold down the power button for about five seconds when the above problem occurs. Then it all boots fine and fsck never finds a problem. Is that okay?

---

### Post by warfacegod on 2010-06-13
> I just have to hold down the power button for about five seconds when the above problem occurs. Then it all boots fine and fsck never finds a problem. Is that okay?

Have you tried using Ctrl+Alt+Delete before you do a hard shutdown? A hard shutdown is much less likely to horribly maim and disfigure Ubuntu than, for example, Windows. XP is rather tolerant of such things. Vista? "Get my squirrel gun Ma! I gots to put this poor critter out its misery, it's a sufferin' somethin' terrible!"

By 30 - 50 boots, I assume you mean every month or so. My advice is to leave well enough alone. What we're talking about here is a monthly 5 minute inconvenience (wish my wife's monthly inconvenience was only 5 minutes). You're probably far more likely to break something if you go tinkering with it than the occasional hard shutdown.

---

### Post by Orographic on 2010-06-13
Thanks for that. Yeah and I have Clonezilla images of Lucid to restore as well, if I want to be fastidious.  Nah, can't seem to do a ctrl-alt-del for this issue.

I have never had a problem once Lucid is loaded, just very rarely during boot, yeah, about once every few weeks or so.

---

### Post by Orographic on 2010-06-15
Okay, it happened again. That is, during boot, I get a 'no signal' from the monitor and the monitor light stays orange instead of green and nothing shows up on the monitor.

There was only an interval of about ten boots this time before this problem occured again.

I tried ctrl-alt-delete with no response but then tried ctrl-alt-F1 and everything closed down fine and was good on reboot.

I thought ctrl-alt-F1 would just take me to a terminal but it seemed to shutdown my computer during this monitor no signal issue. Unless the action of doing ctrl-alt-del first then ctrl-alt-F1 was what allowed the shutdown?


System:
Core i3 540, Gigabyte H55USB3 motherboard.

---

### Post by warfacegod on 2010-06-16
Options:

Run memtest86 to check for bad RAM
Reinstall your video driver
Check the cable connection for the monitor
Video card might be going bad. Aside from switching the card, I don't know how to test this.
Monitor might be going bad. Aside from switching the monitor, I don't know how to test this either.
Check HDD:```
sudo apt-get install gsmartcontrol
```

---

### Post by robert shearer on 2010-06-16
I am getting this behavior too.

Happens on both my Lucid installs and on two different machines.
(Athlon xp2600 and Opteron 3000)

Grub comes up, I select Lucid and the screen blanks and thats it.

Ctrl Alt Backspace followed by Ctrl Alt Delete reboots and always boots second time.

No hard drive activity whilst at the blank screen so it is not a disc check.

Must have happened 3-4 times this month on each machine.

No biggie but strange all the same.

Edit: Other O/s on these machines boot fine first time = Win xp and xp pro, Mepis 8 and 8.5, Ubuntu 9.04 and 8.04.
So I doubt that it is hardware at fault.

---

### Post by warfacegod on 2010-06-16
> Edit: Other O/s on these machines boot fine first time = Win xp and xp pro, Mepis 8 and 8.5, Ubuntu 9.04 and 8.04.
So I doubt that it is hardware at fault.

Your probably right. I was just looking to cover the more simple things first and hardware is almost always more simple than software.

---

### Post by robert shearer on 2010-06-16
> **warfacegod said:**
> Your probably right. I was just looking to cover the more simple things first and hardware is almost always more simple than software.

Yes, though my experience may not be the same cause as the op so you are correct in you advice.  :) 
(both my machines have Hard Drives with little use ie newish)

I am hoping an update will fix the the hanging or that others will chime in and report similar behavior hence my adding my $0.02.

Edit:  just to add that both machines have older ati video cards no longer supported by ati and both have Pata hard drives.

@ Orographic, does this correspond with any of your hardware ?

---

### Post by Orographic on 2010-06-16
> **robert shearer said:**
> Yes, though my experience may not be the same cause as the op so you are correct in you advice.  :) 
(both my machines have Hard Drives with little use ie newish)

I am hoping an update will fix the the hanging or that others will chime in and report similar behavior hence my adding my $0.02.

Edit:  just to add that both machines have older ati video cards no longer supported by ati and both have Pata hard drives.

@ Orographic, does this correspond with any of your hardware ?


Hi guys, thanks for responding. I have three identical model hard drives (only one plugged in at a time) and only the Lucid OS is having this problem. Windows 7 and PCLOS haven't presented this problem - yet. I've even tried Lucid on one of the other drives and it has the problem there too. 

As mentioned in my first post, I don't have a video card but on chip graphics via the CPU of the Core i3. So, I wouldn't need video drivers? This cpu is a quite new one so maybe the kernel or X is having problems with it?

My system is a Core i3 540 with on chip GPU, 4 Gig of Ram and a H55 USB3 Gigabtye motherboard with a BenQ 2200HD 21.5" monitor. This hardware seems to be working perfectly with Windows 7 and PCLOS 2010.

So far, it has only happened about a dozen times in six weeks (at the most) but twice in the last week for some reason.

Ctrl-alt-F1 seems to get it to shutdown fine during this problem. I never have a crash when Lucid is running, its only occasionally on boot. No sign of kernel panic or anything.

---

### Post by robert shearer on 2010-06-16
Yeah, looks like it is something to do with Lucid and as our hardware is wildly different I can't see it being a bug specific to the kernel .

At the moment it is a minor annoyance and I am hoping an update will eventually fix it.(as to what update to what package I have no idea     -blind venison !)

If it starts to happen more often or isn't gone in a week or two then I may be concerned.

---

### Post by Orographic on 2010-06-17
Someone else on another forum in Australia is also getting this issue. They say ctrl-alt-F1 then ctrl-alt-F7 resolves for them until it gets fixed. It may take a while to fix this issue though. Bigger bugs are out there.

---

### Post by robert shearer on 2010-06-17
> Someone else on another forum in Australia is also getting this issue.

Link ? :)

---

### Post by Orographic on 2010-07-08
I had this problem again yesterday after a three week absence. The Whirlpool forums have reference to it:

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1338115&p=53](http://forums.whirlpool.net.au/forum-replies.cfm?t=1338115&p=53)

ctrl-alt-f1 shut my system down then all was well on restart.

It has only happened in Lucid Lynx on my system and not on Windows 7. As mentioned on page 1, I have three identical hard drives installed with only one plugged in at a time. They each have a different OS on them with Ludid only showing this problem.

Is it true that Ubuntu doesn't fully support core i3 with Intel HD graphics until the 10.10 kernel?

Seems so:

[http://intellinuxgraphics.org/2010Q1.html](http://intellinuxgraphics.org/2010Q1.html)

---

### Post by robert shearer on 2010-07-08
Yes, happened to me yesterday as well. A pattern emerges ?.

Possibly related to one of these packages....as they were yesterdays updates and the problem happened afterwards. 

From Synaptic history..
app-install-data-partner (12.10.04) to 12.10.04.3
libatk1.0-0 (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-data (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libpam-modules (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5
libpam-runtime (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5
libpam0g (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5

Did you update, before or after, packages the same or different ??

---

### Post by Orographic on 2010-07-09
Interesting! It was after an update actually. How do I tell what has been updated again?

Here it is from that day:

Upgraded the following packages:
app-install-data-partner (12.10.04) to 12.10.04.3
libatk1.0-0 (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-data (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libpam-modules (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5
libpam-runtime (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5
libpam0g (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5

---

### Post by Orographic on 2010-07-10
Any more feedback on this Robert or others?

---

### Post by robert shearer on 2010-07-11
> How do I tell what has been updated again?

These ...
app-install-data-partner (12.10.04) to 12.10.04.3
libatk1.0-0 (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-data (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libpam-modules (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5
libpam-runtime (1.1.1-2ubuntu2) to 1.1.1-2ubuntu5
libpam0g (1.1.1-2ubuntu2) to 1.1.1-2ubuntu

---

### Post by Orographic on 2010-07-29
Got the no signal message again after an absence for weeks, it happened after these updates:

Upgraded the following packages:
firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-branding (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-gnome-support (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
gdm (2.30.2.is.2.30.0-0ubuntu2) to 2.30.2.is.2.30.0-0ubuntu3
icedtea-6-jre-cacao (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
icedtea6-plugin (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
libdbusmenu-glib1 (0.2.9-0ubuntu3) to 0.2.9-0ubuntu3.1
libdbusmenu-gtk1 (0.2.9-0ubuntu3) to 0.2.9-0ubuntu3.1
openjdk-6-jre (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
openjdk-6-jre-headless (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
openjdk-6-jre-lib (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
software-center (2.0.5) to 2.0.7
ubuntu-system-service (0.1.20) to 0.1.20.1
xulrunner-1.9.2 (1.9.2.7+build2+nobinonly-0ubuntu0.10.04.1) to 1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1

---

### Post by Orographic on 2010-08-25
Interesting, three weeks again since the last no signal error on boot up and it happened again last night. Seems to be a three week interval, possibly, or maybe a certain number of boots.

Ctrl-alt-f1 shuts me down no probelms though then it all still re-boots fine.

I usually just re-image my Lucid install via clonezilla but this time might just leave it and see how often this error occurs. I tend to get a second no signal error  a day or two after the first one then it doesn't occur again for weeks...

---

