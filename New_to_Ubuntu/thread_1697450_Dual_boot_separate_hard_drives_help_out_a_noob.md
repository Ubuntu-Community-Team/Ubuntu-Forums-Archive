---
title: "Dual boot separate hard drives help out a noob"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Ryanlogic on 2011-02-28
First, Im sure this has been encountered before. But I have limited Internet access right now and from my phone, I'm not able to find the information I'm looking for.  I'm really hoping someone can take a few minutes to walk me through this. I'm not familiar with ubuntu and I read some of the stuff and get confused by all the terminal commands. I can absolutely attempt to do whatever is necesary. Just be patient with me. 

I want my computer to start up and give a choice of operating systems. 

I had ubuntu on one drive and then I disconnected it and connected the second, installed windows 7. made sure it booted up, then reinstalled the ubuntu drive and reset the default boot order to that drive as first. 

I've been encountering two problems at startup.

1. Grub rescue no such device..

2. Loading operating system...

I don't remember which came first. 

Even when I removed the ubuntu drive, windows wouldn't boot up.

I have since tried to reinstall ubuntu from scratch while both drive were plugged in and I get the "loading operating system..." Hangup.  I try re arranging the boot order and I've reinstalled ubuntu several times. I can't get ubuntu to work 

I'm using a crucial c300 SSD for windows and a samsung spinpoint  laptop drive for ubuntu. 
The reason I'm able to swap them around and take them out is because they are housed in a hot swappable quad bay. All the hardware is pretty standard. 

I think I'm just making a stupid mistake

---

### Post by Ryanlogic on 2011-02-28
Also, after installing ubuntu, windows would not boot even when the ubuntu drive was taken out.

I had to redefine boot registry (I think) using some command prompts I found on a different forum.

---

### Post by Hedgehog1 on 2011-02-28
I think the key concept here is this:

When you are installing either OS, make sure the drive for the other OS is removed.

This way, each hard drive can boot by itself.

When you want to select an OS and both drives in inserted, if you do a 'select boot device' using (on my home PC F11, on my work PC F12 - depends on your BIOS), you can arrow to the drive you want to boot from.

I expect you fixed your Windows SSD with a /FixMbr command.

To fix the Ubuntu drive, insert if by itself and startup the computer.  Don't select the windows option in grub, pick the top Ubuntu kernel.

Then in the terminal do a:
```
sudo update-grub
```

That will rebuild the grub menu without the windows option.

If you want to be sure your Ubuntu disk never again shows the Windows disk in the options, please do this in the terminal:
```
cd /etc/grub.d
sudo rm 30_os-prober
```

By removing the 30_os-prober, grub will only ever look at linux on it's own disk drive during future upgrades.  I do this for all the bootable USB Ubuntu memory sticks I have.

***The Hedge***

:KS

*p.s. No love required, but thanks for the offer.  A Hedgehog likes to be asked...*

---

### Post by Ryanlogic on 2011-02-28
Thank you for your reply.

But I do not want to press f12.

Years back I was able to have grub promp a choice at startup. 

I can't even get grub(2?) to show up.

Forgive my noobishness.

---

### Post by Ryanlogic on 2011-02-28
Am I barking up the wrong tree? Bump.

---

### Post by Hedgehog1 on 2011-02-28
Here is the thing; a grub across two disks requires that the two disk stay put.  This is because one disk is really the ONLY boot disk, the other a hanger-on.

So if you never remove them, you can grub across them.

If you do want to remove them one at a time, they have to be stand alone (boot wise) to survive that.

:KS

p.s. Please don't bump more than once every 24 hours (unless your computer is on fire).

---

### Post by Ryanlogic on 2011-02-28
I have no real real desire to remove the boot drives while running I just used the quad bay to save space (sff pc) and open up the possibility of changing out other drives used for data. There is the unfortunate possibility that the boot drives could get switched around while the computer is off. But it's unlikely that I will need to take them out. 

that being said, I'd hate to pop out a drive down the line and not be able to boot.

