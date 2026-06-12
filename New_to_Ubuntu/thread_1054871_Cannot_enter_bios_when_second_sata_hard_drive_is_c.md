---
title: "Cannot enter bios when second sata hard drive is connected !!"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Bigmon on 2009-01-30
Hi !

I know this is not a Ubuntu problem specifically but I wonder if anyone can help. When I connect up a second sata hard drive to my motherboard the computer freezes and I cannot get into the bios. I swopped the two hard drives around and put them on different channels just incase the boot process point towards a certain sata channel. But no luck here. The problem is I cannnot get into bios with the two connected to adjust the boot process (if this is the problem). The new sata hard drive is 500GB - I don't know if this is a problem. I have a KV2 Lite motherboard. I don't think it is a power issue as the second hard drive's power is currently connected as it is only the data cable that is now off and I am here using the computer OK.

Any suggestions !!

---

### Post by blazemore on 2009-01-30
That's an issue with the BIOS.
If you visit your PC/motherboard manufacturers website, they can give you a way to update, or "flash" your BIOS to the latest version.

I accept no responsibility for any damage to your hardware as a result of this tip.

---

### Post by fuzzyk.k on 2009-01-30
i
I agree with blazemore but "flashing" or updating your bios may be risky. Proceed with caution

---

### Post by Bigmon on 2009-01-30
> **blazemore said:**
> That's an issue with the BIOS.
If you visit your PC/motherboard manufacturers website, they can give you a way to update, or "flash" your BIOS to the latest version.

I accept no responsibility for any damage to your hardware as a result of this tip.
Thanks. I'll give that a go !!

---

### Post by blazemore on 2009-01-30
If you can, do it from a floppy, not from within Windows.

---

### Post by 73ckn797 on 2009-01-30
> **Bigmon said:**
> Hi !

I know this is not a Ubuntu problem specifically but I wonder if anyone can help. When I connect up a second sata hard drive to my motherboard the computer freezes and I cannot get into the bios. I swopped the two hard drives around and put them on different channels just incase the boot process point towards a certain sata channel. But no luck here. The problem is I cannnot get into bios with the two connected to adjust the boot process (if this is the problem). The new sata hard drive is 500GB - I don't know if this is a problem. I have a KV2 Lite motherboard. I don't think it is a power issue as the second hard drive's power is currently connected as it is only the data cable that is now off and I am here using the computer OK.

Any suggestions !!

Boot up into BIOS without the second drive connected. There make any changes relating to hard drive configurations such as whether it is a raid setup, SATA, IDE or whatever other options are available. Shut the system down then connect second drive and see what happens. Does the second drive show up in the boot-up summary screen?

In regards to flashing the BIOS. The MB manufacturer list of BIOS updates will describe any changes that have been made to the latest version. I would only update if there is something addressing a problem you are having. If you do flash the BIOS do it through the BIOS flash utility program. Many BIOS flash utilities give options to read the update from either a floppy disk or you may be able to designate a removable flash stick or even a CD.

---

### Post by Bigmon on 2009-01-30
> **73ckn797 said:**
> Boot up into BIOS without the second drive connected. There make any changes relating to hard drive configurations such as whether it is a raid setup, SATA, IDE or whatever other options are available. Shut the system down then connect second drive and see what happens. Does the second drive show up in the boot-up summary screen?

In regards to flashing the BIOS. The MB manufacturer list of BIOS updates will describe any changes that have been made to the latest version. I would only update if there is something addressing a problem you are having. If you do flash the BIOS do it through the BIOS flash utility program. Many BIOS flash utilities give options to read the update from either a floppy disk or you may be able to designate a removable flash stick or even a CD.
I have the boot process with the CD ROM as 1st boot and hard drive 2nd but have always had it this way ? This shouldn't make a difference should it ?

---

### Post by 73ckn797 on 2009-01-30
> **Bigmon said:**
> I have the boot process with the CD ROM as 1st boot and hard drive 2nd but have always had it this way ? This shouldn't make a difference should it ?


