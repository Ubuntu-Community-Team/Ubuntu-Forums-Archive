---
title: "First time Ubuntu user needs help"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by geordiepaul2001 on 2010-01-13
Hi all,

Recently my ACER laptop came a cropper due to a known fault whereby if a Windows 7 32 bit operating system is forced to shutdown, it will not boot back up.
Having failed to boot from Winpe discs etc, I came across Ubuntu and managed to boot from it and recover the photos etc from my hard drive.
Ubuntu tells me 'Had disc has many bad sectors'.

Am I able to repair or remove them from within Ubuntu?

I am an experienced computer user but only of the windows variety, I am however going to dual boot my system once its repaired (would just keep Ubuntu but the Wife has only just got the hang of Windows).

Any help would be greatfully appreciated.

Paul

---

### Post by x33a on 2010-01-13
bad sector means there is physical damage to the drive. i don't know of any utility that can fix bad sectors. if the number of bad sectors is high, you'll have to buy a new drive. in the meanwhile, keep everything backed up.

---

### Post by mörgæs on 2010-01-13
With such a machine I would do a clean install of Ubuntu (single boot), wiping any trace of Windows. After that I would check the hard drive from Ubuntu, to see in how bad shape it is.

After that you can decide whether you will install dual boot on the drive or buy a new one.

---

### Post by geordiepaul2001 on 2010-01-13
Thanks for the quick reply.

As the laptop is only 3 months old, who will the repair charge fall with as its still under warranty?
I bought from ebuyer.co.uk, however its an acer laptop, but the microsoft operating system that went belly up.
Hot a feeling I will be passed from pillar to post.

Paul

---

### Post by audiomick on 2010-01-13
Hallo.
I don't know how much basis there is in this, but I have seen a few posts lately that indicate that some people have been getting bad sector messages that are almost certainly erroneous.
Try searching the forum for "bad sectors" and see what turns up.

---

### Post by geordiepaul2001 on 2010-01-13
Thanks for that guys.
I am running HDD Regenerator to see if the bad sectors show on that also.

---

### Post by x33a on 2010-01-13
> **mörgæs said:**
> With such a machine I would do a clean install of Ubuntu (single boot), wiping any trace of Windows. After that I would check the hard drive from Ubuntu, to see in how bad shape it is.

After that you can decide whether you will install dual boot on the drive or buy a new one.

That wouldn't been the ideal solution as installing windows later will wipe out grub, and that'll only add to the problems of a newbie.

> **geordiepaul2001 said:**
> Thanks for the quick reply.

As the laptop is only 3 months old, who will the repair charge fall with as its still under warranty?
I bought from ebuyer.co.uk, however its an acer laptop, but the microsoft operating system that went belly up.
Hot a feeling I will be passed from pillar to post.

Paul
if you do need take it to the dealer/seller, i would advise you to remove ubuntu first, and install windows, since some dealers/companies claim that installing linux voids the warranty.

---

### Post by zkriesse on 2010-01-13
Bad Sectors are not good as you most likely know. Just be careful with your data is all I can say. Also, if it proves to be to much of an issue you'll most likely have to purchase a new drive.

---

### Post by geordiepaul2001 on 2010-01-13
So far I am 2.35% of the way through and I have 59 bad sectors and 43 delays.

I can use the regen tool which may provide a work around but I'm tempted to just use the warranty and hope they agree and provide a new hard drive.

---

### Post by TBABill on 2010-01-13
If you are running Karmic, that's a common and invalid alert. Many people, myself included, had the alert and attempted to take corrective steps before finding out it was just a glitch. If you get your Win7 running again, or use a disk checker while running a LiveCD, you will find your drive is likely just fine. I don't know what causes it, but running updates to your install of Ubuntu will probably clear the problem. Mine went away after installing then allowing it to update.
 
Good luck...hoping it's not a real bad disk.

---

### Post by geordiepaul2001 on 2010-01-13
What is karmic?

I haven't installed ubuntu, I have booted from the cd - the option which does not change your computer.

---

### Post by nothingspecial on 2010-01-13
Karmic is the latest version of Ubuntu. So if you downloaded the latest live disk, that is what you are using.