I have another 5.25inch bay and I'm looking into slim drives and adaptors that accept 2.5inch drives underneath them. In the future it may be wise to mount the two boot drives in a less accessible location.

is it possible to set up my system so that whichever bootdrive is inserted will start the system? what I mean is I can leave a "dead slot" on my drive cage and just toggle between the two drives physically.

I only use windows for casual gaming and Netflix. so if I felt like watching a movie or playing a game I could just swap the Linux drive out for the windows one.

Maybe I'm dreaming. 

sorry for the extra bump.

---

### Post by Ryanlogic on 2011-02-28
> **Hedgehog1 said:**
> So if you never remove them, you can grub across them.

can someone walk me through this? 

Btw. thanks hedgehog!

---

### Post by Ryanlogic on 2011-03-01
?

---

### Post by grahammechanical on 2011-03-01
I suggest that you look again at what hedgehog1 was advising you. I also think that you need to make up your mind what it is that you want to do.

In your third post you say:

> But I do not want to press f12. Years back I was able to have grub promp a choice at startup. 

You seem to be saying that you want to use Grub to choose what drive to boot from.  But as, hedghog1 says Grub has to be installed on one disc. Remove that disc and the other drive may not boot.

In your fifth post you ask this:

> is it possible to set up my system so that whichever bootdrive is inserted will start the system? 

Yes. Hedgehog1 has explained how. But you do not want to press f12.

Can you see the problem that people on the forum have in trying to give you advice.

Regards.

---

### Post by Ryanlogic on 2011-03-02
So much for brainstorming. God forbid I use a forum to gather ideas and weigh my options. And to someone who knows what hedgehog was saying, it may have been obvious that I couldn't hot swap and use grub. But he doesn't make it clear untill later.  When I asked about using a dead drive slot, and physically changing the drives before startup I thought it was clear that I meant without grub, and without having to reprioritize boot sequence or anything else (no f12)  in which case it would be absolutely essential to have only one boot drive in at a time or push f12 at startup. 

Hedgehog was very helpful!  grahammechanical, your attitude is not.

In my case even after installing os on each drive successfully, I was unable to push f12 and successfully boot either.  I fixed windows by resetting the boot sequence (or something) in windows with the imstallation disk using the command prompt therein. That left me with windows and no ubuntu. Using a USB drive, I attempted to reinstall ubuntu while the windows drive was still in hoping to get grub to set itself up across the two drives. Unfortunately, I inconvenienced myself by partitioning the ubuntu drive and installing ubuntu next to itself in hopes that grub would grab all three os because I already had the first ubuntu installation set up and updated, I had been using it for a while without windows.

My solution consisted of reformatting the ubuntu drive via windows and installing ubuntu again in the entire volume. Grub is working just fine and I will make a point not to remove the drives while the machine is on. I lost my updates and software and some other tweaks that I wanted to keep, bit thankfully all my important files are saved elsewhere. 

I need to know one thing though, can the drives be rearranged to different sata ports while the machine is powered off? Or do I need to meticulously make sure they are kept in the same slots? I believe if both of the drives are present it should still load grub and boot just fine thanks to drive letter assignment. But at this point I don't want to risk it untill I know. 

I again apologize for any excessive noobishness, as well as any lack of clarity or decisiveness. this was primarily conducted in haste from a cell phone. If brainstorming and inexperience are not appropriate reasons to enter a forum titled "beginners talk" then please redirect me.

I think ubuntu is developing into quite a nice OS that can and will help people around the world utilize technology and communicate without needing to invest in expensive hardware or software. I can only hope that communities like this will be patient with those like me who are less experienced and rather confused. If I bad been someone in a remote location using a mobile phone to troubleshoot a system with little knowledge and experience it would be quite discouraging to have someone like grahammechanical shoot me down and manipulate my words. Factor in a language barrier or cultural differences and it could have been disastrous. I guess what I'm saying is: keep your eye on the prize. We can't all be experts, some people just want to use a computer. 

