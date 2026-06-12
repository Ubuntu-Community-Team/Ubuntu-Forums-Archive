---
title: "Should install Vista or Ubuntu on a Dual boot machine?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Robert98374 on 2009-02-06
Should install Vista or Ubuntu on a Dual boot machine?

---

### Post by fooman on 2009-02-06
now thats a silly question to ask in the *ubuntu* forums. ;)

since you will be using 2 operating systems in a dual-boot enviroment....why not ubuntu *plus* vista ?

if your asking which one to install *first*....its usually recommended to install windows before linux.

---

### Post by Piraja on 2009-02-06
> **Robert98374 said:**
> Should install Vista or Ubuntu on a Dual boot machine?
Could you clarify your question please?

---

### Post by Robert98374 on 2009-02-06
Basically i am going to be making a dual boot machine but i am having issues with going into ubuntu and trying to format a partion that i had windows leave alone so i could install ubuntu on it. And i was wondering if there should be an order in which need to install them so it would run as smooth as possible?

---

### Post by bwang on 2009-02-06
Install Vista first, then Ubuntu. Otherwise, the Vista MBR will overwrite GRUB, leaving you unable to boot into Ubuntu.

---

### Post by TheLions on 2009-02-06
but don't let vista take your entire drive while partitioning drive in vista installer!

---

### Post by Kellemora on 2009-02-06
Hi Robert

Forget about Vista and get either XP-Pro or Windows7beta to load onto your first partition.
Make an extended 2nd partition and make a partition for Ubuntu in it, and another separate partition inside the extended partition for /home and for swap.
That keeps /home safe if you play around with the distro's later.

TTUL
Gary

---

### Post by theozzlives on 2009-02-06
> **Kellemora said:**
> Hi Robert

Forget about Vista and get either XP-Pro or Windows7beta to load onto your first partition.
Make an extended 2nd partition and make a partition for Ubuntu in it, and another separate partition inside the extended partition for /home and for swap.
That keeps /home safe if you play around with the distro's later.

TTUL
Gary

From what I've seen, Windows 7 is a Vista fix.... I'd do the Beta or wait for the final release of Windows 7. Ubuntu is strong though.

---

### Post by Robert98374 on 2009-02-06
> **Kellemora said:**
> Hi Robert

Forget about Vista and get either XP-Pro or Windows7beta to load onto your first partition.
Make an extended 2nd partition and make a partition for Ubuntu in it, and another separate partition inside the extended partition for /home and for swap.
That keeps /home safe if you play around with the distro's later.

TTUL
Gary

Like i am going to be dedicating 25 gigs of HD space for ubuntu, so make a partition for /home and install Ubuntu to the other?

---

### Post by Spherical on 2009-02-06
I agree with Kelleroma, get XP-Pro or 7 Beta.
I'm running 7 Beta from this machine, and I like it 10 times better than Vista (which runs on my laptop)

Easiest is to install Windows, but make sure you make a partition which you'll be able to use for your Linux installation later.
That eases the stuff for Windows a bit. And, preferably, install Linux directly on the second partition, where Windows is on the first (This because Windows can run into errors when running on a non-primary partition).

Further, a simple advice:
Get 2 OS disks, primary for Windows, secondary for Linux, your third disk will then be your "dump everything I want here" disk.

At least, that's my preference, that way, Windows can never bug out Linux, or vice-versa.
And, a crashed disk, always still leaves you with a running OS which you can (sometimes a bit complicated, but hey! no complaining) reach.

(yes, my desktop runs on 8 disks, thus I can say this easily :P )

---

### Post by Robert98374 on 2009-02-06
Any big issues with using windows 7 that you have had dual booting so far?

---

### Post by cariboo on 2009-02-06
If all the OP has is Vista it is kind of irresponsible suggesting he try XP or Win7. Win7 is in beta and even if he has a product key it is only good until Aug 2009. From the benchmarks run [here]("http://www.tuxradar.com/content/benchmarked-ubuntu-vs-vista-vs-windows-7"), there really isn't that much difference between Vista and Win7.

Jim

---

### Post by Robert98374 on 2009-02-06
Its not that i don't have a copy of XP,i just already have vista reinstalled and am trying to figure out why i am not able to install Ubuntu in the partition that was left specifically for Ubuntu.

---

### Post by Spherical on 2009-02-06
> **Robert98374 said:**
> Any big issues with using windows 7 that you have had dual booting so far?
Nope, none, unless you install an anti-virus on 7, that'll cause BSoD's.
That's the only problem I've encountered... all anti-virus programs (I got a license for Kaspersky, also tried most free software) have filescan-driver issues.

So far, after running 7 for about well... I think almost 4 months (previous beta's, member of TechNet experts), that's the only bug I've encountered, and it shouldn't be a problem running without one, if you handle your files responsibly.

If you need a 7-key, and you are unable to get one from TechNet or MSDN, gimme a PM, I might be able to help you out.
And finally, never, ever, ever trust a beta-OS with your files, even though I haven't encountered any other serious problems, you might. Thus, always store your private and important data on an another partition (actually, for anybody who reads this, you should do that anyway, saves backing up when reinstalling, or any other OS problems!)

---

### Post by Robert98374 on 2009-02-07
As of right now i am also trying to install with the installation from windows....so i hope this might work.

As for installing multiple HDs... my MoBo only has 1 spot for an IDE cable,so i am kinda limited to that one

If the installation while in windows doesn't work what would be the process to adjusting the MBR so it would pick up Ubuntu and give me an option?

---

### Post by Kellemora on 2009-02-07
Hi Robert

If you have an XP key, from perhaps an older machine that died.
Most REAL computer shops will burn an install disk for you for free!  And what's nice is they don't have all that GARBAGE that comes on Manufacturer OEM Reinstall CD's.  All XP and NO Garbage!

The only thing you have to be careful of is there are many flavors of XP out there and the key ONLY WORKS with the identical flavor.
So if you got stuck with one of the XP releases that sucked canal water, like XP-MCE or XP-PRO-MCE, that key will not work for XP-Home or XP-Pro installs.

But if you are short a key, that same shop that burned the CD for you may have some waste XP keys and if lucky they might let you have one.

Even when I get new computers that have XP on them, I still wipe the drives and install the clean version.  Eliminates about 85% of the headaches associated with OEM machines too!

But now, we are almost totally Ubuntu here, just keep a couple of XP machines around to do simple tasks that are missing in 3rd party drivers.  Like change toner cartridges in the printer is one example.  Although the 3rd party driver is better than the OEM driver in many aspects, those who wrote it must have had toner cartridges that never ran out!  As they made no provision to change out an empty toner cartridge in their driver.  But then too, the driver is written to cover many models, and a few of those have an onboard button you push to change the cartridge.  So maybe they didn't know some are only software changeable?

TTUL
Gary

---

### Post by Robert98374 on 2009-02-08
OKees so what i had to do for it to work, was have the partioner on the live CD and adjust the NTFS space to about 80gs. Grub handles going to winblows without and issue :D

---

