---
title: "Partitioning Help"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by McTwitch on 2010-08-09
Alright, I want to put up a partition so that I can run to distros off of one box, as well as have a separate place for boot, running, and back up. I have a 320 gig External Hard drive, running Ubuntu 10.04, Lucid Lynx, and a friend named Ranch Hand. Hoorah.

---

### Post by jtarin on 2010-08-09
Sounds good...what does Ranch Hand advise?

---

### Post by McTwitch on 2010-08-09
I don't know yet. He's going to walk me through it publicly.

---

### Post by jtarin on 2010-08-09
Is the entire drive devoted to Ubuntu 10.04, Lucid Lynx? Use Gparted from the live CD/DVD to create the partitions you want. Where is Grub installed now?

---

### Post by McTwitch on 2010-08-09
At the moment, it's all installed on the HDD. I don't really know all that much about partitions and what not, so I can't really tell you.

---

### Post by flick on 2010-08-09
For whatever it is worth, I have a 500GB drive multibooting :

/dev/sda1 is some extra space
/dev/sda2 has my Windows recovery partition 15 GB
/dev/sda3 has my Windows 7 partition 60 GB
/dev/sda4 is my extended partition
/dev/sda5 is my swap partition 4.5 GB
/dev/sda6 is my /home partition 275 GB
/dev/sda7 is my / partition Ubuntu Lucid 50 GB
/dev/sda8 is my Ubuntu Maverick partition 20 GB
/dev/sda9 is my Linux Mint 9 partition 20 GB

---

### Post by Bucky Ball on 2010-08-09
What's installed and not? Is the a clean blank drive?

OS = 15Gb
Two OS = 30Gb
Rest for storage BUT it is a good idea to have your /home on a separate partition.
Lastly, /swap = 2Gb

When you are installing one of the OSs (if fresh disk) get to the partitioning section then you need advice. Go for 'manual partitioning' and set things up from there in the order described, putting /swap last. 

You would ideally end up with something like this:

OS1 = 15Gb
OS2 = 15
/home = what size you want
/storage = what's left minus /swap (you could call /storage anything you like).
/swap = 2Gb

Simple! You could forget about /storage and just have /home take up the slack. (You are best to backup to another drive, not partition.) ;)

---

### Post by McTwitch on 2010-08-09
Awesome. That's what I want to do. Have my little partition of Linux, for what ever I want to do with it, and then a second partition, for either testing, or just to play around with another distro...but Windows can stay on the family computer.

---

### Post by ranch hand on 2010-08-09
This sounds like fun.

You need to boot to the Live CD.  A screen shot of Gparted on your sdc drive ( I am an mentalist to know that) mainly for a record but seeing it would also be good.  You may want to save it and shots after each step in a file.

You could also install gparted and gimp on the installed OS and do it before booting to the Live CD.

I think you may need to resize the shots to post them.  I lower the larger dimention to 1000 with gimp which you would have to install on the CD.  It will stay as long as you do not reboot.  If you do not want to do that, fine.  We do not really need it.

Let me know.

---

### Post by McTwitch on 2010-08-09
Alright, reporting from the Live Disk. What now?

---

### Post by ranch hand on 2010-08-09
You could still take a screen shot for your records, just save it to a file on your install.

Pull up Gparted and right click on the partition of your install, sdc1 (see I am really good at this mentalist stuff).  Look at the menu.  If unmount is black click on it to unmount the partition.

---

### Post by McTwitch on 2010-08-09
/dev/sdc1 is now unmounted. It was the Gparted thing that threw me off, but I found it. Next?

---

### Post by ranch hand on 2010-08-09
Right click again and sellect the Resize/Move option.  This will give you a graphic of just that partition that is grabable in several places.  The one you want is the black pointed thingy (technical term) at the right hand end of the partition.  If you get the wrong thing you will know it, just fool around with the mouse until you get it.

That is quicker than using the "size following" window and fooling with it unless you have the calculations ready ahead of time.

Run it to the left until the "size" box shows 40000 (40GB).

---

### Post by McTwitch on 2010-08-09
Done, but what I did was type 40000 in the window.

---

### Post by ranch hand on 2010-08-09
This should make it look like that on the main gparted partition bar for the drive (sdc) and let you see what it will look like.

