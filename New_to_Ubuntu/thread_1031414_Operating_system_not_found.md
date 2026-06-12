---
title: "Operating system not found"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by loomnie on 2009-01-05
Hello. I am an absolute newbie so I need serious help.

I just got a Samsung NC10 netbook and i decided to install ubuntu on it. It came with Windows XP but since it does not have a CD Rom drive I tried to install by using UNetbootin. It worked up to a point, and I was able to run the ubuntu live version from a part of the hard disk. But when I tried to install ubuntu on the computer, still running the live version, it tried to partition the hard disk. For some reason, it encountered problems with the installation and it told me that some things would not work until I reboot the computer. I reboot and now it tells me that Operating system not found. I have absolutely no idea what to do.

Thanks.

---

### Post by flytripper on 2009-01-05
dont panic. start over.

---

### Post by XopherH on 2009-01-09
go into your BIOS and boot the restore partition you should have made.  otherwise pull out the CDs and boot the windows restore one.  If you care to figure it out, give atleast 30GB for another hard drive partition when you reformat to save a bigger hassle later.

once you have restored/reformated from the boot CD, run the restore partition setup so you dont have to do this again if its available at that point, i havent had to do it so i dont know.  At that point you should then be asked again whether to resize the drive, if you havent already made a new partition (D: by default) isnt already there, this is the time to make one.

So once that process works and a D: is registering as whatever size you picked in the restore process as a mounted hard drive in My Computer, then you can do this to boot Ubuntu, just start at the sentence that mentions "USB": 
[http://ubuntuforums.org/showpost.php?p=6395188&postcount=12](http://ubuntuforums.org/showpost.php?p=6395188&postcount=12)

(you paid for XP already, you might as well use it as a redundant backup for the times you really have to use windows for certain things.)

---

### Post by sydbat on 2009-01-09
@XopherH - The Op has a Samsung NC10 netbook. Net books do not come with CD drives. Also, it would be impossible for the OP to partition a space larger than the 14GB or so that comes with this particular netbook.

I know you are trying to help, but actually reading the original post will keep us from confusing this person with incorrect information.

Back on topic - I would follow flytripper's suggestion and start over.

---

### Post by XopherH on 2009-01-11
> **sydbat said:**
> @XopherH - The Op has a Samsung NC10 netbook. Net books do not come with CD drives. Also, it would be impossible for the OP to partition a space larger than the 14GB or so that comes with this particular netbook.

I know you are trying to help, but actually reading the original post will keep us from confusing this person with incorrect information.

Back on topic - I would follow flytripper's suggestion and start over.

boot CD/DVDs are supplied with the netbook in the box.
[http://c1.neweggimages.com/NeweggImage/productimage/34-131-015-18.jpg](http://c1.neweggimages.com/NeweggImage/productimage/34-131-015-18.jpg)

I have a NC10, and I guess they assume you will make an iso of the cd and boot it from a USB with it as a forced user training demo or something.  But considering that the OP had already passed a point of no return any suggestion which got them to installing Ubuntu seems to be half the battle.  Creating/editing a new partition from GParted to boot those ISOs to isnt any more complicated than whats already gone on.

And what are you talking about 14GB?  The NC10 comes with a 160GB HDD.  Please do your homework before stomping on a random helpful post.  If you are referring to the model number of the BLUE = B in 14GB, then that only proves you have no idea what you are talking about in regards to automatically denying that my response was worthwhile.

how do you propose to "start over" while agreeing with flytripper?  Wouldn't you have to use the boot OEM CDs supplied in the box?  Wouldnt that be the exact suggestion that I gave originally that you automatically shot down?

The first sentence of my response to the OP explained quite directly that he shouldnt need the CDs in the first place because there should have been a restore partition for this exact purpose.  I have reported you for suspected trolling.

---

