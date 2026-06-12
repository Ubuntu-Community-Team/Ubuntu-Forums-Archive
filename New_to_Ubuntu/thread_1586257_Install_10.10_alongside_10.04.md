---
title: "Install 10.10 alongside 10.04"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by migs73 on 2010-10-01
Right then,
 I've got 10.10RC on live CD. All looks fine, but, how do I go about installing it alongside my 10.04 (want to try it out and then do a clean install if ok). I have a separate home partition I want them to share. When I start on the install process and choose 'install alongside' I get a picture of my 2 partitions (it ignores my swap) and asks me to move the slider to make space. Here is where I get a bit lost. How do I select which partition to install into (want it to be in my current root partition), it is plenty big enough (70GB) and for it to only be root (share my home and swap). Do i need to do this with the advanced installer?
If so, can I do what I have said, or do I need to make a new partition? Also as I don't want to touch my home partition, so do I need to back stuff up first?

Many thanks 

Migs

---

### Post by oregonbob on 2010-10-01
What do you hope to gain by installing 10.10 now? Most likely it will have bugs. I would wait a while until initial bugs are killed off. A 70 gb hard disk isn't all that large for 2 installed of any OS. I'm pretty certain when it partitions the drive it will install on the new unused partition created on right of slider bar. But I would wait a month or two and 10.04 is a LTS version.

---

### Post by migs73 on 2010-10-01
Its a 320GB HDD, the root partition is 70GB, so there is plenty room. I would like to see if 10.10 is to my liking (it is the RC so the bugs should be few in number and I don't mind sticking them on launchpad to help out). If I don't like it or don't think it warrants bumping my LTS then I won't, but to really find out I need a proper (not VM/ LiveCD) install.
If I am possibly going to screw it all up I'll give it a miss. Don't mind a bit of mucking about, but don't want to have to start from scratch!

---

### Post by migs73 on 2010-10-03
Bump

---

### Post by Elfy on 2010-10-03
Personally I would do the partition stuff in the partition editor before I started the installer - but I think that when you do the install alongside the new install gets put in the right hand partition.

BUT if you do it that way I am not sure you'll be able to specify the exisiting /home, this brings us back to "Personally I would do the partition stuff in the partition editor..."

So - I'd do that :) Shrink the existing root then use the manual partition option to select your new / and exisitng /home partitions.

---

### Post by migs73 on 2010-10-03
> **forestpiskie said:**
> Personally I would do the partition stuff in the partition editor before I started the installer - but I think that when you do the install alongside the new install gets put in the right hand partition.

BUT if you do it that way I am not sure you'll be able to specify the exisiting /home, this brings us back to "Personally I would do the partition stuff in the partition editor..."

So - I'd do that :) Shrink the existing root then use the manual partition option to select your new / and exisitng /home partitions.
Thanks for your help, I won't have time to give it a try till tonight, but if I read you right;
Create new partition in my existing root partition (use Gparted from Livecd)
Install 10.10 into the new partition.
Do I need to give it a new home, or if not, when I specify to use my existing home will it leave it as it is?
Again thanks for your assistance,

Mike

---

### Post by slakkie on 2010-10-03
There is one issue if you share your home dir with 10.04 and 10.10: Thunderbird (if you use it). 10.10 has 3.1.4 and 10.04 has 3.0.8. and they don't play nice together.

This is what I would do (if I was you):

1.a) Download the clonezilla LiveCD to backup your currect disk/OS.
1.b) Boot from clonezilla and backup your disk/OS.

2.a) Get the liveCD from gparted
2.b) Boot from the gparted livecd and partition your disk accordingly

3) Install 10.10 and check it out (be sure to select the correct /home, and don't format it!).
4) Remove 10.04 if needed, otherwise remove 10.10

Again, be aware of Thunderbird 3.1.x, since 3.0 cannot deal with the changes.

The other option, since you backup your OS/disk (you are going to do that right?), just upgrade to 10.10 and see if that works, and if you don't think it is ready, just restore your backup. That is what I have been doing and it works for me.

---

### Post by Paqman on 2010-10-03
> **migs73 said:**
> 
Do I need to give it a new home


Nope, just create a new account for your new install so that all the user files are in a different folder.

> 
when I specify to use my existing home will it leave it as it is?


Yes, if you're in "advanced partitioning" and you tell the installer not to format that partition.

---

### Post by migs73 on 2010-10-03
> **Paqman said:**
> Nope, just create a new account for your new install so that all the user files are in a different folder.



Yes, if you're in "advanced partitioning" and you tell the installer not to format that partition.

Bit the bullet and went for it. Writing this from Maverick, and I can still boot Lucid, only problem is I must have mucked up one of the partition set up sections as Maverick does not use my home partition. Never mind at least I can give it a good try.
I'll need to find out how to do it if actually do change to Maverick, but I'll leave it for know.
Thank you all for your help.

---

