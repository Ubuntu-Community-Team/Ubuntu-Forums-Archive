---
title: "How do I upgrade from Iso image disc?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by DoctorLes on 2009-10-25
Hello,

I tried upgrading recently from within 8.1 to 9.04 and my HP desktop broke.  I had a dual boot with Win XP before that was working fine.  

Now I've somehow lost Grub and I boot automatically only to XP.  So I burned an Iso disc with 9.04 on it to see if I can get Grub back, do the upgrade installation and retain XP. 

When I start to install from the iso disc everything looks great up to a point; but I am confused at the partitioning configuration stage.  It asks me if I want to use the whole hard drive space, or install side by side with 8.04 still on my system.  BUT there is a little warning triangle saying that Windows will be wiped--seemingly no matter what option(s) I choose.  

I want to do an install from the iso disc but retain XP, as before.  I'm not sure how to do this without risking losing XP. I've fooled around with this thing all day and checked many forums but I haven't yet found clear, simple instructions on how to install from the iso disc and salvage XP while I already have an older version of Ubuntu still on my drive.  

Incidentally, I have an infamous Nvidia video card too; I think this is why my upgrade broke. 

Thanks

---

### Post by JDShu on 2009-10-26
Are you sure there was no third option where you could partition manually? It probably had "advanced" in brackets next to the option.

---

### Post by fancypiper on 2009-10-26
First I would run the CD test to make sure you have a good download and burn.

Then, when the partitioner starts, look for a manual partition and edit your partitions accordingly, choosing not to format your Windows and /home partitions.


[Ubuntu desktop manual partition guide]("http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide")

---

### Post by mapes12 on 2009-10-26
Read this then have another go: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

