---
title: "Partitioning my hard-drive"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-05
I'm going to partition my hard drive like this
primary /boot 6GB (for the OS)
logical swap space 1GB
primary /usr 93GB (for data/games/software/

Does this sound like it's going to work? I need the operating system to be in one partition and my data/games/software in another.

---

### Post by cam3roon on 2010-11-05
hmm..I think you should give the more gb to the root folder

I have it like this and works perfect:

30 gb for windows
10 gb for /
120 gb for /home

---

### Post by Gone fishing on 2010-11-05
You don't need 6 Gig for a /boot partition mine is 1 Gig (with 64 Meg used) but do you need a boot partition? You do need a root / partition. I'm not much of a gamer but I would have thought that /usr could just be in / rather than a separate partition (what's the thinking?) and that a /home partition would be a good idea as games profiles would be kept in the user home accounts.

---

### Post by psusi on 2010-11-05
/usr is where various parts of the system go.  Your data goes in your home directory, so you want 6 gb for / ( not /boot ) and the rest in /home, not /usr.

---

### Post by leclerc65 on 2010-11-05
I would give '/' 10G (ext4), /home 30G (ext4), 'swap' 1-2G and the rest as a NTFS or Fat32 partition to keep the data. Use gParted to partition it first, don't use Ubuntu install, because you will have problem mounting the NTFS/Fat partition later.
Reason: Linux occasionally goes into checkdisk which can be annoyingly long if you don't have a strong CPU. If you plan to run Virtual Box then give /home about 50G - it should be plenty.

---

