---
title: "Should I upgrade to Jaunty?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Extreedoc on 2009-07-07
Not sure if this is the correct forum to ask this question but... I am fairly new to Ubuntu/Linux, just a few months. I have Intrepid and am thoroughly enjoying the experience, I have it fettled pretty well, no serious issues. So, do I risk having to begin again or should I stick with Intrepid? I appreciate that others must have asked this same question but I haven't been able to find any such posts so am forced to ask anyway.
In gratitude for your patience, John.

This question has now been resolved; thanks to all.

---

### Post by pastalavista on 2009-07-07
Read the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904") and check for any known issues or bugs with your specific hardware. The biggest issue for most people is graphics compatibility.

---

### Post by Michael.Godawski on 2009-07-07
Moved to ABT.

---

### Post by lovinglinux on 2009-07-07
I don't see any reasons to upgrade if you are happy with your current installation. Jaunty has some new features that you might like, but I don't think they are essential. Keep in mind that a new release (Karmic Koala) will be available in October and Intrepid will still be supported until April next year, when a new LTS (Long Term Support) release will be available.

I have upgraded (actually I did a fresh install) from Hardy Heron (the current LTS) mainly because I wanted to try the ext4 file system. I'm quite happy with it now. I don't have more video tearing, most of my hardware was supported out-of-the-box and some applications are working better than in Hardy. Nevertheless, I experienced some performance issues and tweaking was necessary to achieve the desired performance on my machine. I like to tweak the system and find solutions, but if you don't want to eventually fix things, then stick with what you have.

I'm not happy with flash tho. It's worse than before.

Nevertheless, you might want to download Jaunty release, burn it and test it using the LiveCD and then decide for yourself.

---

### Post by binbash on 2009-07-07
Jaunty is very fast but it has serious problems with intel cards.I would wait for Karmic Koala release.

---

### Post by sdbrogan on 2009-07-07
Certainly test Jaunty with the live CD before upgrading/installing over your current installation.  Quite a few people (including me) have had problems that stop them being able to use Jaunty, e.g. 
[http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+freezing](http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+freezing)
.  On the other hand it seems more people have found it to perform better.
Also, always back up important data first (sorry if that's obvious to you).
If Jaunty doesn't work for you & there is some particular software you want a newer version of, or that isn't in the Intrepid repositories, there are other ways to get it without changing from Intrepid - backports, apt-pinning, or downloading .deb files.

---

### Post by AndyCee on 2009-07-07
> **Extreedoc said:**
> Not sure if this is the correct forum to ask this question but... I am fairly new to Ubuntu/Linux, just a few months. I have Intrepid and am thoroughly enjoying the experience, I have it fettled pretty well, no serious issues. So, do I risk having to begin again or should I stick with Intrepid? I appreciate that others must have asked this same question but I haven't been able to find any such posts so am forced to ask anyway.
In gratitude for your patience, John.

Take a look at the "new features" in Jaunty. If you don't see anything that matters to you, I wouldn't bother upgrading. Particularly if you're not confident fixing something a new release might break.

Having said that, I upgraded to Jaunty because I wanted ext4 support. That's about it.

---

### Post by muteXe on 2009-07-07
Stick with what you're happy with.  If it's not broken don't try and fix it.  I really mean this.
I've hated every version (due to many problems) after 8.04, and i'll be sticking with that for a while cuz it does 100% everything I want it to do.

---

### Post by noway2 on 2009-07-07
One other reason to stick with what you are already using is the possibility of losing everything when you install.  Yes, the instructions say you should make a backup, but even then the procedure is not without risk.

On the two occasions, I upgraded, I ended up wiping the whole system and doing a complete re-install.  In an attempt to learn from the experience, the last time this happened I partitioned the PC with separate /boot and / root partitions.  Hopefully this will allow easier upgrading without a total loss of data.

On the up side, I reformatted everything as ext4 and saw a major speed performance increase.

---

### Post by lovinglinux on 2009-07-07
> **noway2 said:**
> ... the last time this happened I partitioned the PC with separate /boot and / root partitions.  Hopefully this will allow easier upgrading without a total loss of data.

Don't forget about a separate home, that's the real deal ;)

> **noway2 said:**
> On the up side, I reformatted everything as ext4 and saw a major speed performance increase.

Me too. Keep in mind that if you decide to go back to Intrrepid or Hardy it will be a pain. As far as I know, you will have to format again as ext3. So bye bye to home partition. Backup is the only way out.

---

### Post by mikechant on 2009-07-07
What I do for each new release is:
1/ Try the LiveCD and test as much as possible. May not be possible to test some features.

2/ Take appropriate backups.

3/ Create a seperate partition and install alongside existing release. Test everything (particularly playing various video types, sound, suspend/resume, fixed/wired networking). Meanwhile you can carry on using the previous version for non-testing stuff.

4/ If anything in the new release is broken and can't be fixed, just carry on with the existing release, occasionally updating and retesting the new release until it works or is replaced by a 'new new' release.

5/ If you are happy with the new release, start using it after copying across or switching in your existing /home (depending on how you've got it set up).

It's more work this way, but you *always* have a fully working system at all times (unless you really screw up the partitioning in 3/, but that's what the backups are for!).

This method has been very sucessful for me. I was on 7.10 and I tested 8.04 and 8.10 but had too many problems (with sound) so I never switched to them. I tested 9.04 thoroughly, switched over to it and it's been just fine. I can still boot my old 7.10 release if I need to check something.

---

### Post by Extreedoc on 2009-07-07
Thanks to everybody who replied, I have given consideration to everything you all have said and I think the best thing for me, a non-techy is to stick with my Intrepid as I have nothing much to complain about with it. I will wait for the new release in October and evaluate that. One thing is for sure...I won't be going back to Windows!

---

### Post by LewRockwell on 2009-07-07
> **Extreedoc said:**
> Thanks to everybody who replied, I have given consideration to everything you all have said and I think the best thing for me, a non-techy is to stick with my Intrepid as I have nothing much to complain about with it. I will wait for the new release in October and evaluate that. One thing is for sure...I won't be going back to Windows!

Note: This post is more for future readers and future reference...

Regarding updating, upgrading, and newer versions/releases

I recommend obtaining each new release whether you intend to install it or not

The biggest reason is to check out the LiveCD so you know in advance how it might work for you on your equipment

You might also have the opportunity to use it for other machines and/or even giving it to someone at a time when they might be receptive to getting away from windows

Also, I do recommend staying current with updates, but I DON'T recommend upgrades to newer releases

The best reason is once the upgrade process of your older version has started...and things don't work out...then you're committed to a fresh install of one or the other

If you just get the newer LiveCD release to begin with, then you can both test-drive it AND have it available for a clean, fresh install

.

---

