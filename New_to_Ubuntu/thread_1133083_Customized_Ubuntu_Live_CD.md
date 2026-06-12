---
title: "Customized Ubuntu Live CD"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Didius Falco on 2009-04-22
Goal: To make an Ubuntu 8.10 Live CD that contains some utilities that don't come "stock" with Ubuntu. I want to add Partimage, the latest version of Gparted, and a few other system utilities.

I've run Remastersys a few times on my current setup, but I just can't get the *.iso smaller than 950 Megs.

What I'd like to do is install a second copy of Ubuntu 8.10 to a separate partition, install just the utilities I'm after and use Remastersys to make an *.iso that will fit on one CD, and then deleted the second copy after I've tested the CD.

I'm familiar (enough) with the Grub issues that I can fix Grub after deleting the second install, so that shouldn't be a problem.

Questions:

Are there any pitfalls to installing a second copy of the same version I need to watch out for?

I have a separate /Home partition that I do not want the second Ubuntu install to use. Will it that be a problem?

Should I use a different username and password, just to be safe?

Are there any trains headed my way that I'm mistaking for the light of day? <G>

Thanks for your time and knowledge.

---

### Post by llamabr on 2009-04-22
> **Didius Falco said:**
> 
Questions:

Are there any pitfalls to installing a second copy of the same version I need to watch out for?

I have a separate /Home partition that I do not want the second Ubuntu install to use. Will it that be a problem?

Should I use a different username and password, just to be safe?

Are there any trains headed my way that I'm mistaking for the light of day? <G>

Thanks for your time and knowledge.

Nope.  Except with number one, you'll want to familiarize yourself with grub and dual booting, but you say that you've done that.  Otherwise, it's just like putting two different distros or whatever on two different partitions.

You could even share the /home between them, if you wanted.

---

### Post by kestrel1 on 2009-04-22
You shouldn't have a problem with a second install. I would partition the drive so that you only have the one partition that would include your /home & not use the seperate /home partition. You can use the same swap partition.

---

### Post by Didius Falco on 2009-04-22
Thanks for the help and reassurance. I just wanted to make sure it wasn't going to screw up my current setup, since the second one will only be around for a few hours before I delete it.

I searched everything I could think of to find out about installing the same version two times, but couldn't find anything.

Thanks again for the help...

On Edit:

It worked! I had to uninstall a bunch of stuff to get the *.iso under 700 megs ( I didn't want to overburn, and I don't currently have a rewritable cd to test with), but I've booted up the cd I made a few times and backed up my default installation.

Now I have a bootable Ubuntu CD that works as a System Rescue disk with a much nicer interface than the usual Rescue CDs have.

I may leave the second installation on the HD for a while longer and try to further refine and personalize the resulting Live CD, but that's just because I'm enjoying learning about the customization process.

Again, thanks for the help, and I'd recommend anyone else that would like a Ubuntu Rescue Disk to try it out for themselves.

---

