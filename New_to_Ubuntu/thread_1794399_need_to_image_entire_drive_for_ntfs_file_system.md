---
title: "need to image entire drive for ntfs file system"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-06-30
I recently made a deal with someone for some old computers. I would recover any data that is on the drives and would try to get one fired up to give back to him, in exchange for all the rest of it.

I also have a desktop machine that does not have any o/s installed on it. (I just put it back together and have other plans for it than a regular o/s). All drives are ide so I decided I would just plug ea drive into that desktop, one by one, and use live cd's and tools to harvest the data from each; and, hopefully, store a raw image on my external usb drive. (Once images for each disk is on that external I can plug it into my laptop that is fully operational and burn them onto dvd with a gui app).

So here's the thing, this guy used Winblows. My first thought was to run Knoppix and use the dd command to make the image. I find out through gparted live though that it is an NTFS file system.

Here's the script I used on **my own, Linux system,** recently to image my drive:

```

dd if=/dev/sda of=/media/Lacie/Backup/HostClone/HostClone.img conv=notrunc,noerror bs=512

```

And these are my questions:

~ Can dd even be used on an NTFS file system?
~ If so, how would that code above be modified so that it is correct?
~ Without a linux File system, will my external usb even show up when I plug it in? (I think it would because Knoppix will have a file system associated with it.
~ Does Knoppix mount usb to the /media folder like Ubuntu does? If not, where does it?

If anyone can help and has a solution I would sure appreciate it. I'm tired fo fiddling around with this project and just want to get it done so I can play with my newly acquired parts.   :)

Thanks guys.
-----------------------

Edit:

I just tried to run Knoppix on the thing and it will run live on the machine; but, when I try to run bash it tells me 'file system not recognized' or something like that.

There has to be an easy way to image this drive.

Here's the software tools I have at my disposal

~ Clonezilla Live (which I'm trying to avoid using because I don't think it gives a straight 'raw' image)
~ Ultimate Boot CD 5.0.3
~ Knoppix, of course
~ Ubuntu 10.04 (which will run live)
~ Parted Magic
~ Oh! And "SMART Ubuntu" also

How can I do this guys?

---

### Post by dFlyer on 2011-07-01
Download clonezilla, it should be able to clone your whole systems.

---

### Post by dFlyer on 2011-07-01
You might want to try Macrium Reflect. It also works great. Here is a link.

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by ClientAlive on 2011-07-01
> **dFlyer said:**
> Download clonezilla, it should be able to clone your whole systems.


Yeah, I have Clonezilla Live and could use it but I wonder if that will cause a problem for him when I give him this image created with a Linux distro.

I'm also trying to think of what the easiest thing for that guy will be to access his recovered data. I mean I'm specifically trying to think whether a raw image is the best thing for him, if I should give him something else, or even if I should provide him with a couple different options. I can give him a copy of Clonezilla Live but is it going to work on a windows system for him when he tries to do something with that recovered data?
----------------------

Edit:

Another thing is that one of those drives is 80 gig, yet only has 3 gig of data on it. Clonezilla (or, I think, any other method of making a raw image) will cause the person to need 80 gig of fee space wherever he tries to restore to (not just the 3 gig).

I thought about using parted magic to create a partition in the unused space, just slightly over the size of the data. Move/ copy the data over to that partition and then make an image of just that partition (would make the restore require less total space). The problem is I'm a little leery of doing anything invasive on that drive. What if some change I make to it causes data loss?

---

### Post by jtarin on 2011-07-01
I carry a 1GB flash drive around with me just for backup and rescues. I have done this for several years. On this drive I have installed [Paragon Partition Manager]("http://www.paragon-software.com/home/br-free/") (free edition). It is by far the best freeware I have come across for backing up and restoring. It's Linux based and boots into ram....other tools are included. Can backup, restore and make partitions. You'll need windows to create the USB.
Give the guy an image and the application.

---

### Post by dFlyer on 2011-07-01
Macrium relect is windows based, but uses linux for the restore cd. I use it to clone my daughters windows7 for when she gets a virus. Easier to restore if I can't clean it than reinstall windows. Usually less than an hour for a complete restore.

---

### Post by ClientAlive on 2011-07-01
> **jtarin said:**
> I carry a 1GB flash drive around with me just for backup and rescues. I have done this for several years. On this drive I have installed [Paragon Partition Manager]("http://www.paragon-software.com/home/br-free/") (free edition). It is by far the best freeware I have come across for backing up and restoring. It's Linux based and boots into ram....other tools are included. Can backup, restore and make partitions. You'll need windows to create the USB.
Give the guy an image and the application.


> **dFlyer said:**
> Macrium relect is windows based, but uses linux for the restore cd. I use it to clone my daughters windows7 for when she gets a virus. Easier to restore if I can't clean it than reinstall windows. Usually less than an hour for a complete restore.


Ok, well these sound like fine options. In fact, I think we've cleared my initial questions; but, there is this one, last thing.

I'm wondering if either of these will still require restore space equal to the entire size of the disk (80 gig is nothing to just wink at). He's gonna have to deal with that if I use Clonezilla and I'm not sure whether this is the case with iso images in general. I kind of think it is.

So is there an option that only copies the 3 gig of data and not the entire 80 gig drive (mostly unused space)?

I know I can go through the whole hassle of using zero free on the iso and deleting the unused space to shrink the thing but that's exactly what it is - a hassle. There's gotta be an easy way to do this that's fast.
---------------------

Edit:

From what I see on Macrium's site I don't gather that this thing runs live and that's the only kind of solution that would work for me. I don't have windows installed on any of my machines and putting it on there is the last thing I'd want to do. Even creating a vm of windows kinda grosses me out (no offense). I hope I can just use some live tool to do this and do it in a way that makes it convenient for the owner to deal with the end result.

---

### Post by dFlyer on 2011-07-01
Macrium reflect can be restored to any size disk provided there is enough space for the image. I clone her drive to 60 gig disk and restore to 320 gig disk.

---

### Post by jtarin on 2011-07-01
> [Restore an entire disk, separate partitions or only files you need from the previously created backup image]("http://www.paragon-software.com/home/br-free/")Don't take my word for it.

---

### Post by dFlyer on 2011-07-01
> **ClientAlive said:**
> Ok, well these sound like fine options. In fact, I think we've cleared my initial questions; but, there is this one, last thing.

I'm wondering if either of these will still require restore space equal to the entire size of the disk (80 gig is nothing to just wink at). He's gonna have to deal with that if I use Clonezilla and I'm not sure whether this is the case with iso images in general. I kind of think it is.

So is there an option that only copies the 3 gig of data and not the entire 80 gig drive (mostly unused space)?

I know I can go through the whole hassle of using zero free on the iso and deleting the unused space to shrink the thing but that's exactly what it is - a hassle. There's gotta be an easy way to do this that's fast.
---------------------

Edit:

From what I see on Macrium's site I don't gather that this thing runs live and that's the only kind of solution that would work for me. I don't have windows installed on any of my machines and putting it on there is the last thing I'd want to do. Even creating a vm of windows kinda grosses me out (no offense). I hope I can just use some live tool to do this and do it in a way that makes it convenient for the owner to deal with the end result.

That will rule of Macrium. It must be installed on windows to clone, but uses a live cd to restore. Sorry.

---

### Post by ClientAlive on 2011-07-01
> **jtarin said:**
> Don't take my word for it.


Looks like a wonderful tool. Thank you jatarin for the link. But . . .

1) I have to install Windows on my machine to do it? A several hour process that I may then have to deal with when I go to put XCP on the machine - it's real purpose in life.

