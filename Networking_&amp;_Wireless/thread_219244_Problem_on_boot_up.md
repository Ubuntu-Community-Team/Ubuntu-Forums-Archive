---
title: "Problem on boot up"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by mouldy on 2006-07-19
On a fresh installation of Ubuntu Dapper everytime it boots up into gnome, the network doesn't work. So I run the Networking tool in System > Administration, click on my ethernet device, click deactivate. Then click it again, click activate and OK the window and voila, the network works again.


Any reason behind this? Is there a way to fix it?


Before I've deactivated/reactivated it, there is nothing in the "Default gateway device" dropdown box, and if I select my device (eth0) and click OK, it just ignores what I did, the network won't work and next time I run that network tool, the box will be empty again. When I do reactivate it though, eth0 is put in the drop down box and it stays there.

Any help is much appriciated.

---

### Post by John.Michael.Kane on 2006-07-19
mouldy not enough system info given. are you behind a router? if you are have tried installing ubuntu without the machine connected to the router?

---

### Post by mouldy on 2006-07-20
Sorry, yes I am behind a router, the network is configured with DHCP from the router and unfortunately I don't have enough wire to connect the computer directly to the cable modem and see if that works.



The problem only happened when Dapper went final. I used Dapper 6.04 for a while and it was fine, the minute I upgraded to 6.06 it went how it is now, then I did a reformat recently and went straight to 6.06 and the same thing happens.

Edit:

