---
title: "i7 gaming rig and ubuntu"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Pevichaey5 on 2010-10-08
Hey

I tried to boot the live CD, and I got an instant kernel panic

Might be because of the new hardware/config not sure, but I was
booting 10.04

Do you know if 10.10 will have support for this hardware

i7 920
Ati 5870
Samsung 22" LCD
Asus P6T mobo

I think the rest of my rig is recycled older hardware that I
used with 8.04 so these are all I can think of that might cause
problems with the live CD

Any ideas ?

---

### Post by Paddy Landau on 2010-10-08
> **thexero said:**
> Do you know if 10.10 will have support for this hardware
Cannot predict.

The best thing is to download the current 10.10 (remember -- it's still in development!) and try with the Live CD.

If it doesn't work, try again in a month; keep trying until the formal release.

Another alternative is to try a different distro, such as SUSE or Fedora. I don't know which distros make a point of being as up-to-date as possible; they could give you better results.

---

### Post by jaycee23 on 2010-10-08
I've got a very similar rig to yours but different mobo - I have the
**[FONT=Verdana][SIZE=1]Gigabyte GA-X58A-UD3R mobo.[/SIZE][/FONT]**

My setup works fine both with 10.04.1 and 10.10RC

---

### Post by Pevichaey5 on 2010-10-08
Note taken

Thanks :)

---

### Post by Pevichaey5 on 2010-10-08
I'm using Raid 0, using the onboard raid controller for that

We are using a SAN (raid 1+0) on our Red Hat Linux host machines
but I dunno

:: Edit ::

I have 6gigs of DDR3 (3x 2GB), I think I downloaded the 32bit
version of 10.04, could that be a possible issue here?

---

### Post by jaycee23 on 2010-10-08
> **thexero said:**
> I'm using Raid 0, using the onboard raid controller for that

We are using a SAN (raid 1+0) on our Red Hat Linux host machines
but I dunno

:: Edit ::

I have 6gigs of DDR3 (3x 2GB), I think I downloaded the 32bit
version of 10.04, could that be a possible issue here?

Honestly can't see either of those 2 things being an issue.
Have you googled the mobo for compatability issues?

---

### Post by Pevichaey5 on 2010-10-08
Doing that now (:

---

### Post by Pevichaey5 on 2010-10-08
After some Googling OpenSuse 11.1 doesn't seem to have a problem
with the Asus P6T

So I think I'll just wait for 10.10 to be released and try again

Cheers peeps :D

---

### Post by Paddy Landau on 2010-10-08
> **thexero said:**
> I have 6gigs of DDR3 (3x 2GB), I think I downloaded the 32bit
version of 10.04, could that be a possible issue here?
AFAIK, the only issue with 32-bit for 6Gb RAM is that most of your RAM won't be used, but it won't prevent it working. But you can try 64-bit, see whether it works.

---

### Post by cascade9 on 2010-10-08
> **Paddy Landau said:**
> AFAIK, the only issue with 32-bit for 6Gb RAM is that most of your RAM won't be used, but it won't prevent it working. But you can try 64-bit, see whether it works.

Ubuntu should instal the PAE kernel if it detects 4GB+ of RAM. 

I'd try 64bit though, why run a 64bit CPU with a 32bit OS?

---

### Post by Pevichaey5 on 2010-10-08
I have a few machines, and due to my unreliable internet
connection, (I goes down fairly often) I got the 32bit version so
that hopefully it would run on all my machines and I wouldn't
have to download the 32bit and 64bit versions

Back|Track 4 (Ubuntu 8.04 I think) is my primary os, and this i7
machine is only my gaming rig at the moment, so I'd like to get 
Ubuntu on there as well so that I can get the best of both 
worlds :D

---

### Post by khelben1979 on 2010-10-08
> **thexero said:**
> Do you know if 10.10 will have support for this hardware

i7 920
Ati 5870
Samsung 22" LCD
Asus P6T mobo

According to [this source]("http://www.ubuntu.com/testing/maverick/beta"), [2.6.35.3]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.35.y.git;a=log;h=refs/tags/v2.6.35.3") is the default kernel (released 6 weeks ago).

I think that your graphics card would be the most difficult part to get working if you want fast and stable graphics, but hopefully it works!

---

### Post by jaycee23 on 2010-10-08
I would give 10.10RC a go - if you wait for Sunday the server will be swamped with the official release.

As I said I'm running it without any major issues (as long as you don't call the new default fonts a major issue!!)

---

