---
title: "Overheat (Ubuntu 10.04)"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Mekc on 2010-07-06
Hello. Before posting, I looked through the forum trying to find the solution, but only found similar problems some people are experiencing.

When I run Ubuntu from a CD, I see a huge boost in videocard temperature. First I thought that could be because it wasn't installed, so tried installing it. After some of the steps in the installation procedure, the notebook started making a lot of noise (coolers) and the temperature of my videocard went up to 95(!!!!) celsium. So I just switched off the installation.

I have a notebook - ASUS G73J, with ATI HD5870 1GB videocard, I7-720M processor, 8GB of DDR3 memory. The videocard is at maximum of 75-77 celsium in Windows 7 playing e.g. WoW in HD and all maxed video. Usually - in windows - in MS office, browsing and so on, the temperature is just 50-60.

The notebook is brand new, there's no dust in the coolers.

Question: how to get Ubuntu running/installed without danger of breakage due to overheat? (please don't say 95 degrees is okay) And what's the reason of such overheat?

---

### Post by Mekc on 2010-07-06
Up.

---

### Post by AAccount on 2010-07-06
Do you have compiz and desktop-effects turned on to the max? Sometimes it may just be the linux distribution. When I ran Fedora on my laptop the temperatures were generally 5 degrees celsius warmer than running ubuntu. Try making a live USB and installing the temperature monitoring tools to see if that helps. Also, try installing the ATI drivers from their website, NOT from the ubuntu repository.

---

### Post by MooPi on 2010-07-06
If you'd like to install Ubuntu without the live CD, give the alternate install CD a go. Because it uses significantly less resources it may not tax the video card at all during the install. No worries of destroying the laptop before you get Ubuntu loaded :-) . After you've got Ubuntu installed you'll be able to configure a video driver that best suites the thermal demands of the card. I'd suggest doing research on the best alternatives. Supposedly ATI /AMD drivers have advanced recently and could offer a good solution. I'm an Nvidia  user due to past results with ATI but ATI is taking great effort to improve their opensource  drivers.

---

### Post by alphacrucis2 on 2010-07-06
> **Mekc said:**
> Hello. Before posting, I looked through the forum trying to find the solution, but only found similar problems some people are experiencing.

When I run Ubuntu from a CD, I see a huge boost in videocard temperature. First I thought that could be because it wasn't installed, so tried installing it. After some of the steps in the installation procedure, the notebook started making a lot of noise (coolers) and the temperature of my videocard went up to 95(!!!!) celsium. So I just switched off the installation.

I have a notebook - ASUS G73J, with ATI HD5870 1GB videocard, I7-720M processor, 8GB of DDR3 memory. The videocard is at maximum of 75-77 celsium in Windows 7 playing e.g. WoW in HD and all maxed video. Usually - in windows - in MS office, browsing and so on, the temperature is just 50-60.

The notebook is brand new, there's no dust in the coolers.

Question: how to get Ubuntu running/installed without danger of breakage due to overheat? (please don't say 95 degrees is okay) And what's the reason of such overheat?

Probably because the open source drivers don't have proper thermal control for that model of card yet. What you would need to do is install the proprietary ATI driver via "Adminstration - Hardware Drivers". You may not be able to do that from the live CD - it probably would require a real install first.

---

### Post by Mark Phelps on 2010-07-07
While it's possible that the ATI proprietary drivers MIGHT attack the overheating problem, from what I read recently, the temp control stuff had not been incorporated into the Linux drivers yet.  But, since I don't use those drivers, I could be wrong.

For current info, would be best to check the Phoronix forum, searching with your card model number.

Second problem, though, is that while you will probably be able to install the ATI drivers in LiveCD mode, you will probably then have to reboot to enable the drivers -- effectively, starting over from scratch.  So, unless you actually install Ubuntu, you may not be able to actually use the proprietary drivers.

---

### Post by warfacegod on 2010-07-07
> **Mark Phelps said:**
> While it's possible that the ATI proprietary drivers MIGHT attack the overheating problem, from what I read recently, the temp control stuff had not been incorporated into the Linux drivers yet.  But, since I don't use those drivers, I could be wrong.

For current info, would be best to check the Phoronix forum, searching with your card model number.

Second problem, though, is that while you will probably be able to install the ATI drivers in LiveCD mode, you will probably then have to reboot to enable the drivers -- effectively, starting over from scratch.  So, unless you actually install Ubuntu, you may not be able to actually use the proprietary drivers.

This can be gotten around by using a LiveUSB with persistence.

---

### Post by cloyd on 2010-07-07
I had trouble with display misbehaving in 10.04. Misbehavior started after appox 40-50 minutes Overheating? I don't know. I tried this:
[COLOR=#000080][U][http://news.softpedia.com/news/How-t...4-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

[/U]There are two solutions suggested on this site . . . one simple, one a little more involved. I tried both, got the more involved to solve my problem. I don't understand exactly what it did, but now I have a blank screen during boot up where it used to have "ubuntu" in the middle of the screen. Since I did this, I have had no video issues, with machine running 4 hours plus. I also have an ATI card:, though not the same as yours.
 
[/COLOR]   	 	 	 	 	 	  01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
 
Don't know if this will help you, but it might.  Also, what to some more experienced think about this solution? I've been with Ubuntu since last Nov and still consider myself a rank noob. 

As I solve a few issues like this, I'm liking 10.04, but it has had a few problems.

---

### Post by warfacegod on 2010-07-07
I can't speak to the fix concerning the resolution. As far as the second goes, removing the Logo, I got the same result by removing the plymouth-theme-ubuntu-logo package. I prefer my way for two reasons.

.01 It didn't leave the Logo in my system.

.02 I didn't have to install anything to do it. (Although, Startup Manager is a decent tool.)

---

### Post by alanotero10 on 2013-03-21
Hi.
I wonder if you still have the same machine. I also have an ASUS G73JH with ATI Radeon HD5870 using ubuntu 12.10 and still having the overheating problem. So i wonder if you found out how to solve the problem. Which kernel are you using, which drivers? As far as i know i've tried everything to solve the problem which i have had since 6 months ago.

---

### Post by QIII on 2013-03-21
Thank you for sharing.  Everyone’s questions are important and answers are valuable.

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

*Thread **closed.***

---