It would seem a LOT of people are having the same problem;
[Click](http://www.ubuntuforums.org/showthread.php?t=205914&page=2&highlight=boot+network+activate)
[Click](http://www.ubuntuforums.org/showthread.php?t=190129&highlight=boot+network+activate)

But there is no fix? Do any of the devs know about it/working on a fix?


I have a *feeling* it has something to do with the nForce4 chipset, simply because "Chill" (first link) mentioned he/she has the nForce4 Ultra chipset, and I too have the nForce 4 ( I believe ultra) chipset.

---

### Post by John.Michael.Kane on 2006-07-20
I have an nforce 4 based board and router,however.at this time i can't check this problem.

---

### Post by mouldy on 2006-07-21
*Le bump*

Does anyone atleast know of a script I could download/make that'll just disable then renable eth0 everytime it boots?

---

### Post by Haiyadragon on 2006-07-21
Same problem here. It has nothing to do with my routers. It's something with Ubuntu. I know this because it can dhcp just fine at all times. It just refuses on boot.

It works fine with plain dhcp no additional settings on Arch Linux (every other boot :p, guess networking it's pretty hard still), Win2k, WinXP. It worked during Ubuntu install. All the settings are correct. I just have to deactive en activate again every boot.

Annoying bug.

---

### Post by mouldy on 2006-07-24
Well as there seems to be no official word on this, whether or not it's being looked into, does anyone know of a shell command that'll disable then renable the network device so I can make a script to do it automatically?

---

### Post by IcyEars on 2006-07-24
I've got exactly the same thing.  Some more info to add though.

I've got an Athlon 64 and I couldn't decide whether I wanted to x64 or 386 version of Ubuntu when I rebuilt my machine last week.

I started off by installing the x64 build from the Dapper 6.06 LTS Live CD (Fresh download done last Sunday).  Once installation was complete, rebooted and did the updates. This problem did not occur.

I changed my mind last Tuesday and wiped everything and re-installed Ubuntu from the 386 disc (downloaded at the same time).  Fine, everything installed great.  Again, rebooted but no network connection.  I had the same problem on one of the pre-release versions I was playing with a couple of months agao, so went to networking, deactivated my eth0, reactivated it and it connected.  I then did all the upgrades and everything worked great (i.e. had a connection every time I booted.)

Changed my mind yet again (I know, I'm fickle), wiped everything (as in reformat all my partitions), re-installed x64, rebooted, everything fine.

Yesterday, decided that I would settle on the 386 version until I'm more familiar with Ubuntu and then I might switch to x64.  Reformatted, installed from the same 386 disc as before.

Near the end of the install, I got an error message about not being able to connect to something.  Didn't pay any attention to it, clicked OK, it went away, 5 minutes later, the install finished and said I needed to re-boot.

Dutifully did this and did not get asked to do any updates.  Thought this was a bit odd so I tried to manually run Update Manager.  Clicked on the check button, the box saying downloading files came up, stayed for about 10 seconds and went again.

So again, deactovated and re-activated eth0. Then ran an update and got something like 146 updates.  All these installed correctly so I thought this would have fixed the problem.  It didn't.  I now have to manually restart my eth0 connection everytime I boot.

The only difference on this install is that I had that error message when installing.  Nothing else, either hardware or in terms of the disc I am installing from has changed.  Does anyone know if there is a log anywhere that would tell me what the error was?  Hopefully this might shed more light on things.

*[edit: just remembered, when it booted after the install, none of my sources were enabled.  I manually uncommented them out and things seemed to work OK, maybe things didn't work as well as I thought.  Anyone know how to revert to your original sources list?]*

I'm pretty certain that if I re-installed, there is a good chance that this problem might go away but since quite a few other are having the same problem, I thought I might be able to help.

Like I said, I'm very new to Ubuntu so if someone can let me know where to look, I'll see what I can find out.

---

### Post by tigerteeth on 2006-07-24
I have a bit more on this problem. I installed Dapper Drake on an old eMachines Intel Celeron 366 MHz computer and then plugged in a Hawking 80211g PCI Network card (HWPG1).

If I run Ubuntu from the install disk, everything works fine but slow. But then I installed Dapper to the hard drive, went to the Networking option and adjusted the settings. It worked. I rebooted and it worked briefly, then failed. The browser simply said "Looking for www.google.com" until it timed out.

I tried rebooting several times and each time the system hangs during startup on "Configuring Network interfaces..." It freezes for several minutes, then switches from the Ubuntu interface to a blank black screen with white text, but saying the same thing.

I've tried reinstalling. Problem remains. Hope that helps.

---

### Post by Trizik on 2006-07-25
> **tigerteeth said:**
> I tried rebooting several times and each time the system hangs during startup on "Configuring Network interfaces..." It freezes for several minutes, then switches from the Ubuntu interface to a blank black screen with white text, but saying the same thing.

I've tried reinstalling. Problem remains. Hope that helps.

Same problem here. Ubuntu booted fine before I activated my Linksys wireless adapter (WMP45GR). Now it hangs at "Configuring Network Interfaces..." and if I skip it with Ctrl+C, a dark orange/red background appears along with a mouse cursor as if the desktop is loading but that's as far as it gets. Any ideas?

---

### Post by mouldy on 2006-07-25
> **IcyEars said:**
> I've got exactly the same thing.  Some more info to add though.

I've got an Athlon 64 and I couldn't decide whether I wanted to x64 or 386 version of Ubuntu when I rebuilt my machine last week.

I started off by installing the x64 build from the Dapper 6.06 LTS Live CD (Fresh download done last Sunday).  Once installation was complete, rebooted and did the updates. This problem did not occur.

I changed my mind last Tuesday and wiped everything and re-installed Ubuntu from the 386 disc (downloaded at the same time).  Fine, everything installed great.  Again, rebooted but no network connection.  I had the same problem on one of the pre-release versions I was playing with a couple of months agao, so went to networking, deactivated my eth0, reactivated it and it connected.  I then did all the upgrades and everything worked great (i.e. had a connection every time I booted.)

Changed my mind yet again (I know, I'm fickle), wiped everything (as in reformat all my partitions), re-installed x64, rebooted, everything fine.

Yesterday, decided that I would settle on the 386 version until I'm more familiar with Ubuntu and then I might switch to x64.  Reformatted, installed from the same 386 disc as before.

Near the end of the install, I got an error message about not being able to connect to something.  Didn't pay any attention to it, clicked OK, it went away, 5 minutes later, the install finished and said I needed to re-boot.

Dutifully did this and did not get asked to do any updates.  Thought this was a bit odd so I tried to manually run Update Manager.  Clicked on the check button, the box saying downloading files came up, stayed for about 10 seconds and went again.

So again, deactovated and re-activated eth0. Then ran an update and got something like 146 updates.  All these installed correctly so I thought this would have fixed the problem.  It didn't.  I now have to manually restart my eth0 connection everytime I boot.

The only difference on this install is that I had that error message when installing.  Nothing else, either hardware or in terms of the disc I am installing from has changed.  Does anyone know if there is a log anywhere that would tell me what the error was?  Hopefully this might shed more light on things.

*[edit: just remembered, when it booted after the install, none of my sources were enabled.  I manually uncommented them out and things seemed to work OK, maybe things didn't work as well as I thought.  Anyone know how to revert to your original sources list?]*

I'm pretty certain that if I re-installed, there is a good chance that this problem might go away but since quite a few other are having the same problem, I thought I might be able to help.

Like I said, I'm very new to Ubuntu so if someone can let me know where to look, I'll see what I can find out.

I too have an AMD 64 with the 386 version of dapper installed, maybe that's the problem.


I'll see if I can work on a script or something that'll fix it.

---

### Post by mouldy on 2006-07-25
Fixed it:

Add the following two lines to your /etc/rc.local file, you'll need to sudo it;

```
ifdown eth0
ifup eth0
```

I *think* you have to do it before the exit 0, I did and it works, didn't try it any other way.

Here's what my file looks like;
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ifdown eth0
ifup eth0
exit 0

```

---

### Post by Trizik on 2006-07-25
where/how do you sudo it? i can't even get to the command prompt if i boot normally. if i boot into safe mode, i still have to Ctrl+C to bypass "Configuring Network Interfaces..." and once at the command prompt, commands do nothing.

---

### Post by IcyEars on 2006-07-25
That worked for me too.

Nice one!

---

### Post by Trizik on 2006-07-26
I think my problem is a tad different. I made a new thread to focus on my exact problem @ [http://www.ubuntuforums.org/showthread.php?p=1301594](http://www.ubuntuforums.org/showthread.php?p=1301594)

Any help would be greatly appreciated!

---

### Post by mouldy on 2006-07-26
No prob IcyEars

Trizik, Yeah, you have a different problem, sorry though, can't help you.

---

