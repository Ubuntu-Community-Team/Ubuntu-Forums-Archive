---
title: "Creating a live USB"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by johngreen12 on 2009-07-02
Hello.  I have been trying to create a live usb version of ubuntu because my parents don't ubuntu on the computer.  Whenever I try to create one to the specifications that I want, it seems to run into problems.  A friend of mine said that there is not limit to the allocation size of ubuntu on a flash drive, but whenever I try to make the size around 14Gbts, or close to that, it gets to ~4% completed and then says that it's done.  When I try to boot into the usb, it comes up with the normal startup screen, but after that it can't seem to find GNOME.  It can find GNOME only if I put the allocation size around 1Gbt, but then it doesn't shutdown or restart correctly... I'm really lost as to what the problem might be.  Any help would be greatly appriciated!  Thanks!

---

### Post by kylehotchkiss on 2009-07-02
Honestly, I have been the same boat as you sharing a computer with you parents. I now have two of my own to mess with ;) but for you, I would try a USB hard drive... it would be a little quicker and hold some actual data for you. And as far as parents go, they prolly wouldn't notice if you hide grub ;) ;)

---

### Post by johngreen12 on 2009-07-02
It's nice to hear that I'm not the only one with parents who don't want ubuntu.  :)  We have an external hard drive, but my family is using it for backing up the computer.  I got a 16 gigabyte flash for my B day and i thought that would be more than enough to hold me... but I keep on running into problems with getting ubuntu onto it.  Would you happen to know if there's a limit on how much you can tell your live flash to take up?  I don't think this matters, but I'm doing all of this off of the ubuntu disk, not of of a computer with ubuntu installed on it.  What do you think?

---

### Post by johngreen12 on 2009-07-07
anyone??

---

### Post by xc1024 on 2009-07-07
What do you want to do sounds less like LiveUSB and more like mobile Ubuntu INSTALLATION. If you want LiveUSB the easy way, try unetbootin. Should do the trick.

---

### Post by pizza-is-good on 2009-07-07
I know how to do it IN Ubuntu... So find someone that has Ubuntu, and create the live usb through it. 
 
I have done it before, to try Ubuntu 64 bit, and it worked flawlesly. I used gparted to split the flash drive into 2, one for the OS, and the other for data (I have a 4 GB drive).
 
What you can try is to burn a live CD, and use Ubuntu in the CD to create the live usb. The live CD has gparted, so you can do it all form there.
 
If you decide to do that, let me know, and I'll give you a step by step process.
 
Good luck.

---

### Post by johngreen12 on 2009-07-07
I've been trying to create a mobile version of ubuntu using a live cd.  I don't think the problem is with the cd because it passed the integrity test and it seems to work well when I'm using it.  Whenever I try to put ubuntu on the flash though, it always gets to about 5% and then says that it's done... then when I try to load it it loads ubuntu but it doesn't load the default gui.  (this is when the allocation size is at the most possible for the flash)  Thanks!

---

### Post by green-snake on 2009-07-07
Here is what worked for me not sure what you mean by live though, if you mean you can launch it from your usb then this should work as it did for me, I used Unetbootin here is the website. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Let me know if it works.

---

### Post by johngreen12 on 2009-07-08
Ok, I installed it from the iso file that I downloaded and created the live cd from.  When I rebooted it though, it said "Boot MGR is missing."  Any ideas?  Could it be that my iso file is corrupt?  I'm going to try having it downloaded again.  Thank you very much for the suggestion.  It looks very promising.

---

### Post by johngreen12 on 2009-07-08
I misread... it said "BOOTMGR is missing."  Does anyone know how to fix this?

---

### Post by pizza-is-good on 2009-07-08
Could I please ask that you quote whomever's message you are answering? That way we'll all know if it's our assistance you are wanting, or the person's of the other post.
 
Thank you

---

### Post by pizza-is-good on 2009-07-08
> **johngreen12 said:**
> I misread... it said "BOOTMGR is missing." Does anyone know how to fix this?
 
