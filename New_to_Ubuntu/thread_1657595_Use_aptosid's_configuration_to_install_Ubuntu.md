---
title: "Use aptosid's configuration to install Ubuntu?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2011-01-01
I have an old Dell Dimension 4100 running at 900 mhz or a bit higher with 512 MBs of RAM I am having a miserable time getting a working modern install of Linux with Gnome running on.  I had it set up with Gutsy (Ubuntu 7.10) at one point where upon it was put in the closet after my parent's internet plans were put on hold.  I now have the unenviable task of trying to get something slightly more modern running on it in preparation for their long delayed internet installation.

I tried doing an upgrade (but apparently the recommended path is to install as upgrades every release until you manage to get current.  Not. Gonna. Happen.)  Then I installed a command only installation of Lucid and proceeded to install xorg, etc.  Hello frozen KMS!  Part of the problem seems to be this desktop has an ancient ATI onboard card and a more recent nvidia PCI video card I used with success in Gutsy and which the bios is supposed to detect the presence of and automatically disable the onboard ATI in favor of.  I also noticed that ACPI had been taken out when I tried the upgrade, which I suspect could be causing my troubles?

So far I have tried Ubuntu 8.04, 9.10, 10.04, 10.10, LinuxMint 10, Debian netinstaller, Salix LXDE 13.1.3, Fedora 13, Fedora 14, and Fuduntu 14.7-3  As of now only Ubuntu 8.04 and aptosid have been able to boot, let alone install!  You can't say I haven't been trying!

What I'm wondering now is if there is a way to install a base aptosid and then upgrade to Ubuntu somehow, to get the configuration and repositories?  Or to see whatever it is that aptosid is doing right and what Ubuntu is doing that makes it fall over on me?  Help from any users with this model of desktop is sincerely appreciated!

--bornagainpenguin

---

### Post by gordintoronto on 2011-01-01
Have you tried boot parameters such as nomodeset? I have never needed it myself, so I can't give you a blow-by-blow on how to do it.

I would try Lubuntu on that configuration, and also Puppy Linux.

According to the aptosid web site, it has access to a large repository.

---

### Post by QLee on 2011-01-02
[QUOTE=bornagainpenguin]I have an old Dell Dimension 4100 running at 900 mhz or a bit higher with 512 MBs of RAM...[/QUOTE]

So, a 933MHz P3. I don't have the same system but one close and from the same era. A 1GHz Celeron with 512MB, that runs 10.04. Because of the larger cache of the P3, those systems should be pretty close in resources. Mine doesn't boot up as fast as a modern computer but Firefox, for example, is adequate for surfing which is probably what your parents need.

[QUOTE=bornagainpenguin]...Part of the problem seems to be this desktop has an ancient ATI onboard card and a more recent nvidia PCI video card I used with success in Gutsy and which the bios is supposed to detect the presence of and automatically disable the onboard ATI in favor of.  [/QUOTE]

That won't be an onboard card, it will be an AGP card in an AGP slot and removeable. Are you sure about the BIOS detecting and automagically disabling when a second card is added?

If I was trying what you are trying, I would pull out one of the video cards and try the live CD with only one inserted. If That didn't work, I would try it with only the other one. Depending on the card you might still have to use nomodeset or one of the other choices but maybe not. You might also try with the alternate CD instead of the live CD.

You mentioned that you were able to boot with 8.04. Note: The upgrade path from 8.04 to 10.04 is direct because they are LTS releases. Remember 10.04 is what I have running on my old system and could be a good choice for your parents machine.

[QUOTE=bornagainpenguin]I also noticed that ACPI had been taken out when I tried the upgrade, which I suspect could be causing my troubles?[/QUOTE]

The implementation of ACPI was and could be problematic in computers of that era. On mine, works with 10.04.

[QUOTE=bornagainpenguin]... Help from any users with this model of desktop is sincerely appreciated![/QUOTE]

As mentioned, not the same desktop but something close. Of course with old hardware like that, there might be hardware issues, it is from the era when there were a lot of bad
capacitors around that bulged or leaked over time.

So, try some of my suggestions if you choose to continue. At the very least, you could try installing 8.04LTS and upgrading to 10.04LTS.

---

### Post by bornagainpenguin on 2011-01-02
> **gordintoronto said:**
> Have you tried boot parameters such as nomodeset? I have never needed it myself, so I can't give you a blow-by-blow on how to do it.

I have.

> **gordintoronto said:**
> I would try Lubuntu on that configuration, and also Puppy Linux.

