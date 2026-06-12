---
title: "Why is GRUB2 still a beta version?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-29
I've got 2 grub packages installed on my Ubuntu 9.10 PC - grub-pc and grub-common.

The version is shown as being 1.97~beta4-1ubuntu4.1

What surprises me is the worrying word 'beta'.

Why is the basic repository version of **any** software a beta version??? This seems to me to be even more risky when it's as fundamental a building block of a Linux system as GRUB.

---

### Post by QIII on 2009-12-29
Because there is one lonely and very busy guy developing it, as I understand.

---

### Post by drs305 on 2009-12-29
Grub 2 has a team of developers, but I know there is one guy who does a lot of the Ubuntu stuff. When he goes away for vacation or whatever a lot of the decisions on the Ubuntu side of things slow way down.

My guess is they wanted to introduce G2 before the next release, which will be a LTS (Long Term Support) version. Generally the LTS releases tend to be a bit less "bleeding edge" since the goal is even more stability than normal. With the major changes involved with Grub 2, I can see why they preferred to release it in Karmic even though it was still in beta (for Ubuntu).

There is a 1.97 version of Grub 2, but it hasn't been introduced into the Ubuntu repositories yet. By the way, Grub legacy never made it to 1.0, but remained at 0.97.

And finally, G2 is still being actively worked on, even though it is out of beta for other distros. Things still being developed or tested include theming, RAID, encrypted password protection, and more.

---

### Post by chriswyatt on 2009-12-29
I guess it was deemed safe enough to use.  If it caused too many issues during the alpha/beta stages of Karmic I'm sure they would've just rolled back to GRUB legacy.

---

### Post by ezsit on 2009-12-29
> Why is the basic repository version of any software a beta version???

With Grub2, a.k.a. grub 1.97~beta4-1ubuntu4.1, Debian and Ubuntu are switching to this newer version to support future capabilities and development. We, the users, are the testers and bugs need to be worked out. So, we get to report bugs and help troubleshoot Grub2 while its beta with the hope that our problems will help yield a better Grub2. Grub2, or Grub 1.97.1 which is now the current stable release, should be relatively complete in the near future.

---

### Post by tbessie on 2009-12-31
> **ezsit said:**
> With Grub2, a.k.a. grub 1.97~beta4-1ubuntu4.1, Debian and Ubuntu are switching to this newer version to support future capabilities and development. We, the users, are the testers and bugs need to be worked out. So, we get to report bugs and help troubleshoot Grub2 while its beta with the hope that our problems will help yield a better Grub2. Grub2, or Grub 1.97.1 which is now the current stable release, should be relatively complete in the near future.

Well, the available Ubuntu package for it (the beta version) STILL doesn't work when installed to a logical partition.  I have heard that 1.97.1 fixes this bug, but what it means is that, using the Ubuntu installer for 9.10, there is NO WAY I can install Ubuntu and Grub2 to a logical partition and be able to boot it.  A helluva lousy thing to release if you can't do that, despite the "inadvisability" of installing Grub to a partition instead of the MBR.

- Tim

---

### Post by louieb on 2010-01-01
> **tbessie said:**
> ... (the beta version) STILL doesn't work when installed to a logical partition. 

Had Karmic installed in a logical partition - has since been replaced by Lucid Alpha 1. Both use GRUB2  beta as the boot loader.  The GRUB installer did put out a message that it is a bad idea to be put in the boot sector of a partition. It installed anyway and works just fine.  :P

> What surprises me is the worrying word 'beta'.

A Ubuntu release starts by taking a snapshot of Debian unstable - not stable - not testing - but unstable.  Ubuntu  was one of 1st distributions to replace init with upstart - Jaunty boots a lot faster that Hardy does. Pulse audio replaced the older alsa.   If I wanted a distribution that always uses well tested and stable software I would be running Debian stable or CentOS. :P But the last time I checked CentOS is using firefox 3 linux kernel 2.6.18:)

---

### Post by kansasnoob on 2010-01-01
Just a little FYI:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

So Lucid now has grub2 - 1.97+20091130-1ubuntu1, but it will not be updated in Karmic:

> Colin Watson  wrote on 2009-12-07:  	  #4

By the way, we're not going to do a full update in karmic-proposed; the changes are just too big and very many of them are not required in a stable release. If you want to help to identify individual isolated changes that are needed, feel free (in separate bugs).


---

### Post by matty83 on 2010-01-20
> **chriswyatt said:**
> I guess it was deemed safe enough to use.  If it caused too many issues during the alpha/beta stages of Karmic I'm sure they would've just rolled back to GRUB legacy.

BETA is the final testing stage it tests compatability with diffrent hardware formats ie  diffrent laptops /desktops .

releseing a beta product for a final OS is rediculas but while ubuntu pulls stunts like these microsoft will remain top dog with xp being used by 75% of the world market and ubuntu linux about 2% .sad because fundamentaly ubuntu is far better but developers remain smug and rigid this BETA RELESE  is lazzyness you have a job / deadline you do your job and meet your deadline.

---

### Post by tom.swartz07 on 2010-01-20
To be completely honest, its only really deemed a 'beta' because the developer is working on making it 'look better'

Right now, grub is just as how you see it- plain text, simple colors. The newer releases will eventually look like this [http://www.youtube.com/watch?v=zBCR0jVzMFs](http://www.youtube.com/watch?v=zBCR0jVzMFs)


Dont fret that its only a 'beta', its just a build ON TOP OF the original grub- the version that was really solid.

---

### Post by cenzorrll on 2010-01-20
> **matty83 said:**
> releseing a beta product for a final OS is rediculas but while ubuntu pulls stunts like these microsoft will remain top dog with xp being used by 75% of the world market and ubuntu linux about 2% .sad because fundamentaly ubuntu is far better but developers remain smug and rigid this BETA RELESE  is lazzyness you have a job / deadline you do your job and meet your deadline.

ummm, I think you need to do more research on what exactly GNU/linux is. there's no one company in charge of every package, and small teams don't have the resources to test their releases on every machine, and open source and linux projects are usually VERY strict on what they deem beta and final releases (you can't have a server go down because your release wasn't completely finished).

Microsoft does pull the same stuff, they just hide it better. Anybody who's tried mapping a network drive in windows 7 knows what I'm talking about. (security my donkey)

---