Does it give you that error after you boot the CD?
If so then there is probably somthing wrong with the CD, because it should come with a boot manager.
 
Try burning another one, or ordering one from the Ubuntu website. After you write, check the md5. The site you download Ubuntu from has the instructions on how to do that.

---

### Post by johngreen12 on 2009-07-08
I'm sorry about not just editing my previous message... I'm new to this forum and am still trying to figure out how things work.  Please bare with me.

About the error message, it reads "BOOTMGR is missing.  Press Ctrl + Alt + Del to restart."  This occurs when I'm attempting to boot from the flash drive.  The cd works perfectly and doesn't seem to give me any trouble... and I made the bootable flash drive from the iso file that I made the cd with.  I read about this kind of error on [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/).  I followed the directions for making sure that the flash drive partition is active but it didn't solve my boot error.  Do you know of any file that I could be missing or whatever would cause a BOOTMGR error message?  To solve it on windows vista I found that you would use the installation disk... could I somehow use the ubuntu disk for the usb in the same way?

I'll check the md5, but I really don't think that the problem is with the disk.  The disk works, the usb doesn't, and they were both derived from the same download.

---

### Post by pizza-is-good on 2009-07-08
> **johngreen12 said:**
> I'm sorry about not just editing my previous message... I'm new to this forum and am still trying to figure out how things work. Please bare with me.
 
About the error message, it reads "BOOTMGR is missing. Press Ctrl + Alt + Del to restart." This occurs when I'm attempting to boot from the flash drive. The cd works perfectly and doesn't seem to give me any trouble... and I made the bootable flash drive from the iso file that I made the cd with. I read about this kind of error on [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/). I followed the directions for making sure that the flash drive partition is active but it didn't solve my boot error. Do you know of any file that I could be missing or whatever would cause a BOOTMGR error message? To solve it on windows vista I found that you would use the installation disk... could I somehow use the ubuntu disk for the usb in the same way?
 
I'll check the md5, but I really don't think that the problem is with the disk. The disk works, the usb doesn't, and they were both derived from the same download.
 
Please, take no offense, I was new here not so long ago either. We all had to learn, I was just giving a suggestion.
 
Ok, so your live CD is working, correct? Can you use Ubuntu if you boot from it?
 
If so, let me know, because then it would be an 'easy' fix.

---

### Post by The Jinx on 2009-07-08
Is your flash drive one of those U3 flash drives? maybe it has something to do with that

---

### Post by pizza-is-good on 2009-07-08
OK, here are the instructions on how to create the USB startup disk.
 
You will be using the Ubuntu LiveCD to make this work, so start by booting into it.
 
