---
title: "Help a beginner - Ubuntu &amp; HP Omnibook"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by steve99 on 2009-01-12
Hi,
This is first post.

I would like to try out Ubuntu and have an old laptop - HP Omnibook 900B

The Ubuntu Wiki says this works with Unbuntu v5.04 (Hoary) - whatever that is.

I've seached posts and it would seem that at least some versions work but I have come across comments about upgrading from Hardy to Feisty and Xubuntu Dapper. What are all these? 

Should the latest version of Ubuntu work.

Is there a guide for complete Ubuntu dummies to read?

What's edubuntu & kubuntu? :confused:

I've worked with computers all my working life & am very familiar with Windows, but obviously not with Ubuntu and its terminology.

I'm sure I will lots more questions but some answers to these would be most helpful to start with.

thanks in anticipation

steve

---

### Post by oilchangeguy on 2009-01-12
what are the specs of this computer? cpu speed, amount of ram, and hard drive size.

---

### Post by mapes12 on 2009-01-12
> Is there a guide for complete Ubuntu dummies to read?Click the link in my signature file below.

The different version numbers of Ubuntu are just more up to date releases with 8.04LTS being the one with the longest term of support (hence LTS). Unlike windows the newer versions of Ubuntu do not require more and more powerful hardware to be bought to run it. Although you will need a reasonable spec on your machine. To try it out run it from a Live CD. If that works OK then it should be reasonable to assume that a full install to your HDD will work OK as well.

---

### Post by Terl on 2009-01-12
If I found the right model, it has 128 megs of ram and is a P3 processor at 450Mhz.  You may want to try a much lighter weight Linux Distribution with those specs; like DSL for example.  I googled for an HP Omnibook 900B.

---

### Post by steve99 on 2009-01-14
> **Terl said:**
> If I found the right model, it has 128 megs of ram and is a P3 processor at 450Mhz.  You may want to try a much lighter weight Linux Distribution with those specs; like DSL for example.  I googled for an HP Omnibook 900B.

This one has 192Mb RAM, but yes 450Mz P3  processor.

Let me explain what I'm trying to do.

Firstly I would like to explore Linux/Ubuntu as an alternative for Windows. But secondly I have this laptop which runs Windows NT. I only use it occasionally when I go away - mainly word processing to capture thought or edit some documents. As its Windows NT it doesn't support USB so I can't get the docs off via a memory stick. I used to have access to a network I could connect it to where I could strip them off but don't now. So its part a practical reason and part just interest that I would like to do this. I could just put Windows 98 on instead of NT but this way might be more fun.

I would like to retain the Windows NT. HD is 6GB, currently divided into 2GB NTFS for Windows & programs & 4Gb NTFS for data (only uses very little of that). So I could divide 4GB into 2 x 2Gb, one partition for Ubuntu & the other for data (aceesible by both?) and dual boot.

Does that sound feasible?

---

### Post by steve99 on 2009-01-14
> **mapes12 said:**
> Click the link in my signature file below.

The different version numbers of Ubuntu are just more up to date releases with 8.04LTS being the one with the longest term of support (hence LTS). Unlike windows the newer versions of Ubuntu do not require more and more powerful hardware to be bought to run it. Although you will need a reasonable spec on your machine. To try it out run it from a Live CD. If that works OK then it should be reasonable to assume that a full install to your HDD will work OK as well.


Hey the tutorial look great. Thanks for the link. I shall read it carefully. I expect you cover this somewhere in the tutorial but what is a Live CD.

thanks

---

### Post by Terl on 2009-01-14
> **steve99 said:**
> This one has 192Mb RAM, but yes 450Mz P3  processor.

Let me explain what I'm trying to do.

Firstly I would like to explore Linux/Ubuntu as an alternative for Windows. But secondly I have this laptop which runs Windows NT. I only use it occasionally when I go away - mainly word processing to capture thought or edit some documents. As its Windows NT it doesn't support USB so I can't get the docs off via a memory stick. I used to have access to a network I could connect it to where I could strip them off but don't now. So its part a practical reason and part just interest that I would like to do this. I could just put Windows 98 on instead of NT but this way might be more fun.

I would like to retain the Windows NT. HD is 6GB, currently divided into 2GB NTFS for Windows & programs & 4Gb NTFS for data (only uses very little of that). So I could divide 4GB into 2 x 2Gb, one partition for Ubuntu & the other for data (aceesible by both?) and dual boot.

Does that sound feasible?

It does, but, I am not sure that Ubuntu is the best choice for you.  The specs are fairly light on that pc.  You may want to check out Damn Small Linux.  With only 4 gigs of hard drive space with two OS's it will be fun.  You need a small footprint as well as one that will still run well on that laptop.  Try DSL, it will run from disk so you can test it first.  Puppy Linux might be another option.

---

### Post by steve99 on 2009-01-14
> **Terl said:**
> It does, but, I am not sure that Ubuntu is the best choice for you.  The specs are fairly light on that pc.  You may want to check out Damn Small Linux.  With only 4 gigs of hard drive space with two OS's it will be fun.  You need a small footprint as well as one that will still run well on that laptop.  Try DSL, it will run from disk so you can test it first.  Puppy Linux might be another option.

Thanks I'll look into them

What about Xubuntu - I've read that needs less memory than Ubuntu?

---

### Post by Terl on 2009-01-15
I would give it a try.  Xfce desktop is lighter and Xubuntu needs less ram.  It should work just fine.  I misread your hard drive allocation the first go around so I was concerned about space.

---

### Post by mapes12 on 2009-01-15
> Hey the tutorial look great. Thanks for the link. I shall read it carefully. I expect you cover this somewhere in the tutorial but what is a Live CD.The tutorial site isn't mine but one where I and others have found the solutions to many issues in starting out with Ubu.

A Live CD is just a CD you burn from the Ubuntu website from an iso file that can be booted straight from your CD drive without installing it to your HDD. If everything works OK from the Live CD then your machine has demonstrated that it can run Ubu. If you then want to install it to your HDD then just select that option. 

BTW - I agree with other posts about choosing Xubuntu for lightness.

---

### Post by steve99 on 2009-01-17
Hi,

I've bought an Xunbuntu Lived/Instalation CD off e-bay and have been trying it out. However there appears to be a problem. 

I start booting from it in Live CD mode and it comes up with the message:
ACPI: Bios age (1999) fails cutoff (2000), acpi=force is required to enable ACP

It then continues booting and the Xubuntu screen comes up with the bar going back and forth. AFter a while that goes and I get a blank screen with a flashing cursor - and thats it. It just hangs there.

I've disabled the ACP in the Bios but that makes no difference.

I also tried the alternative option for safe graphics mode. It gives the original message + 2 more:
invalid compressed format
and
Kernal panic -not syncing: VFS unable to mount root fs on unknown-block (8,1)

Note- the whole disc is formatted in NTFS (2 partitions). Does Xubuntu in Live CD mode still need access to some disc space for swapping? Could that be the problem?

Any suggestions welcome.

---

### Post by steve99 on 2009-01-18
* Bump * 

Any suggestions?

---

### Post by dollzii on 2009-01-18
Looks like you need to find and install a more recent BIOS. 
Found two threads that you might get some help from;

[https://answers.launchpad.net/ubuntu/+question/6522](https://answers.launchpad.net/ubuntu/+question/6522)

[http://ubuntuforums.org/showthread.php?t=790026](http://ubuntuforums.org/showthread.php?t=790026)

---

