---
title: "adding memory to ubuntu"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by thunter9116 on 2011-07-17
ok i am new to ubuntu but i have figured out almost everything so far except one thing. for some reason i only have 30 gigs of space for ubuntu but my hard drive has around 200 gigs free... is there a way to fix this or can i only use 30 gigs for ubuntu. Thanks

---

### Post by Gone fishing on 2011-07-17
There are various ways - you could use gparted on the live CD to resize your Ubuntu partition. Probably the best way would be to use gparted to create a second Linux partition (ext4) and then mount that as /home by modifying your fstab file and the copying your existing /home directory into the new partition.

Post edit here's a link [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) and there is also a gui program called mount manager for easily writing fstab

---

### Post by thunter9116 on 2011-07-17
wow you lost me lol but i will try to do what you said, thanks

---

### Post by yeats on 2011-07-17
If you're dual booting with Windows, you will probably want to do the resizing from the Windows end first.  There is a "Shrink Partition" function (I'll leave you to Google that) that should allow you to create more space for Ubuntu.  Then use gParted to resize the Ubuntu partition.  If you try to do the whole thing with gParted, as suggested, you will risk overwriting parts of the disk that Windows needs to run.

---

### Post by jmszr on 2011-07-17
thunter9116,

You must be using Wubi which has a 30GB limit by design. You will need to dual-boot if you wish to go beyond the 30GB limitation.

