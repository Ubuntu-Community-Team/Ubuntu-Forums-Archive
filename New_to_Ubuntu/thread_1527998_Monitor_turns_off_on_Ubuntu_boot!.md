---
title: "Monitor turns off on Ubuntu boot!"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by roguemirror on 2010-07-10
Ok, heres my story: I installed ubuntu on my netbook and it worked fine, and it really really interested me.  So, I wanted to try it on my desktop, this time i downloaded the desktop version of the cd  and burnt it and tried to boot the live version and my monitor just went off.  SO, i figure id try a different monitor... same problem it just went off a few seconds after boot, than I tried a 3rd, same problem.   So than i googled around and read to use alternate cd, so I did that and I got Ubuntu installed now.   It dual boots with windows xp.   So now when i boot up i get an option windows xp, or Ubuntu 10.04 when I select ubuntu it shows some text than the monitor goes off, just like before, but this time I hear a congo drum sound or something.  I tried pressing alt+ctrl+f1 i still dont see anything.   I read on google to enable vesa drivers, so i googled how to enable them and it just says select the option at startup and i dont have that option.   I ve been trying to fix this problem for the last 3 days and i just really want to have ubuntu on my desktop, any help would be appreciated.

---

### Post by okplayer02 on 2010-07-10
well its obvious its a video card problem can you identify what video card you have? Does this occur in Windows XP? 

you can also identify your video card with this command 

```
lspci
```

---

### Post by roguemirror on 2010-07-10
> **okplayer02 said:**
> well its obvious its a video card problem can you identify what video card you have? Does this occur in Windows XP? 

you can also identify your video card with this command 

```
lspci
```

Oh i'm sorry thought i did.(ive made so many post on this i cant keep up)

It's a compaq sr1910nx desktop, with nvidia 6150 LE Gfx card
i hear the ubuntu sound at start up, start a terminal but screen still has no signal and i also tried xdriver=vesa added to boot line 
Yes, Xp works fine, im on it now actually, and ive tried it with the ubuntu desktop disc, and the alternate one.  An error that says something along the lines of nforce parsing error pops up really fast ( like subliinal message kinda fast)

---

### Post by waynefoutz on 2010-08-01
> **roguemirror said:**
> Oh i'm sorry thought i did.(ive made so many post on this i cant keep up)

It's a compaq sr1910nx desktop, with nvidia 6150 LE Gfx card
i hear the ubuntu sound at start up, start a terminal but screen still has no signal and i also tried xdriver=vesa added to boot line 
Yes, Xp works fine, im on it now actually, and ive tried it with the ubuntu desktop disc, and the alternate one.  An error that says something along the lines of nforce parsing error pops up really fast ( like subliinal message kinda fast)


I'm having the same problem on a Compaq desktop with a similar video card. Monitor goes to sleep during boot up on the live CD. It happens on every distro Ive tried that's based off of Lucid. I've tried, Linux Mint, and Peppermint. Boots up fine off of the new PCLINUXOS CD, and  anything running based on Karmic. I've tried all the "Blank screen at start-up" fixes, (nomodeset, xforcevesa) to no avail. I still get the sleeping monitor. This system ran Karmic fine. I did the update, got this problem, so I tried to clean install, nope, no joy. 

Anyone find a fix?

---

### Post by d0ida on 2010-08-06
I have the same problem with both a live CD of Lucid or a USB bootable stick.  I get to the purple screen with the icons at the bottom, I press Enter, I get the options menu to try Ubuntu or install it, etc, I try to use either of those first two options by selecting them and pressing Enter, I get a purple screen with Ubuntu and dots that progressively change color until my monitor turns off in a minute or so.  I was able to the check the disc for errors and the monitor did not turn off during that process, and it found no errors.  

I am trying this on a Asus Essentio CS5111 with Intel GMA X3500 (Intel 82G35 chipset) that already has 9.10 Karmic (Super OS variant) running great on it and it can also boot into Windows 7.

BTW, I also tried a live cd of Kubuntu 10.04 and it acted the same and gave a really quick error message before it went black on screen.

