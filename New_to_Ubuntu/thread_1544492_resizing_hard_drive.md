---
title: "resizing hard drive"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by beew on 2010-08-02
Hi, 

I have installed Ubuntu 10.04 on a 35 G hard drive with 15G for  the ./ directory and 20G for ./home.  The ./ partition is to the left (in front of ) the ./home partition. I am not experienced in this and many online tutorial I found recommend a 10 to 15 G for the ./ directory and a large ./home directory for data. But now I realize that I should have made a bigger partition for ./ instead because almost all my programs end up there instead of ./home and I don't really have that much data (unlike most normal people I don't care for junks like family photographs :pand I store my music and ebooks in  an external drive. The data files I work with  can't be more than 2 G at the moment and it may grow to no more than 6 to 8 G even by the most generous estimation) 

So now I am thinking of expanding the ./ partition at the expense of  ./home . I am wondering if it is possible to do that without losing my local settings (I don't really care for the little data  that I have as I can easily move them somewhere else)

Thanks.

---

### Post by sandyd on 2010-08-02
> **beew said:**
> Hi, 

I have installed Ubuntu 10.04 on a 35 G hard drive with 15G for  the ./ directory and 20G for ./home.  The ./ partition is to the left (in front of ) the ./home partition. I am not experienced in this and many online tutorial I found recommend a 10 to 15 G for the ./ directory and a large ./home directory for data. But now I realize that I should have made a bigger partition for ./ instead because almost all my programs end up there instead of ./home and I don't really have that much data (unlike most normal people I don't care for junks like family photographs :pand I store my music and ebooks in  an external drive. The data files I work with  can't be more than 2 G at the moment and it may grow to no more than 6 to 8 G even by the most generous estimation) 

So now I am thinking of expanding the ./ directory at the expense of the ./home folder. I am wondering if it is possible to do that without losing my local settings (I don't really care for the little data  that I have as I can easily move them somewhere else)

Thanks.
yeah, its possible. Boot up from a ubuntu livecd.
Go to System -> Administration -> Gparted

Right click on the "home" partition and click resize.
You will see a slider there. drag the LEFT hand slider to the right until you believe you have freed enough space.

then click "ok"

Right click on the roo (/) partiition and choose resize.
On the RIGHT hand side of the slider, drag, it to the right.
click "ok" and then click the checkmark to apply

---

### Post by marshmallow1304 on 2010-08-02
Yes, it is.  Simply boot up the LiveCD used to install the system, select "Try without installing..." and run System->Administration->GParted.  You'll be able to shrink your /home on its left side then expand your / on its right.  The procedure will probably take a while, so be prepared for that.


Here's a [guide]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") that may be helpful; though it's for resizing a Windows partition, the same method can be used for any type of partition.

---

### Post by beew on 2010-08-02
Thanks guys for the speedy reply. But I read somewhere that you can't move  a partition on the left side, only on the right. Maybe you only cannot expand to the left but you can shrink from the left side?

---

### Post by sandyd on 2010-08-02
> **beew said:**
> Thanks guys for the speedy reply. But I read somewhere that you can't move  a partition on the left side, only on the right. Maybe you only cannot expand to the left but you can shrink from the left side?
see screenshot

---

### Post by oldfred on 2010-08-02
You can move partitions left, I just try to avoid it if possible as all the data has to be moved which is slow and slightly higher risk. Always with partition editing make sure you have good backups.

Real question. With 15GB how are you running out of space?

I generally recommend 10-20GB for / especially if /home is separate. My root has lots of programs and is only 6GB, my /home is 1GB and data is in separate data partitions.

---

### Post by beew on 2010-08-06
Ok, guys,

I think I am in trouble. 

I shrinked the /home partition (the partition on the right) on the left end and it worked as you guys say it would. But now I am having problems in expanding the left hand partition (/) into the unallocated space that has been created on its right. 

So the configuration now is basically: / partition on the left, unallocated in the middle, a shrunken /home partition on the right and I want to expand the / partition into the unallocated space. 

Gparted's "resize" option somehow can only shrink but not expand apparently. Help..!

---

### Post by beew on 2010-08-06
carlee

> Right click on the roo (/) partiition and choose resize.
On the RIGHT hand side of the slider, drag, it to the right.
click "ok" and then click the checkmark to apply                                                                                               Here is the problem. Even though I choose "resize/move" the right border of / doesn't move to the right.  Please see the screenshot.

---

### Post by Bachstelze on 2010-08-06
> **beew said:**
> carlee

Here is the problem. Even though I choose "resize/move" the right border of / doesn't move to the right.  Please see the screenshot.
That's because the Extended partition (light blue) is in the way. You have to resize it first.

---

### Post by beew on 2010-08-06
> **Bachstelze said:**
> That's because the Extended partition (light blue) is in the way. You have to resize it first.

Oh I see!! Thanks a million. It seems to be working now.

---

