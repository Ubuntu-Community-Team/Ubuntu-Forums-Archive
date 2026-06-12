---
title: "cd install fails"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-11-14
I have two identical amd 64 computers 9.10 installed just fine on one. On the other I am trying to install and it stalls every time. I have changed the bios to boot with cd and f10 changed the boot to boot from cd, tried regular install tried running cd live it always stalls. The live cd I get to the ubuntu boot up sound but blank screen. The fix?

Is there a 64 bit 9.10 download?

I just installed Fedora no prolem/suse 11.2 no problem/ ubuntu9.10 fails. Ubuntu 9.04 fails so what could it be?

---

### Post by Jon Monreal on 2009-11-14
So what you're saying is that the LiveCD won't get to the desktop? Or the install is stalling?

From your description, I'm assuming the LiveCD is the problem.

One thing you could do to help us would be to tell us a little more about your hardware. Is there a specific model?

---

### Post by rosswmcgee on 2009-11-14
Thanks, both computers are AMD Athlon Processor LE-1640/ memory 1931MB 

If I try a live cd install I get to the ubuntu music but not to the desktop. If I try a regular install It stalls before the desktop and no music. At the moment I am doing a clean install of Suse 11.2, just to see if it works again, and it seems to be. We run two Ubuntu 9.10 computers and one Suse 11.2. I decided to go 100% ubuntu 9.10 on three computers, but can't seem to. It is just a guess but perhaps Suse hates to see me go?

A new suse 11.2 clean install has been performed.

---

### Post by chriscross93 on 2009-11-14
Hmmm...  Thats interisting, maybe try the alternate?

---

### Post by Jon Monreal on 2009-11-15
Could you post the output of "sudo lshw -C video" from a terminal window?

---

### Post by rosswmcgee on 2009-11-15
This is from the Ubuntu Machine the Suse machine does not recognize the command, using su zypper sudo lshw -C video
does not recognize lshw

rosswmcgee@rosswmcgee-desktop:~$ sudo lshw -C video
[sudo] password for rosswmcgee: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable)
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by Jon Monreal on 2009-11-15
> **rosswmcgee said:**
> This is from the Ubuntu Machine the Suse machine does not recognize the command, using su zypper sudo lshw -C video
does not recognize lshw

rosswmcgee@rosswmcgee-desktop:~$ sudo lshw -C video
[sudo] password for rosswmcgee: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: nVidia Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:80000000-8001ffff(prefetchable)
rosswmcgee@rosswmcgee-desktop:~$

Thanks.

I believe [this earlier post provides a solution]("http://ubuntuforums.org/showthread.php?t=1172355") (gdm fails to start and you get a blank screen with GeForce 6150SE).

If you need additional help, please feel free to ask for it.

---

### Post by rosswmcgee on 2009-11-15
Thanks I will ponder this one as the machine with suse 11.2 is the one I would need to change and I am unsure if those commands as listed in the othe post will work. If it were installing on an already installed ubuntu say 9.04 they may.

---

### Post by Jon Monreal on 2009-11-15
> **rosswmcgee said:**
> Thanks I will ponder this one as the machine with suse 11.2 is the one I would need to change and I am unsure if those commands as listed in the othe post will work. If it were installing on an already installed ubuntu say 9.04 they may.