I do not think that would matter. I am not talking about boot order but how BIOS sees the second drive (boot order is just a part of this) and how it is configured to operate as mentioned before.

---

### Post by egalvan on 2009-01-30
By "computer freezes" do you mean the computer does not run AT ALL?
Or that it only refuses to enter BIOS?

You said you swapped SATA ports, have you swapped cables as well?

Does the computer boot into BIOS with JUST the problem drive attached??

Have you tried to let the computer run for AT LEAST three minutes to see if it continues?

The drive may be defective...
and the BIOS is attempting to access the drive.
Try, at least once, giving it ten minutes.

And finally,
Does the errant drive work in any other computer?

I hope this list will help.

Gotta go work, be back tomorrow.

ErnestG


OK two more thoughts...

no, being 500GB is not an issue, the BIOS would just see less, if it was limited.

Second, SATA comes in SATA-I and SATA-II flavors. 1.5gb & 3.0gb transfers rates respectively.

SATA-II drives usually have a jumper to make them SATA-I.

Is your mobo SATA-I or SATA-II?
Is your drive SATA-I or SATA-II?

Note, this should NOT be an issue, either...
just throwing out ideas for all to use.

---

### Post by blazemore on 2009-01-30
Had a thought: Some motherboards have special SATA ports for RAID.
Might you have plugged one or other of the disks into this?
If there's two SATA ports next to each other, these might be the best bet, or they have lables printed next to them that could be more descriptive.

---

### Post by Bigmon on 2009-01-30
> **blazemore said:**
> Had a thought: Some motherboards have special SATA ports for RAID.
Might you have plugged one or other of the disks into this?
If there's two SATA ports next to each other, these might be the best bet, or they have lables printed next to them that could be more descriptive.
In the bios with the original hard drive the Sata setting has a choice of ATA or Raid. Has been set to ATA all this time but with a Sata hard drive yet working fine. Do you think that it should be set to raid for 2 sata hard drives to work ?

Thanks for your time

---

### Post by Bigmon on 2009-01-30
Cheers. Seems to be something to do with the new hard drive itself. When I turn on the computer with no hard drives it gets to the screen saying incorrect boot please insert disk etc. (set to boot to CD Drive first). When I turn on the computer with the "dodgy" HDD the computer freezes at the motherboard splash screen. All I can do is turn the power off. I have tried swopping the data cables around but both cables work with the "good" HDD and I have tried the "dodgy" HDD on both sata 1 and 2 connections on the mobo but still hangs the computer.

I have also tried the same process with "boot to HDD first" and the same problem occurs. There only seen to be 2 sata connections on the mobo from what I can see.

---

### Post by Bigmon on 2009-01-30
The motherboard info says Sata 1/2. Not sure if this makes a difference. Think the HDD is Sata II.

---

### Post by Bigmon on 2009-01-30
I havent touched any jumpers on any of the sata hard drives. Without sounding too thick - didn't know I had to do this. I have done a bit of hunting on the net and it seems that you may have to remove jumpers. Would this explain why the bios sees my sata hard drive as "IDE chanel 3". Have never been able to understand this. Works alright though.

---

### Post by fudoki on 2009-01-30
Try this:  Unplug your existing drive.  Plug in the new drive using the same cable.  Can you enter BIOS and see the drive?  If yes, swap the second cable and try both drives.  If yes - bad cable.  If no, the BIOS will probably need to be upgraded, or even the motherboard.  Usually parts with a "Lite" designation have older chipsets, etc.  Make sure your chipset can see 500Gb, some cannot.

If you must update your BIOS, go to the newest version, it will have all previous fixes in it.  If your MB has a "Flash Utility", use it!  Be sure the new drive is NOT CONNECTED when you upgrade the BIOS.  Read ALL the instructions on your MB maker's website BEFORE you do the upgrade.  BIOS upgrades are very simple, but if you miss/skip a step your MB becomes inert.  Printing out the instructions and checking them off step by step is what I do, and I have been building/maintaining computers since 1978...

