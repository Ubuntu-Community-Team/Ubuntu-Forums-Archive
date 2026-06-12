---
title: "Claen install advice"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Garthhh on 2009-11-25
I installed 8,04 on an old desktop of questionable Quality, which would freeze up at pre boot. So I installed the HDD & CD in what was to be my donor machine
DEll optiplex GX1
300g hz
500 mb ram
40g HDD Maxtor
having various issues, mostly sound

I would like to do a new install, but haven't been able to do the search in such a way as to get a good idea of how to do this?

I have an install CD[ version 8.04 i386 desktop], that got me up & running.
But I see now that I need to set up as a server so I can use this machine to print & be the home for my music collection which is on a Seagate go 250g USB external hard drive.

I would prefer to just download a file & do it all electronically.  I don't see the partition manager in system>admin & don't have any files here, so I don't need a back up.

This machine is my test bed, I've been playing around with synaptic & terminal & am getting the hang of things...

A leg up would be most welcome

Can't figure out how to fix the typo in the title LOL

---

### Post by arnab_das on 2009-11-25
you could check this:

[http://exploreubuntu.wordpress.com/2009/11/17/install-ubuntu/](http://exploreubuntu.wordpress.com/2009/11/17/install-ubuntu/)

---

### Post by Paqman on 2009-11-25
> **Garthhh said:**
> 
But I see now that I need to set up as a server so I can use this machine to print & be the home for my music collection which is on a Seagate go 250g USB external hard drive.


You could set it up as a server, but it's not essential to do these two things.

I'd just install with the normal LiveCD you've got. Just boot up from the disk, hit "install" and follow the prompts.

---

### Post by Garthhh on 2009-11-25
I'm unemployed & only have a couple of CD's so I would like to do it all without burning a new CD, yet need a server install this time.

---

### Post by Garthhh on 2009-11-25
Samba won't work because I can't change the server setting since that option doesn't exist?
I need to be able to see the ex HDD from 2 other windows [1xp, 1vista] machine on my home network, I can see them, but they can't see me?

---

### Post by Paqman on 2009-11-25
> **Garthhh said:**
> I'm unemployed & only have a couple of CD's so I would like to do it all without burning a new CD, yet need a server install this time.

If all you've got is a desktop LiveCD then you could install the desktop system, install the server packages you need, then remove and desktop bits you didn't want. The desktop and server systems use the same repos. It'd be a bit of a faff, but not at all hard to do.

One option that would involve burning a CD: burn the minimal ISO. Then you'd have a single CD that could install _any_ type of Ubuntu system (X/K/Ubuntu, server/desktop, etc, etc). Sure, it'd mean burning a disk, but it'd be the last disk you ever needed ;)

---

### Post by Garthhh on 2009-11-25
Thanks Paqman,
I got stuck on the server bits on this thread:
[http://ubuntuforums.org/showthread.php?t=1334490](http://ubuntuforums.org/showthread.php?t=1334490)
I wouldn't mind making a new partition, if that would let me do a fresh install & go back & delete this seemingly corrupted install... no sound, beta of audacity i can't seem to get rid of, rythmbox can't seem to find anything but the titles of my music library.  
If I were dealing with a XP machine I would back up & wipe back to factory settings.:D

I don't have to do a fresh install, but I notice dell machines seem to have their own unique issues for linux, so it would probably be better to start from a clean slate, with the correct sort of install to increase my chances of success.

how about just a bit more direction on burning a minimal iso...

---

### Post by Paqman on 2009-11-26
> **Garthhh said:**
> Thanks Paqman,
I got stuck on the server bits on this thread:
[http://ubuntuforums.org/showthread.php?t=1334490](http://ubuntuforums.org/showthread.php?t=1334490)
I wouldn't mind making a new partition, if that would let me do a fresh install & go back & delete this seemingly corrupted install... 


You don't need to create a partition for that, just install over the top of your current one.

> 
how about just a bit more direction on burning a minimal iso...

Sure, you can download it from here: [Ubuntu Minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD"). Burn it to a disk just like you did for the LiveCD, and boot up into it. It's a text based installer, but not difficult to use. You'll be given a list of many different types of setup you can choose from (desktop, file server, web server, etc)

---

### Post by Garthhh on 2009-11-28
That's a bust
I end up on the command line running from room to room typing in code that doesn't work [& can't even find a mad smiley].
So i threw in the desktop iso back in

---

### Post by Garthhh on 2009-11-28
when I was installing, i was promised the opportunity, to choose more than one package, But couldn't quite get there, & the real time download took overnight, to even get back to that point.... & I'm not seeing the advantage, since I can't seem to find a repository of the code, let alone how I would access when I'm stuck in commandline world.. 
I don't even know what I trying for at this point, by doing a minimal...
I need this thing to run audacity, so I can import music, be able to see this machine from my other 2 windows machines & occasionally print a page or so.
Rant over;)
Please help

---

### Post by Bartender on 2009-11-28
Yeah, I was gonna say you're not gonna like the server version but you found that out for yourself...

---

### Post by Garthhh on 2009-11-28
How do I get where I'm trying to go?

have the other 2 windows machines be able to see & access the files on this machine?

---

