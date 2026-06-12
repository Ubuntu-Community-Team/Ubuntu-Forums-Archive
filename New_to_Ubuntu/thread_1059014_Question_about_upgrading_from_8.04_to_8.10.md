---
title: "Question about upgrading from 8.04 to 8.10"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by 5nak3 on 2009-02-03
Hi all, was looking at an upgrade from 8.04 to 8.10 but I have a few questions. To upgrade i was just going to run "update-manager -d" in terminal. But then a couple of things crossed my mind:

1) I know this says upgrade, but I'm not clear if this will completely wipe 8.04 and start a fresh install. I'm going to back up crucial documents but my worry is that I've spent so long customizing 8.04 installing programs I want, getting rid of those I don't want etc... that I don't want to do the whole thing again.

So in essence, will the upgrade keep all my programs, themes, fonts etc.. the way i left them?

2) Will 8.10 support my graphics card?

lspci gives me the following read out 

VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP].

The 8.10 release notes state that "r3xx Hardware does not work with fglrx [EPR#257839]"

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)
But i couldn't quite understand if I am supported or not...or if it even matters.

3) Assuming I upgrade now, I reckon the April release 9.04...shouldn't pose any problems or is it simply better upgrading from LTS to LTS release i.e. from 8.04 to 9.04?

I think there was one more milling around in my head, but I cant remember it right now.

---

### Post by snowpine on 2009-02-03
Sorry I can't help you with the graphics card question, but the good news is that, yes, you should keep all of your applications and settings when you upgrade to 8.10. It is a good idea to back up any important documents, of course, but if all goes well, the upgrade should be seamless.

9.04 is not a LTS release. The next LTS will be April 2010.

---

### Post by 5nak3 on 2009-02-03
Hi thanks for the quick response, while i was busy waiting for a response I've downloaded the live CD for 8.10 and have booted into that, everything seems to be working just fine...Compiz from what i can tell ran straight out of the box.

Sound is not an issue both through the headphones and speakers. Video works, FPS seem to have increased a tiny bit from the 500fps average to 600fps...still don't think that the card is running at full capacity but it is an improvement, direct rendering is turned on (cant remember the terminal command i used "glxinfo" i think...)

I will play a bit longer with the live cd see if i can find any problems, would ideally like to try out an opengl game so might look into that for the time being.

In regards to the LTS, i thought that each X.04 update was the recommended LTS upgrade. Must have been mistaken, but you live and learn :)

If anyone can just give me some info regarding the graphics card question I had that would be great :)

---

### Post by perlluver on 2009-02-03
This can explain an LTS better than I can so: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) or here, and focus on Releases: [http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu)

---

### Post by 5nak3 on 2009-02-03
@ perlluver:

Thank you for the links, cleared things up for me regarding the LTS heading :)


Played with the liveCD from what I can tell things were working just fine, internet, sound, graphics, mounting and unmounting devices etc... etc...and the update seem to have actually has also fixed a couple of small niggles I was having with hardy

However as you all can imagine, a problem may develop at some point in the future with long term use which i have over looked. So one last question before i update:

Say if something does occur in the future and I cannot find a solution, is it possible to revert to an older distrobution (in this case 8.04) without having to do a fresh install?

Right i'm going to back up my documents and i'll be back to check for a reply :)

---

### Post by snowpine on 2009-02-03
No, no cannot easily "downgrade" to a previous version of Ubuntu.

