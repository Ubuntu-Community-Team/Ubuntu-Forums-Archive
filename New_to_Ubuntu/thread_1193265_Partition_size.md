---
title: "Partition size"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by SkipRat on 2009-06-21
Hi there, fairly new to unbuntu here...

I'm dual booting with windows xp, I've installed ubuntu with no problems.

When I go to update it says I don't have enough space on / to install the updates.

What do I do to enlarge the partition its installed on? (other than starting again)

Like I say, I'm not familiar with everything yet so a step by step would be very helpful. 

Thanks in advance :)

---

### Post by lindsay7 on 2009-06-21
First, defrag the drive using windows. This will insure (hopefully) the windows will be fine with the partition resizing.


Next. use Gparted to resize the partitions to you liking.  Any drives that you work on need to be unmounted and I have found the best way to do that is to use the Gparted live cd. Go to their web site and download and burn it to a cd. It will be bootable and you can go form there.

The other way is to use the Ubunut live cd and use gparted from there. right click on the drive you want to work on and unmount it. then do your work.  The Gparted web site has good tutorials on the process.

---

### Post by Gen2ly on 2009-06-21
+1 for lindsay7's comment.  Probably what you are going to have to do.

Also you can free a bit of space by deleting the downloaded package containers by:

```
sudo rm /var/cache/apt/archive/*.deb
```

You can see available diskspace with:

```
df -h
```

---

### Post by LewRockwell on 2009-06-21
gparted is also one of the included tools in this:

[http://www.partedmagic.com/](http://www.partedmagic.com/)

---

### Post by kansasnoob on 2009-06-21
> **SkipRat said:**
> Hi there, fairly new to unbuntu here...

I'm dual booting with windows xp, I've installed ubuntu with no problems.

When I go to update it says I don't have enough space on / to install the updates.

What do I do to enlarge the partition its installed on? (other than starting again)

Like I say, I'm not familiar with everything yet so a step by step would be very helpful. 

Thanks in advance :)

The most helpful information you could provide is a screenshot of Gparted, aka: Partitition Editor.  

Since space is a problem, and since resizing need be done from a live CD anyway, it might be best to simply boot the live CD and go to System > Administration > Partition Editor and take a screenshot, then attach it here.

Of course it may (or may not) be necessary to use something like Photobucket to accomplish this. Images can be attached simply using the paperclip icon at the top of these pages.

---

### Post by SkipRat on 2009-06-22
I'm on my laptop at the minute... I'm also having the same problem as in my first post though.

I'm making the partition size of Vista smaller.

Which one do I need to add to for the updates to have enough space?

Image is attached.

---

### Post by carml on 2009-06-22
If I would you, I would expand your sda3 by adding let say 4 Gb of space,just in case you have the idea to use Ubuntu often and save data or install new applications under Ubuntu.
All you need to do is to select the button named More/Resize and move the partition limit up to the wanted amount. 
If you have got any doubts, just post here :)

---

### Post by SkipRat on 2009-06-22
Thanks. I have dabbled with it many years ago. This time I'm going to spend some time learning stuff.

Options to change sda3 is greyed out. I'm booted in ubuntu at the moment using the live option from the cd.

---

### Post by Amilo1718 on 2009-06-22
an unallocated space of 47 Gig... :confused:

---

### Post by carml on 2009-06-22
> **SkipRat said:**
> Thanks. I have dabbled with it many years ago. This time I'm going to spend some time learning stuff.

Options to change sda3 is greyed out. I'm booted in ubuntu at the moment using the live option from the cd.

Of course you should use one of the methods suggested before to change your sda3.

---

### Post by SkipRat on 2009-06-22
> **Amilo1718 said:**
> an unallocated space of 47 Gig... :confused:


Yeah. I recently formatted my laptop entirely. Was going to have xp/vista/ubuntu on it so I've got some space left over :P


I don't really understand whats going on here :P As far as I can see the drive itself isn't mounted or anything... no drives are.

Do I need to try the gpart live cd or something?

Sorry for being a total annoyance with what to you guys must be obvious questions :( .

---

### Post by carml on 2009-06-22
Yes, use a LiveCD if you have one at your disposal or download Gparted Live to expand your sda3 partition.
You can also choose what partitions to mount automatically under Ubuntu at any boot,if you don't bother to have always Windows partitions mounted,you can mount them manually,and in general you can mount any partition you want to, under Ubuntu (or GNU/Linux in general). :)

---

### Post by SkipRat on 2009-06-22
Worked a treat :D Thanks very much for your time mate :)

No doubt I shall be back again.

---

