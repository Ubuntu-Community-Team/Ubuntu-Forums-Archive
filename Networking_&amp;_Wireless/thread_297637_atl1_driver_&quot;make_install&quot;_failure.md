---
title: "atl1 driver &quot;make install&quot; failure"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by PgR on 2006-11-11
Hi folks,

I've installed 6.10 on an amd64. The motherboard (M2V) has an on-board NIC, Attansic ATL1. The drivers are on the CD, which is handy.

I can run "make" ok; but when I try "make install" it tells me 
cannot write to /var/cache/man/cat7/atl1.7.gz in catman mode.

Any bright ideas? I know the card is OK and the driver works - I installed it 2 days ago and it worked fine - but since then I've wiped the disk 
:^(

---

### Post by lloyd_b on 2006-11-11
Try:

**sudo make install**

Lloyd B.

---

### Post by PgR on 2006-11-11
Thanks for the quick reply, Lloyd.

I am using sudo (didn't mention it in the O.P.)
I also tried giving root a password and su'ing but that didn't work either.

---

### Post by lloyd_b on 2006-11-11
> I am using sudo (didn't mention it in the O.P.)
I also tried giving root a password and su'ing but that didn't work either.

I always go for the most obvious thing first (as that's *usually* the problem).

Ok - next step:

The error involves running "catman", and is attempting to write to a directory "/var/cache/man/cat7".  So:

1.  Verify that "catman" is installed on your system
```
which catman
```

Should show "/usr/bin/catman" (at least it does on my box).

2.  Verify that there is a directory "/var/cache/man/cat7".
```
ls /var/cache/man
```

And see if there's a "cat7" entry.

Hopefully these suggestions will get you closer to a solution....

Lloyd B.

---

### Post by PgR on 2006-11-11
I get the same /usr/bin/catman and yes, there's a cat7 directory with the same permissions as the others.

Thanks for the help - I'll keep trying.

---

### Post by PgR on 2006-11-11
Well the NIC's working now - I tried (out of desperation) modprobe atl1 and it seems to have worked. I think the catman error must have been a red herring.

---

### Post by bsalt on 2006-12-10
> **PgR said:**
> Well the NIC's working now - I tried (out of desperation) modprobe atl1 and it seems to have worked. I think the catman error must have been a red herring.

thank you for this thread! i just installed edgy on my asus p5l-mx mobo, and i had the same EXACT results you did. it turned out that after **make install**, all that is needed is the sudo modprobe atl1.


thanks man!

---

### Post by fiskem on 2006-12-15
> **bsalt said:**
> thank you for this thread! i just installed edgy on my asus p5l-mx mobo, and i had the same EXACT results you did. it turned out that after **make install**, all that is needed is the sudo modprobe atl1.


thanks man!

same situation here ;)
thanx !

but first of all, i made a hard looking to find out to solve "Linux Kernel Source Not Found" error,
(i did first "uname -r" to see the correct kernel ARCH
then "apt-get install linux headers" choose correct one to load, then your helps here, let me finish the game :))

---