You can, however boot into the old kernel using grub, so if the new kernel gives you problems (which it doesn't sound like it will), you have the old kernel to fall back on.

---

### Post by dawynn on 2009-02-03
Couple notes from my own experience...

You indicate that you've spent a lot of time changing which programs you use (removing some, adding others), and wonder whether the system will keep your choices as you upgrade.  The right answer is -- not always.

The default for most apt-based tools is to apply recommends as if they were depends.  I run an older system.  I have no interest in compiz or anything bluetooth, so I have stripped them from my system.  But because these are recommended by every one of the '*-desktop' meta-packages, the system tries to reinstall them when I do an upgrade.  You may find that some of the stuff that you cleared from your computer may creep back in.

Also, the powers that be at Ubuntu make changes now and then as to which are preferred applications, and which programs are even available.  Some apps also become obsolete because they utilize old libraries, and they have a defunct upstream author.  So, sorry to say, you may see favorite tools disappear to be replaced by other tools.  Typically, if there is no replacement at all, your package will be relegated to the "Local and Obsolete" section in your favorite package manager.

It is a noted complaint that, as tools are upgraded, their configuration settings can sometimes become obsolete.  So, if you *really* like your system settings, be aware that you may see some configurations ignored or reset as you upgrade.

From my experience, the powers that be for each distribution have been known to set things up on the install CD in a way that just isn't replicated by an upgrade.  This isn't always intentional, but more testing is typically given to fresh installs being right, then to ensuring that upgrades produce a similar experience to a fresh install.


Finally, to your other question, it is possible to downgrade, but its not pretty.  It is a very time-consuming process, and because the package creators don't intend for users to downgrade, usually its far more messy than an upgrade.  I've done it before (package by package) but I wouldn't suggest it for newbies.

---

### Post by kansasnoob on 2009-02-03
> **5nak3 said:**
> Hi all, was looking at an upgrade from 8.04 to 8.10 but I have a few questions. To upgrade i was just going to run "update-manager -d" in terminal. But then a couple of things crossed my mind:

1) I know this says upgrade, but I'm not clear if this will completely wipe 8.04 and start a fresh install. I'm going to back up crucial documents but my worry is that I've spent so long customizing 8.04 installing programs I want, getting rid of those I don't want etc... that I don't want to do the whole thing again.

So in essence, will the upgrade keep all my programs, themes, fonts etc.. the way i left them?

2) Will 8.10 support my graphics card?

lspci gives me the following read out 

VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP].

The 8.10 release notes state that "r3xx Hardware does not work with fglrx [EPR#257839]"

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)
But i couldn't quite understand if I am supported or not...or if it even matters.

3) Assuming I upgrade now, I reckon the April release 9.04...shouldn't pose any problems or is it simply better upgrading from LTS to LTS release i.e. from 8.04 to 9.04?

I think there was one more milling around in my head, but I cant remember it right now.

Some of your customizations may be lost! Basically a few dependencies may change.

As far as the Graphics Card goes I'd always try running the live CD before installing any distro!

8.04 is good for a long, long time yet!

---

### Post by 5nak3 on 2009-02-03
Ok thank you very much for the very insightful posts in regards to the downgrade.

The two areas i've spent a bit of time customizing are Compiz and Cairo-Dock. Other then that, i've not messed with the program recommendations too much (if at all).

My big concern was that I've downloaded several games for instance which are 700 odd meg, they are working fine at the moment, and I would hate to lose them.

In terms of programs, I know which ones I want and can get those installed quickly. And since I've not messed with their settings too much i will not worry about them (they all came from the add/remove section anyways).

To be perfectly honest, I don't keep crucial things on the system, I just ensure that I have my needed files to operate, so a fresh install isn't a problem in terms of data loss, it is just time consuming.

My real concern was if time was going to be spent having to download every single program again, but from my understanding they will all still be there, though if some dependencies are broken they may not work and require an upgrade and/or complete removal.

@ kansasnoob

I thought it was best to run the liveCD first as well, and from what I saw everything was there and was operating fine. So my understanding is that my graphics card is good to go.

While I know 8.04 is still good to go, there were two changes in teh 8.10 liveCD which is making me really consider the upgarde.

Increase fps from my gfx card, about 100 more than 8.04 is delivering
Sound now works like it did in Windows, i.e. when you plug the headset in the speakers cut off.

The second problem is the big one in my opinion because i use headsets a lot. And despite attempts to get 8.04 to work with a headset/earphones switch, I couldn't manage it.

---

