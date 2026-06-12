---
title: "How do I find the chipset type (AMD PC)"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by penguinv on 2010-01-12
I want to be able to do dialup (dial-up) in Ubuntu 9.04 and so I need to be able to find out what my modem and chipset is.

How do I do that?

And while I am on the subject, how do I find out how much of my disk is free|used from Ubuntu? I can look at a second drive but on the main drive all I can see is "filesystem" and I am blind to the rest of the drive, with XP and files.

--- What is my setup? --- It's an older PC with an AMD m'board.
My installation is a Windows XP formatted drive with Ubuntu 9.04 installed as wubi. My XP has not been "approved" by MS and will not allow me to log on until I phone them (or connect by broadband) and get the secret sauce (number). 
    SOLUTION to the MS locking: Booted into safe mode (F8) and went into the Administrator account which bypassed the need for MS approval. 
I then installed linux as wubi and so I never need look at windows again. Why am I doing this? I want the disk to be NTSF so any system (ie MS also) can read the files on the hard drive. I haven't (yet) figured out how to make a new partition though so I can have 2 systems working and a partition that both can read. At this moment I can only do that by having 2 drives, which I do on another machine (this one I am typing on now).

----------------------------
Thank you for all assistance.

---

### Post by tom.swartz07 on 2010-01-12
> **penguinv said:**
> I want to be able to do dialup (dial-up) in Ubuntu 9.04 and so I need to be able to find out what my modem and chipset is.

How do I do that?

And while I am on the subject, how do I find out how much of my disk is free|used from Ubuntu? I can look at a second drive but on the main drive all I can see is "filesystem" and I am blind to the rest of the drive, with XP and files.

--- What is my setup? --- It's an older PC with an AMD m'board.
My installation is a Windows XP formatted drive with Ubuntu 9.04 installed as wubi. My XP has not been "approved" by MS and will not allow me to log on until I phone them (or connect by broadband) and get the secret sauce (number). 
    SOLUTION to the MS locking: Booted into safe mode (F8) and went into the Administrator account which bypassed the need for MS approval. 
I then installed linux as wubi and so I never need look at windows again. Why am I doing this? I want the disk to be NTSF so any system (ie MS also) can read the files on the hard drive. I haven't (yet) figured out how to make a new partition though so I can have 2 systems working and a partition that both can read. At this moment I can only do that by having 2 drives, which I do on another machine (this one I am typing on now).

----------------------------
Thank you for all assistance.

To get your stuff just type
```
lshw
```
itll be listed there

Your chipset is listed under core and the network things under network.

---

### Post by 73ckn797 on 2010-01-12
Are you saying you have a pirated copy of Windows? If so, you will likely not find much help. If not then why not go ahead and get that "secret sauce"?

---

### Post by tom.swartz07 on 2010-01-12
> **73ckn797 said:**
> Are you saying you have a pirated copy of Windows? If so, you will likely not find much help. If not then why not go ahead and get that "secret sauce"?

True, while we dont condone using pirated software here, we also have a commitment to helping people get the information we need.

I know in my case, way back when I used Windows, a virus got a hold of my registration keys and effectively 'unregistered' my computer. 

Im not saying that may be the case, but he is clearly trying to fix the problem. We should at least help him get the information regarding his system so that he could rectify his certification errors and 're-enable' his system.

---

### Post by tom.swartz07 on 2010-01-12
Additionally, if you want to dump Windows completely, you could install ubuntu on a minimal scale (just give ubuntu 10% or 5gigs, whatevers bigger) and format the rest of the drive as blank NTFS. This way you could have your NTFS partiton and get away scot-free without any copyright theft.

---

