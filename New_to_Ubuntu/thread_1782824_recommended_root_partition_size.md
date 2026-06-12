---
title: "recommended root partition size?"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by soylentcola on 2011-06-15
So I've got a 40GB partition on my hard drive for Ubuntu, 8GB going for swap, 500MB for /boot, and now I'm down to the root directory, but I haven't got a clue what size to give it...is 4GB not enough? Should I go for 8 or 10?

---

### Post by shibu_sawyer on 2011-06-15
My root partition is 3.5GB, and currently about 2.1GB is used up. This is partially because I use this partition  as storage space for package files that I download, and partially because I install everything that comes my way. Your mileage will vary, of course, but I would  think 2-3GB would serve well for starters. If you're short on space, you  can leave out some of the bigger packages and install in 1GB or less. If you have a giant hard drive like I do (30GB), leave room to expand.

---

### Post by mastablasta on 2011-06-15
10 Gb or a bit more for root.
 
you can also let the system installer do the partitioning. it will automaticly give the right partitons.

---

### Post by soylentcola on 2011-06-15
awesome, guess I'll shoot for that 4GB then, just to see. :D

---

### Post by jtarin on 2011-06-15
/ (root directory) and /root (the home directory of the root user) "/" is the top of the tree, everything is under it. At one time (in the distant past) I made separate partitions for "/",boot,/home, /var and swap. Now I dedicate the whole partition to Linux and a separate swap partition of about 2GB's. The reason....I make a partition image and back it up on another drive once a week. If you want to play around with different flavors of Linux and you have personal files in /home.....it would be a good idea to make a separate partition for it......just don't overwrite it on next install. :p

---

### Post by 3rdalbum on 2011-06-15
Swap should be a maximum of 1 GiB unless you want to hibernate the computer (in which case, it should be the size of your RAM).

/boot is pretty unnecessary, unless you really know that you need it.

The rest should go to /, assuming you dont want a separate /home partition. If you do, then make / about 10 GiB.

If you reinstalled Ubuntu it would preserve the /home even if its on the same partition, so you might as well have the flexibility of all one partition.

---

### Post by r-senior on 2011-06-15
I'd always recommend a separate /home partition: 8-10GB for /, whatever you want for swap depending on your RAM size and hibernation, then allocate the rest to /home.

The advantage of a separate /home partition is that you can easily reinstall rather than upgrade. Synaptic has the option of exporting your currently installed packages. Install a new version, formatting only the / partition, update, then optionally import your packages back into Synaptic and update again.

---

### Post by Anuovis on 2011-06-15
I have a separate /home and everything else under / which is 15 GB. Just wanted to be on the safe side. 

During my use it has always stayed under 10 GB (around 6GB or 8GB at most) but at least 10 GB is probably necessary. You could go with less but there is a risk it might run out of space.

---

### Post by kimda on 2011-06-15
Make root partition 10gb or more since its going to hold all the software, logs etc.. With desktop systems I make partitions for /, /boot, /home and swap. Swap 1 to 2 gb depending on ram. /boot - 500m is more than enough. /home the rest you've got.

---

### Post by moraxu on 2011-10-26
I have another question regarding the root partition. Why does everybody say that their "/" has less than 20 GB ? Did I make a big mistake by setting my root partition's size to 50 GB ? (I've read it is similar to **C:\**, so...).

---

### Post by BeRA on 2011-10-26
I use 8GB partition for "/" (but you could use a bit more if you think you'll need it) and the rest goes to "/home" partition; as for swap partition size - it's equal to my RAM size :)

---

### Post by beew on 2011-10-26
Make in around 20G it should be more than  enough. I have lots of crap installed and it uses only around 13G, my / partition is 30 G and it is way too much.

---

### Post by drs305 on 2011-10-26
> **moraxu said:**
> I have another question regarding the root partition. Why does everybody say that their "/" has less than 20 GB ? Did I make a big mistake by setting my root partition's size to 50 GB ? (I've read it is similar to **C:\**, so...).

It depends where you keep your data and other personal files. If you are using Ubuntu with your documents in Documents, music in Music, etc, the size needed for Ubuntu could swell to huge numbers - don't worry, there are solutions if that happens. If you keep all your data outside of the Ubuntu partition, 50GB is pretty large. 