Despite being able to run Gutsy withojut issue and compiz working (which was the reason why I had originally had Gutsy on this box and not Hardy--for some reason the ability to run compiz on this box with Hardy was disabled) I have never had any issues running Gnome on the box.  Seemed fast enough to me any way.  I was considering LXDE which was why I had Salix downloaded but even the venerable Slackware was unable to boot(!)

> **gordintoronto said:**
> According to the aptosid web site, it has access to a large repository.

I'm sure it does, being based on Debian just as Ubuntu is.  Thing is, despite some of the issues I've had in the past with some of the Canonical developers' choices in configuration--they do provide a lot of sane defaults and I find that I prefer the way they style the desktop over most other distros.  I would really prefer to just run Ubuntu on this box, but failing that would like to get the hardware detected and get as much of the default Ubuntu desktop installed as I can.

Thanks for the reply!

--bornagainpenguin

---

### Post by bornagainpenguin on 2011-01-02
> **QLee said:**
> So, a 933MHz P3. I don't have the same system but one close and from the same era. A 1GHz Celeron with 512MB, that runs 10.04. Because of the larger cache of the P3, those systems should be pretty close in resources. Mine doesn't boot up as fast as a modern computer but Firefox, for example, is adequate for surfing which is probably what your parents need.

Exactly my thinking.  Well that and Frozen Bubbles which my Mom loves...  ;)

> **QLee said:**
> That won't be an onboard card, it will be an AGP card in an AGP slot and removeable.

No, it is an onboard ATI AGP video "card" built right into the motherboard.  I have an nvidia PCI video card installed.

> **QLee said:**
> Are you sure about the BIOS detecting and automagically disabling when a second card is added?

