---
title: "Why would 4gb of RAM be slower than 1gb?"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by tahitiwibble on 2011-07-07
Good day to one and all,

I finally did it and went for 4gb of memory. The "expert" in the store explained that he didn't have DDR2 533 240-pin but he did have DDR2 800 240-pin.

I mentioned that my motherboard was rated for 533 and that I was actually using 667 (that's what came with the computer when I bought it new), and asked him how the 800 would be. Answer was that at worst the 4gb would run at 533 but with a huge improvement in performance anyway.

My computer runs worse than before. Could anyone spread some light on this issue for me?

---

### Post by terrykiwi83 on 2011-07-07
1. does the full 4gb show up on your system?
2. are you using a 64bit OS?

cheers

---

### Post by papibe on 2011-07-07
You probably want to check what sales rep told you. Check the package, or the manufacture website. Nevertheless, most of them do support slower rate.

All I can think is, you have a faulty RAM stick. If I were you, I'd run the memtest86 at least one hour to check them.

Just a thought, Hope it helps.
Regards.

---

### Post by tahitiwibble on 2011-07-07
> **terrykiwi83 said:**
> 1. does the full 4gb show up on your system?
2. are you using a 64bit OS?

cheers

Hi Terry, thanks for chipping in. The system only shows 2.9gb and I'm using 32bit.

---

### Post by tahitiwibble on 2011-07-07
> **papibe said:**
> You probably want to check what sales rep told you. Check the package, or the manufacture website. Nevertheless, most of them do support slower rate.

All I can think is, you have a faulty RAM stick. If I were you, I'd run the memtest86 at least one hour to check them.

Just a thought, Hope it helps.
Regards.

Thanks papibe, I never came across that little program before ... just what the doctor ordered. I'll run it over lunch.

Cheers

---

### Post by LowSky on 2011-07-07
RAM speed is going to be barely noticeable.

Some motherboard can only take certain types of RAM for instance Mac's dell's and a some ASUS motherboard croak on RAM that isn't approved. While the speed can be different, the voltage requirement cannot. For instance if your motherboard only accepts 1.5 Volt sticks, you cannot use 1.6 or higher no matter what.

---

### Post by terrykiwi83 on 2011-07-07
have you tried re-seating your ram in different slots, then try them one at a time to find the culprit. 

If they all seem to work, then pop in a Ubuntu 64bit Live CD and see how much RAM is showing then

---

### Post by dFlyer on 2011-07-07
If your running the 32bit OS you should install the pae kernel to take advantage of the full 4 gigs. Also it shouldn't be running slower.

---

### Post by tahitiwibble on 2011-07-07
FYI from the Super Talent website:

Part Number 
old - T667UB1GV
new - T800UB2GV

Density 
old - 1 GB
new - 2 GB

Speed 
old - 667 Mhz
new - 800 Mhz

Data Rate 
old - PC2-5300
new - PC2-6400

Module Config 
old - 128M x 64
new - 256M x 64

Chip Config 
old - 64M x 8
new - 128M x 8

CL 
old - 5
new - 6

ECC 
old - N
new - N

Heat spreader 
old - N
new - N

Voltage
old - 1.8V
new - 1.8V

---

### Post by tahitiwibble on 2011-07-07
> **dFlyer said:**
> If your running the 32bit OS you should install the pae kernel to take advantage of the full 4 gigs. Also it shouldn't be running slower.

Hi Flyer (heehee),

I found this on wiki "The Linux kernel includes full PAE mode support starting with version 2.3.23,[6] enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE. As of 2009,[7] some common Linux distributions have started to use a PAE-enabled kernel as the distribution-specific default[7] because it adds the NX bit. [8]" ........... don't I already have it installed?

---

### Post by tahitiwibble on 2011-07-07
> **terrykiwi83 said:**
> have you tried re-seating your ram in different slots, then try them one at a time to find the culprit. 

If they all seem to work, then pop in a Ubuntu 64bit Live CD and see how much RAM is showing then

Hmmm, funny thing, right now I have the old card and one of the new .... and I'm showing a full 3GB

---

