---
title: "should i upgrade to jaunty"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by kdreimiller on 2009-05-19
im totally stumped on this.  i ran the live CD tonight and it seemed to work fine, tho couldn't run video because it doesn't have the codecs.  but everything else seemed good - it even detected my second monitor, my wireleess (intrepid didnt), and printer, and sound worked fine.

my fear is that since i have an ati radeon 3100 vid card it wont work properly, namely the video. 

im using a toshiba satellite l305d series.  3 gigs ram, ati radeon 3100.  almost no problems in intrepid except that it seems a little sluggish lately.  the live cd seemed to run faster than my intrepid install.

and if i do upgrade and it doesnt work right, id like to be able to just revert back to my setup now, but i dont' know if thats even possible?

thanks,
kevin

---

### Post by Melk79 on 2009-05-19
Searching on your ATI card it does look like some jaunty users are having trouble with the driver.  I supposed you could create a separate partition and try it out there to keep your original install safe.  Can you install the restricted codecs while on the live cd and see how that works?

---

### Post by kdreimiller on 2009-05-19
yeah my card seems to fall into the gray zone.  

the live cd would search for the codecs, but it couldn't get them - im not sure why - maybe because the repositories weren't enabled?

how difficult would it be to create a new partition where i could install jaunty?  my skills are very sketchy at best.

---

### Post by Bradtek on 2009-05-19
It's usually easy to create another partition.
Is Ubuntu 8.10 the only OS on the computer ?
Or are you Dual Booting with Windoze ?

---

### Post by kdreimiller on 2009-05-19
100% intrepid.  i wiped vista when i found ubuntu.

do i create the partition in 8.10, or can i create it when installing from the live CD.  also, assuming jaunty works well, will i be able to access the partition that 8.10 sits in so i can access all my files?  and will i be able to migrate those files over if i want to switch over completely?

when i installed 8.10 i only created the 3 standard partitions, swap, ext3, and /.  i didn't creat a home partition

---

### Post by thraxsa on 2009-05-19
> **kdreimiller said:**
> 100% intrepid.  i wiped vista when i found ubuntu.


I love it !!!!

---

### Post by Bradtek on 2009-05-20
Because the partition will be in use while using Ubuntu you can only partition it with the Live CD, either run the partitioner from there or just do it during the install.

Not sure what choices it will give you if you already have Ubuntu, but I would assume it should be similar to installing dual boot with windows where it offers to do a 50/50 partition.
If it doesn't, just use the Manual option and set what ever size you thi nk necessary for 9.04

---

### Post by TransitMan on 2009-05-20
I installed Jaunty and run an "ancient" X300 ATI card that works just fine. While the ATI drivers/packages won't work, the RADEON packages in the repos do.
Because you're in this grey area, if you install Jaunty, use the Radeon driver/packages and you should have no problems.

---

### Post by nhasian on 2009-05-20
You'll want to boot off the liveCD and select the first option to boot ubuntu without making any changes to your hard disk.  Once ubuntu loads, go to System->Administration->Partition Editor.

Here you can resize a partition to make room for a new ubuntu install.  You can shrink your biggest partition (which is probably your / EXT3 partition)  I dont know how big your hard disk is, but 15Gigs for your new ubuntu install should be plenty of space to test it out.

On another note, I'd actually recommend against upgrading.  You said that your Ubuntu 8.10 Intrepid Ibex was working great.  Dont rock the boat!  Personally I like being on the cutting edge, and doing all the debugging that comes with it.  Really theres no killer feature that 9.04 has that you need to upgrade for.  I'd wait for 9.10 to come out in october if i were you :)

In 9.04 remote desktop is broken because of compiz, theres problems with some ATI & Intel graphics cards, some wifi adaptors that worked before dont work in 9.04, theres scratchy sound problems, and thats just off the top of my head.

> **kdreimiller said:**
> do i create the partition in 8.10, or can i create it when installing from the live CD. 

---

### Post by kdreimiller on 2009-05-20
sounds good.  thanks for the input.  i might give it a shot tomorrow.

good point nhasian.  intrepid seems a little sluggish lately and when i ran the live CD i was shocked how fast it ran from the CD no less and it made me want for system that doesn't seem sluggish.

---