New MB's are cheap.  Don't risk your data/system if your MB is not up to the task.  Get a MB that is being closed out or has been refurbished if you are tight for cash.  You can usually find one for $25 to $50.  Of course, if you can afford the best, get the best, but I have a couple "refurbs" that cost <$50 and are over 5 years old...

Hope this helps.

fudoki

---

### Post by fudoki on 2009-01-30
> **Bigmon said:**
> I havent touched any jumpers on any of the sata hard drives. Without sounding too thick - didn't know I had to do this. I have done a bit of hunting on the net and it seems that you may have to remove jumpers. Would this explain why the bios sees my sata hard drive as "IDE chanel 3". Have never been able to understand this. Works alright though.

WOW!  Your drive is almost certainly DOA (Dead on Arrival).  This does happen.  But follow up on the BIOS advice that I, and others, have suggested first - before you go to the trouble of an RMA swap; to rule out a mismatch with your BIOS or chipset.  Trying the drive alone on the KG (known good) cable will flush this out quickly.

---

### Post by fudoki on 2009-01-30
In case I am reading your post wrong, and you mean THAT YOUR CURRENT SATA DRIVE is identified as IDE 3, your problem is a MB that needs a BIOS upgrade JUST TO SEE A SATA DRIVE.

If this is the situation, take the new drive, put it back in it's box, and work on getting your existing SATA drive to show up as a SATA drive.

Question:  Is the plug that goes into the hard drive the same kind as goes into the CD drive?

If so, your working drive is not a SATA drive, it is an IDE drive.

If this is the case, get a friend who builds their own computers to take a look at your box and see what she/he says.

fudoki

---

### Post by Bigmon on 2009-01-31
It is definately a sata drive. I built the computer myself. Plugged onto a sata port on the mobo. I didn't really worry about it too much what it came up as in the bios as long as it worked at the time. But do you think that the fact that it is not coming up as a sata drive means the bios would need upgrading. Would the manufacturers make a mobo that had sata ports but not recognise sata drives ? This doesn't explain the fact that it still works on the sata 1 or Sata 2 connections on the motherboard ?
Thanks for your input

---

### Post by blazemore on 2009-02-01
I don't think the problem lies with the motherboard.
After all, the first SATA drive works.

Try booting with just the potentially faulty drive, using a LiveCD. Try mounting the drive and see what happens.

It might be that your drive is DOA (Dead on Arrival), in which case it might be worth getting a replacement from the retailer/manufacturer. If it still doesn't work, flash your BIOS.

Flashing your BIOS should *always* be a last resort.

---

### Post by Bigmon on 2009-02-01
I think I am getting warmer but still not solved the problem. I have at least got into bios with the two hard drives connected to the motherboard. For this to work successfully, the bios must be set to RAID. However, I noticed in the mobo manual that the two sata hard drives can only be used for data storage and not bootable when using the RAID config. This leads me to think that two sata drives are only of any use when using an IDE HDD as the bootable drive and the sata as RAID arrays. 

I cannot, however, get the second sata HDD to get recognised by the BIOS at any stage whatsoever !!! Even when I am in the bios with the two connected. What I have confirmed though is that the mobo certainly recognises SATA HDDs. If I press Tab during start up when the BIOS is set to RAID config. I can get into the RAID menu (this only works with the original bootable sata drive and not my new one - even if the bios is set to boot from DVD drive only). There, the computer tells me that I have not enough disks for a raid config, but it does list the drive as Sata and tells me its size etc.

Will not give in !!!!!!

---

### Post by egalvan on 2009-02-01
> **Bigmon said:**
> However, I noticed in the mobo manual that the two sata hard drives can only be used for data storage and not bootable when using the RAID config. This leads me to think that two sata drives are only of any use when using an IDE HDD as the bootable drive and the sata as RAID arrays. 

No, not true, unless your mobo is extremely unique.
I have NEVER seen this setup.

