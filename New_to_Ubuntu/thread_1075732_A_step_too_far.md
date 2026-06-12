---
title: "A step too far"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by the.scarecrow on 2009-02-20
I have two hard drives for my laptop that can be mechanically swapped over in about 10 minutes. I started out using HDD A with just Hardy on it and got on very well with that. With more experience I find that living without WinXP causes just a few small but important problems.

So the drive I use now, HDD B, has WinXP pro and Intrepid duel booting on it and I find this to be the optimum configuration for me. So I want to make HDD A the same.

I plan to do this by installing HDD A, booting from the Intrepid live CD, then use GParted to create one blank partition. Next I will install WinXP allowing it to use the whole of HDD A and I think this will also install the Windows MBR. Once WinXP is working OK I will partition and install Intrepid in the normal way. This should replace MBR with GRUB to duel boot.

Will this work?

Sorry about the bad title and posting in Absolute Beginners, but I find if I give a descriptive title in the most appropriate group nobody will answer my question. HoHum.:-\"

---

### Post by hayden92 on 2009-02-20
This should work except for that fact that you can never really be certain...
I did the same a while ago and it (usually) works best this way because Ubuntu is more 'friendly' to Windows and generally Windows isn't the best of friends in terms of co-existing with Ubuntu ;)

Just give it a go and let us know how you fare,

P.S. Try to keep posts that don't really belong in the ABT out, we want beginners to have this section to themselves.

Hayden

---

### Post by the.scarecrow on 2009-02-20
> **hayden92 said:**
> This should work except for that fact that you can never really be certain...
I did the same a while ago and it (usually) works best this way because Ubuntu is more 'friendly' to Windows and generally Windows isn't the best of friends in terms of co-existing with Ubuntu ;)

Just give it a go and let us know how you fare,

P.S. Try to keep posts that don't really belong in the ABT out, we want beginners to have this section to themselves.

Hayden

I hope to do this over the weekend, maybe Sunday. Thanks for your reply and I will post how it goes anyway.

---

### Post by the.scarecrow on 2009-02-24
If your interested, it all worked out perfectly. WinXp installed fine on the blank 160GB HDD created with GParted including re-creating MBR.

I then divided the HDD into three 50GB partitions, one for WinXP, one for Intrepid and one left blank for the next version of Ubuntu when its released (Jaunty). I also created a swap partition that I hope both versions of Ubuntu can share.

Files I want to access from all three OSs can go into WinXP. I will have two Ubuntu home folders for settings and also Ubuntu specific files. This gives me the advantage of having a stable Ubuntu installation for working with and a development version of Ubuntu for testing new releases.

---

