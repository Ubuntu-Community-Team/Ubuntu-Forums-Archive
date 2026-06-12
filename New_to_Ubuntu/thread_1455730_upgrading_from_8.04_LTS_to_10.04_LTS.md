---
title: "upgrading from 8.04 LTS to 10.04 LTS?"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Alex82 on 2010-04-16
Ok so I have been using ubuntu for a while now and love it. It is time for the heron to fly..or is it?

I have worked out most of the niggles on the heron and my computer is running to an acceptable standard most of the time (few flash and java errors here and there)

If I upgrade..

1 what is the best/easiest way to do it

2 will I have all the problems I originally had when I did a clean heron install (broadcom wireless card/flash,java/graphics/sound)

3 will it keep my all my settings (wine/compiz)

4 will mediamonkey work ;)

I am a 64bit pc


thanks

---

### Post by Zintha on 2010-04-16
I'm a complete newbie still to Ubuntu overall however,

I went from Koala to Lynx and, if anything, had less issues even in Beta.
Not had any issues with Wireless drivers or Graphics drivers or any drivers to be blunt.

It kept all my Wine settings I believe but I had a couple of Compiz problems but i'm pretty sure that was my fault personally.

I don't know the answer to any more of your questions but I figured i'd bump with at least some attempt at answering what I can.

---

### Post by venicequeen7706 on 2010-04-16
This might help you with a couple of those questions.

[http://ubuntuforums.org/showthread.php?t=1436926](http://ubuntuforums.org/showthread.php?t=1436926)

As for the details, I'm new to linux so i'm still working on interpreting much of that.

---

### Post by clhsharky on 2010-04-16
HI

1 A fresh install is the easiest and best way.

2 Flash java sound are easer and better than 8.04, broadcom wireless couldn't tell ya "search forum". Graphics, you didn't say what chip you have.

3 Wine no, start over. compiz to many bugs, I use a different compositor.

4 don't know

I'm on 64 Lucid the best release yet.

Sharky

---

### Post by snowpine on 2010-04-16
Hi Alex, when Lucid Lynx is released later this month, your Update Manager should show you that the new release is available. Upgrading is as simple as clicking one button! And it should keep all your applications, documents, and settings. :)

That being said, new releases sometimes have new bugs. I would highly recommend burning a Live CD of the new release and thoroughly testing it, before upgrading. If there are any bugs/problems/incompatibilities with your hardware, it is better to know about them *before* trying to upgrade.

If you are super-conservative, and have enough hard drive space, you can set up a "dual boot," keeping your perfectly-working Hardy install on its own partition and booting Lucid side-by-side. Also remember that Hardy will be fully supported through April 2011, so you don't need to upgrade immediately when Lucid is released. Many users wait a month, 6 months, even a year to give Canonical a chance to fix the inevitable bugs of a new release.

Good luck! :)

---

### Post by rolnics on 2010-04-16
To be honest with you, unless you're really have major problems with Heron then I would hold fire, especially if you haven't got another working system to fall back on.

In answer to your questions though:-

1) I would go for a clean install with a seperate /home, this will make the installion of future releases easier and it will allow you to keep your settings(or most) when upgrading etc. Although I've got an spare HD in my machine at the moment running 9.10 so I'm going to copy those partitions over the weekend and try the upgrade on one of them and see what happens. But my install of Heron is staying for a week or two after 10.04 is launched.

2) Personally I would download and run the live-cd that's probably the only true way on answering that one as everyone's pc is slightly different.

3) I've not 100% sure on this, if upgrading then it sure, but perhaps another someone else can answer that one better, if more confidence.

4) I honestly don't know as I haven't got that program installed.

But all that answered, I would leave 8.04 at least until the first week is over! At least the servers won't be liable to break due to the extra demands placed on them!

---

### Post by Rifester on 2010-04-16
This is something I have often wondered.... What is the success rate of the LTS user during the upgrade process?   Is this tested before the next LTS is released?  I