> I **cannot get the second sata HDD to get recognised by the BIOS at any stage whatsoever** Even in the bios with the two connected. What I have confirmed though is that the mobo certainly recognises SATA HDDs. If I press Tab during start up when the BIOS is set to RAID config. I can get into the RAID menu (this only works with the original bootable sata drive and not my new one - even if the bios is set to boot from DVD drive only). There, the **computer tells me that I have not enough disks for a raid config,** but it does list the drive as Sata and tells me its size etc.


This tells me that new drive is probably dead. 

Is there any way you can try it our on another SATA equiped computer?

If not, and it is under warranty, send it back.

And about your other posts...

> 
Would the manufacturers make a mobo that had sata ports but not recognise sata drives ?
Highly un-likey, but it may be that the mobo may not recognize **SATA-II** drives.

So, many newer SATA-II drives have a jumper block next to the SATA/power connectors.
(It looks the same as the older PATA jumper used to select Master/Slave/Cable-Select.)
The jumper is used to select SATA-I/II mode or SATA-I-mode only.
Some older SATA-I ports are not able to negotiate with newer SATA-II drives, so the jumper locks them in "legacy" mode.

> Would this explain why the bios sees my sata hard drive as "IDE chanel 3". Have never been able to understand this

I don't understand this either, but it may mean that the mobo has a PATA-SATA "bridge".
Dunno, but some older mobo's used this frankenstien's monster.

A thought....

How many PATA connectors are physically on your mobo?
1, 2, 3, 4?
None?

As an aside...
I have a mobo that has four PATA connectors, allowing eight PATA drives.
And it has four SATA connectors, allowing four SATA drives.

Adding two PCI PATA adaptors, jumps this to 16 PATA drives.

Adding two PCI SCSI allows me to boot Linux off 4 15k-rpm drives,
leaving 20 drives (yes twenty) for storage.
It's a HUGE Lian-Li Server Case.
I love it.

ErnestG

---

### Post by tomsk2 on 2009-02-04
Hi all,

Have been reading through this thread with interest, and am having a very similar problem to the one mentioned.

Firstly and most importantly, I am running Windows XP, not UBUNTU, but the problem seems to be so similar, I couldn't help but mention it.

For some time now I have had a 500gb SATA drive on my ECS KV2 Lite, working alongside a 120gb IDE drive.  My IDE drive started to die on me, so I bought another 500gb SATA drive and installed it.  I plugged the second one in, using the second set of leads that came with the motherboard, and successfully partitioned it and got it running. For a couple of days, it ran without a hitch, and then yesterday morning, when I turned on my PC, it refused to get any further... basically it would get stuck on the ACPI Controller message in POST, and refuse to move ahead.  I could get into BIOS on a restart, but the keyboard would not have been loaded, meaning I couldn't check/change settings.

I tried unplugging the new drive and trying with just the original 500gb drive, no change, I tried with an old (working) IDE drive with an OS on it, no change, I tried resetting CMOS using the jumper, small change.

The small change from CMOS reset was that a) It will take me as far as a "Cmos Checksum Error" message, with F1 or Del as options.  If I press F1 (to continue) it'll run POST and hang on ACPI Controller again.  If I press Del (to enter setup) the screen goes black and monitor switches off.  I cannot get into BIOS at ALL any more...

Now I confess I haven't the faintest idea what RAID is or what it does or how to set it, so I've probably been using whatever the alternative is... but I think it's odd that we should BOTH have problems with a new 500gb drive that's a secondary SATA to one that was already working.  Seeing as we've both got the same motherboard, it suggests that perhaps the HDs aren't DOA as some have suggested, as mine worked just fine for two days before displaying exactly the same symptoms.

Any suggestions? Because I'm going bonkers too!

Many thanks in advance.

Additional info:  The motherboard only has two SATA ports, and I'm almost certain they're SATA II, which the drives appear to be also (my two drives are identical models).
Also, during POST the second drive IS recognised, unlike the other poster's drive, but it still won't allow me to get past POST!

---