Hitting OK may be needed to get that.  This will not start anything.

Take a look and see if it is right.  If so hit the little apply arrow up on the tool bar, right most option on the left end of tool bar.  Running your cursor over it will give you text label for function.

---

### Post by McTwitch on 2010-08-09
It says 39.06 GiB, but when I go back to the resize thing, it says that it's at 40. Is that alright?

---

### Post by k3lt01 on 2010-08-09
I don't want to spoil anyones fun here but can I just say if you intend to keep Windows on this machine you really should let Windows do a defrag etc before you go moving anything around. In other words let Windows clean itself up a bit first, then you can start moving/shrinking partitions.

Now back to your regular programming.

---

### Post by McTwitch on 2010-08-09
Oh, we're partitioning an External hard drive, not the Internal. We shouldn't have to mess with Windows...I hope.

---

### Post by k3lt01 on 2010-08-09
OK, just making sure you didn't accidentally damage something you wanted to keep.

---

### Post by McTwitch on 2010-08-09
I understand. Better to be safe then sorry, and thanks for being worried about me, lol.

---

### Post by ranch hand on 2010-08-09
A>39.whatever is fine.
B>I don't do windows. (Hi k3lt01)
C>Just hit apply

I have no idea how long this will take.  Do not interrupt the process.

If it is too late we can finish this tomorrow.  This should change nothing except the size.  I would try rebooting when this is finished to make sure.  If there is a problem chrooting in and restoring grub to MBR (with update-grub included) should do the trick.

A problem booting would really surprise me.

If it is not too late let us know and we will do the next resize.

---

