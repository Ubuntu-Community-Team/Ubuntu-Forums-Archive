---
title: "Installing Ubuntu on a pre-made partition?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by DutchShrek on 2009-03-25
Hi all.

First off, my main question is:
I have a 15GB partition (NTFS) on my 160GB hard drive,
Is it possible for me to use that partition to install Ubuntu on, and use it for dual booting?

A little more info:

I got introduced to Ubuntu yesterday when I was unable to boot into windows due to a faulty system file.
I burnt a liveCD with the name "Slax"
It was just a temprorary thing because I needed to fix that windows file, but I was impressed by how it looked.

So, now I want to see more of Ubuntu. 
But preferably as a full install, through dual boot.

I first got Wubi, and with that I installed the Kubuntu desktop.
There was some flickering going on and I assume that has to do with the GFX drivers (EVGA Gforce 9500GT 1G)
Then I looked around a bit and read that Ubuntu tends to have better compatibility then Kubuntu does.
Not sure why or how though, I assumed they were the same just with a different look.

Anyway, I tried to uninstall with the Wubi uninstaller but it refused to run.
I got rid of all the files thanks to a post made on this forum.
This made me think it would just be better to install Ubuntu on it's own without Wubi.

So I want to try again, but this time with a full install on a seperate partition.
I figured, since I already have a 15GB partition I'll just use that.
Well for some reason, Ubuntu's installer doesn't see the partitions.
All it can see is the full 160 gig HDD.
But that is split up with 80GB for Windows, about 54GB for my documents and then the remaining 15GB as a random partition.

See when I install Windows it just shows all those partitions seperately and asks me where I want to install.
I thought Ubunutu would have done the same.
I looked around for some guides but couldn't find a definitive answer.
I know Ubuntu has the optioon to resize partitions while installing, but I didn't expect that to be the only option I had.

Perhaps I'm overlooking something.

Any advice I can get on this is greatly appreciated.
Thanks in advance.

---

### Post by cholericfun on 2009-03-25
there should be a "manual" options @ the partition part.
and it should display all your partitions.
there you should select the part. you want ubuntu to be on, format it to ext and set the mount point to "/"

problem is... and i'm not sure if it is really a porblem but did see that with 7.10 recently:
you need another partition for swap space.
its only supposed to be say 1 GB big.

you can split your 15GB part up while installing somehow but i'd recommend to boot the liveCD first and go to System->Admin->gparted to manage youre partitions.

hope this helps!

---

### Post by jhenager on 2009-03-25
There is a great free Pocket Guide available via pdf here:
[http://www.ubuntupocketguide.com/download3.html](http://www.ubuntupocketguide.com/download3.html)
It has a great explanation in Chapter 1 on how to install. Look on page 9 for Step-by-step: Installing Ubuntu
Very clear and concise guide.

---

### Post by Hospadar on 2009-03-25
You can't install ubuntu *into* the ntfs partition, for one, typically only one OS can be installed to a partition, while I suppose theoretically possible, it would require massive reconfiguring and recompiling which I can guarantee you do not want to do (even if it is actuallu possible).

What you probably *do* want to do, is resize your windows partition and make space for a linux installation (or just completely blow away windows, but it's probably better to go for a dual boot until you really know what you are doing in linux, in case something breaks)

You should check out the guide linked above, or search google or the community docs in my sig for installing dual boot ubuntu, but basically it will boil down to:
shrink windows partition after a defrag (or two) and a clean windows shutdown
Install ubuntu into the free space.

Probably you will want to use a tool like gparted (it's on the live cd, Alt-F2 from the desktop, "gksu gparted") to shrink your ntfs partition and make free space. Then I believe the installer will just install your system into the free space.  There's other nice things you can do like making a seperate home partition for convenient re-installs and upgrades, and other things, but don't worry about that now, if you want you can look into it. gparted is a very straightforward graphical way to manage partitions, I think you'll find it easy to use.

---

### Post by DutchShrek on 2009-03-25
wow thanks for the quick reply guys!
Try getting that from M$ lol

ok so I just went into the livecd (still on there actually) and deleted the 15GB partition. By doing this I am now looking at a chuck of free space.

I keep looking at tutorials and docs, but for some reason all I can find is a good reading about the guided part.
I don't see much on "Manual".
I do see a LOT on installing so I wouldn't be surprised if I overlooked it.

Anyway, now in the installer, in step 4 (Prepare disk space) I select Manual correct?
After that I see my 2 partitions, and the free space.
I have to select the free space, simple enough.

But as mentioned I need space for "swap", so does that mean I should create a new partition of say 2000mb while selecting swap? 

Creating a new partition comes up with witha set of 5 options.
-type = logical
-size = 2000
-location = beginning
-use as = swap area
-mount point = (greyed out now)

is the above correct?

if so, do I simply select the remaining free space for the install?
Or does that require a partition as well? 

talk about being noobish....thanks for the help so far.

---

### Post by cholericfun on 2009-03-25
i'd strongly recommend creating the partitions in the LiveCD via gparted !

(right click on the empty space and select new partition, after that you can shift the size to leave some space for swap and select the type of filesystem (Linux-swap and ext3).)

sure its "easy enaugh" to do it while installing but gparted is just so much more easy to use

keep us up to date ..

PS: dont rush things... ;)

---

### Post by DutchShrek on 2009-03-25
"don't rush things"
You're funny, obviously you don't know who you're talking to lol

seriously though, I didn't even think about creating the partitions using gparted.
Stupid I suppose, since I already saw that it was very powerful and easy to use.

None the less, I went thorugh the install process, created a partition ext3 for Ubuntu, and made one for swap at about 2gb.
This was during install though.
In the end, everything installed just fine, and I am now typing this from a fully installed Ubuntu.
Running the update manager now.

At the moment it seems Ubuntu is labeled first in the boot loader.
So if I don't push any buttons it will load before Vista.
I also saw that it has a few more options besides simply Ubuntu or Vista. (like a safe mode for ubuntu)
I read something about customizing Grub, guess I'll look into that a bit further once I finish playing around with my new playmate (that being Ubuntu it self)

So in conclusion, Ubuntu is running properly. 
And it looks tres zexy I might add.

Thanks again for the help and advice.
Any future questions will be on a different topic, but I'm assuming there will be a few so I guess I'll see you in a new thread :D

---