Once in the Live CD, hook up your flash drive (The one that you plan to run Ubuntu in) 
Then go to System >> Administartion >> Partition Editor[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C0.5.png[/IMG]
 0.png
After that, click on the top right corner, and find your flash drive on the drop down menu.
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C1.png[/IMG]1.png
 
I'll continue on other post....

---

### Post by Sub101 on 2009-07-08
> **johngreen12 said:**
> Hello.  I have been trying to create a live usb version of ubuntu because my parents don't ubuntu on the computer.  Whenever I try to create one to the specifications that I want, it seems to run into problems.  A friend of mine said that there is not limit to the allocation size of ubuntu on a flash drive, but whenever I try to make the size around 14Gbts, or close to that, it gets to ~4% completed and then says that it's done.  When I try to boot into the usb, it comes up with the normal startup screen, but after that it can't seem to find GNOME.  It can find GNOME only if I put the allocation size around 1Gbt, but then it doesn't shutdown or restart correctly... I'm really lost as to what the problem might be.  Any help would be greatly appriciated!  Thanks!

There is a utility within Ubuntu to do this in System ==> Admin ==> USB Startup Disk. I would try that before trying any other methods.

---

### Post by pizza-is-good on 2009-07-08
Then unmount it
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C2.png[/IMG]2.png
 
After that, format the entire thing to FAT 32.
 
Now we are going to split the drive into 2 partitions, one for OS, other for data. That way your saved data is more secure.
 3.png
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C3.png[/IMG]
 
Now, you'll choose the size of your seconf partition. You said you had a 16GB, so I would just use 6GB for data. So where it says 'Free Space Following', write something around 6100.[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C4.png[/IMG]
 4.png

Then click on 'resize/move', click on apply on top, and wait for it.
5.png
 
Note: If you plug your drive into windows, it will not see your 'data' partition.
 
I'll continue on other post....

---

### Post by pizza-is-good on 2009-07-08
Now we need to format the empty space.
Right click the 'gray' partition, and click new.
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C6.png[/IMG]6.png
 
Then select FAT32 as the File System
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C7.png[/IMG]7.png
 
And click on Add
 
I'll contunue on other post...

---

### Post by pizza-is-good on 2009-07-08
OK, so now your flash drive is ready for installing Ubuntu in it.
 
Go to System >> Administration >> USB Startup Disk Creator
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C8.png[/IMG]8.png
 
Click on other, add the Ubuntu ISO file. (Save it somewhere on your computer where you can find it before all of this, and add it from there)(You will need to mount the windows C: Drive to do this (For that, go tot Places >> and click on the drive, then you will be able to search in the USB creator))
 
Then select the drive, since it is now split in two, you'll have 2 flash drives showing. Click on the one you want the OS installed on  (since we made the other one around 6BG, you'll be using the one that is around 10GB)
 
Then at the bottom, click on 'Discarded on Shutdown, unless you save them somewhere else', because you will be saving your files on your flash drive's second partition.
 9.png
 
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C9.png[/IMG]
 
After all that, click on 'Make Startup Disk', and you should get a window like this
 10.png
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C10.png[/IMG]
 
This could take a while.
 
After it is done, the contents of your flash drive (on the OS partition) should look like this:
[IMG]http://ubuntuforums.org/C:%5CUsers%5Calessandro%5CPictures%5CLinux%5CSteps%20to%20USB%20installation%5C11.png[/IMG]11.png
 
After that, you are ready to start using Ubuntu off a flash drive.
 
Please print all of these instructions and have them ready when you do all the steps.
 
 
Let me know if you have any question. If I am not clear somewhere, please let me know.
 
Good luck.

---

### Post by pizza-is-good on 2009-07-08
Bummer, I had added pictures to show everything. Here they are all together.
I'll edit my other posts and write the picture # so you can reference it to here.
I'll put the rest in next post

---

### Post by pizza-is-good on 2009-07-08
More screen shots

---

### Post by pizza-is-good on 2009-07-08
Last 2 screen shots

---

### Post by pizza-is-good on 2009-07-08
OK, everything is there. Let me know if I forgot something. (I hope not)

Also, let me know how it goes.

---

### Post by johngreen12 on 2009-07-08
Thank you very much for all of your help and time.  All of the pictures were very helpful.  I had one more question... is there any way to store the settings, documents, etc in the os?  Instead of discarding everything on shutdown I wanted to store it in a reserved extra space, but whenever I try to use that choice and set it to the max amount of memory, it doesn't work.  What would be ideal, is if the os could save everything that is added to it and all of the changed settings.  The only way that setting will work is if the reserved extra space is really small.  

Thank you very very much for all of this!

---

### Post by johngreen12 on 2009-07-08
> **The Jinx said:**
> Is your flash drive one of those U3 flash drives? maybe it has something to do with that

I've already taken the U3 system off of it.  Thanks for the suggestion though.  :)

---

### Post by pizza-is-good on 2009-07-08
> **johngreen12 said:**
> Thank you very much for all of your help and time. All of the pictures were very helpful. I had one more question... is there any way to store the settings, documents, etc in the os? Instead of discarding everything on shutdown I wanted to store it in a reserved extra space, but whenever I try to use that choice and set it to the max amount of memory, it doesn't work. What would be ideal, is if the os could save everything that is added to it and all of the changed settings. The only way that setting will work is if the reserved extra space is really small. 
 
