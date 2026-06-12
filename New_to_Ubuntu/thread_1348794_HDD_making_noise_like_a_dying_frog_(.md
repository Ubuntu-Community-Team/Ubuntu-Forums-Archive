---
title: "HDD making noise like a dying frog :("
date: 2009-12-07
forum: New to Ubuntu
---

### Post by The_Pirate_King on 2009-12-07
I JUST figured out how to get Ubuntu configured exactly the way I like it, had a working dual boot going, everything was looking peachy, when out of nowhere... bam. 
Seems like a hard drive failure; I'm booting from Live CD and GParted can't even detect the drive. 
Plus it's making.... what is best described as a literal croaking noise. I really hope it's not a HDD failure; this laptop is under two years old, but that's the way it seems... 

Anybody have an idea as to what I can do to fix this, if anything? 

Also, anybody have any tips as to how I can convince my dad that this wasn't due to the fact that I loaded two operating systems on one Hard Drive?

---

### Post by starcraft.man on 2009-12-07
> **The_Pirate_King said:**
> I JUST figured out how to get Ubuntu configured exactly the way I like it, had a working dual boot going, everything was looking peachy, when out of nowhere... bam. 
Seems like a hard drive failure; I'm booting from Live CD and GParted can't even detect the drive. 
Plus it's making.... what is best described as a literal croaking noise. I really hope it's not a HDD failure; this laptop is under two years old, but that's the way it seems... 

Anybody have an idea as to what I can do to fix this, if anything? 

Also, anybody have any tips as to how I can convince my dad that this wasn't due to the fact that I loaded two operating systems on one Hard Drive?

Open a terminal and type :

```
sudo apt-get install gsmartcontrol
```

Then run the program via run dialog (alt + F2) with the following:

```
gksudo gsmartcontrol
```

gsmartcontrol will read the SMART data from a HDD and tell you if there are large amounts of errors on it. If it's just the HDD, you can RMA it back to the manufacturer assuming it's under warranty. Generally speaking when a drive makes noises like that, not a good sign. Also, not likely to be anyone's fault unless ya dropped it really violently.

I suppose the gsmartcontrol info can be used as "proof", though it's not full proof.

---

### Post by The_Pirate_King on 2009-12-07
It says "no drives found".

---

### Post by starcraft.man on 2009-12-07
> **The_Pirate_King said:**
> It says "no drives found".

Really? Interesting, in a not good way.

In a terminal please (and paste back output in code tags (# button):
```
sudo fdisk -l
```

---

### Post by Dark_Stang on 2009-12-07
Make sure your cables are hooked up properly. If they are you've got a bad drive or a bad motherbaord. But, if the hard drive is "clicking" (the read/write arms slamming into the sides of the drive) it's toast.

---

### Post by The_Pirate_King on 2009-12-07
Tried that already, but here you go... 

```
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 

```

---

### Post by The_Pirate_King on 2009-12-07
> **Dark_Stang said:**
> Make sure your cables are hooked up properly. If they are you've got a bad drive or a bad motherbaord. But, if the hard drive is "clicking" (the read/write arms slamming into the sides of the drive) it's toast.
It's not exactly clicking.... more of a scratching/croaking noise.  I wouldn't know how to check the cables since I have a laptop... if it were a desktop I probably could but...

---

### Post by starcraft.man on 2009-12-07
Making me work today... after consulting with someone else they recommend following command: Post the output.

```
sudo udevadm trigger
```

---

### Post by ScottinSoCal on 2009-12-07
This is an unusual thing, but it's worked for me in the past with server hard drives.

First, stop turning on your laptop and get a replacement drive ordered. Don't touch it again until the new drive  is delivered. Once the new drive is in your hands, take the old drive out of your laptop and (this is the weird part) put it in the freezer for a few hours - long enough to get very cold. While it's cooling off, install your new hard drive, the operating system, the applications - just get things in place and ready to run. Then take your old drive, put it in an external case, and see if it will power up and run long enough to pull the data files off. You might get all, some, or the drive is just so far gone that nothing will work.

As I said, this has worked for me on server hard drives, it might work on your laptop hard drive.

---

### Post by NoaHall on 2009-12-07
See if it's listed in the BIOS.

---

### Post by cariboo on 2009-12-07
> **ScottinSoCal said:**
> This is an unusual thing, but it's worked for me in the past with server hard drives.

First, stop turning on your laptop and get a replacement drive ordered. Don't touch it again until the new drive  is delivered. Once the new drive is in your hands, take the old drive out of your laptop and (this is the weird part) put it in the freezer for a few hours - long enough to get very cold. While it's cooling off, install your new hard drive, the operating system, the applications - just get things in place and ready to run. Then take your old drive, put it in an external case, and see if it will power up and run long enough to pull the data files off. You might get all, some, or the drive is just so far gone that nothing will work.

As I said, this has worked for me on server hard drives, it might work on your laptop hard drive.

I done the same thing several times to retrieve data from a dead/dying hard drive.

---

### Post by ScottinSoCal on 2009-12-07
> **cariboo907 said:**
> I done the same thing several times to retrieve data from a dead/dying hard drive.

An old computer hardware trick used by old computer admins. ;)

---

### Post by Chris Edgell on 2009-12-08
I wish you luck.

---

### Post by The_Pirate_King on 2009-12-08
> **ScottinSoCal said:**
> This is an unusual thing, but it's worked for me in the past with server hard drives.

First, stop turning on your laptop and get a replacement drive ordered. Don't touch it again until the new drive  is delivered. Once the new drive is in your hands, take the old drive out of your laptop and (this is the weird part) put it in the freezer for a few hours - long enough to get very cold. While it's cooling off, install your new hard drive, the operating system, the applications - just get things in place and ready to run. Then take your old drive, put it in an external case, and see if it will power up and run long enough to pull the data files off. You might get all, some, or the drive is just so far gone that nothing will work.

As I said, this has worked for me on server hard drives, it might work on your laptop hard drive.
Thanks, I might give it a try just to experiment, but I had most all my "important" data backed up so I don't think it will be much of an issue.  I've been living off a 4 GB flash drive the past couple months anyway...

---

### Post by Dark_Stang on 2009-12-08
The freezer trick is fantastic, but please remember to put it in an air/water tight freezer bag first. Condensation kills data.

---