### Post by Bigmon on 2009-02-04
Hi ! Good to see I'm not the only one ! I have had the Sata HDD checked by the people I purchased it from and they say that there is nothing wrong with it (so they won't take it back). I wanted to swop it with a IDE HDD since I know that the BIOS recognises the two IDE channels no problem. I was fed up with it. But now I'm stuck with it. What I was going to try but have not got round to it yet was starting up the computer with the Ubuntu boot up disc with only the Sata attached and see if it is recognized (this is what a previous post suggested). Have you tried booting up the computer with windows operating system disc with only the 500GB Sata attached ?

Apart from that I am lost !!!!

---

### Post by tomsk2 on 2009-02-04
Unfortunately my PC doesn't even get far enough to try booting up via a Win Xp or Ubuntu disk (which I usually use when Windows goes wobbly).

It doesn't even take me as far as the boot from CD option, constantly hanging on the ACPI Controller check.

The boot sequence is currently CD/HD which worked just fine until yesterday, but now I can't get far enough to initiate either!!

With any luck, someone out there will have a magical easy fix!!

---

### Post by Bigmon on 2009-02-05
I had a similar problem. I left the computer in the frozen state at the ACPI Controller check and came back ten minutes later and it had progressed. Have you left it long enough ?

---

### Post by tomsk2 on 2009-02-05
I had tried leaving it for a while whilst stuck on ACPI Controller, but to be certain I tried again this evening.  I left it for an hour on ACPI, and nothing happened... so I gave up.

Feels like I'm going nowhere fast with this problem!!

---

### Post by drumfire420 on 2009-02-05
In a situation like this there are very few things it can be, because there is very little loaded yet (no drivers, etc). 
That leaves, in order that I usual encounter them (read YMMV)
BIOS settings
Boot loader configuration/installation
Hard drive cables (in my experience SATA cables are much weaker than PATA)
Hard drive malfunction (read "get a new hard drive")
Mother board malfunction  (read "get a new computer")

I would hope that the issue is BIOS settings, or cables.  For the settings, I don't really know enough to tell you what you should put there.  To test for cables, get new different ones, swap out with the old ones, and if it works your problem is solved.  

As far as RAID it defines some ways that you may relate your hard drives, and might be really handy if you do get your system working again.

[ Wikipedia article on RAID]("http://http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks")

I say all this, but there are much smarter and better people on this forum that may have better advice.

---

### Post by Bigmon on 2009-02-06
I wonder if this may be the problem. The 500gb Sata drive that I am having a problem with is 300GB/s. The one that works OK is Sata I - half that speed. Although they are supposed to  be backward compatable, I have found out that there are a few exceptions. Here are a couple of illustrations of this. The first from the Wiki........

Given the importance of backward compatibility between SATA 1.5Gb/s controllers and SATA 3Gb/s devices, SATA/300's autonegotiation sequence is designed to fall back to SATA/150 (1.5 Gbit/s) speed when in communication with such devices. In practice, some older SATA controllers do not properly implement SATA speed negotiation. Affected systems require the user to set the SATA 3Gb/s peripherals to 1.5 Gbit/s mode, generally through the use of a jumper,[6] however some drives lack this jumper. Chipsets known to have this fault include the VIA VT8237 and VT8237R southbridges, and the VIA VT6420 and VT6421L standalone SATA controllers.[7] SiS's 760 and 964 chipsets also initially exhibited this problem, though it can be rectified with an updated SATA controller ROM.[citation needed]

Well I have a VT 8237R southbridge. Does anyone know how to update a SATA controller ROM. And does anyone know anything about this ? This is a comment by someone that bought the said hard drive. Unfortunately I do not have another computer without a "buggy" chipset.

"....There is no jumper on this drive to set the speed down to 1.5 Gb/s. This isn't usually a problem, controllers that do not support 3.0 Gb/s should negotiate 1.5 Gb/s automatically.

However there are a few buggy chipsets that can't do that: VIA and SIS chipsets VT8237, VT8237R, VT6420, VT6421L, SIS760, SIS964 (see Wikipedia). 

If you have one of those then you can still buy this drive if you also have access to a machine without a buggy chipset: 