I can also confirm the bad disk bug. My laptop has been reporting it since I first installed karmic. No problems yet.

Keep everything backed up though, just incase.

---

### Post by geordiepaul2001 on 2010-01-13
Ah ok.
I am running hdd regenerator from the hirens boot cd, surely if this says I have bad sectors then it must be correct

---

### Post by nothingspecial on 2010-01-13
> **geordiepaul2001 said:**
> Ah ok.
I am running hdd regenerator from the hirens boot cd, surely if this says I have bad sectors then it must be correct

I don`t know what that is, but if it is a linux program using the same backend as the utility on the live cd then not necessarily.

If it is a completely seperate program then probably, yes.

---

### Post by audiomick on 2010-01-13
Hallo.
There is this
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

I haven't used this, but I believe you should be able to download and use it even from the live CD. From what I have read about it here, it is something that uses the HD's own tools to check with.
It would give you another opinion, at least.

---

### Post by x33a on 2010-01-13
> **nothingspecial said:**
> I don`t know what that is, but if it is a linux program using the same backend as the utility on the live cd then not necessarily.

If it is a completely seperate program then probably, yes.

Hiren's boot disc is a windows based utility disc (though it is considered warez), and hdd regenrator is a win based software. so i suppose, if it shows up errors, then it should be correct.

To the original poster, also try the diagnostic utility from the manufacturer of your hard drive. for seagate drives, it is seatools.

---

### Post by anubis2497 on 2010-01-13
i agree with [ZachK_]("http://ubuntuforums.org/member.php?u=883479") but a good idea might be to download a copy of hirens boot cd and use it to check and diagnose your system.

---

### Post by geordiepaul2001 on 2010-01-14
Just to update that ACER have said it may need to be returned under warranty but will charge about £70.00 if its found to be a software fault.
The diagnostic tests showed up 1686 bad sectors.

I am tempted to just run the repair tool (I know they can't actually be repaired) and see if the machine works from there.

Thoughts anyone?

---

### Post by x33a on 2010-01-14
it's almost definitely a hardware fault. just to be sure, run a scan with spin rite 6.0, it is within hiren's disc if i remember correctly.

---

### Post by xeross on 2010-01-14
Acer doesn't have the right to charge you 70 bucks if you mistake a software fault for a hardware fault afaik.

---

### Post by anubis2497 on 2010-01-16
aperently they do but if its a hardware fault i would recomond just trying to clone your hardrive with a copy of nortin ghost or somthing if possible and purchassing a new harddrive and cloneing it to the new harddisk and if ur using a netbook u will probably have to make a bootable usb of the disk or iso image i would recomend u net bootin for that if that dosent wrok google will help. ^_^

---

### Post by admiralspark on 2010-01-16
Heh, I've been in this situation before, the only gripe I've ever had with my Compaq is that the harddrive quit on me maybe three and a half months after I'd purchased it. From what I've heard from other Acer users is that they tend to be like Compaq's: cheap, entry-level products using cheap, entry-level hardware. It sounds like your HDD is having serious physical problems, and you should take full advantage of the manufacturer's warranty. Their tests will undoubtedly pick up the same messages you're getting from your diagnostics.

If you're trying to save your data, I suggest using the Ubuntu LiveCD (since you already have it) to boot into your computer and see if you can access the harddrive from there (it should be listed under the Places tab). If you can pull it up, copy everything you want/can onto a USB stick. 
There are professional tools that will work more effectively than that, but they've got a hefty price tag  ;)

---

### Post by Muskegman on 2010-01-16
I have an Acer 4520 laptop and when i was installing Karmic for the first time I also got the " bad sectors found problem" definatley is a bug of some sort because i ignored it and carried on installing. I have been using my laptop with Karmic on it trouble free now since the install with no problems what so ever.

I would not rush out and buy a new hard drive yet, try doing a clean install of karmic first and ignore the bad sector bug.

---

### Post by houseworkshy on 2010-01-16
There is another live linux cd, also free, which may be of use to you.  It is called puppy linux and can be loaded to ram after which one can eject the cd.  This is handy as it allows you to use the cd/dvd drive to back up to dvd's or cd's...much cheaper than getting lots of usb sticks.

---