Here is the Ubuntu dual-boot documentation: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) and here is a tutorial re migrating Wubi to its own partition: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
This may also be of help: [http://www.linuxcandy.com/2011/05/wubi-tutorial_13.html](http://www.linuxcandy.com/2011/05/wubi-tutorial_13.html) .

Hope that helps.

Edit: Please confirm whether you are, in fact, using Wubi or not.

---

### Post by thunter9116 on 2011-07-17
ok yes i used wubi so i am gonna redo everything the other way

---

### Post by XubuRoxMySox on 2011-07-17
Oh, I know what you mean about getting lost, lol! Partitioning used to scare the heck out of me too! But it's easy, after all, and in the long run it's awesome because with a separate **/home** partition you can re-install Ubuntu without losing pictures, documents, music, e-mail settings and folders, browser favorites and all that!

During the installation process, instead of "giving Ubuntu the whole drive" (which is default I think), choose manual partitioning.

My little old hard drive is an 80-GB drive, and I set my partitions up like this:

1st is "**[COLOR="Purple"]Linux Swap[/COLOR]**." I made it 1000 megabytes because that's roughly double my 'puter's RAM (512).

The second partition mounts as "**[COLOR="Purple"]/[/COLOR]**" (yup, just a slash. It's the root partition), and I gave it 20 gigs, which is at least double what it should ever ever need! But I'm generous to my Xubuntu, lol.

The third one is mounted as "**[COLOR="Purple"]/home[/COLOR]**." This is where all my dance choreography, music, photos, schoolwork, browser favorites and e-mail settings and folders are stored. I gave /home the remainder of the drive.

The partitioner in Ubuntu is very graphical and self explanatory. When I re-install Xubuntu (which I only do every 3 years now, since I stick with LTS versions on this old box), I format "/" and *leave "/home" unformatted* so it doesn't erase all my data.

This is not dixiedancer-proof though, so I always back up all my important stuff first anyway!! Be sensible and unhurried about it. But that partition scheme has been great on my aging, very modest hardware. It runs at mind-bending speed all the time, even faster than when it was brand new with WinXP on it!

I hope this helps a little,
Robin

---

### Post by thunter9116 on 2011-07-17
> **dixiedancer said:**
> Oh, I know what you mean about getting lost, lol! Partitioning used to scare the heck out of me too! But it's easy, after all, and in the long run it's awesome because with a separate **/home** partition you can re-install Ubuntu without losing pictures, documents, music, e-mail settings and folders, browser favorites and all that!

During the installation process, instead of "giving Ubuntu the whole drive" (which is default I think), choose manual partitioning.

My little old hard drive is an 80-GB drive, and I set my partitions up like this:

1st is "**[COLOR=Purple]Linux Swap[/COLOR]**." I made it 1000 megabytes because that's roughly double my 'puter's RAM (512).

The second partition mounts as "**[COLOR=Purple]/[/COLOR]**" (yup, just a slash. It's the root partition), and I gave it 20 gigs, which is at least double what it should ever ever need! But I'm generous to my Xubuntu, lol.

The third one is mounted as "**[COLOR=Purple]/home[/COLOR]**." This is where all my dance choreography, music, photos, schoolwork, browser favorites and e-mail settings and folders are stored. I gave /home the remainder of the drive.

The partitioner in Ubuntu is very graphical and self explanatory. When I re-install Xubuntu (which I only do every 3 years now, since I stick with LTS versions on this old box), I format "/" and *leave "/home" unformatted* so it doesn't erase all my data.

This is not dixiedancer-proof though, so I always back up all my important stuff first anyway!! Be sensible and unhurried about it. But that partition scheme has been great on my aging, very modest hardware. It runs at mind-bending speed all the time, even faster than when it was brand new with WinXP on it!

I hope this helps a little,
Robin
THANK YOU lol this makes tons of sense this is what i needed

---

### Post by Swagman on 2011-07-17
1Tb HD here... I gave mine 

2gb /boot (ext4) <--- dunno what it's for but it sounds kinda "boot-ish"
100gb / (ext4) <-- I reckon that should * just about* cover it. ;)
10gb swap 
850gb-ish /Home

---

### Post by XubuRoxMySox on 2011-07-17
> **thunter9116 said:**
> THANK YOU lol this makes tons of sense this is what i needed

Yaaaaay! =D> Be sure and let us know if it worked for you! And it's always sweet when someone says [COLOR="Purple"]thank you[/COLOR]!

@ Swagman: Wow, what an enormous hard drive you have! I imagine I'll need a bigger one someday when I grow up and have to have zillions of files on there for business and stuff, but for this kid, 80 gigs is still more than I've even come close to using, even with all that edited music and choreography and stuff I keep on it. And with "the cloud" being the "wave of the future," I don't imagine big ol' hard drives will be needed for the traditional stuff... but I've gone off topic now, sorry, lol!

Happy to help,
Robin

---

### Post by Elfy on 2011-07-17
> **dixiedancer said:**
> ... because with a separate **/home** partition you can re-install Ubuntu without losing pictures...

You know you don't need a seperate /home to do that - all you need to do is not let the installer format / 

I've done it that way. 

Though to be honest now I rarely keep anything in /home I want to keep - the only things I copy to a new install are things like .mozilla .tbird etc 

[http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home-s/3603#3603](http://askubuntu.com/questions/247/whats-your-recommendation-on-drive-partitioning-schemes-for-a-desktop-and-home-s/3603#3603)

---

### Post by jmszr on 2011-07-17
thunter9116,

+1 to 20GB for / ; I'm using 15GB and getting entirely too close to filling that.

---

### Post by Swagman on 2011-07-17
lol

Well big drives are dirt cheap now aint they.

I remember paying £250 for a tiny 170 megabyte ide drive

£400 for a scsi 2 Fast & Wide 4gb

That 1Tb sata2 was about 60 quid

---

### Post by Gone fishing on 2011-07-17
If you're using wubi ignore my post I was assuming you already had Ubuntu installed on its own partition. If you are going to start again and install not using wubi but Ubuntu on its own partition then the Ubuntu installer can use whatever space you let it use, it can even resize Windows partitions to make space. 

If you are using Windows 7 or Vista, Windows can resize the windows (ntfs) partition in Computer Management then Disk Management Shrink partition and this might be a better way of creating free space (there used to be an issue with gparted and Windows 7, I don't know if it is still a problem)

Personally I would use a seperate home partition but that up to you it can make upgrading easier.

---