### Post by ranch hand on 2010-08-09
You probably have school tomorrow and I have some day work (unemployed ranch hands can't be real picky) loading hay.  Will be home in afternoon some time.

---

### Post by McTwitch on 2010-08-10
Actually school doesn't start for another week, so I'm trying to get everything I need done, so I won't have to monkey with it then. But yeah, talk to you tomorrow afternoon.

---

### Post by McTwitch on 2010-08-10
Hopefully this doesn't throw too big of a wrench into things, but is it possible to put up a partition, so that I can actually use the External like I would a USB flashdrive? Because right now when I plug it into windows, it won't even be read.

---

### Post by k3lt01 on 2010-08-10
> **ranch hand said:**
> B>I don't do windows. (Hi k3lt01)Hi RH, I still have to deal with Windows occasionally. Not on my personal machines though but it is a complete bummer trying to fix it if precautions haven't been taken beforehand.

> **ranch hand said:**
> I have no idea how long this will take.  Do not interrupt the process. If your up to the install stage it can take as little as 10 minutes up to an hour depending on your CPU and RAM.

---

### Post by McTwitch on 2010-08-10
Alright, finished. If you're on, what next? If you're not, talk to you tomorrow afternoon.

---

### Post by ranch hand on 2010-08-10
OK, you are loosing me here.

Are you saying that Ubuntu can't read the MS files?  That is weird.

Are you saying the Win JerryLewis Pro, or what ever you are running, can't read or recognize Ubuntu?  That is just right.  Keeps your Ubuntu install secure when someone gets into the MS install.  MS, last I knew, can't read ext4.  I hope it stays that way.

If, for some strange reason, you think MS needs to fine your data files.  Then the /home partition needs formatted to ext3 which MS can read.

I would not do that, myself.  You can read and write to MS.  Put them there from Ubuntu if needed and do not give that security hole a chance at anything else.

Disclaimer for other folks who stumble on here.  You can post rants defending MS so called OS' until you are blue in the face.  I will enjoy them.  Do not come visit me and expect to bring your MS laptop, even dual booted with Linux, inside my house.  You are welcome, MS products are not.

---

### Post by McTwitch on 2010-08-10
That completely lost me, so let's focus on the problem at hand. I'll just use my 8 gig for files.

---

### Post by ranch hand on 2010-08-10
Ah, I am about whipped (261 bales loaded, temperature in field 102).  However, I have not eaten since 6:30AM and am not sure I can keep it down yet.

So. did you reboot to check the bugger.  If it needs fixed this is the time.

---

### Post by McTwitch on 2010-08-10
Not yet, but it'll just take a second.

---

### Post by ranch hand on 2010-08-10
Good do that and get back and we will go on.

---

### Post by McTwitch on 2010-08-10
It went through just fine, and now I'm back on the Live Disk.

---

### Post by McTwitch on 2010-08-10
Alright, I've got to get off. I'll meet you back here tomorrow afternoon though.

---

### Post by ranch hand on 2010-08-10
Oh boy.  From here on there are no real worries, even in the case of a major power outage, which may cause us to have to go to a CLI partitioner to straighten things out but should not effect sdc1.

Pull up gparted and right click on the swap partition (sdc5), unmount, then right click and select "delete".  This is not really needed but it will not hurt an will just make things easier.  Unless you have less than a half a gig of ram, swap is rarely used.  Some folks do not even use one at all.  I think you will survive.

If you boot to your installed OS you will, I hope, get a message that not all things in your fstab would load.  Should not stop you from booting.  If it does, Boot the Live CD, get nautilus up as root  and comment out ( put ## in front of) the Swap line in that file (ect/fstab).  We will uncomment it when you put it back so if the lack of it doesn't effect booting just ignore the warning.  Nope it won't mount.  We know why and do not care.

Hit apply.  This should be fast so be ready to right click on sdc2 and unmount if needed then choose the Resize option again.  Use the mouse for this.  We do not want to overlap (I am good at this) partitions.

Use the pointy black thingy on the left hand side or the partition and slide it down to the new sdc1 partition.  Check it and see if it looks good.  If so hit apply.

As an alternate, which is faster, you could just delete sdc2 too.  Then right click on the empty space and create a new partition, selecting "extended" as the type.

The reason for resizing is to let you see the process in a totally safe environment.  You will want to expand a partition you are using (like shrinking sdc1) some time.  This would give you experience with expanding too so that you know what it looks like.

Deleting and just creating another does not have to worry about the "file system" as that will happen with the install.

Take your pick.  Do it.

---

### Post by McTwitch on 2010-08-10
Alright, I right clicked on it, but there is no "unmount" option. There's "Swapon". So...stale mate at the moment.

Never mind. I found the "delete" option. Guess it's already unmounted, or it doesn't have to be?

I booted to my Ubuntu 10.04, and everything worked there. I haven't tried Windows yet, but since we aren't really messing with it, I don't think it should cause any harm Windows in the internal, should it?"
Okay, I was messing around with the black pointy thingy, but I didn't understand what you meant by "Slide it down to the new sdc1 partition" so I just went with deleting it, and making the new part. It's Unallocated, and it has 259.03 GiB. What now?\

Oh, and lastly, in front of my SDC1 partition, there's this little space of "unallocated" it's 1 MiB. Should I delete it?

---

### Post by ranch hand on 2010-08-10
You can't delete the unallocated stuff.  Leave it for now.  Later you can simply, if it is bothering you, go back and make you sdc1 partition bigger in that direction.  For 1 Mb I, personally, would have no trouble ignoring it for a really long time.

I just got back from unloading yesterdays load and loading another.  We will be leaving again about 6PM (mountain time) to unload this one when it will be cooling off a bit.

Doing a little math tells me that creating an ext4 partition at the beginning of sdc2 that is 25Gb, creating another ext4 partition directly next to it that is 150GB will leave plenty of room for swap and room to play on.

You should create those 2 partitions at the start (left end) of sdc2.  You should also create an swap partition at the end of sdc2 that is just a hair bigger than two times the size of your Ram.

You can find the size of your ram at System>Administration>System Monitor.  When that is up just look at "System" (top left of screen).  Under "hardware" your memory will be listed.  That is the amount of ram detected.  Round that up to nearest GB and double that (mine says 2.9 so that iwould be 3 making swap 6Gb and a bit) unless it is in MB, in which case double it and make it a bit bigger at your discretion.

That much swap is probably not needed (6Gb) but that is the recommendation.  It is needed if you "suspend" your box.

Just go with that type of figure.  You have plenty of drive space.

I am going to the Hardware store to pay our bill.  Be back before you get that done.

---

### Post by McTwitch on 2010-08-10
The ext4 partition, should it be a logical partition, a primary partition, or an extension partition? Something is telling me that it is an extension partition.
Nevermind. It will only allow a logical partition.

---

### Post by McTwitch on 2010-08-10
Alright, I'm posting a screen shot now, because I want to make sure I'm doing it right...and because I've only now figured out how.

---

### Post by McTwitch on 2010-08-10
Alright, as far as I can tell, I've finished all of that. Is there anything else that I should/have to do?

---

### Post by McTwitch on 2010-08-10
Here's a screen shot, so that you can look it over, if that's alright..

---

### Post by ranch hand on 2010-08-10
Just got back from unloading another trailer of hy.

It looks like you made the partitions too small.  14GB and 24GB.  That would be plenty for testing but I was thinking of a secure main OS on those partitions.  25Gb and 150Gb would be better.

I would just delete the buggers and make bigger ones.  This should leave you with a little better than 80Gb unused for future fun.

Did you put the boot flag on sdc1 or did it just turn up?  Seems strange to me.

---

### Post by McTwitch on 2010-08-10
It was just there, actually. Other than those two things, does it look alright?

---

### Post by McTwitch on 2010-08-11
Alright, another odd question. After putting the partitions up on the HDD, when I get on the live disk to check things out on it, I get three Icons popping up. One for Lounge-root, then 16 GB Filesystem, and 26 GB Filesystem

Alright, I just opened GParted to edit those partitions, it comes up as SDB now. So, instead of changing that stuff now, I'm going to wait, and make sure I didn't screw something over.

---

### Post by ranch hand on 2010-08-11
Every thing looks fine.

You really do not need much more than about 5 GB for a whole install.  No storage at that rate at all.  The reason I like a large root is I think;
A>It runs a little faster if not more than 50% full
B>I like to run a lot of apps (all installed on root)

The 150Gb /home is probably on the small side if you store movies or a lot of videos.  Music and your own photos (the better the camera the bigger the files) also take up a lot of room.

You have more drive if you need it.

I would make the bigger partitions and install 10.04 on those 2 partitions.  Copy files to it from the other one.  Bookmarks and so forth.

You need to use manual partitioning (advanced in the installer) and select the two new partitions for installation.

On the last screen where you click OK for installing, don't do it.  There is a little box marked "advanced" on that box too.  Click on it and it will be  where you want grub installed.  Mark that you do not want grub installed anywhere.

Give us another screen shot and I will send you a working menu entry for that install to put on your sdc1 install and you can use that grub to boot.

---

### Post by McTwitch on 2010-08-11
Alright...haven't quite got around to all of that yet, I just remade the partitions at the moment...again I ask though, is it normal for it to have just randomly switched over to SDB?

---

### Post by McTwitch on 2010-08-11
Two screen shots, one after editing, the next after applying...it doesn't look good.

---

### Post by ranch hand on 2010-08-11
Delete it and do them one at a time.  It looks like you had an over lap in the partition boundries.  Don't try to crowd them.  The best way to avoid it is create them one at a time.

I always try it more than one at a time first.  Usually works.  If not I just do them one at a time.

---

### Post by McTwitch on 2010-08-11
I deleted it, and tried again. Everything went well (How can it go wrong just entering numbers?) But when I hit apply, I got an error message. 

There is also a little bit more under the details part of the progress meter, but I can't get a full shot of it.

---

### Post by ranch hand on 2010-08-11
This is where using the slider is actually easier to do.  You just put your pointer on the black point on the right end of the slider and hold down the left mouse button and move it to the left.

There is a box, in the box that you are using to enter the numbers and that has the slider, that says "round to cylinders".  You want that checked (I think it is the default).  If you keep getting the error leave a bit of space (just a hair) before the partition.

---

### Post by McTwitch on 2010-08-11
Alright, while I have your ear though, I'd like to ask again..is it normal that SDC changed to SDB?

I used the slider again, and got the same error message.

---

### Post by ranch hand on 2010-08-11
Not really.  However, I have been wondering why it was sdc.  It really seems like it should be sdb.  Dell uses one configuration for the Mother Board and I think they are pretty much the same and use pretty much the same bios.

My external is sdb if my internal is on.  It is sdf or sdg if I am on my main drive and turn on the external.  You can see why I have a little trouble with sdc.

This may require hitting e at the grub menu an editing you menu entry to read sdb1 and then running update grub when you get in.

Or you may have to restore grub from the live CD.

It is late, I am whipped and have to do it again tomorrow.  Why don't you try booting into your installed OS and see what is up with grub and we will call it a night.

---

### Post by McTwitch on 2010-08-11
The HDD boots just fine. Sleep well, and don't work too hard tomorrow. See ya in the afternoon.

---

### Post by ranch hand on 2010-08-11
This is great.  Try the live CD again when you get the chance and see what it is calling the drive now.

This is kind of neat.

---

### Post by McTwitch on 2010-08-11
Yeah, it's still SDB. Hm...If I remember correctly, the power went out while I was trying to boot from the HDD, and when I got back on the Livedisk, that's when it was SDB, but I might be wrong.

---

### Post by ranch hand on 2010-08-11
Well, what ever the cause, it is a relief to me.  It should never have been sdc in the first place.

Just get the new partitions on, one at a time.

I will be back in a few hours.  We are doing more than we should in this heat as the guy I am working for is headed out of town for 2 weeks on Friday.  Got contracts to fill before he leaves.

---

### Post by McTwitch on 2010-08-11
Alright, well, we're going to have to pause this project for a bit; I'm downloading the ISO image for Mandriva. I have a question, though. When you said install Ubuntu on those two partitions, did you mean on SDB2 in general? I was wondering if I shouldn't just install it on the 146.48 GiB partition.

---

### Post by ranch hand on 2010-08-11
What you really need is a main OS (I think all OS') installed on / and /home partitions.  This is just a whole lot better than being on one partition.

If you are going to use 10.04 as your main OS then it should be mounted on the large partitions.  Mandriva could then be mounted on on smaller partitions (/ = 10GB /home = 20 or 30Gb).  40Gb is a pretty good size for an OS.  It was the only size my son used for years.

On an OS you are going to use for some time though bigger partitions are really best so that you have plenty of breathing room for the buggers.  They are happier that way.

---

### Post by McTwitch on 2010-08-11
Madriva's been postponed for a bit (Internet problems). I have the two partitions made, so let's start there.

---

### Post by ranch hand on 2010-08-11
That is great.  Do you want to install 10.04 or set up partitions for Mandriva?

I am not going anywhere tonight, just back from unloading a big load (306 bales) which gets us over 500 for the day.  Kinda tired.  Just not going to be running around at all.

---

### Post by McTwitch on 2010-08-11
Well, Mandriva's sort of a dead end, so...I think just reinstall Ubuntu on the larger partition, and then leave space for what ever I choose as my next project? How does that sound to you?

---

### Post by ranch hand on 2010-08-11
Well this should be real hard to do.  Are you on the Live CD (booting to it should be the hard part)?

If you are not absolutely sure what the partition numbers of the new partitions are you should pull up gparted and check that.  I ALWAYS write it down to avoid mistakes.  Gparted needs to be closed to run the installer or the partitioner in the installer will not work and it has to work.

If you have all that info I would open the installer on a different work space from FF with the forum open on it.

You need to just follow the instructions up to the partitioner.

When you get there select the manual method of installing.

This will get you a list of partitions.  Highlight and right click on the partition you made for / and select "change".  Then just go from top to bottom on the box that  comes up with ext4, format, and / (root).
And then I think it is an OK button.  It may be called some thing else.  I am sure you can handle it.

Do the same for the partition you created for /home with the selected mount point the only difference (choose /home).

There are several other mount point choices.  Don't use them.  You can try them on some other, experimental installation later.  /boot is, to me, just silly.  There is some merit to the rest of them but I do not use them as it complicates chroot dealings with the OS and I do that a lot in testing.

---

### Post by McTwitch on 2010-08-11
Alright, so the 150 partition, and then the other one, the 25 are...what ones?

---

### Post by McTwitch on 2010-08-11
I'm at the end of step three, and I've gotten a warning:

The installer has detected that the following disks have mounted partitions:

/dev/sdb

Do you want the installer to try to unmount the partitions on these disks before continuing? If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install existing partitions there.

Then a yes or no choice, so which do I go with?

---

### Post by ranch hand on 2010-08-11
Yes, you want to do that.  It is the easiest way to unmount a bunch of partitions or I would have mentioned it.

You could have gone to System>Administration>Disk Utility and unmounted it before you started.  I do not do that as it needs to be done one at a time that way and I have LOTS  of partitions to unmount.

---

### Post by McTwitch on 2010-08-11
Alright, about the 150 and the 25 GiB partitions. What do I use those for?

---

### Post by ranch hand on 2010-08-11
25Gb mount point = / (root)

150Gb mount point = /home

---

### Post by McTwitch on 2010-08-11
Awesome. Thanks for that, hopefully this goes smoothly. Wish me luck?

---

### Post by McTwitch on 2010-08-11
Alright, take a look at this.

---

### Post by ranch hand on 2010-08-11
We don't do luck.  Just depend on skill.

When you get to the screen that wants to do the install, click on advanced and tell it not to install grub anywhere (this is referring to the MBR and so forth.  You can boot it from your other 10.04 by simply running "sudo update-grub" in terminal there and rebooting to the new one from there.

This will avoid potential problems with MS on the internal.

---

### Post by ranch hand on 2010-08-11
> **McTwitch said:**
> Alright, take a look at this.
Does that reflect the real size of the partition?  It is "only" 100Gb.

You need to select ext4 for the /home partition unless you want MS to be able to read it.  In that case use ext3 which will not be quite as fast but I doubt you would notice the difference in spite of my liking for ext4.

---

### Post by McTwitch on 2010-08-11
and then /home, right?

---

### Post by ranch hand on 2010-08-11
Yup.  That is just right.

---

### Post by McTwitch on 2010-08-11
For the 25, I don't see a /root. I see a /boot, is that what I'm looking for, or is there something else?
Unless root is just the /.

---

### Post by Bucky Ball on 2010-08-11
root = /

... NOT /root. None such. You can of course create a partition with whatever name you like, and that might be /root.

But the REAL root = /

---

### Post by ranch hand on 2010-08-11
Thus the designation that I gave / (root) to indicate just that.

---

### Post by McTwitch on 2010-08-11
Thanks, and another stupid, beginner question, this one's ext4 as well, right?

---

### Post by ranch hand on 2010-08-11
I would do that for both of them.  It is what the default is for 10.04 and what the release was developed on and for.

---

### Post by ranch hand on 2010-08-11
Just be real sure that / is the small one and /home is the big one.

---

### Post by McTwitch on 2010-08-11
Okay, can you take a look at this, and make sure everything looks right? Sorry for taking up so much of your time.

---

### Post by McTwitch on 2010-08-11
> Just be real sure that / is the small one and /home is the big one.
Out of morbid curiosity,what happens if it's the other way around?

---

### Post by ranch hand on 2010-08-11
You then have space you will never use in / and not enough in /home.  It would boot and run fine untill you got an "out of room" warning for your /home partition.

You could resize/move them but it would be easier on a clean install to simply reinstall correctly.

---

### Post by McTwitch on 2010-08-11
Oh, not nearly as bad as I thought then. Good deal.

---

### Post by McTwitch on 2010-08-12
Okay, so I set SDB6 to be /, and when I hit forward it tells me that it has, but then the prompt also tells me that it has not been marked for formatting. "Directories containing system files (/, etc, /lib, /usr, /var...) that already exist under any defined mountpoint will be deleted during the install." So, what do I do?

---

### Post by ranch hand on 2010-08-12
This is because you did not check the box to format the partition.  You should have formatted it to ext4 with gparted when you created it.

As for loosing all the directories, I would really be worried if I were you, there is nothing on the partition.

You could easily go through the "change" procedure again and check that box and the one for /home.

This will ensure that you get ext4.

You will not get a warning about /home.  This is part of the advantage of installing this way.  If you have a real foul up and need to reinstall you can do by formatting the / partition and not formatting the /home partition (back up still recommended).  Doing this generally (99.5% of the time) will result in 0 data loss.

---

### Post by McTwitch on 2010-08-12
Good. Formatting and data loss are danger phrases for me, but I'm doing my best to get used to them.

---

### Post by McTwitch on 2010-08-12
Step seven of eight, Migrate Documents and Settings. It said that there were not operating systems suitable for transfer. I'll take it that I don't have to transfer from my already made Ubuntu partition yet?

---

### Post by McTwitch on 2010-08-12
"If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

The following partitions are going to be formatted:
 partition #5 of SCSI4 (0,0,0) (sdb) as swap"

Just making sure that this is all alright.

---

### Post by ranch hand on 2010-08-12
So, I hope you pre formatted to ext4 on gparted.  Other than that it is great.

There is an advanced button on that screen.  Use it to have grub not installed anywhere.  We have lucked out on the possible problems with Vista so far.  Lets not screw it up now.

We can deal with any booting issues easily later and be safe doing them.  You should, doing this reboot to your old 10.04 install.  Pull up the terminal and run;
```

sudo update-grub

```
reboot and select your new install from the menu.

---

### Post by McTwitch on 2010-08-12
This late at night (It's not actually that late, but there's been no caffeine in my house for over a couple of days), I'd be much obliged if you'd put that in layman's terms, so that I can be sure not to screw anything over...at least not that badly.

---

### Post by ranch hand on 2010-08-12
There is an advanced button on the screen you just took a screen shot of (if not it is the next screen).  click on it.

All it is for is to say where grub is installed.  MBR of sdz, sda, whatever, also partitions like sda1.  There is, or should be, an option to not install it.  Use that.

We really have been lucky not to screw your families beloved Vista so far.  Let continue that.

---

### Post by McTwitch on 2010-08-12
I got that part. I'm wondering if I couldn't just grab all of the files that my family wanted, put them on a flashdrive, then pop Ubuntu through the entire thing.

---

### Post by ranch hand on 2010-08-12
If you are talking about installing on sda1.
A>you better have permission well in advance
B>yes you can grab anything you want off an MS install
C>Install on 2 partitions
D>I do not think it is a good idea until they can try it out

---

### Post by McTwitch on 2010-08-12
Well, honestly, I'm the only one that uses the machine all that often. My mom uses it to have me do Google searches, and other such things. She also plays some card game, FreeCell or something or other, and that's about it.

---

### Post by McTwitch on 2010-08-12
Alright, install complete. Is there anything that I should do before restarting it?

---

### Post by ranch hand on 2010-08-12
Well there is nothing you have to do but I would open gparted and label the partitions.  This makes chrooting easier and also they are listed by label in nautilus so that it is easy to find the info you want from your original installation or any other Linux OS.

Something that identifies the OS and / or /home.  Like 10.04-root or Lucid-root, 10.04-home or Lucid-home.  Your girl friends name, anything.  I have one named after my horse.

It really makes for an easier to use partition table.

---

### Post by McTwitch on 2010-08-12
Alright, that's done (I went with 10.04-root and 10.04-home, real original, eh?) I'll talk to you tomorrow, thanks once again for all the help.

---

### Post by ranch hand on 2010-08-12
Great, I have dinner about cooked too.

You will have to do the update-grub thing on your old install to get the menu entry for the new install if you did not have grub installed anywhere.

---

### Post by McTwitch on 2010-08-12
Yeah, I'll do that tomorrow, when my mind isn't singing everything to me in a soothing baritone.

---

### Post by QLee on 2010-08-12
I don't want to intrude on your fun, guys (Don't know if I'm correct calling you guys, I've been referring to McTwitch as he but could be a she too). Definitely these long posts give me something to read and as I try to appreciate Ranch Hand and McTwitch's sense of humour.

In the first post McTwitch stated he wanted a "separate place for boot", which I took to be a separate boot partition and the scheme you are currently working with doesn't provide that. Of course, McTwitch may have changed his mind about that but I thought I would mention it before you get too far along with partitioning. He also mentioned a partition for backup too but that can easily be carved out of unpartitioned space at the end of this process.

---

### Post by ranch hand on 2010-08-12
I think he may have been reading a bit too much on the forums.  A separate /boot had more use with grub-legacy than it does with grub2.

The backup and a couple more partitions will be created sometime.  Right now we want to get a solid install of 10.04 rather than the single partition installation that is the original.

---

### Post by QLee on 2010-08-12
[QUOTE=ranch hand]I think he may have been reading a bit too much on the forums.  A separate /boot had more use with grub-legacy than it does with grub2.
[/QUOTE]

Your opinion is respectfully acknowledged Ranch Hand, however, it is different from my opinion. I think a separate boot partition on systems that multiboot can still be useful, but I don't think doing it that way is easier nor that I need to make people conform to my opinion. I'm just noticing what the OP called for in the beginning. 

I'm confident that McTwitch will get what he wants by the end of the thread.

---

### Post by McTwitch on 2010-08-12
Alright, I ran the update-grub, and am now on my new account. What do I do now?

---

### Post by McTwitch on 2010-08-12
So, installation went alright, but I did run into something that I was unsure of while installing updates and what not on my new Ubuntu 10.04 system.

---

### Post by ranch hand on 2010-08-12
> **QLee said:**
> Your opinion is respectfully acknowledged Ranch Hand, however, it is different from my opinion. I think a separate boot partition on systems that multiboot can still be useful, but I don't think doing it that way is easier nor that I need to make people conform to my opinion. I'm just noticing what the OP called for in the beginning. 

I'm confident that McTwitch will get what he wants by the end of the thread.
I am sure that in a year or less he will actually know what he wants and have a pretty good idea how to get it on his box.

Keeping it simple for now to let the learning get started and then I think we can sit back and enjoy the show.

I have some hopes for this one.

---

### Post by ranch hand on 2010-08-12
> **McTwitch said:**
> So, installation went alright, but I did run into something that I was unsure of while installing updates and what not on my new Ubuntu 10.04 system.
Installation on sda would make your removable drive be needed to boot an internal drive.  If it is removed the internal will not boot without restoring the Vista boot loader to the MBR.

Sdb6 is not really workable with your set up.

Sdb is the option you want unless you want to keep using grub from your other install.  If that is the case just do not choose any of them and it will stay as it is.

---

### Post by McTwitch on 2010-08-12
Okay, so how do I transfer files over to my new install? I already have most of the documents, but I heard that there was a way to transfer your preferences (Like I have the windows go transparent). How does one transfer those, or is it even possible?

---

### Post by ranch hand on 2010-08-12
Those files should be in your users home folder.  They start with a prefix of . and that hides them.  In Nautilus you can click on "view" and then on "show hidden files".  the most likely places for the type of config files you mention, I think would be .compiz, .config and .gconf.

You can explore the buggers and find them.  You will see a bunch of others there too.

Some of those files do mention the user name so if you have a different one for the new install you will have to edit the files.

I would copy the current ones to a safe backup location in case you screw something up.  Then you can just replace the bugger and start over.  They are kind of fun to play with.

The stuff in the .gconf file has a gui, installed by default on 10.04.  It is not shown on your applications menu for some reason.  Right click on Applications and choose Edit Menus.  Click on System Tools and then Configuration Editor.  You will then have it on your Apps menu.

In terminal you can open it by;
```

gconf-editor

```

---

### Post by McTwitch on 2010-08-12
I hate asking about this again, because it makes me feel stupid and inexperienced, but how do you open Nautilus? I can't find it in any of the menus.

Nevermind, I figured it out.

---

### Post by ranch hand on 2010-08-12
Good for you.  I suppose you went to Places>Home Folder.  You can also open it with;
```

nautilus

```

---

### Post by McTwitch on 2010-08-13
Actually I used the command line. It was simply a lucky guess, though.

---

### Post by McTwitch on 2010-08-13
Just a couple more things, then I think I can format the old partition, other than the GRUB thing that you told me about, Ranch Hand, if you don't mind, I'd enjoy a more thorough form, but anyway...All of the items that I have installed (programs and such) is there any way I can transfer those, or am I going to have to install them all again? And what about my saved passwords and bookmarks in Firefox?

---

### Post by ranch hand on 2010-08-13
I have never tried to save passwords in that manner.  You would have to hunt down the keyrings somehow.  Should be possible but I do not know about that.

The programs would need reinstalled.  You do have the config files for them and the .deb package should be in /var/cache/apt/archives.  You could grab the .debs there and install with Gdebi package installer (right click on the .deb package and that should come up as an option).

I would at least do that with the grub from the old one.

---

### Post by McTwitch on 2010-08-13
Alright. Where do I find the GRUB, will it be in roughly the same area? And I'm on the Debian site, and I don't know which download option to go with. I want to make another Livedisk (I'm thinking of starting a collection. Seems like they all might be useful in their own right), but I don't quite know which option that is. I'm thinking it is  Download a minimal bootable CD image.

---

### Post by ranch hand on 2010-08-13
You should find the grub packages at /var/cache/apt/achive/grub-pc and /grub-common

---