2) (1) Is pretty much moot anyhow since the only machine I have capable of accessing those drives is the desktop I mentioned which has no o/s installed on it. (No offence, but I'd rather brush my teeth with a cheese grater than install Winblows on that desktop - I'm sure you understand).

* What about using rsync? It would only copy the used space right? I would use Knoppix for something like that but it's wierd. Apparently it tries find a home directory on the drive to mount rather than having on in and of itself.

---

### Post by GMachine_24 on 2011-07-01
Clonezilla live will copy a drive/partition (your choice) sector by sector - so it's not really whether it can *create* a Windows clone or not - Clonezilla doesn't care; it just copies the info on a drive or partition (or both) to a new drive/partition.

The problem: As far as I know, and I believed I checked on this again last week, you can only clone/copy a 40GB drive/partition to a 40GB drive/partition - they need to be the same size. Of course you can create a partition that is the same size as your original partition/drive - but you would need a Windows CD to do this; having said that, I'm sure 'someone' you know has one - 

back in the day you could create a windows boot disk from this site: [http://bootdisk.com/](http://bootdisk.com/) 

it's still up but I haven't tried their stuff in years.

If I had to do it, I'd try the resource user jtarin advocated. It sounds like it has exactly what you need.

And, as far as USB drives go, I kinda think FAT32 is the default file system they are "universally" read/writable.

---

### Post by jtarin on 2011-07-01
You don't have to install windows only use a windows machine to create the USB. I understand your position. I only use this tool after trying all the others. Someone will come along if you only want to use Linux tools for this and help. I don't recommend anything else. Like I've said...I've tried them and this suits my purpose exactly.

---

### Post by GMachine_24 on 2011-07-01
There is one more thing I can think of:

If you have an iso file on a cd or dvd, or wherever, you can use the archive program in Ubuntu to pretty much just rip all the files onto a (fill in the blank) hard drive. Maybe everyone knows this - I just stumbled upon it when trying to copy something.

Hope at least something helps.

---

### Post by jtarin on 2011-07-01
I am downloading the newest version as we dialog here and it is telling me that it is a Dos/Win executable????? Interesting!....but it also says the download is .msi......so it needs a ms installer.

---

### Post by ClientAlive on 2011-07-01
> **jtarin said:**
> I am downloading the newest version as we dialog here and it is telling me that it is a Dos/Win executable????? Interesting!....but it also says the download is .msi......so it needs a ms installer.

I'm not sure I understand what you're getting at. Sorry, I am a bit of a newb. I do have wine on 'this' machine but it doesn't help me without having a drive enclosure (this is a laptop - I was using the fact that that desktop over there is all opened up and all I have to do is plug and unplug each drive right into the mobo.

It's a complicated sitch for me. While I am invested in doing a good job for the guy, there is a limit. I probably should have some installation of Widows one of these days though. If I keep this kind of work up I'm sure I'll need it.

I do really appreciate your help jtarin. I think that app is something that belongs in my toolbox - that's for sure - just maybe not tonight.


> **GMachine_24 said:**
> 
Hope at least something helps.


It does. I'm not trying to be difficult - really, That's why I've refrained from really going into a lot of fluffy detail about the specific concerns and objectives I have. I may end up having to just let him deal with Clonezilla and 80 gig.

> **GMachine_24 said:**
> 
There is one more thing I can think of:

If you have an iso file on a cd or dvd, or wherever, you can use the archive program in Ubuntu to pretty much just rip all the files onto a (fill in the blank) hard drive. Maybe everyone knows this - I just stumbled upon it when trying to copy something.


I would like to look into this a little more. This sounds like it might be a nice solution under the circumstances right now. Do you know what program it is a part of? I tried "man archive" but that is not the name of the program in ubuntu. Is it an option for one of the other commands like cp or rsync or something?

---

### Post by ClientAlive on 2011-07-01
Well I think I just realized something but I'm not sure I'm right about it. You talk about an iso on a cd or dvd. So then, if I have an iso image that is 3 gig of used space/ data and 80 gig total space, I can still burn that onto a 4.7 gig dvd because the image is still only 3 gig? That the issue of total drive size only comes into play when restoring the image?? If that is correct then I can totally see the logic in burning to dvd then just copying over the contents. That would make sense. Question is whether I'd be trying to burn 80 gig or 3 gig though.

---

### Post by GMachine_24 on 2011-07-01
> **ClientAlive said:**
> I'm not sure I understand what you're getting at. Sorry, I am a bit of a newb. I do have wine on 'this' machine but it doesn't help me without having a drive enclosure (this is a laptop - I was using the fact that that desktop over there is all opened up and all I have to do is plug and unplug each drive right into the mobo.

It's a complicated sitch for me. While I am invested in doing a good job for the guy, there is a limit. I probably should have some installation of Widows one of these days though. If I keep this kind of work up I'm sure I'll need it.

I do really appreciate your help jtarin. I think that app is something that belongs in my toolbox - that's for sure - just maybe not tonight.




It does. I'm not trying to be difficult - really, That's why I've refrained from really going into a lot of fluffy detail about the specific concerns and objectives I have. I may end up having to just let him deal with Clonezilla and 80 gig.



I would like to look into this a little more. This sounds like it might be a nice solution under the circumstances right now. Do you know what program it is a part of? I tried "man archive" but that is not the name of the program in ubuntu. Is it an option for one of the other commands like cp or rsync or something?



Applications>Accessories>Archive Manager

---

