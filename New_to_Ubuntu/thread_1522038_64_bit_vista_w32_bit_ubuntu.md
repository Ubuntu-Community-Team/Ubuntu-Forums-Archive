---
title: "64 bit vista w/32 bit ubuntu"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Lil' Ol' Me on 2010-07-01
I read the post where you can put a 64 bit ubuntu on a 32 bit machine with no problems but could not find any thing about this question.  can you put a dual boot running 32 bit ubuntu on an 64 bit alien running vista? 
Its my son computer and we really do not want to mess things up before we try so here's hoping someone has tried this and can give us an idea of it works or not. thanks.

---

### Post by howefield on 2010-07-01
If the machine is capable of running a 64 bit operating system, it will run both 32 and 64 bit systems.

---

### Post by pitbullface on 2010-07-04
is it necessarily better to install the 32 bit version over the 64 bit?  i'm running windows 7 64 bit and just downloaded the ubuntu 64 bit (first time with ubuntu), but now i'm having reservations because maybe i won't be able to find all the right drivers?  any insight would be appreciated

---

### Post by howefield on 2010-07-04
> **pitbullface said:**
> is it necessarily better to install the 32 bit version over the 64 bit?

Haven't a clue what you mean here.

> i'm running windows 7 64 bit and just downloaded the ubuntu 64 bit, but now i'm having reservations because maybe i won't be able to find all the right drivers?

Driver issues you may have won't be because of 64 bit. Burn the iso to CD and test the Live environment, so you can check everything works for you.

---

### Post by JC Cheloven on 2010-07-04
> **howefield said:**
> If the machine is capable of running a 64 bit operating system, it will run both 32 and 64 bit systems.

... but not the opposite! A 32 bit computer won't run a 64 bit OS.

AFAI understand, the OP is concerned about the co-existence of a 64 bit vista with a 32 bit ubuntu, in a dual boot setup. There should be no problem (not sure if using wubi, virtualization, or whatever alternative). But you will want to install the 64 bit version, specially if you have more than 3Gb ram.

---

### Post by Paqman on 2010-07-04
> **pitbullface said:**
> now i'm having reservations because maybe i won't be able to find all the right drivers?

Drivers aren't really an issue on 64-bit Linux. The only road bump you might run into is that some third-party apps don't have a 64-bit version (Adobe is particularly bad for doing this). All the stuff in the Ubuntu repositories come in both 32- and 64-bit versions though.

---

### Post by KdotJ on 2010-07-04
The two operating systems will be independent of each other. It won't make a difference if one is 64bit and the other is 32bit. The computer itself doesn't care, they are two different OS's

---

### Post by yetiman64 on 2010-07-04
From the OPs first post> I read the post where you can put a **64 bit ubuntu** on a **32 bit machine**...also,
> can you put a dual boot running **32 bit ubuntu** on an **64 bit alien running  vista**?  These two quotes conflict re the type of machine processor in use OP.

Note what howefield says and what JC Cheloven replies
>      Quote:
                                                                      [SIZE=2]Originally Posted by **howefield**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9535225#post9535225")[/SIZE]                 
                 *[SIZE=2]If the machine is capable of  running a 64 bit operating system, it will run both 32 and 64 bit  systems.[/SIZE]*
                                 
... but not the opposite! **A 32 bit computer won't run a 64 bit OS**.
@ OP _If_ your machine is 64 bit and you are referring to dual booting with 32 bit Ubuntu and (32 or 64 bit) Vista- **yes you can do it**.

Also if your machine has greater than 4 gig of RAM and you want to access all of it with a 32 bit Ubuntu install, consider installing a **pae** kernel as well. 

On 64 bit hardware and with 32 bit Karmic installed at the time (dual booting Vista as well -64 bit) I added the pae kernel and found my RAM access increased from ~2.8 GB to 7.9 GB in Ubuntu (8GB installed).

+1 to what KdotJ added.

---

### Post by JC Cheloven on 2010-07-05
@yetiman: exactly, thanks for making it clearer ;)

---

### Post by howefield on 2010-07-05
> **yetiman64 said:**
> Also if your machine has greater than 4 gig of RAM and you want to access all of it with a 32 bit Ubuntu install, consider installing a **pae** kernel as well.

Just to add, a clean install with the 32 bit version of Ubuntu 10.04 will automatically detect more than 3 gigabytes of RAM and  install a PAE kernel.

---

### Post by Frogs Hair on 2010-07-05
Running W7 32 x and Ubuntu  64x the video driver flips  depending on what I boot.

---

### Post by yetiman64 on 2010-07-05
> **Frogs Hair said:**
> Running W7 32 x and Ubuntu  64x the video driver flips  depending on what I boot.
Hi Frogs Hair, What do you mean by "the video driver flips" ? Is it integrated or dedicated video and what make / chipset etc ?

A 64 bit processor will handle either 32 or 64 bit OSes of either Windows or Linux and video problems etc are likely to be specific to the video hardware in use.

I personally can switch between 64 bit Vista and 32 or 64 bit Ubuntu on my desktop machine with absolutely no video hitches. Mind you I use a dedicated NVidia chipset card (GeForce 8400GT when I had Karmic installed - now a GeForce GT 240 with Vista and 32 and 64 bit installs of Jaunty and partitioned for 4 more ubuntu installs to come).

---

### Post by KdotJ on 2010-07-05
> **Frogs Hair said:**
> Running W7 32 x and Ubuntu  64x the video driver flips  depending on what I boot.



This is more likely due to your graphics drivers in ubuntu. As I stated before, the two operating systems are different, your processor or grapics card themselves do not store any configuations themsevlves. Nor does windows and ubuntu share configuation for such hardware.

Your graphics behaviour is due to the setup in one or both of the OS's, not due to the mixture of OS architectures

---