and thank you hedgehog1

---

### Post by Hedgehog1 on 2011-03-02
***[SIZE="2"]Oh boy...[/SIZE]***

Ummm - My wife often says to me (when I geek out) doing her 'Tarzan' imitation: **'Me-Human. You-Nerd.'**

It is a separate language based on a number of assumptions.  Sorry about all that...

To your specific question about moving the drives to different SATA ports.  **No.**  Their internal ID is assigned based on the SATA port order (/dev/sda from the first STAT port found occupied, /dev/sdb from the second STAT port found occupied, etc.)

So they are a set in that order as long as they share a GRUB menu.

As to the F12/F11 to select to boot a specific drive - the exact function key varies by every motherboard manufacturer.  I was (again) assuming you already knew that. Sorry.

***The Hedge***

:KS

---

### Post by Ryanlogic on 2011-03-02
In my case it is f12, and I am familiar with such differences. It is wise to mention other possibilities just in case others are not.

---

### Post by mick8985 on 2011-03-02
Whoa whoa whoa, what's going on here.

He has two hard drives 1 with Ubuntu and 1 with Windows.

If he makes the first boot device Ubuntu

Boot device priority.

(*) sda Ubuntu
( ) sdb Windows

on the ubuntu drive he has grub installed, on the windows drive he has the windows boot loader installed, if he removes the Ubuntu drive Windows will still boot.
Because windows will get boot device priority automatically.

If he removes the windows drive the ubuntu drive will retain boot device priority and ubuntu will still boot. Only issue will be that grub will still have an entry for windows and but it will not boot.

---

### Post by Hedgehog1 on 2011-03-02
> **mick8985 said:**
> 
.... if he removes the Ubuntu drive Windows will still boot.
Because windows will get boot device priority automatically.

If he removes the windows drive the ubuntu drive will retain boot device priority and ubuntu will still boot. Only issue will be that grub will still have an entry for windows and but it will not boot.

**mick8985** believes you can pull either hard drive and the other will still boot OK.

He may well be right (a.k.a. ***The Hedge*** is sometimes wrong - ask his wife).

I suppose an empirical test is in order?  Pull the drives with power off, swap their locations, and try to boot. Then try each drive on their own and see if they boot.

Live and learn...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-02
> **mick8985 said:**
> 
**If he removes the windows drive the ubuntu drive will retain boot device priority and ubuntu will still boot**. Only issue will be that grub will still have an entry for windows and but it will not boot.

mick8985,

There is a possible flaw in your Logic. The Ubuntu disk will only boot if it is a bootable drive.  In a standard 2-disk install, the boot block on the fist drive (typically the Windows drive) is the only boot block. Pull it, and the second drive is not able to boot.

However, if both drives are bootable, then I agree that this can be make to work.

:KS

---

### Post by Mark Phelps on 2011-03-03
I have a multi-drive system setup this way for the reason that I need to be able to boot each drive individually at times.

My solution is to have the default BIOS set to boot from the Ubuntu drive.  That way, the GRUB menu comes up, and I can choose which OS.

When there is only one drive connected, the BIOS sees only that one, so not only does it boot, I don't have to do anything to the BIOS.

But, when I connect the other drives back, I DO have to change the BIOS because the default "order" in the BIOS is not the "order" in which I wish the drives to be seen.

So, in THIS case, if each drive is setup to be bootable, as long as only one drive is connected, no BIOS manipulation will be needed.

But if both drives are connected, unless the default BIOS order has the Ubuntu drive first, the BIOS order will have to be changed.

---

### Post by Firem4nJoe on 2011-03-12
My level of Linux expertise: I can lift heavy things.

I am also in this position having installed Ubuntu 10.10 on my slave HDD less than 72 hours ago with XP already on the Master.

Any chance of idiot proof instruction?

Thanks.

---

### Post by Firem4nJoe on 2011-03-12
Oh yeah, and I'm using PATA not SATA. :)

---

