---
title: "Any Way to Speed-up NFS?"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2007-09-08
*just as the title implies: is there any way to speed up nfs?*

---

### Post by Jose Catre-Vandis on 2007-09-08
How slow is yours, mine is fine, much quicker than SSH file transfer. About 1GB per 1 minute 40 secs over 100mb nics and cable. do you have a bottleneck somewhere (hardware or software)?

---

### Post by CyberCod on 2007-09-09
Mine is slow as molasses also... much slower than samba

One PC is hooked via eth0 and the other is on wireless

700MB file, taking about 45 minutes.

---

### Post by moore.bryan on 2007-09-09
> **Jose Catre-Vandis said:**
> How slow is yours, mine is fine, much quicker than SSH file transfer. About 1GB per 1 minute 40 secs over 100mb nics and cable. do you have a bottleneck somewhere (hardware or software)?
*i wish i had those kind of speeds... but it is faster than ssh.  i can't find any bottlenecks; perhaps you know the "secret" way to double-check?*
> **CyberCod said:**
> Mine is slow as molasses also... much slower than samba
[i]really?  samba wouldn't even work between my two ubuntu machines, that's why i went with nfs.

i'm simply trying to browse files on the "base" computer, but it takes forever for each one to load.[/i]

---

### Post by moore.bryan on 2007-09-09
[I]okay, so after fiddling around with lots of things and not really knowing how, i've successfully sped-up nfs quite a bit.  

i should really take notes on what/when/how i do things...
[/I]

---

### Post by CyberCod on 2007-09-09
do you remember anything about how you did it? what files you were changing?

anything?

---

### Post by moore.bryan on 2007-09-09
*well, i reinstalled portmap, like, a dozen times, double-checked all my port settings, reset my router... beyond that, no idea.  i got so bleary-eyed from looking at files.*

---

### Post by CyberCod on 2007-09-09
Well, its something...
I'm still working on it all.

Just used the following command in terminal to time a file copy
```

time command cp ~/Desktop/Fog2.flv ~/Desktop/SharedFolder

```

it was a 5.6MB file and it took 19.121 seconds.

5.6/19.121 = 0.292871712 MB/s
times 8 gives 2.342973696
or
2.34Mbit/s
on an 11Mbit connection.

a 700MB file would take 2390 seconds or 39.8 minutes.

That still seems a bit high to me.

---