If you have the disk space, it's not a problem. If you end up needing the space, you can use Gparted CD, SystemRescueCD or Live CD and Gparted to shrink the Ubuntu partition. It has to be unmounted for resizing, which is why you need a CD or be running from another OS. I've resized Ubuntu many times with Gparted without problem - but always back up your irreplaceable files first.

---

### Post by moraxu on 2011-10-27
Well, I need 50 GB since I'm gonna install VirtualPC with Windows 7. That's the main reason :)

> **drs305 said:**
> It depends where you keep your data and other personal files. If you are using Ubuntu with your documents in Documents, music in Music, etc, the size needed for Ubuntu could swell to huge numbers

What do you mean ? I set /home's size to 150 GB and those directories were in /home as far as I know.

---

### Post by cryptotheslow on 2011-10-27
If you run Win7 in a virtual machine (VirtualBox, VMWare etc.) then the files for it will be deposited within your home directory structure - so within your 150GiB. Unless of course you deliberately create the VM files outside your home structure.

With that in mind, your / partition is probably a little oversized - but it won't hurt anything and you can always shrink it if you start to need the space adding into your /home partition at some point in the future.

---

### Post by moraxu on 2011-10-27
OK then. I've one more question (the last one :)) just to make sure I get it right. Do all of these directories:

[http://www.computeractive.co.uk/IMG/037/141037/image-linux-folders3929-580x358.jpg?1292954854](http://www.computeractive.co.uk/IMG/037/141037/image-linux-folders3929-580x358.jpg?1292954854)

belong to **"/"** except the **home** directory ? If so, then it's kinda strange - folders in the same parent directory (here it's root - **/**) belong to 2 different partitions (all folders except home to 1st partiton and home directory to the 2nd one)... Something like this wasn't possible on Windows.

---

### Post by philinux on 2011-10-27
> **moraxu said:**
> OK then. I've one more question (the last one :)) just to make sure I get it right. Do all of these directories:

[http://www.computeractive.co.uk/IMG/037/141037/image-linux-folders3929-580x358.jpg?1292954854](http://www.computeractive.co.uk/IMG/037/141037/image-linux-folders3929-580x358.jpg?1292954854)

belong to **"/"** except the **home** directory ? If so, then it's kinda strange - folders in the same parent directory (here it's root - **/**) belong to 2 different partitions (all folders except home to 1st partiton and home directory to the 2nd one)... Something like this wasn't possible on Windows.

Even if home is on its own partition the file path is still /home/username and /home has root permissions.

Forgot. I have 2 gig swap, 12 gig root and rest of drive is home on its own partition.
In root the file system is using about 5 gig. It's a 250 g hard drive.

---

### Post by satanselbow on 2011-10-27
> **moraxu said:**
> Something like this wasn't possible on Windows.

It is available in windows but not used with any regularity. It is certainly not possible as part of the setup/installation routine.

If you were to create a partition with Windows Disk Mangler you get the option to mount your new partition in a folder (instead of a drive letter E:, F: etc) - more or less the windows equivalent of what linux does (quite sensibly and for good reason) by default ;)

---

### Post by searchfgold6789 on 2011-10-27
Actually that's an interesting question. All usable folders and files are contained in the root file system / , no matter what device they are on. The only exception to this is a network share.
Therefore a better term to use for / would be the root file *structure*.

---

### Post by drs305 on 2011-10-27
> **moraxu said:**
> 
What do you mean ? I set /home's size to 150 GB and those directories were in /home as far as I know.

What I mean is that if /home is on a separate partition, and you store your data in the default folders (~/Documents, ~/Music, etc) all that data is going to be stored on the partition with HOME on it. 

If you don't keep data in your /home folder, it will be approximately 1-2 GB, more or less (I'm finding Duplicity backups can take a lot of space and are by default also stored here).

If you keep 100GB of music and data in ~/Music, your /home on a separate partition is going to take up 101 GB of space. Of course, it will take up 101 GB of space if your /home partition isn't on a separate partition, so your / partition in that case would have to be increased accordingly.

I keep all my data in a large separate partition. It allows me to know within a GB or two how large my OS is going to be and I'll never need to resize / or /home no matter how much data I have.

---