I also tried adding "i915.modeset=1" to the boot parameters and just got a bigger, off-centered Ubuntu logo before the monitor went to sleep after trying to boot.

Results of uname -a  on the Asus running Karmic:
Linux 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux

A live cd of Kubuntu 10.10 alpha actually booted into a desktop after a very long time and with low-res graphics only.

I can't get openSuse 11.3 to boot either, same thing--monitor goes to sleep.

***PCLinuxOS 2010.7 live cd boots just fine.  Info about the driver:
modinfo i915:      
filename:       /lib/modules/2.6.33.5-pclos1.bfs/kernel/drivers/gpu/drm/i915/i915.ko.gz

uname -a:       Linux localhost 2.6.33.5-pclos1.bfs #1

***Pardus live cd 2009.2 boots and tells me through System info in Konqueror I have this:
Mesa DRI Intel(R) 965G GEM 20091221 2009Q4 x86/MMX/SSE2[ Tungsten Graphics, Inc ]
   2.1 Mesa 7.7.1[ 3D Supported ]
and modinfo gives me: modinfo i915
filename:       /lib/modules/2.6.31.13-131/kernel/drivers/gpu/drm/i915/i915.ko

---

### Post by d0ida on 2010-08-07
I found this 

[https://bugs.launchpad.net/ubuntu/+bug/531027]("https://bugs.launchpad.net/ubuntu/+bug/531027")

and it seems people were getting the error message I saw when I tried the Kubuntu 10.04 live cd and experiencing similar problems.

---

### Post by d0ida on 2010-09-17
Fedora 13 does the same: looks like it will boot into the live cd and then after a few minutes, the monitor turns off.

Now I am wondering if it is a problem with Grub, or perhaps Gnome?  I don't know enough to ask the right questions to get an answer.  I am afraid that at some point I will upgrade my 9.10 to whatever is causing this problem.

I just looked at [http://fedoraforum.org/forum/showthread.php?p=1396065]("http://fedoraforum.org/forum/showthread.php?p=1396065") which sounded similar.  I tried the steps on both a Fedora 13 live cd and on a 10.04 live cd without getting to a desktop.

Perhaps this is a problem with the Nouveau driver (except I have an Intel video chipset).  

Does anyone know?

---

### Post by d0ida on 2010-09-17
Okay, I thought maybe it was related to KMS kernel mode setting but it appears to be enabled already on my 9.10  (which once in a blue moon now fails to boot to anything other than a black screen)

dmesg | grep drm
[    3.887120] [drm] Initialized drm 1.1.0 20060810
[    4.433922] [drm] fb0: inteldrmfb frame buffer device
[    4.433976] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.512776] [drm] DAC-6: set mode 1280x1024 11
[   18.645437] [drm] DAC-6: set mode 1024x768 13

---

### Post by d0ida on 2010-10-10
I am writing this after a 10.10 live cd finally booted (by finally, I mean after three failed attempts.  Trying to boot the first time, I just let it go normally until it asked whether I wanted to try or install.  I clicked the try button but it just hung.  I was able to click on the link to read the release notes, which opened in Firefox. The second try, I used the nomodeset option only and ended up with a text prompt and failures to start X.  Then later I marked all the options except nomodeset and that worked. So here I am, using the live cd to post.

This gives me hope that I will be able to upgrade someday and stick with Ubuntu.

=D>

---

### Post by jtarin on 2010-10-10
> this time I hear a congo drum sound Do you know where you are??? :)

Can you boot the live CD to the Gnome desktop?

---

### Post by nikefalcon on 2010-10-14
try these:
[B][http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379)
[/B]

---

### Post by ravenousj on 2012-12-15
> **nikefalcon said:**
> try these:
[B][http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379)
[/B]
thank you, this worked. ubuntu forums are awesome! when i first put this pc together with this card it worked fine but had trouble with sound, so i tried another video card but this time i had speakers connected and all worked fine. so i was thinking maybe it was because speakers were not connected during install. so i gparted hard drive and connected other video card and the sleeping monitor occured. once again, thank you.

---

### Post by overdrank on 2012-12-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

