---
title: "How to use unallocated space Safely in GParted"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by zenawenliang on 2011-03-26
Ok after much questions I found out that Im just gonna try to use my unallocated space and add it to ubuntu, So tell me how can I SAFELY add that unallocated space

[IMG]http://i56.tinypic.com/2zxzb7l.png[/IMG]

---

### Post by samcot on 2011-03-26
I suppose you mean that you want to add in the unallocated space without affecting your current Ubuntu installation? I really like GParted, and I've been using it quite a bit, but I haven't experimented with adding space to existing partitions.

---

### Post by jerome1232 on 2011-03-26
Before you messaround with partition editing, ALWAYS backup your data, there's always a chance something will go wrong (like gremlins cutting power to your machine during the process)



Anyways you should be able to "move" sda5 all the way to the left up against the begining of your extended partition sda3. This will take a very long time as gparted has to copy the partition and all of the data to a new location, including free space.

Once that is complete you can then drag the edge of sda5 to the right to extend the partition and grow the filesystem.

I'm going to emphasize backup'ing up. While this is a fairly safe procedure, data is much to valuable to risk to accidental "oops didn't want to delete that partition", or other mishaps.

edit: Also you'll have to do all of this from an Ubuntu live CD or a Gparted live cd, since the partitions can't be mounted during the process. Did I mention you should make backups?

---

### Post by zenawenliang on 2011-03-26
Alright, but how do I "Move" the partion over?

---

### Post by jerome1232 on 2011-03-26
See my edit, it's been awhile since I've used gparted but there is a move partition button in there somewhere, I'll start my virtual machine and see if I can make screenshots of it.

---

### Post by Miljet on 2011-03-26
I think someone has already mentioned this in answer to your many posts, but you can not resize a partition that is in use. So you will need to boot from a live CD so your Ubuntu partition is not mounted. Or from a gparted CD.

After you open gparted, click on the partition you want to change ( in this case sda5), click resize from the top menu, then click and drag the Left edge of sda5 to the left so it includes the unallocated space. Then click apply from the top menu.

It will take a long time to complete. Anytime you expand a partition to the left, everything in the partition has to be rewritten.

---

### Post by Rasa1111 on 2011-03-26
If you don't have much data on your Ubuntu install..
(it doesn't appear so)..
to be honest..
 I would just save whatever files I want to keep, (say, to a folder on an external drive named "Home")- 
pop in the CD and do a fresh install and use the entire HDD. 

Once install is finished, drag the contents I saved to the external in the "home" folder i made, to the "Home" folder in Ubuntu.
and do my updates, install my apps/programs, and call it a fresh, new ubuntu machine!  lol

This way i know for sure that *_everything windows_* has been removed, and the only thing on my HDD is Ubuntu. :)
and I also know that everything is installed/partitioned properly so there is less chance of failure in the future. 

If this doesn't sound useful to you, Please disregard. lol

 Congrats on ditching windows! :D
I did it a little over a year ago..
and have never been happier with my computers! :)

Have fun.
 Peace

---

### Post by jerome1232 on 2011-03-26
First boot from an Ubuntu Live CD, select "Try Ubuntu"

Get into Gparted and...

Select the partition you want to edit, click the "resize/move" button it looks like an arrow point to the right at a line, then to move the partition you grab it's center and move it toward the left or right, to resize you grab it's right or left hand side and drag it right or left.

So you may be able to simply grow it to the left instead of having to move it then grow it to the right.

I couldn't easily get screen shots while in a live cd in a virtual machine, so hopefully you get it from that.


I see other's chimed in while I was playing with my virtual machine, I'll leave this up anyways.

---

### Post by samcot on 2011-03-26
I like the way you're thinking, Rasa. After all, he just installed Ubuntu, so how much could he need to backup? Perhaps nothing! It sure would be faster and easier the way you suggest.

---

### Post by zenawenliang on 2011-03-26
Ok I loaded up my livedisk, I went to linux-swap right clicked clicked swapoff, then I resized my sda5 to use the allocated space, then I increased my linux-swap to 3 gigs, because I have 3gs ram.

[IMG]http://i53.tinypic.com/23mk0m1.jpg[/IMG]

---

### Post by Miljet on 2011-03-26
Congratulations, see how easy that was?

---

### Post by zenawenliang on 2011-03-27
It isnt working out, getting errors, just gonna wipe windows off clean install

---

### Post by samcot on 2011-03-27
Why would you wipe out the Windows partitions?

---

### Post by Rasa1111 on 2011-03-27
> **zenawenliang said:**
> It isnt working out, getting errors, just gonna wipe windows off clean install

Good idea! :)

samcot~ he is getting rid of windows and going all ubuntu! :D lol <3

---

### Post by samcot on 2011-03-27
Throwing Windows out the window, eh? So breaking a mirror is bad luck, but breaking windows is good luck? :-)

---

### Post by beew on 2011-03-27
> **zenawenliang said:**
> It isnt working out, getting errors, just gonna wipe windows off clean install

What error? I told you on the other thread that moving the left end of the boot partition to the left may not be safe,--as oppose to moving the right end,--, is this what happen? I am curious to find out if this is the case. Thanks.

---

### Post by jerome1232 on 2011-03-27
> **beew said:**
> What error?


Agreed, what are the errors?

---

