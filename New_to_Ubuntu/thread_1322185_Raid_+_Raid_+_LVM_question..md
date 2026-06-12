---
title: "Raid + Raid + LVM question."
date: 2009-11-10
forum: New to Ubuntu
---

### Post by BT1 on 2009-11-10
I have a few questions but before I ask them, I want to state a few things so that others don't waste their time telling me these things (not that I'm impatient, just don't want you nice people wasting your time).

1.) I'm aware that RAID 0 can really mess up data if one disk in the array fails.
2.) I'm at least somewhat familiar with what RAID 1 and 5/6 does, and how it works.
3.) I'm also aware of what the purpose of LVM (logical volume manager) is supposed to serve.

Now, those things being said... my questions are:

1.) What are the average read/write boost% in speed for two (or more) drives in linux software RAID 0/1/5/6?

2.) Is it possible to set up a desktop that has a hardware RAID controller for 4 Hard Drives, to make **two** RAID 0 drives (combining 2 drives to form one raid drive, and then combining 2 more drives to form another raid drive), and then take those 2 hardware raid 0 drives, and use linux to combine those 2 hardware raids into one software raid drive?

3.) If yes, would there be a bonus to the read and write of that software raid drive (that's built on two hardware raid drives)?

4.) Is it possible to use LVM on that final "drive"?

5.) If yes, will an LVM stacked on that configuration increase read/write, or will there start to be some hidden overhead for all that stuff.

------------------------------

Lol now I know that's a lot, and I can see it in my head, but if you can't, ask me to clarify.

Anyways my uncle is giving me the funds to do that if it works. For safety, I'm going to have all of this backed up by a local network hard drive system. I got my uncle interested in this because I have a Ubuntu 9.04 "book" that is about 3 inches thick that explains raid and lvm, and how you can stack LVM with a software raid. My big question is will ubuntu let you stack a software raid on a hardware raid. I saw that the book stated that even software raids get bonuses to speed, and that's what caught his interest. He says if it works right he'll seriously consider moving to linux and abandoning his apple stuff (which means he'd be selling his apple laptops within the week.

Does this all work with ubuntu desktop or just ubuntu server?

Thanks for the assist!

---