No I am not sure that this is happening at all.  That is the way it is supposed to work though, according to the reports I read earlier when I had this box in the past.  Around Feisty or before Ubuntu had some issues like this and I was able to successfully get Fedora installed until the release of Gutsy which fixed issues and allowed me to return to Ubuntu.  The posts I read from people on the issues then said that this was the way the bios worked, because at first I was trying to use an old ATI video card I had laying around and was surprised to discover this would not work because the hardware detection would get confused and the recommendation (from Dell's forums IIRC) was to use an nvidia card instead.

> **QLee said:**
> If I was trying what you are trying, I would pull out one of the video cards and try the live CD with only one inserted.

That might work, but how well do you think things will run with an anemic 2-4mb video card?

> **QLee said:**
> If That didn't work, I would try it with only the other one.

I don't think you're understanding me.  The ATI is *ON BOARD VIDEO.*  It is not possible to remove it.  (Well unless we're talking blowtorches and then I think the secondary effects would invalidate any gains...might feel good though!  ;)

> **QLee said:**
> Depending on the card you might still have to use nomodeset or one of the other choices but maybe not. You might also try with the alternate CD instead of the live CD.

You mentioned that you were able to boot with 8.04. Note: The upgrade path from 8.04 to 10.04 is direct because they are LTS releases. Remember 10.04 is what I have running on my old system and could be a good choice for your parents machine.

Yeah I did that already--I see I forgot to mention it in my request for help here and assumed it was already listed because I copied some of my post from that thread on one of my other forums.  I tried a command only net install, I tried installing 8.04 and upgrading, and I tried a few other command line options.  None of which helped me.  Trying the upgrade seems to work but then the system halts on the reboot and never makes it to the desktop again, stuck on the bootsplash.

> **QLee said:**
> The implementation of ACPI was and could be problematic in computers of that era. On mine, works with 10.04.

I'm not even sure that ACPI is even a part of the issue, I just listed it because it was among the items the upgrade from 8.04 remoeved, so I pondered if that could be the difference between the two causing me issues?


Thanks for the post.  Now that I've explained that I was unable to upgrade have you any suggestions for me?  Since the computer freezes entirely (unable to get to a console at all) and requires a hard reset to get out of I am unsure what logs if any would be useful.  I could still try booting from the 8.04 live cd and posting any logs available if you can recommend any that might be useful?  Any other ideas?

--bornagainpenguin

---

### Post by QLee on 2011-01-02
> **bornagainpenguin]...

That might work, but how well do you think things will run with an anemic 2-4mb video card?[/QUOTE]

Only way I know would be to try it. Mine works OK with an 8MB video card. If you got it to work you could try the upgraded card after you had a working system.

[QUOTE=bornagainpenguin]I don't think you're understanding me.  The ATI is *ON BOARD VIDEO.*  It is not possible to remove it.  (Well unless we're talking blowtorches and then I think the secondary effects would invalidate any gains...might feel good though!   said:**
> 
I read what you wrote, but that doesn't track with the specifications I looked up on the Dell site. In addition, onboard video wasn't common on mainboards of that era. I'm an old guy who has seen quite a few. Definitely, any onboard video should have a way in the BIOS to option it off.

[QUOTE=bornagainpenguin]...

Thanks for the post.  Now that I've explained that I was unable to upgrade have you any suggestions for me?  Since the computer freezes entirely (unable to get to a console at all) and requires a hard reset to get out of I am unsure what logs if any would be useful.  I could still try booting from the 8.04 live cd and posting any logs available if you can recommend any that might be useful?  Any other ideas?


Still the same suggestion, try with only one video interface.

The comment about bad capacitors might still apply, that can cause many and varied troubles, I had one mainboard that would boot sometimes, sometimes not, sometimes lock-up, sometimes not, very intermittant and irregular, other times it seemed to work OK. While you have the case open to remove the PCI video card, inspect the capacitors on the mainboard carefully.

---

### Post by bornagainpenguin on 2011-01-02
> **QLee said:**
> Only way I know would be to try it. Mine works OK with an 8MB video card. If you got it to work you could try the upgraded card after you had a working system.

I suppose its worth a shot, if for no other reason than to eliminate a few things...

> **QLee said:**
> I read what you wrote, but that doesn't track with the specifications I looked up on the Dell site. In addition, onboard video wasn't common on mainboards of that era. I'm an old guy who has seen quite a few. Definitely, any onboard video should have a way in the BIOS to option it off.

Well this bios doesn't seem to have that option.  Closest thing I've seen was an option to choose which port to try first AGP or PCI.  It has been a few years since I opened it up though so I'll have to look around and make sure everything is as I remember it.

> **QLee said:**
> The comment about bad capacitors might still apply, that can cause many and varied troubles, I had one mainboard that would boot sometimes, sometimes not, sometimes lock-up, sometimes not, very intermittant and irregular, other times it seemed to work OK. While you have the case open to remove the PCI video card, inspect the capacitors on the mainboard carefully.

Point.  I'll also have to make sure the video card itself is still in good shape while I'm in there.  Seemed to be alright when I dropped in the PCI WiFi card, but I suppose it could have blown something when I turned it on again later.  If nothing else and the ATI works, I'll see if the old voodoo card I have laying around will do anything...  ;P

Or try and see if I can get a low riser WiFi for some of the more recent boxes I have laying about.  It seems to be harder and harder to find *anything* with a low profile slot these days though...

--bornagainpenguin

---

### Post by bornagainpenguin on 2011-01-03
> **QLee said:**
> I read what you wrote, but that doesn't track with the specifications I looked up on the Dell site.

That would be because I was thinking about a different box entirely, also a Dell but not THIS Dell.  In my own defense I'd like to say that they look identical outside and it *has* been a bit since I've opened the box.  Still mea culpa you had the right of it and I was wrong.

There is no onboard video on this one, just the standard three or four PCI slots and a single AGP which housed the nVidia card.

Since opening the box and checking the motherboard for any capacitor issues (didn't see any) I've tried swapping out the nVida card with a spare AGP ATI but am still having the box freeze in the booting process and lock on me at the same point.  I tested the cdrom to ensure it had been burnt correctly and am now doing a memory test to eliminate that possibility.

Still very frustrated at not being able to boot the live cd or install the operating system.

Any ideas on what aptosid is doing differently that allows the distro to boot their live cd and install to the disk without issue?

Thanks again for all help given and posts made!

--bornagainpenguin

---

### Post by QLee on 2011-01-04
[QUOTE=bornagainpenguin]...

Still very frustrated at not being able to boot the live cd or install the operating system.

Any ideas on what aptosid is doing differently that allows the distro to boot their live cd and install to the disk without issue?
...[/QUOTE]

Well, you did write that 8.04 CD booted and I did mention that the upgrade path from 8.04LTS was to 10.04LTS.

I used sidux, the old name for aptosid, a few years ago but have no experience with aptosid. When it was sidux, the developers were good coders and maybe they use a very basic video driver for the install. Have you tried all the kernel line options from the live CD boot menu? Or, tried the alternate CD?

Next is something I hesitate to mention in a beginner forum, because it is filled with danger and not for anyone unsure of themself. Since this system has nothing that has to be saved at this point, the danger is moot in your case. If your old aptosid install isn't upgraded at all, it may have version numbers low enough to allow just changing the sources list to Ubuntu Maveric repositories and doing an update and upgrade then installing things like ubuntu-desktop. This easily could make a mess, and there won't be support for it, that wouldn't be appropriate here anyway. Just something you could try for the learning experience.

That's about the end of my ideas.

---