Thank you very very much for all of this!
 
The discard everything on shutdown is for files only. Configurations, apps, and packages should stay there.
 
I told you to choose the discard everything on shutdown because I thought that saving on the extra partition would be much safer.
 
You are very welcome for the help. I am happy when someone gives detailed explanations to me when I have a problem.

---

### Post by johngreen12 on 2009-07-09
> **pizza-is-good said:**
> The discard everything on shutdown is for files only. Configurations, apps, and packages should stay there.
 
I told you to choose the discard everything on shutdown because I thought that saving on the extra partition would be much safer.
 
You are very welcome for the help. I am happy when someone gives detailed explanations to me when I have a problem.

In the Make USB Startup Disk option it specifically says that when starting up from the disk, documents and settings will either be discarded on shutdown or stored in reserved extra space.  When I tried reloading the os from the usb that we created the settings and documents weren't saved.  What I don't understand is why the other option (to store the documents and settings in extra space) doesn't work when I make the extra space over 2 or so gigs.

---

### Post by pizza-is-good on 2009-07-09
> **johngreen12 said:**
> In the Make USB Startup Disk option it specifically says that when starting up from the disk, documents and settings will either be discarded on shutdown or stored in reserved extra space. When I tried reloading the os from the usb that we created the settings and documents weren't saved. What I don't understand is why the other option (to store the documents and settings in extra space) doesn't work when I make the extra space over 2 or so gigs.
 
OK, my bad! Must've read over that.
 
Well, 2 gigs, is plenty of room for settings, and if you save the files on the extra partiton, you should be OK.
 
Also, if the hard drive on your computer is big, you could sneak in a small 10 or so gig ext3 or ext4 partion, and your parent will never know that it is there, becaue windows doesn't see linux filesystems. You coulld save all your data there, and use the entire flashdrive for the OS.
 
Again, sorry about the wonrg suggestion.

---

### Post by johngreen12 on 2009-07-09
> **pizza-is-good said:**
> OK, my bad! Must've read over that.
 
Well, 2 gigs, is plenty of room for settings, and if you save the files on the extra partiton, you should be OK.
 
Also, if the hard drive on your computer is big, you could sneak in a small 10 or so gig ext3 or ext4 partion, and your parent will never know that it is there, becaue windows doesn't see linux filesystems. You coulld save all your data there, and use the entire flashdrive for the OS.
 
Again, sorry about the wonrg suggestion.

That's fine... I'm new to all of this and I just wanted to make sure that I had it straight.  Are there any advantages to giving the os more memory than is needed?  What I could do is repartition the usb so that the os takes up about 3 gigs (2 for extra space and one for the os) and then the rest could be just data.  What do you think?  
Oh, I was also wondering about if I could format the second partition for data so that it would be ntfs.  That wouldn't mess up the way ubuntu looks at it, would it?

---

### Post by pizza-is-good on 2009-07-09
> **johngreen12 said:**
> That's fine... I'm new to all of this and I just wanted to make sure that I had it straight. Are there any advantages to giving the os more memory than is needed? What I could do is repartition the usb so that the os takes up about 3 gigs (2 for extra space and one for the os) and then the rest could be just data. What do you think? 
Oh, I was also wondering about if I could format the second partition for data so that it would be ntfs. That wouldn't mess up the way ubuntu looks at it, would it?
 
The advantages of bigger OS partition is that you can install more programs, and save more settings.
 
If you wanted to you could have the data partion be NTFS, but I see no advantage to it. Ubuntu would have no problem seeing or writing in it. The thing is that the 'format' in FAT32 would take up less space than NTFS, not a whole lot less, but noticeble. Unless you want to have files bigger than 429497295 (2^32 - 1) bytes, which won't even fit in your drive, then you are OK using FAT32.
Your choice.

---

