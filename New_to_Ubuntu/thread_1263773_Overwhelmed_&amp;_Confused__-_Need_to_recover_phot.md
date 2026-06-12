---
title: "Overwhelmed &amp; Confused  - Need to recover photos with Rescue remix ( I think )"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Iandb on 2009-09-11
Folks,
 
I've been trying to figure this out myself but the more I click the more I get lost and confused.  Can you help.
 
I have a PC with XP on it containg 2 drives.  I have a lot of photos on the slave drive which I think the partition is shot.  The drive is iirc 13gb 
 
I have burned a rescueremix 9.04 cd, so far so good, but now I'm lost and need help.  Is this what I actually need otr should I durn a live cd?
 
Is there a idiots walkthrough that I can follow?  With all the clicking various links I have got my self so confused and lost I have no idea where I am.

---

### Post by aysiu on 2009-09-11
Here is a step-by-step walkthrough with screenshots:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

Please let us know if you have any questions or get stuck at any point.

---

### Post by LewRockwell on 2009-09-11
> **Iandb said:**
> Folks,
 
I've been trying to figure this out myself but the more I click the more I get lost and confused.  Can you help.
 
I have a PC with XP on it containg 2 drives.  I have a lot of photos on the slave drive which I think the partition is shot.  The drive is iirc 13gb 
 
I have burned a rescueremix 9.04 cd, so far so good, but now I'm lost and need help.  Is this what I actually need otr should I durn a live cd?
 
Is there a idiots walkthrough that I can follow?  With all the clicking various links I have got my self so confused and lost I have no idea where I am.

might confuse you more, but great information nevertheless

we were here:
[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

which led us to:
[http://en.wikipedia.org/wiki/SpinRite](http://en.wikipedia.org/wiki/SpinRite)

which finally led us to:
[http://www.roadkil.net/program.php?ProgramID=29](http://www.roadkil.net/program.php?ProgramID=29)


we have also previously recommended the PartedMagic LiveCD:
[http://partedmagic.com/](http://partedmagic.com/)

here is a link to the utilities included on PartedMagic including TestDisk and PhotoRec:
[http://partedmagic.com/programs.html](http://partedmagic.com/programs.html)

.

---

### Post by Iandb on 2009-09-17
Thanks both for the links.  Apologies for the late reply but I've only got a connection at work.

---

### Post by Udayakiran on 2009-09-17
> **LewRockwell said:**
> _**might confuse you more**_, but great information nevertheless

we were here:
[http://en.wikipedia.org/wiki/Dd_(Unix]("http://en.wikipedia.org/wiki/Dd_%28Unix"))

which led us to:
[http://en.wikipedia.org/wiki/SpinRite](http://en.wikipedia.org/wiki/SpinRite)

which finally led us to:
[http://www.roadkil.net/program.php?ProgramID=29](http://www.roadkil.net/program.php?ProgramID=29)


we have also previously recommended the PartedMagic LiveCD:
[http://partedmagic.com/](http://partedmagic.com/)

here is a link to the utilities included on PartedMagic including TestDisk and PhotoRec:
[http://partedmagic.com/programs.html](http://partedmagic.com/programs.html)

.

:lolflag:

---

### Post by Iandb on 2009-09-17
> **Udayakiran said:**
> :lolflag:
 
I know.  See how I get on first befor venturing into others

---

### Post by djbushido on 2009-09-17
If the drive is going, it might be worthwhile to look into backing it up first - do a bit-for-bit copy off using the "ddrescue" command. Then the drive will at least be stable, and you *probably* won't corrupt anything else.

---