### Post by 4Orbs on 2009-02-03
You could make an installation dvd backup copy of your system, with all programs, files and user settings intact, that works just like an Ubuntu live cd. The program is called [remastersys]("http://hacktolive.org/wiki/Create_a_custom_Live_CD_of_ubuntu").

---

### Post by snova on 2009-02-03
> **5nak3 said:**
> 1) I know this says upgrade, but I'm not clear if this will completely wipe 8.04 and start a fresh install.

Kinda. A dist-upgrade simply fetches new versions of every updated package it can find. If that means every package on the system, then aside from keeping previous configuration files, it's pretty much a reinstall.

> I'm going to back up crucial documents but my worry is that I've spent so long customizing 8.04 installing programs I want, getting rid of those I don't want etc... that I don't want to do the whole thing again.

Settings are stored in your home directory, which will never be touched during an upgrade. Nor will any package management operation.

---

### Post by longtom on 2009-02-04
> **snowpine said:**
> 
9.04 is not a LTS release. The next LTS will be April 2010.


[Here](http://ubuntuguide.org/wiki/Ubuntu:Intrepid) they say October 2009.  Is that outdated?

longtom

---

### Post by 5nak3 on 2009-02-04
Hi all many thanks for all the replies.

Just to update the situation, I have successfully updated, but have found two problems.

One, .mp4 or .3gp files do not play sound with the video. I fixed this in Hardy by following the following guide:

[http://www.munz.li/?p=11](http://www.munz.li/?p=11)

But have been unable to replicate this success in Intrepid (i also installed the w32 codecs if that makes any difference)

Two, this is the most worrying of the problems:

When I reboot the computer starts scanning the hard drive which it is meant to do every 30 or so boots. I'm fine with that. The problem is that for some reason the scanning hangs. It stops at around 6-10%. No matter how long i leave it it does not complete. 

I can bypass it by pressing esc before it reaches the hang point, but once it hangs there is no key activity and i have to hard reset. 

I have disabled the scan at the moment by using

sudo touch /fastboot

But I don't like doing that, and would prefer if the scan actually completes itself and remains there for every 30 or so boots. Can anyone shed some light as to why this might be happening?

Many thanks

---

### Post by 5nak3 on 2009-02-04
Just wondering if anyone could provide any insight as to whie the start up scan (fsck) does not complete / freeze

If it is of any use i have noticed that since i upgraded from hardy the number of files it is scanning has dropped for several thousand in hardy to about 572 for intrepid and usually it gets stuck at around 68-90 files through.

Any information or advice would be very much appreciated :-)

---

### Post by crho85 on 2009-02-04
You know, I just did this. I had an 8.04 Wubi install and went to a straight 8.10. I always had issues with my graphics card (ATI IGP 320M/ Mobility U1). But when I loaded up 8.10 I had desktop effects and 3d rendering.

The only thing I had to change in my .conf was the resolution (was set too low). 

I had my customised the way I like it but wanted a non windows dependant install. 

If you spent all that time on a custom set up, I would consider keeping it until the next LTS

If you do run into problems with the video card perhaps [this may help]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by 5nak3 on 2009-02-04
Ok, I've been doing some reading on the whole fsck issue I'm having.

And even after reverting back to hardy (fresh install with a guided install using the entire disk) i still cannot run a fsck on boot.

Forcing the computer to do so with:

sudo touch /forcefsck

Will get it to load up to a certain percentage and then the whole system will freeze and it will not move, no matter how long i leave it, requiring a hard reset.

While reading i found someone suggesting to do a fsck from the live CD.

In goes hardy's live CD, I open up terminal and i run

sudo fsck -f /dev/hda1

And the out put it returns with is:

ubuntu@ubuntu:~$ sudo fsck -f /dev/hda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/hda1: 127857/4685824 files (0.8% non-contiguous), 1155534/18729774 blocks

it seems to me something is wrong, and this is concerning me because I would like the option of running fsck on boot regularly it was a feature I liked. But not being able to run it, forcing hard resets cannot be doing good to the hardware.

If anyone has any input on the matter i'm all ears :)

---

