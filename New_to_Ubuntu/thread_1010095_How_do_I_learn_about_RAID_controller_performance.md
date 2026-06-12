---
title: "How do I learn about RAID controller performance?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-12-13
This may be a stupid questions and I dont know it, but my research is fruitless. 

Short question: Is RAID0 faster (noticable to a reasonable person)then a regular WD 500 GB HDD you can buy off the shelf? If not, then why would so many MOBO makes put RAID capabilities on MOBOs? AND how do I search to find out measuring why ASUS would use an after market controller vs the Intel South Bridge (what Intel calls ICH10R)one that already exists? 

Long version:

I just bought a MOBO and had a question about RAID.

But before we get to specs. I was going to buy another HDD (Confirmed it matched mine by the model number on the back of the Box), but the sales guy said RAID0 makes no difference over a regular single drive, so I should buy Seagates Baracuda 1.5TB 32MB cashe BC it is faster then a Raptor. It just didnt make sense as to why. When I pushed the issue he said he set up his "$300" one year old MOBO in a single and RAID0 and benchmark testing showed they performed the same. Thus I should buy the Seagate 1.5TB ($180 vs $75 WD Caviar 500GB)

First, after some research 1.5TB's, are seriously screwed and not working. There has been a recent flash update, but I could not find reviews saying these work. I mean this is Seagate wost moment in history, people are complaining everywhere, and they were playing it off like "Its just a vocal few". No its not! Shame on Seagate. Second, the reviews I saw showed the raptor as faster an most benchmarks.

Anyway Im glad I didnt bother with the 1.5 that he was pushing on me. But now I trying to understand why his $300 SLI evga MOBO wasnt improving with RAID0 (measured by benchmarks). His logic was that "RAID uses the south bridge and the CPU". He was very adimant RAID0 doesnt work. Still, its a $300 board! I assume it would have its own RAID controller like mine so it works apart from the CPU and South Bridge? On mine (See link below) ASUS put on a Silicon Image Sil5723 with two direct SATA ports so they dont run through the South Bridge. 

See where I going with my questions? There just doesnt seem to be a good source of info on what I'm searching as "Chipset RAID vs after market Controller RAID". 

Any help on how to learn more about this would be great. I had to read through hours of argument of weather RAID) works and "depends" for and answer. It appears that RAID0 does work for most people and as long as you backup, the scare of losing data is null, for me.

Again, I may be wrong, but Consider this:
1.) If a 1.5GB Barracuda is faster then Raptors, why hasnt their price dropped at least $100 to the Barracuda range?
2.) If RAID0 is worthless then why would there be Software RAID, Chipset RAID, and even multiple companies that specialize in add-on-to-MOBO RAID chips? 


Here is my board: 

[http://www.bit-tech.net/hardware/2008/05/28/asus-p5q-deluxe-intel-p45-has-arrived/1](http://www.bit-tech.net/hardware/2008/05/28/asus-p5q-deluxe-intel-p45-has-arrived/1)

---

### Post by sdennie on 2008-12-13
I don't have any experience with hardware RAID or RAID0 but, I used to run a server with software RAID5 and the performance of writing to the RAID5 array was measurably (benchmarked) far, far beyond the performance of writing to a single disk of the array.  If you put 2 of the same disks into a RAID0 array, it's not unreasonable to expect something close to a 2x speedup compared to a single disk.  At a certain point, you'll saturate the SATA bus and adding more disks to the array won't speed things up but, 2 identical disks in a RAID0 array will *always* be faster than just running 1 disk of that mark.

---

