---
title: "partition and installation question"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by launchy on 2011-04-25
hi,

i have created a partition using the built in windows 7 partition tools and created a new volume G: and formatted it to NTFS, which route should i take considering im a newbie?: 

1. install them side by side choosing between them each startup
2. erase and use entire disk
or 
3. specify partitions manually?

and pls tell if i did something wrong in my partition process.

thanks

---

### Post by Dutch70 on 2011-04-25
What version of Ubuntu are you talking about? 10.04, 10.10, or 11.04 which is scheduled for official release on April 28th.

Create a live cd or usb stick, and try Ubuntu to make sure it runs well on your hardware. This will also allow you to be online during the install, because you can also install from there.

If you've already created a partition for it. You will need to do everything else from the live cd/usb. 

C,D,G, these are windows drive letters & don't really mean anything in Ubuntu. They will be named sda1, sda2, etc. A 2nd physical hdd, would be named sdb.

I believe you would need to select partitions manually since you already have your hdd partitioned. It will need to be formatted to ext3 or ext4.

---

### Post by launchy on 2011-04-25
im gonna use 10.04 since im not liking the unity interface.
alrite will make sure hardware works fine first,
 but on this video that i found:
 [http://www.youtube.com/watch?v=OIoR7yp_nYc](http://www.youtube.com/watch?v=OIoR7yp_nYc), he did not format it, just left as free unallocated space and when he boot it up and install it [http://www.youtube.com/watch?v=KSXJQ2zFJ4U&feature=related](http://www.youtube.com/watch?v=KSXJQ2zFJ4U&feature=related) at 1.58 of the video select the largest free space, does this work too vs having a formatted NTFS partition? 
i mean if i have it formatted as NTFS in windows, what steps should i take on the installation part involving the partitions?

---

### Post by Dutch70 on 2011-04-25
Looks like what he's doing in that video is fine. 

To be honest, I'm not sure if it will format it for you that way, or if you will need to open Gparted and format it there. Either way it's fairly simple.

Boot up your live cd/usb and see if you've got Gparted installed. I believe it's under System>>Administration>>[COLOR="Red"]G[/COLOR]nome [COLOR="red"]PART[/COLOR]ition [COLOR="red"]ED[/COLOR]itor

---

### Post by launchy on 2011-04-25
so ur saying to format the free space to the correct ext4 thing for ubuntu at the live cd environment and then proceed to the installation?

---

### Post by Dutch70 on 2011-04-25
That is what I would do...yes.

Just open Gparted, right click the partition & select "format to ext4". Be sure to format the correct partition. It's best if you know the size as they will not be called C,D,E...etc.

LOL, spammer didn't last long did he/she. :)

---

### Post by launchy on 2011-04-25
alrite thanks! yah i was like wtf O___O

---

### Post by Dutch70 on 2011-04-25
Yeah, I reported them and they were gone before I could edit my post to tell you not to give them the pleasure of clicking a any links. 
Not that it would have done any harm. It's the principle of the matter. We didn't come here to check out advertisements.

---

### Post by flemur13013 on 2011-04-25
> **launchy said:**
> so ur saying to format the free space to the correct ext4 thing for ubuntu at the live cd environment and then proceed to the installation?

> [http://www.youtube.com/watch?v=OIoR7yp_nYc](http://www.youtube.com/watch?v=OIoR7yp_nYc), he did not format it...Use your windows tools to get the disk back to 1 partition (as it was before you created the new one, G: and select "install side by side". Like in the video.

Then the installer knows that Windows exists and it will also make a Linux partition from part of the largest existing partition.  

If, instead of "side by side", you choose to "Select" the new partition you made, you're liable to lose your windows install.  I've gone thru this myself recently a few times and the installer *should* have a choice of "side by side" AND "select partition"; every time I Select the partition I have to fix the bootup afterwards.

---

### Post by Sunfist on 2011-04-26
I just installed Ubuntu on my new computer that came with Win 7 already installed and this is how I did it. I used the Win 7 partition editor to shrink the windows partition by 50gb (that's just what I chose to use for Linux). Then I ran the live Ubuntu CD and selected that partition and divided that down to a 40 and a 10gb partition, then ran install. Selected the option to manually select partitions, picked the 40, formated and made that the root (\), selected the 10 and made that the swap partition and away we went. I can further break down the root to add home or other options later but I am up and running just fine as is.

---

### Post by K_45 on 2011-04-26
> **Sunfist said:**
> I just installed Ubuntu on my new computer that came with Win 7 already installed and this is how I did it. I used the Win 7 partition editor to shrink the windows partition by 50gb (that's just what I chose to use for Linux). Then I ran the live Ubuntu CD and selected that partition and divided that down to a 40 and a 10gb partition, then ran install. Selected the option to manually select partitions, picked the 40, formated and made that the root (\), selected the 10 and made that the swap partition and away we went. I can further break down the root to add home or other options later but I am up and running just fine as is.

 10GB is way too much for swap . . .

---

### Post by Dutch70 on 2011-04-26
Sunfist is right about 1 thing, there is a box you can check to format it as you install. Although it won't hurt & is easy enough to format with Gparted. K_45 is also right, 10GB is too much swap unless you have 9-10GB of RAM. Your swap partition only needs to be equal to your physical RAM (slightly larger for overflow if you want) unless you have less than 1GB of RAM. Then make it double your RAM. 

However, in Sunfist's case with only 50GB of hdd space, I would have used a swap file instead of a swap partition.

---

### Post by Sunfist on 2011-04-26
Actually I do have 8gig of memory so I though 10g swap would be about right..its certainly not going to hurt anything and I have tons of HD space left it's not like I am going to run out anytime soon.

---

### Post by launchy on 2011-04-27
thanks for all suggestions! i followed the video posted and worked without any hassles didnt break my win7 either!
loving ubuntu!! <3

---

### Post by Dutch70 on 2011-04-27
Great, glad to hear it worked out well for you. Thanks for letting us know & marking the thread solved. :)

---