As suggested by [chriscross93]("http://ubuntuforums.org/member.php?u=435454"), have you tried the alternate CD? It comes in 64-bit and 32-bit versions, just like the LiveCD: [http://ubuntu.osuosl.org/releases/9.10/](http://ubuntu.osuosl.org/releases/9.10/) (ubuntu-9.10-alternate-amd64.iso for 64-bit, ubuntu-9.10-alternate-i386.iso for 32-bit).

EDIT: It's a text-based installer, so you shouldn't have any troubles with gdm not starting. After you install, you would of course be able to follow those instructions.

---

### Post by rosswmcgee on 2009-11-15
No this the first I have heard about it. Let me check this out. Thanks

I am downloading the amd 64 iso now. 

Reservations:

I have a 9.04 64 cd which I tried and it had the same problem, we shall see!

Ok I have downloaded the amd 64 iso file, but it looks like a usb rather than cd. What do I do with it?

Ubuntu gave me no options on what to do with the file, so I downloaded it on the Suse 11.2 computer

burned it to a cd and Voila it looks like we will have a successful install, now about 50% there,

---

### Post by rosswmcgee on 2009-11-15
Installation completed but left me with a blank screen. Now what?

---

### Post by Jon Monreal on 2009-11-15
You can now refer to the solution I mentioned in post 7: [http://ubuntuforums.org/showthread.php?t=1172355](http://ubuntuforums.org/showthread.php?t=1172355).

---

### Post by rosswmcgee on 2009-11-15
Solution does not work. For the life of me I have never had this much trouble installing Ubuntu, been at this problem now for several days.

---

### Post by Jon Monreal on 2009-11-15
> **rosswmcgee said:**
> Solution does not work. For the life of me I have never had this much trouble installing Ubuntu, been at this problem now for several days.

At what point does it fail?

If the first part does not work, pick it up at the Grub part where you hit escape and select recovery mode. This should work even if gdm is completely bricked. Remember that you might need to hit ESC repeatedly while booting if Grub isn't set to display for a longer amount of time.

---

### Post by rosswmcgee on 2009-11-15
I get to the root drop to root shell prompt:
I run the sudo dpkg-reconfigure-xorg:
All that happens is I get back to the root@ubuntu:~#


I have had enough! I will re install Suse 11.2, until I hear that Ubuntu has fixed the problem and comes out
 with a new iso cd. I mean this  is just stupid. 

Thanks for you help it is appreciated.

---

### Post by Jon Monreal on 2009-11-15
> **rosswmcgee said:**
> I get to the root drop to root shell prompt:
I run the sudo dpkg-reconfigure-xorg:
All that happens is I get back to the root@ubuntu:~#


I have had enough! I will re install Suse 11.2, until I hear that Ubuntu has fixed the problem and comes out
 with a new iso cd. I mean this  is just stupid. 

Thanks for you help it is appreciated.

It's supposed to be "sudo dpkg-reconfigure xserver-xorg".

At any rate, the best of luck to you.

---

### Post by rosswmcgee on 2009-11-15
I'll give it another go, right now checking disc 9.10 amd 64 for defects, and will try to re-install as all the re- boots and messing around have messed things up for lack of a better word. Just can not figure out why the ubuntu folks did not wait
until they had it right.

---

### Post by rosswmcgee on 2009-11-15
Installation failed second and third try with the amd64.so file.

---

### Post by Jon Monreal on 2009-11-15
> **rosswmcgee said:**
> I'll give it another go, right now checking disc 9.10 amd 64 for defects, and will try to re-install as all the re- boots and messing around have messed things up for lack of a better word. Just can not figure out why the ubuntu folks did not wait
until they had it right.

It's very upsetting to me. If new users experience problems right off the bat, they are more likely to return to proprietary operating systems. Ubuntu has gained a reputation for being easy to use and very compatible; everything possible should be done to maintain this reputation.

At any rate, I hope that it is fixed quickly so that you can enjoy Ubuntu once again.

---

### Post by rosswmcgee on 2009-11-16
Thanks! I agree!

Here is a wee story. I have used Ubuntu for years. I like to play around to increase my knowledge. So we have three computers, two are same and brand new, one new and one old are using ubuntu 9.10 one is an upgrade, both work fine. On the other new computer I have been using Suse 11.1 and everything was working fine after a lot of 
forum help. I decided to upgrade Suse 11.1 to 11.2 with a clean install. All went well, but as perfectionist, one litte thing on Opera would not work. I tried everything, to no avail. So I thought to heck with this I will install ubuntu 9.10 and have all three computers on ubuntu. That is where I ran install problem. First I used the same CD that installed just fine on the other computer, which is the same computer. I could not for three days trying new cds new downloads, nothing worked. 
Finally the computer stalled completely and would stop at the f10 and f2 boot up screens. So by this time I am exhausted. I unplugged the computer and let it sit for 
a minute, plugged it back in and was able to boot up. So throwing caution to the winds I installed Fedora 11. Zippity doo dah all works and no flaw in opera like I had with Suse. So I will stay with the one Fedora on this computer since for some reason unknown to me it refuses to install Ubuntu. Thanks for your kind and gentle 
help, allways appreciated. So mext on the menu, I helped a man install 9.10 on his computer, all works well, but alas no sound. So again a glitch of some kind, I will try and help him fix. It seems to me Ubuntu should not confine themselves to a release date, but release only when the new release is relatively bug free.

---

### Post by oldsoundguy on 2009-11-16
just for grins, clean your playback optical. Had similar issues and found it was the opticals, not the computer itself as they were not reading properly.

---

### Post by rosswmcgee on 2009-11-16
Well if that were the case Fedora and Suse would fail as well, but only the Ubuntu cds would not work. Same cd, I tried other cds as well. But I guess it is still worth a try, but now that I have fedora working beautifully I am going to leave it alone. As I said I already have two 9.10's working.

---

### Post by oldsoundguy on 2009-11-16
When I was a smoker, and my mom was living with me and she was a smoker .. and we had a small furry dog, I would clean ALL drives as a matter of routine once a month.  And clear out the dust bunnies at the same time.
I have computer boxes that have been ON and running for well over 5 years 24/7/365. Only shut down for internal maintenance and for hardware upgrading. (those opticals DO die and need to be replaced IF you use them a lot as I do.)

---

### Post by Jon Monreal on 2009-11-16
> **rosswmcgee said:**
> Well if that were the case Fedora and Suse would fail as well, but only the Ubuntu cds would not work. Same cd, I tried other cds as well. But I guess it is still worth a try, but now that I have fedora working beautifully I am going to leave it alone. As I said I already have two 9.10's working.

Very true. Seems strange that an identical system is having no problems, making me wonder if there is some difference, if even incredibly subtle, in hardware configuration that could be causing this. At any rate,

> So mext on the menu, I helped a man install 9.10 on his computer, all works well, but alas no sound. So again a glitch of some kind, I will try and help him fix. It seems to me Ubuntu should not confine themselves to a release date, but release only when the new release is relatively bug free.

I think Ubuntu could be fine with a set release date, so long as we limit the amount of time put into new features and even defer them to the next release if it means not spending enough time to make sure everything worse. A set release date does have some advantages, such as eliminating possible long times between release dates that can force people away (*cough* Gentoo, as much as I love it *cough*).

If you have trouble getting it working, please feel free to PM me.

---