- First put it in the machine with the non-buggy chipset. 
- Download Hitachi's 'Feature Tool' program, a.k.a. ftool. 
- Reprogram the drive to 1.5 Gb/s using ftool. 
- Then reinstall it in the target machine with the buggy chipset. "

Help appreciated !!!!

---

### Post by _duncan_ on 2009-02-07
> Well I have a VT 8237R southbridge. Does anyone know how to update a SATA controller ROM. And does anyone know anything about this ? This is a comment by someone that bought the said hard drive. Unfortunately I do not have another computer without a "buggy" chipset.

I think you're on the right track.

My friend has a VT8237 southbridge and MSI motherboard (MS-7061). To update the SATA controller, I went to the MSI website and used their live update utility to flash BIOS. Had to do it through Windows-XP. This update solved the problem of SATA drive not being recognized at boot, but still neither XP nor Ubuntu can make use of it.

The original SATA drive my friend had also didn't have facility to put jumpers to scale down to 1.5gb/s. Fortunately he was able to exchange it for a Seagate Barracuda. After scaling down to 1.5 Gb/s the drive worked flawlessly without any change to BIOS settings.

---

### Post by egalvan on 2009-02-09
> **Bigmon said:**
> 

If you have one of those then you can still buy this drive** if you also have access to a machine without a buggy chipset**: 

- First** put it in the machine with the non-buggy chipset**. 
- Download Hitachi's 'Feature Tool' program, a.k.a. ftool. 
- **Reprogram the drive to 1.5 Gb/s using ftool. **
- Then reinstall it in the target machine with the buggy chipset. "

Help appreciated !!!!

Don't know if you are still working on this...
If the sellers will not refund or exchange, maybe they would be willing to do the setup you described above?
they may want to keep a (more-or-less) satisfied customer. :)

ErnestG

---

### Post by Bigmon on 2009-02-12
Hi ! Yes I am working on it still. Got a mate with Sata connections and will send him the drive to try and re program. Good idea though - will use it as a last resort. Let you know how I get on !!!

Hi ! Back again. A friend re-programmed my SATA drive to 1.5 speed through the Hitachi program and now the BIOS recognises the hard drive. Doesn't appear anywhere though when computer booted. At the moment the two hard drives are in IDE mode in the BIOS. The only other option is RAID mode - whereby the new drive does not appear listed if this is used. But as I have said previously, the original hard drive has always been in IDE mode and worked fine. They both appear as "Master" though. This doesn't sound right does it. 

If I go into the RAID option and start to create a RAID array, it tells me that all data will be lost on the disks. Which obviously troubles me. Anyway, I don't really want RAID. I want the HDD just as extra storage. I didn't think that you had the issue with Master/Slave with Sata disks ?

---

### Post by egalvan on 2009-02-19
> **Bigmon said:**
> Hi ! Yes I am working on it still. 

Hi ! Back again. re-programmed  SATA drive to 1.5 speed , the BIOS recognises the drive.
 Doesn't appear anywhere when computer booted.
 the two hard drives are in IDE mode in the BIOS.
 The only other option is RAID mode - whereby the new drive does not appear listed if this is used.
 But as I have said previously, the original hard drive has always been in IDE mode and worked fine. 
They both appear as "Master" though. This doesn't sound right does it. 

If I go into the RAID option and start to create a RAID array, it tells me that all data will be lost on the disks. Which obviously troubles me. I don't  want RAID. I want the HDD as extra storage. I didn't think that you had the issue with Master/Slave with Sata disks ?


OK, just to re-cap...

Your Hitachi SATA-II drive has been set to SATA-I speed.
I assume it's a Hitachi, because you used Hitachi software.
If not, big mistake.

Have you up-dated the BIOS to the latest version available for this mobo?

As for master/slave...
I'm still hazy on this.

I *believe* SATA is strictly numbered.
Don't quote me on this.

The fact tha5t you have them set to IDE may be the issue.

Again, check for an up-date on the BIOS.

In the final analysis, you may need a SATA adapter card.
I have used them to good effect.
Since you don't need to boot, any cheapy one will do.

ErnestG

---

