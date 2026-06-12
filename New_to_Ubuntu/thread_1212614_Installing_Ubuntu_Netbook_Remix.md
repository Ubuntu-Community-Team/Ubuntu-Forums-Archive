---
title: "Installing Ubuntu Netbook Remix"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by hypnonebula on 2009-07-13
Hello all,

Firstly I'd like to apologize if this questions have been answered before in this forum...

I need help installing the ubuntu remix for netbook... I'm an absolute beginner in ubuntu... 0 knowledge... 

I recently bought an Asus Eee pc 1000he, with xp prenstalled in it...
the hard drive has already been partitioned to two, with almost equal capacities...

now i've got the usb with ubuntu netbook remix image in it...

do i just proceed the installation on any partition? (I know ubuntu doesn't recognize a partion as c or d... but, i don't know of other ways of asking)

or do I install it in the partition with xp, C  ?

or do i install it in the partition without xp, D  ?

Please, any help would be much appreciated...

ps: someone said that I'll need at least four partitions, if not I will lose all the data in my ubuntu each time I update my ubuntu... is it true?

pps : I would like to keep my xp

ppps : wouldn't partitioning destroy/delete some of my preexisting data?

---

### Post by nhasian on 2009-07-13
probably the easiest thing for you to do is boot into windows, insert the ubuntu usb key and install ubuntu within windows using wubi.  then you dont have to worry about partitions.

---

### Post by earthpigg on 2009-07-14
from amazon,

> XP-Preloaded with _***160G large H.D.D***_. Intel Atom 280 Processor (1.66 GHz, FSB: 667MHz)

plenty of space to do a wubi install, if you aren't to computer savvy.

keep in mind that wubi will make it very difficult, later on, to remove windows XP if you choose to.

if you think that may be an option, then traditional dual boot is the route you want to go:

1) boot from the usb drive
2) follow onscreen directions
    2a) i suggest 80 gb for windows, and the rest ubuntu... for now.

---

### Post by hypnonebula on 2009-07-14
> **earthpigg said:**
> from amazon,



plenty of space to do a wubi install, if you aren't to computer savvy.

keep in mind that wubi will make it very difficult, later on, to remove windows XP if you choose to.

if you think that may be an option, then traditional dual boot is the route you want to go:

1) boot from the usb drive
2) follow onscreen directions
    2a) i suggest 80 gb for windows, and the rest ubuntu... for now.

Thanks for everyone who replied! 


Yeah so that's what i heard about using wubi... I really want to go for the dual boot option for now...

So I guess now I'll install it to the second partition, right?

And would you mind to elaborate on ' for now'?

---

### Post by jrox717 on 2009-07-14
You should be able to change the sizes of your partitions without losing any of your data. Before you change your windows partition though, make sure you defragment it, and ALWAYS back up your important files.
About the 4 partitions... that person is probably suggesting you have one windows partition, one swap partition (only needs to be 1-2 times the size of your RAM, eg if you have 1 gig of RAM you could have 1 to 2 gigs for your swap), a partition for ubuntu mounted at root (/), and a home partition (mouted at /home), which is where you can keep all your personal files. It IS possible to upgrade the distro without having a seperate /home partition, but it's riskier, and if you have a seperate one you can do a clean install instead of an upgrade. That said, as long as you back up your data, it's fine if you don't want to deal with that for now.
Good luck!

---

### Post by hypnonebula on 2009-07-14
> **jrox717 said:**
> You should be able to change the sizes of your partitions without losing any of your data. Before you change your windows partition though, make sure you defragment it, and ALWAYS back up your important files.
About the 4 partitions... that person is probably suggesting you have one windows partition, one swap partition (only needs to be 1-2 times the size of your RAM, eg if you have 1 gig of RAM you could have 1 to 2 gigs for your swap), a partition for ubuntu mounted at root (/), and a home partition (mouted at /home), which is where you can keep all your personal files. It IS possible to upgrade the distro without having a seperate /home partition, but it's riskier, and if you have a seperate one you can do a clean install instead of an upgrade. That said, as long as you back up your data, it's fine if you don't want to deal with that for now.
Good luck!

thanks for the reply,

may be this sounds stupid to you, but I really need to ask this,

how do I mount the partition to home and root? Do i do this before the installation or I can adjust the size of the partition later on?

thanks again!

---

### Post by Sef on 2009-07-14
> may be this sounds stupid to you, but I really need to ask this,

how do I mount the partition to home and root? Do i do this before the installation or I can adjust the size of the partition later on?


You would have to manually paritition the hard drive.  Read [Psychocats]("http://www.psychocats.net/ubuntu/index"), then ask any more questions that you want to.

---

### Post by earthpigg on 2009-07-14
> **hypnonebula said:**
> 
And would you mind to elaborate on ' for now'?

just that a lot of dual-booters, myself included, ended up wiping windows after a few months :P

---

### Post by LewRockwell on 2009-07-14
search for "acer aspire one" and you'll find my commentary in several places regarding my wonderful success partitioning and installing Ubuntu 9.04 Jaunty(full version) AND Puppy Linux for a triple-boot with WinXP Pro SP3

and I've set aside five more partitions for five more *nix distros...

I posted a screenshot of my partition editor yesterday...let me find it...

Here's the thread I posted it in. The only way I can view the attachment is from this thread page so hopefully you can just scroll down to find it:
[http://ubuntuforums.org/showthread.php?t=1212409&page=3](http://ubuntuforums.org/showthread.php?t=1212409&page=3)


.

---

### Post by LewRockwell on 2009-07-14
you'll want to make sure you burn any recovery disks that you're supposed to burn right after you get a windoze machine

then you should look at the hard drive partitioning with something other than windows so you can see if the manufacturer has hidden partitions on the drive

you'll figure it out...just take your time and see what others have done

hey, if I can do all this stuff...anybody can...

.

---

