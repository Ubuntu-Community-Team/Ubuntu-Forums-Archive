---
title: "How much space for Swap?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by jaycee23 on 2010-03-17
My new desktop has 6GB of RAM. Simple question do I really need to assign some space to Swap and if so how much?

Other specs are Intel Core i7 930 overclocked to 4GHz, 1.5Tb Hard drive, ATI Radeon HD 5870.

---

### Post by derekeverett on 2010-03-17
I'm no expert here, so I well may be corrected by someone else..

But I believe a swap partition is required. For reasons of optimization if nothing else.

The installer will just create one for you if you don't specify.

If I'm wrong about this than I look forward to being corrected.

---

### Post by tad1073 on 2010-03-17
With linux, the smallest swap space you can allocate is 8mb's, I believe.

---

### Post by cgroza on 2010-03-17
A 512 mb swap partition is more than enough...at you memory size you computer probably will never swap.

---

### Post by mbzn on 2010-03-17
If you manually partition:
I have 2GiB ram only use me swap when i have 1.5GiB set to a virtual machine, so i dont think you need swap. Remember if you hibernate your PC all of the RAM is written to swap, in that case the size of your swap depends what you have in RAM. If you have the free space do 6GiB, for hibernating purposes. I doubt you'll ever use up your RAM if you dont run 2 or 3 VBoxes at once..

Hope this helps

---

### Post by jaycee23 on 2010-03-17
Thanks for the replies - won't be using hibernate and will do manual partition when install Ubuntu - so 512Mb seems reasonable to people?

Any other opinions?

---

### Post by cgroza on 2010-03-17
512 mb swap will suit considering you don't hibernate.

---

### Post by HermanAB on 2010-03-17
Hmm, depends...

If you want suspend and hibernate to work, then you need 2x RAM for /swap.

---

### Post by t1nm@n on 2010-03-17
my friend the old trend was twice the amount of ram for swapspace..and i'm following that...in ur case 12gigs huh.... make an exception if u r gonna do slashand burn ur computer 2 gigs is more than enough.

Any way i'd go with the 1st post abt the installer making the swap partition.

---

### Post by aeiah on 2010-03-17
with 6GB of ram unless you're doing some pretty demanding stuff i doubt you'll see your swap space used. regardless, 512mb won't eat into your storage space so you might as well make the partition. ive ran a 2GB system without swap before and right now my 1GB netboot isnt using any swap (although i just have firefox, a terminal and a text editor open).

back when people had less than 1 or 2 GB a swap was useful but windows vista and 7 have pushed the demand for ram so most modern systems have loads of ram that's hardly used with linux unless you're running a server or virtual machines.

---

### Post by YannBuntu on 2010-03-17
In the ubuntu-fr wiki we recommend:
if RAM<1Go: SWAP should be 1,5x ~ 2x RAM size 
if RAM>1Go: SWAP should be 1x ~ 1,5x RAM size 

See also [https://help.ubuntu.com/community/Partitioning/Swap](https://help.ubuntu.com/community/Partitioning/Swap)

---

### Post by audiomick on 2010-03-17
Hallo
You said you don't want to hibernate, so therefore your swap doesn't need to be as big as your RAM

The rule swap = 2 x RAM has been mentioned. This was once the case, but is now obselete and can be disregarded (given that you don't want to hibernate). The rule (of thumb) dates back to times when RAM was typically 256MB or less.

With 6GB RAM, you will probably never even scratch your swap in normal use, so 512MB is  probably enough. However, I guess that if you have 6GB RAM in there, you probably have lots of drive space as well. Why not give it 1GB to be sure?

---

### Post by Roger Allott on 2010-03-17
As you've got a 1.5 Tb hard disk, what is the value of skimping on swap? Even if you push it to the max with 2xRAM, that only costs you 12 Gb, which is less than 1% of your total storage capacity.

---

### Post by anaconda on 2010-03-17
In your case I wouldnt bother to make a swap partition at all.

however I propably would make a small 512MB or 1024MB swap file
here is the instructions for making a swap file
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

PS 6-12GB swap size would be ridiculous.. (if yu dont need hibernation) I once had my system use ~700MB of swap, and the machine was really really really slow. cant even imagine how slow it would be with >4GB of swap in use.

---

### Post by cascade9 on 2010-03-17
> **Roger Allott said:**
> As you've got a 1.5 Tb hard disk, what is the value of skimping on swap? Even if you push it to the max with 2xRAM, that only costs you 12 Gb, which is less than 1% of your total storage capacity.

Makes sense to me. 

Your not going to miss even 12GB with that HDD. Its a lot easier to setup a swap at install time than you play with partitons later (and safer).

---

### Post by philinux on 2010-03-17
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

However, with 6gig of ram and not using hibernate/suspend then swap is not needed at all.

I have 2gig ram. I use hibernate so my swap is 2gig. I have set swapiness down to 10 and swap never gets used.

The old 2times ram adage was in the days of expensive, hence not so much ram in use.

---

### Post by rnerwein on 2010-03-17
hi
i think in the case of a system crash you will need the swap space. as far as i know a core image of your RAM ( compressed ) is first synced to the swap partition.
ciao

---

