---
title: "Resizing Partitions?"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by mickeymouseatlinux on 2011-07-27
Sorry if this has been posted before, I couldn't find anything that helped my situation.

Hey, some of you might have read my thread of accidently deleting Windows Vista ...

Well, I've come to enjoy ubuntu, but I guess whilst I was playing around with the installation, I must have made my disk space really low? (Yeah, once again, I'm really bad with this I.T stuff... Sorry!)

anyway, searching through the internet, I found out that I'm to download Gparted - Done! :D

So my question is ... now what? I'm faced with this menu:
[ATTACH]198593[/ATTACH]

From what I've heard, it should be simple, but I guess I'm too 'nooby' to understand, as you can see, I've a lot of free space, I'm wanting to expand my dev/sda1

---

### Post by mickeymouseatlinux on 2011-07-27
anyone able to help?

---

### Post by amjjawad on 2011-07-27
> **mickeymouseatlinux said:**
> Sorry if this has been posted before, I couldn't find anything that helped my situation.

Hey, some of you might have read my thread of accidently deleting Windows Vista ...

Well, I've come to enjoy ubuntu, but I guess whilst I was playing around with the installation, I must have made my disk space really low? (Yeah, once again, I'm really bad with this I.T stuff... Sorry!)

anyway, searching through the internet, I found out that I'm to download Gparted - Done! :D

So my question is ... now what? I'm faced with this menu:
[ATTACH]198593[/ATTACH]

From what I've heard, it should be simple, but I guess I'm too 'nooby' to understand, as you can see, I've a lot of free space, I'm wanting to expand my dev/sda1


24.21GB SWAP Partition? this is way too much and you do NOT need that.

Run Ubuntu from the LiveCD, Start GParted, remove sda5 (your swap) - I guess you need to right click and select swap off. Then Remove sda2 (the extended partition). Click Apply.

Now, try to increase the size of sda1. If Ubuntu is all what you'll install and use on that machine, try to use the whole thing and leave 1-2GB for SWAP.
Here some info about swap: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you are planning to install another system, that's different story and has totally different scenario.

After you are done, I think you need to edit your fstab to add the new swap partition.

If this is Fresh New Installation, you can wipe the whole thing and start all over.

Here is some info about partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

How to edit fstab:
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+edit+fstab&as_qdr=all&sa=Google+Search&lang=en#1114](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+edit+fstab&as_qdr=all&sa=Google+Search&lang=en#1114)

---

### Post by Redblade20XX on 2011-07-27
Take a look at this:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

-Red

---

### Post by cloggyjohn on 2011-07-27
Hi Mickeymouse,

I've not used Gparted but it looks very much like EaseUS Partition Manager so I assume it operates similarly. Assuming you want the unallocated space added to the sda1 partition you first need to move the sda5 partition out of the way - place the cursor somewhere in the middle of that partition, press and hold the left-hand mouse button, drag the partition all the way to the right and release the mouse button. Now place the cursor over the right-hand *edge* of sda1 and drag this ( not the whole partition, that would only move it not increase the size ) in the same way until it is adjacent to sda5. Release the mouse button and click on Apply or some such similar command. Once Gparted has moved/resize everything you might have to re-boot your system.

WARNING: I've never had problems carrying out these operations but things *can* go wrong so ALWAYS backup your data beforehand.

Hope this is of some help.

Cheers

---

### Post by mickeymouseatlinux on 2011-07-27
> **amjjawad said:**
> 24.21GB SWAP Partition? this is way too much and you do NOT need that.

Run Ubuntu from the LiveCD, Start GParted, remove sda5 (your swap) - I guess you need to right click and select swap off. Then Remove sda2 (the extended partition). Click Apply.

Now, try to increase the size of sda1. If Ubuntu is all what you'll install and use on that machine, try to use the whole thing and leave 1-2GB for SWAP.
Here some info about swap: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you are planning to install another system, that's different story and has totally different scenario.

After you are done, I think you need to edit your fstab to add the new swap partition.

If this is Fresh New Installation, you can wipe the whole thing and start all over.

Here is some info about partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

How to edit fstab:
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+edit+fstab&as_qdr=all&sa=Google+Search&lang=en#1114](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+edit+fstab&as_qdr=all&sa=Google+Search&lang=en#1114)


Hi, thanks for the reply.

I tried to do what you've asked, but I am unable to resize /dev/sda1 , infact, the only options I have is to Unmount and manage flags.

---

### Post by amjjawad on 2011-07-27
> **mickeymouseatlinux said:**
> Hi, thanks for the reply.

I tried to do what you've asked, but I am unable to resize /dev/sda1 , infact, the only options I have is to Unmount and manage flags.

Are you running GParted from the LiveCD? you can't do anything while you are logged in to Ubuntu.

---

### Post by mickeymouseatlinux on 2011-07-27
Sorry, must have missed that part, It's worked, thank you very much! :D

---

### Post by amjjawad on 2011-07-27
> **mickeymouseatlinux said:**
> Sorry, must have missed that part, It's worked, thank you very much! :D

It's ok :)

Can you please post a screen shot?

---

### Post by mickeymouseatlinux on 2011-07-27
[attach]198597[/attach]

---

### Post by XBMC old School on 2011-07-27
Hey Mick,

Please mark this thread as solved, for other n00bs to find.

---

### Post by amjjawad on 2011-07-27
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198597&d=1311776801[/IMG]


Great Job, well done :)

You can also create separate /home partition. It's not a must but recommended. I'm sorry, I forgot to mention that earlier.

[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Again, it's not a must :)


As for how to mark this thread SOLVED, this is how:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

