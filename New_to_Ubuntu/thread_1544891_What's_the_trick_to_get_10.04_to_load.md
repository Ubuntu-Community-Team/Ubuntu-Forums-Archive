---
title: "What's the trick to get 10.04 to load?????"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Kellemora on 2010-08-03
Hi Gang

I tried a few months back with no luck.  Waited for the newest releases.

I've spent the past 4 days, downloading and burning CDs, over 25 of them actually.  
I also tried using 3 different brands of USB sticks as well.

I'm running 8.04 64 bit, so tried the 10.04 64 bit, finally gave up on it and downloaded the 32 bit version.  Exactly the same problem.

It loads up to a purple screen with a little man at the bottom with a bar to his left.  Then it CRASHES!

The computers (I've tried it on 4 different computers now too) flat out LOCK UP, the screen goes black and the only way to get it going is to pull the plug and do COLD BOOT to get it back running again.

I've probably burned a dozen 8.04 CD's and every one worked just fine.
And have installed Hardy on at least 15 different computers over the past year, maybe even more.

Apparently 10.04 works for a couple of users!

I've used 5 different burners, at 1x speed and 4x speed and automatic.
I've tried Brasario, Backpack, SpeedyCD, all have the burn as ISO option.

So far all I have is a stack of coaster, and 3 USB sticks that are getting tired of being erased and reloaded as a bootable stick.

I've even tried downloading and installing LIVE on-line, that didn't work either.

What gives guys?????

By the way, it's 4:30AM and I have to be up by 6:30AM bright eyed and bushy tailed, loading Ubuntu should NOT be so problematic.
This is the second time I've spent over 40 hours ATTEMPTING to get 10.04 installed.  

I don't think it's ME since I can reload 8.04 back onto the very computers I tried loading 10.04 on with ZERO PROBLEMS......

TTUL
Gary

---

### Post by alenn on 2010-08-03
when I install Ubuntu there is no purple screen, there is black screen with a man at the bottom, and when I press any key than it shows me list of languages and then just follow instuctions. Maybe you should try to download that ISO image from other computer, or even other network.

---

### Post by sikander3786 on 2010-08-03
Hi.

A very basic question at first. Did you check the MD5SUM of the downloaded images?

Did you try other options like nomodeset and acpi = off etc. Are you even able to get to that step?

Regards.

---

### Post by ankspo71 on 2010-08-03
Hi,
I didn't see you mention trying the alternate Ubuntu install cd. Have you tried that already? You can find them here: [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) 
Hope this helps.

---

### Post by Kellemora on 2010-08-03
THANK YOU ALENN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

NOBODY told me you had to hit ENTER while the little man was up!

Nor did I see it any of the install directions!

However, that only brought up the Language Selection Screen and then the MENU, selecting ANYTHING from the menu causes the same CRASH, this is where I usually check a disk from.

BUT on the bright side, I now have 25 CD's I can try to see if any of them work.

FWIW:  I have downloaded the iso image using three different computers, this computer, my next newest and my wife's brand new machine with the DOZE on it.  All are new enough they boot from USB too.

I also checked the BURN and it matches the downloaded ISO.
I even tried different brands of CD's just in case I had a bad batch.

The automatic mode will burn at around 48x.
I've tried everything below that clear down to 1x and no go.

Well, I need to slap some more cold water in my face and get back to work here.

TTUL
Gary

---

### Post by jimbop99 on 2010-08-03
I feel your pain. My son's computer won't load 10.4 and 9.10 crashes and freezes all the time. My father-in-law's computer wouldn't load 10.4 but I got 9.10 installed via Wubi and it seems to be working well. Both these computers are AMD 754 CPUs on NForce boards. I finally just bought a new motherboard and CPU for my son and hoping for no problems. I have successfully installed 10.4 on my machine and my other son's machine. I love it.

---

### Post by Nick_Jinn on 2010-08-03
I had a similar problem where the screen would go dead and all I could see was blackness past the boot loader. I found a solution. Two actually.


One is to get an older disk, pre karmic, then upgrade....you can upgrade twice, or it might be easier to just set it to 'LTSR only' so you can skip anything that isnt a stable release....make sure to install all the updates and video card drivers.


The other solution is to find a different PC with a different video card....I dont know if one is available, but it might load on a different PC. If so, physically take out the hard drive and swap it....or if you cant get to all the screws, run your SATA cable from one PC to the other. Even laptops share the same SATA cables if its SATA.

Install it there and then do all the updates. Once the updates are installed, swap it back into your old PC and then let it do the adjustments.


This way is actually faster than the first way.

---

### Post by Nick_Jinn on 2010-08-03
I would have decided that its probably not the CD by now.

---

### Post by philinux on 2010-08-03
> **Kellemora said:**
> THANK YOU ALENN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

NOBODY told me you had to hit ENTER while the little man was up!

Nor did I see it any of the install directions!

However, that only brought up the Language Selection Screen and then the MENU, selecting ANYTHING from the menu causes the same CRASH, this is where I usually check a disk from.

BUT on the bright side, I now have 25 CD's I can try to see if any of them work.

FWIW:  I have downloaded the iso image using three different computers, this computer, my next newest and my wife's brand new machine with the DOZE on it.  All are new enough they boot from USB too.

I also checked the BURN and it matches the downloaded ISO.
I even tried different brands of CD's just in case I had a bad batch.

The automatic mode will burn at around 48x.
I've tried everything below that clear down to 1x and no go.

Well, I need to slap some more cold water in my face and get back to work here.

TTUL
Gary

I've been using cheap pcline cdrws for yonks and they've been reused again and again since Feisty. The odd coaster that would not blank but on the whole a success. I always check the md5sum and I always use Check CD for Defects before I attempt to boot them.

---

### Post by alenn on 2010-08-03
> **Kellemora said:**
> THANK YOU ALENN!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

NOBODY told me you had to hit ENTER while the little man was up!

Nor did I see it any of the install directions!

However, that only brought up the Language Selection Screen and then the MENU, selecting ANYTHING from the menu causes the same CRASH, this is where I usually check a disk from.

BUT on the bright side, I now have 25 CD's I can try to see if any of them work.

FWIW:  I have downloaded the iso image using three different computers, this computer, my next newest and my wife's brand new machine with the DOZE on it.  All are new enough they boot from USB too.

I also checked the BURN and it matches the downloaded ISO.
I even tried different brands of CD's just in case I had a bad batch.

The automatic mode will burn at around 48x.
I've tried everything below that clear down to 1x and no go.

Well, I need to slap some more cold water in my face and get back to work here.

TTUL
Gary

I think that you should go to your friend and download ISO image from his compputer, because I believe that something is wrong with you network

---

### Post by Kellemora on 2010-08-03
Hi Gang

Well it turns out there was NOTHING WRONG with the CD's at all!
Nor the USB stick!

I installed 10.04 onto the following machines 3 times each using different CD's I had burned as well as the USB stick.
E-Mach T6524
HP Pavilion 753n (an antique)
Built Up Asus M2n68-AM (two of them)
Built Up BioStar MCP6P M2+

Where I went wrong I guess was I kept trying the Compaq SR1907CL first.
I also tried a Compaq 5420US
and a E-Mach T4165

Ubuntu 8.04 LTS 64bit is currently running on all the machines.
I just wiped out the partition with CentOS to check the installs.

I could have saved burning 25+ disks had I known they were OK and Ubuntu is just not friendly with the other computers for some reason.

By the way, I've tried the on-line update to 10.04 on those machines, that failed also.

Makes no sense to me WHY 8.04 loads and runs just fine, no problems, but 10.04 Locks the computers up!

No biggie losing CentOS I never used it anymore anyhow since 8.04 has been darn near perfect.

I have a compare disks program on the Doze that is currently comparing the known working copies to the rest of the 25+ disks to see if they match, if so, I'll pass them out to some friends.

FWIW:  I have tried separate CD drives to install, so it's not that.  The same external I used to install on the other machines fails on the others.

The OLD HP Pavilion that it installed on without a hitch only has 512 memory, all the rest of the machines are 1 gig and above, the newest are 2 gig as 4 gig was a waste.

If you have any ideas on how to get 10.04 onto the other machines, I'm all ears.

I can't do a disk swap as it messes up the Doze which we use for POS.

TTUL
Gary

---

### Post by Keen101 on 2010-08-03
Wow. Never heard of these kinds of issues in a while. I'd guess that ubuntu doesent yet support your graphics cards out of the box, or maybe some other hardware on those machines.

Hmm... the only suggestion is to try Ubuntu Derivatives, and see if they have better driver support. Maybe Linuxmint?

ie: Linuxmint, Gos, ect....

---

### Post by JKyleOKC on 2010-08-03
I've been having a similar problem installing 10.04, but finally discovered that it was simply a lack of patience on my part!

Specifically, by hitting ESC when the screen is black, I get the traditional text stream of messages. The first dozen or so lines, however, are reporting failure of various attempts by the boot routines to determine what is going on!

Eventually, it reports that it's generating locales, and that it has finished doing so. Then come a few more failures, and finally it launches into a more-or-less normal boot process.

Had I not hit ESC to get the reports, it would simply have stayed on the black screen for a quarter-hour or so while going through all the contortions before getting to the final boot.

FWIW, I've experienced this with both Ubuntu and Xubuntu live CDs, and on a 2009-model Compaq mini-tower and a 2005-vintage custom-built box with Pentium-4 CPU. Both boxes have Nvidia video and plenty of RAM (3 GB on the Compaq, 2 GB on the P4). I suspect it has to do with the attempts to speed up booting. Once it gets to the actual boot, it goes quite rapidly -- but getting there takes far longer than the old 8.04 "slow" boot routines!

---

### Post by Nick_Jinn on 2010-08-04
Told you so.

---

### Post by linux18 on 2010-08-04
You can try my distro (see sig) it's mostly the text installer with a few modifications and a 225MB smaller ISO. after it installs just grab your choice of ubuntu flavored desktop environment ( lubuntu-desktop, xubuntu-desktop, ubuntu-desktop, or kubuntu-desktop)

---

### Post by Gene_J on 2010-08-04
Of the dozen or so machines I have installed 10.04 on, only one time have I encountered the problem stated here. Most of the time the alternate install has worked fine. The one time nothing worked, I just put the hard drive temporarily in a machine I knew would load 10.04 fine and then placed the hard drive back in the problem machine after loading 10.04 on it. Everything started fine and it has been running flawless ever since. I think it is a hardware issue with some boards.

---

### Post by Kellemora on 2010-08-04
Hi Guy's  I don't think TIME is the issue here, I let it sit all night trying to install, mainly because I had forgotten and left it in that mode.

I'm going to try pulling the HD and putting it into a new computer and installing it there, then putting it back to see what happens.

I'm sorta glad I made almost all of my computers triple boot systems!
That way I can delete the old CentOS I don't use and still keep the Doze and 8.04 up and running on each.
That's why I didn't think I could pull the hard drive and drop it into another machine, but if I bypass the Doze and boot with GParted and then the install disk, it don't try changing anything on the other partitions.

TTUL
Gary

---

### Post by Nick_Jinn on 2010-08-07
It worked for me.

---

