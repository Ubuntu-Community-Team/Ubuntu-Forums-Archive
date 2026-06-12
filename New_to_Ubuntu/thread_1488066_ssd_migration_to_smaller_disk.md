---
title: "ssd: migration to smaller disk?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Knacker on 2010-05-19
Hi,
I've searched around and found a lot of partial (and often conflicting/outdated) information on this. If there's some resource or forum post that I've overlooked, sorry... 

I've got a 160gb hdd that is failing and I'm looking at replacing it with a 80gb SSD. Since most of my data is now on a mounted remote drive (sshfs), I actually don't need all the 160gb. 

I'm wondering what the best way is for me to migrate to the ssd and ideally without reinstalling/reconfiguring everything (always fun to do, but I don't have time for it at the moment).

I'm using Lucid 10.04 and my installation has three ext4 partitions (and a swap): (1) root partition, (2) home partition and (3) data partition (documents, music, etc.). The first two are tiny and the last (data) is about 130gb. I'm going to simply copy, folder by folder, what I need from the big (130gb) data partition to the new disk...so I'm really only worried about whether I can simply copy my root and home partitions to the ssd.   

My specific questions are:
1) Can i simply copy my root partition and my home partition to corresponding partitions on my new ssd, reinstall grub and be on my merry way? 

2) If this (1) is possible, what are the downsides of doing it this way (as opposed, for example, to a clean install) and what steps would I need to make it work properly (i.e. how would I need to edit fstab or other things related to the new hard drive)?

3) Do I still need a swap partition (I have 4gb of ram)? And, if I can remove swap when I migrate to the new ssd, are there any other steps I need to take to be sure that ubuntu doesn't get confused by its sudden absence?

4) Is it necessary or worth it to look into all the stuff I keep encountering about turning off journaling when using a ssd?  

Sorry for length of my question. Would be super grateful for any help, suggestions, experiences anyone has to share. 

Many thanks in advance!

---

### Post by ubunterooster on 2010-05-19
1,you will need to use Gparted (via liveCD) to shrink them first.

3,I think  you sould keep at least 1 GBjust in case

4, no need, but you can if you want

---

### Post by Knacker on 2010-05-20
thanks so much for your reply! 

hm...the two partitions i'm moving (root and home) will fit with lots of extra room, so I don't see why I'd need to shrink it, but maybe i'm missing something... 

good to know that i should keep 1gb of swap, just in case...though it's annoying that i need to have it there, if it's almost certainly never getting used. 

from what you've written, i'm going to take away the answer that I can copy root and home partitions over, reinstall grub and the new disk should work like a charm. I hope this is correct...seems too simple by far, but I trust you know what you're talking about. 

of course, (anyone) please correct me if anything here seems mistaken. thanks again.

---

### Post by ubunterooster on 2010-05-20
If you have an 8GB partition with only 1 GB used, you will still need to shrink the 8 GB partition to at most 4 GB if it is to fit in a 4 GB partition.

SWAP does something with hibernation and some other processes. I never Used my SWAP (or hibernate) but I keep 1 GB to my 8 GB of RAM


[COLOR=Blue]Analogy: Partitions are folders with all free space filled with junk. You _still_ need to remove the junk by shrinking the partition/folder.

 Not entirely exact, but it gets the idea across....I hope[/COLOR]

---