---

### Post by Alex82 on 2010-04-19
Thanks for all of the replies, I think I will stick with hardy for a while before burning a live cd to test out lucid and if it works ok I will go for a full clean install and start afresh.

---

### Post by sandyd on 2010-04-19
> **MRife said:**
> This is something I have often wondered.... What is the success rate of the LTS user during the upgrade process?   Is this tested before the next LTS is released?  I
the sucess rate is undefined, because a lot of people end up getting a partial upgrade (like me) and then we just install fresh

---

### Post by muteXe on 2010-04-19
I went from 32bit 8.04 to 64bit 10.04 last night. I did a fresh install though. Apart from a few grub2 oddities which i intend to fix tonight, i'm rather impressed with it :)

I normally back up my /home and some config files, then copy all the files back afterwards.

I have tried upgrading in the past and personally it's never gone well with me. But that could just be me doing something idiotic.

---

### Post by Gaweph on 2010-04-19
If your home folder is on a separate partition, then you wont have to loose anything, just tell the new install where you current home drive is.

This means that when you boot into your new system, all of your program settings (wine, pidgin etc.. will be already available.

If you don't have a home partition separate from the root install, then I would suggest making one this time.

My usual hard drive set up is:

50GB for /
2Gb for Swap
the rest for /home

Then whenever you reinstall you just use the same /home every time.

If you curent dont have a seperate home partition, then you can move your old /home/username files to your new one after install, thus savign all of your settings.

Gaw

---

### Post by Kellemora on 2010-04-19
Well, after 3 good installs, I hit a really bad one!

Boot, Grub appears, can boot the old distro 8.04 OK and the Doze FWIW:
But when you select Lucid, it starts to boot then crashes so bad you have to unplug the computer to get a cold boot up back into grub.

In checking the hard drive, looks like everything is there EXCEPT /home disappeared and a home folder appears on the system partition.  However, my /home/gary folder appears in what was once my original /home but it's empty.

I think I know what happened there!  I hit the checkbox to format /home to ext3 doh!  No biggie, no data lost as I use a stand alone file server.

OK, I tried installing 8.04 but not all the updates.  8.04 ran just fine.
Did an upgrade from terminal which reinstalled Lucid from the web.  Not bad, under 45 minutes.  However, same problem on boot up.  Grub opens, all the distro's except Lucid work just fine.  Computer locks up tighter than a drum instead of booting into Lucid.  yes I tried Recovery, same problem.  From the old 8.04 install, I can look at the partitions and find all the files.  So just maybe I won't have to install it again for the 3rd time.  I just need to figure out which file is corrupt.
None appear as corrupt using Gparted to check them.

Any ideas, I'm all ears!

TTUL
Gary

---

### Post by mal1958 on 2010-04-19
I had no problems going from 9.04 to 9.10 via the update online thing.  But I did prepare before hand.  9.04 uses Grub .97 or something, while 9.10 uses grub 2 (translates out to 1.96 or such). if you keep the old grub and upgrade to either 9.10 or higher from 9.04 or lower this is a recipe for disaster.  

  I removed the old grub and then installed the new version before I upgraded.  All my old settings were kept and I am still running smoothly.  There are a few Tutorials on the forum here that explain how to change the Grub boot loader, and you can search them out.  Also,  a user did an upgrade with-out redoing the grub and he/she is now going through more he** then trying to get Windows to behave.  He/she is trying to rebuild their boot loader from scratch.  

While I have no real experience with 10.04 yet, I thought that I would put that warning out there.  I believe that 10.04 uses Grub 2 and if so, then you will either have to remove then reinstall grub From the .97 (or whatever) to the Grub 2 (1.96 I believe)  or do a full clean install.

Mike

---

### Post by Georgia boy on 2010-04-20
I also have a question on going from Hardy to Lucid. I'm dual booting, have only been back to Windows about five times since installing Ubuntu. When I set up dual boot I followed some tutorials and Youtube videos. Didn't set up a home root. Don't have anything important to worry about on my system. All music has been transfered to CDs', pictures have been forwarded to another account.What I'm wanting to do is a complete install this time round. So, I know that I have to download and burn a Live CD, test and make sure that Lucid plays nice with my PC. What I'm wondering is if they get along together and I do a complete install will it do a wipe out of the HD and go from scratch thus removing the Hardy and Windows? 
Sorry, might sound stupid but I want to know if it will be a brand new install with no left over mess from the previous two(Hardy & Windows).Just tell it to use whole HD and let it ride right?

Thanks

Tom

---

### Post by t0p on 2010-04-20
**Georgia boy**: If you do a fresh install, you will be asked if you want to use the entire disk. If you choose that option, the whole disk will be reformatted, including the Windows partition. Make sure you back up all important files before you begin your install.

---

### Post by Kellemora on 2010-04-20
I've now downloaded 3 copies each of Lucid I386 and X64.
Burned 15 disks, 8 work on other machines and Lucid loads just fine.
The other 7 disks are coasters.  Overburns, underbuffers, checksums didn't match, etc.
Had no problems until I tried Lucid on the newer computers.
I even tried installing 8.04 Hardy, which installed and works just fine, and used on-line upgrade, still have the same problem.
Computer boots into Grub just fine, selects the Windows partition just fine, selects the original Hardy install just fine, but when I try Lucid, it flat out locks up the computer.

As far as Grub goes, whatever version of Grub was on the older computers is probably still the same grub originally installed and Lucid was just added to the list.  In most cases, I used the Partition that had CentOS and reformatted that partition to install Lucid.

On a newer machine, we started with brand new 250 gig sata drive, nothing on it, partitioned it out, installed the Doze, went fine, installed Hardy, went fine, installed Lucid, and upon boot up, after Grub, selecting Lucid (all 4 options) we get as far as a few errors showing UUID wrong, etc. then it stops at initrfa or something like that, and the computer locks up to the point it requires a cold boot to get it going again.

The fact I installed Lucid on other machines without a problem, should indicate the CD's I'm using are OK.  Even did 4 reinstalls to test them.
Ran a Compare program and they match perfectly.

One thing I did learn is you cannot install Hardy and NOT get the 345 updates, then install Lucid.  You MUST get all 345 updates for Hardy in order for Lucid to install from the network (internet install).....

Guess I just wait now until they come up with the final release!

I like Hardy, it's never given me any problems, once I got all the hardware humming along nicely.  I keep up with updates and new kernels as they come out!  I'm not savvy enough about Linux to understand why they have 6 month upgrades on the non-LTS versions or why (other than they quit supporting Hardy next year) one needs to update, unless they are building a new computer with new hardware.  
Up until the Frau made me dump my old machines collecting dust, I still had some ancient 286 machines, but several Doze95 machines that worked great except CGA monitors, no can find anymore, so it got dumped. 3 win98 machines just got dismantled and dumped with parts going to recycle places.  And this week I will be dumping some older Compaq's with only 256meg memory sticks.  Adding memory to them cost more than new computers.
I have brand new Asus Mobo's sitting here with Athlon dual core CPU's to slap in some of the old cases I will be retiring the mobos in them, due to small aggravations with the on-board peripherals.
At 62 years old and semi-retired, the frau doesn't see my need to be running 5 to 8 computers all day, she would rather I attack the pile of honey do lists, hi hi........

Maybe Lucid won't run on a cheap **** Sempron +3400 200mHz chip?
Don't blame me, I only buy AMD Athlon, can't help what others toss my way!

TTUL
Gary

---

### Post by Georgia boy on 2010-04-20
Thanks tOp. Thought so. Just wanted to verify so that when the time comes I know what to expect.

Tom

---

