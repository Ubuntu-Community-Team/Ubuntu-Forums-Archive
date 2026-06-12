---
title: "Trying to install Starcraft from ISO"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by juggleclown on 2011-06-26
First of all, this problem might have more to do with Wine than Ubuntu (I'm running 10.04, though it shouldn't matter too much), but bear with me here.

I'm trying to install Starcraft on a machine without an optical drive, using two ISOs I ripped from the two discs. It's a copy of one of the later releases that installs Brood War at the same time as Starcraft and doesn't use a CD check to play.

I've tried using the "mount -o loop" command as well as using gmount-iso, with the same result. It'll allow me to install it half way, but upon asking for the second disc, it refuses to continue. It just won't find it.

I mount the disc manually, as the archive mounter seems to give me problems with permissions, to "/media/cdiso", which I have mapped as the D:\ drive in Wine. I've tried mounting "SCDisc1.iso", letting it install halfway, unmounting it and mounting SCDisc2.iso in the same place, but for some reason, the installer doesn't seem to see this as disc two in the cd-rom drive and refuses to continue. I've even tried mounting both discs as d:\ and e:\ simultaneously, but this doesn't work either.

Anyone have any idea how to get this to work? :confused:

---

### Post by jtarin on 2011-06-26
Have you tried running two instances of Gmount-iso? Before you run Gmount-iso, you will want to create a folder to mount the ISO at.

---

### Post by haqking on 2011-06-26
> **juggleclown said:**
> First of all, this problem might have more to do with Wine than Ubuntu (I'm running 10.04, though it shouldn't matter too much), but bear with me here.

I'm trying to install Starcraft on a machine without an optical drive, using two ISOs I ripped from the two discs. It's a copy of one of the later releases that installs Brood War at the same time as Starcraft and doesn't use a CD check to play.

I've tried using the "mount -o loop" command as well as using gmount-iso, with the same result. It'll allow me to install it half way, but upon asking for the second disc, it refuses to continue. It just won't find it.

I mount the disc manually, as the archive mounter seems to give me problems with permissions, to "/media/cdiso", which I have mapped as the D:\ drive in Wine. I've tried mounting "SCDisc1.iso", letting it install halfway, unmounting it and mounting SCDisc2.iso in the same place, but for some reason, the installer doesn't seem to see this as disc two in the cd-rom drive and refuses to continue. I've even tried mounting both discs as d:\ and e:\ simultaneously, but this doesn't work either.

Anyone have any idea how to get this to work? :confused:

[http://koti.mbnet.fi/hoppq/sc-howto.html](http://koti.mbnet.fi/hoppq/sc-howto.html)

and there is an issue for disc 2

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)

---

### Post by juggleclown on 2011-06-26
> **jtarin said:**
> Have you tried running two instances of Gmount-iso? 


No. What good will that do? :confused:


> **jtarin said:**
> Before you run Gmount-iso, you will want to create a folder to mount the ISO at.

Yes, the folder is at /media/cdiso. I placed it there myself with "sudo mkdir /media/cdiso" before even making this thread. That's an incredibly obvious suggestion. :(



> **haqking said:**
> [http://koti.mbnet.fi/hoppq/sc-howto.html](http://koti.mbnet.fi/hoppq/sc-howto.html)

I'm not seeing what it is I'm supposed to be looking at here. Have you tried installing Starcraft on your own machine, or are you merely linking me to the first reference you found? The text here bears little resemblance to my problem, and reading over it several times, I've still failed to find anything relating to both my problem and a solution to it.

That was a glorious waste of time. I'm sorry, but are you sure you read my original post or have a decent understanding of the problem? :frown:

> **haqking said:**
> 
and there is an issue for disc 2

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)

The winehq page is one of the first places I looked. I have installed Starcraft from the cd-rom drive before, and it ran flawlessly in Wine. I imagine if I tried to install a non-Battle Chest copy of the original Starcraft, I could avoid having to deal with the disc swap conundrum entirely, but going out and buying or downloading such a thing would be side-stepping the issue (as would purchasing an external cd-rom drive, I'd rather learn how to flawlessly emulate a disc swap should I run into the same problem in the future).

The only relevant question I could find when I was there was from "Vincent", who had posted "Cannot Switch CD" and had the same problem. "Todd Hammersmith" replied with a solution which I tried. I did as he said and copied the contents of both discs into a folder, mounted disc 1 and had it set as the D:\ drive in Wine, and ran the installer from the folder, but the resulting error is


"No installer data could be found. If this problem persists, please contact Blizzard Technical Support."


So, that didn't work either, and Vincent resorted to buying the digital download version from Blizzard. I've been scouring about this forum and the rest of the internet for a solution, and the few things I hadn't yet tried didn't seem to work. Disc swapping with physical discs worked the last time I had to, so I'm left wondering if there's a more ingenious way to trick Starcraft, and perhaps Wine, into thinking that I've physically swapped two discs, as a simple mount of the second iso into the same place doesn't seem to be completely identical for whatever reason...

---

### Post by jtarin on 2011-06-26
Let me give you another _very obvious suggestion_ which you have failed to mention...did you try burning one of the disk and actually using your cdrom?

---

### Post by haqking on 2011-06-26
> **jtarin said:**
> Let me give you another _very obvious suggestion_ which you have failed to mention...did you try burning one of the disk and actually using your cdrom?

he said he has no optical drive

---

### Post by jtarin on 2011-06-26
> **haqking said:**
> he said he has no optical driveWhoops! He said a lot of other things ...too.:P

---

### Post by idoitprone on 2011-06-27
i am going to give a brief guide.

get acetoneiso

its gui is easy to use and simple. It so simple one day i might forget how to use the commandline because it so dawm easy.

and another thing

you may need a no-cd crack.

---

### Post by juggleclown on 2011-06-27
> **idoitprone said:**
> i am going to give a brief guide.

get acetoneiso

its gui is easy to use and simple. It so simple one day i might forget how to use the commandline because it so dawm easy.


I set my computer to download acetoneiso last night, and this morning, 40 MB later, I have to say I'm not sure it was worth the wait.

It can mount ISO files, just as well as "Gmount-iso" (but arguably with a worse gui) and "mount" itself, but there's the problem. What is the advantage over these two programs? I have no idea what your intention was for me to use this. The most obvious application is simply to mount ISOs, which does little good as I can already do that with little trouble, both with and without a gui using the aforementioned programs.

Unfortunately, mounting with acetoneiso produced *worse* results by default, as the installer could not find the data, just as copying the files from inside the iso to a folder in Wine's "C:\" path did. I'm sorry, but what exactly did you intend for me to do here? :confused:


> **idoitprone said:**
> 
and another thing

you may need a no-cd crack.

In my experience, and I have a fair amount of experience in this area, no-cd cracks are usually designed for use *after* software has been installed, to prevent having to insert a cd or mount an iso while running a program. Starcraft no longer uses a CD check, aside from needing a second disc to install all of the game data, and finding a no-cd crack intended to defeat the need for the installer to find and use the files on the second CD seems, in all likelyhood, very, very, *very* unlikely. #-o](*,)

---

