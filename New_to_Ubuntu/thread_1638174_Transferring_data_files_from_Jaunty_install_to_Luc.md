---
title: "Transferring data files from Jaunty install to Lucid install"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-12-05
Awhile back I installed Lucid 10.04 LTS to my computer.
My Jaunty install is still in place as well. You can select wish version to boot upon start up.

My problem is 1. no user data was transferred during the Lucid install from Jaunty. My Desktop is empty etc. 2. I cannot figure out where to put my Jaunty data files in the new Lucid install.

I have two partitions. One for Linux and one for MSDOS. I have attached a file that shows a screenshot of folders. Do i transfer the folders under Places: Filesystem > Home > Ed (my name) to the
Media > Disk > Home area? "Disk" being the partition for Linux and "Disk-1" the MSDOS partition.

Should I use Nautilus under Root Terminal to accomplish this as file permissions are giving me a headache.

Thank You.

Ed

---

### Post by pricetech on 2010-12-07
I've got a response in your "..back to windows.." thread as well.

It looks like you're booted to Jaunty and the window on the right is Lucid.

To move the files, just drag and drop them from left to right, matching folders.  In other words /home/ed/documents to /home/ed/documents, /home/ed/desktop to /home/ed/desktop, and so on.

You'll need to change ownership once they're in the new location since "ed" under Jaunty is different from "ed" under Lucid.  To do this; boot to Lucid and open a terminal and type;

sudo chown -R ed:ed /home/ed/

This will make "ed" the owner of /home/ed and everything in it.

If I'm over simplifying, please don't take offense.  I've been where you are and I'd much rather over simplify that over complicate.

Let us know if you need more help.

Joe

---

### Post by Michaelg14 on 2010-12-07
For future reference, I would set up a separate partition to use as your "home". Then it makes no difference what updates/upgrades you do, your data is always there and unchanged.  I am using 10.10 for everyday and 11.04 for when I want to live dangerously but the home partition is the same and all my data is available to both systems.

---

### Post by owiknowi on 2010-12-07
You've already got your answers so i only will add a little.

First always make a back up or copy of your files to external media (CD/DVD/HD/etc.)
Even if your computer crashes you still got the files that are important to you.

A basic partition lay-out for a multiple boot system with separate /home partition could look something like this:

1. primary partition for first OS (or ms wx, then set flag to boot).
2. linux swap (4GB or 4096MB)
3. primary partition for your files (/home)
4. extended (here you can make several logical partitions for other OS).

Gparted or PMagic are free bootable partitioning tools which you can use.

---

### Post by ozark_hillbilly on 2011-01-02
Okay two steps forward one step backwards...

I received my new zipdrive and started to transfer files.
I successfully put my Desktop files and my wife's /home folder on to the zipdrive and then to the Lucid install (10.04).

But I now have no internet connection. I could use the browsers under Lucid before transferring these files.

Do I have to transfer the entire home directory at once? I have 8 gig on the zipdrive.

Is it necessary to transfer anything out of /etc to the new install or is just /home all that is required? Do you have to tell it to transfer hidden files? Is all your config data for your browsers kept under the /home folders or elsewhere?

I do want to set up a new partition to put /home under so future upgrades are less messy. When I make a new partition do you have to tell Linux that is where my /home folder now resides or does it automatically figure this out?

---

### Post by ozark_hillbilly on 2011-01-03
Anybody out there????

Ed

---

### Post by ozark_hillbilly on 2011-01-03
Bump....anybody out there?

---

### Post by Paqman on 2011-01-03
> **ozark_hillbilly said:**
> 
But I now have no internet connection. I could use the browsers under Lucid before transferring these files.


That's odd. If you create a new account are you able to get online with it? If not, then it's a separate problem.

> Do I have to transfer the entire home directory at once? I have 8 gig on the zipdrive.

You don't have to, but I don't see why you wouldn't.

> Is it necessary to transfer anything out of /etc to the new install or is just /home all that is required?
If you just want to preserve your data and settings then you only need the contents of your home folder.

> Do you have to tell it to transfer hidden files?

Yes, make sure you grab these. Hit Ctrl-H in Nautilus to see hidden files, these are where your settings live.

> Is all your config data for your browsers kept under the /home folders or elsewhere?

It's in home, but the location will vary. Firefox's config is in ~/.mozilla.

> 
I do want to set up a new partition to put /home under so future upgrades are less messy. When I make a new partition do you have to tell Linux that is where my /home folder now resides or does it automatically figure this out?

No, you'll need to tell it where it is. It's easily done at install time. If you've already installed then it becomes [a bit more complicated]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by ozark_hillbilly on 2011-01-03
PAQMAN,

Thanks!

I'll have to try another transfer WITH HIDDEN FILES! Hopefully this will straighten things up...

---

### Post by dBuster on 2011-01-04
> **owiknowi said:**
> You've already got your answers so i only will add a little.

First always make a back up or copy of your files to external media (CD/DVD/HD/etc.)
Even if your computer crashes you still got the files that are important to you.

A basic partition lay-out for a multiple boot system with separate /home partition could look something like this:

1. primary partition for first OS (or ms wx, then set flag to boot).
2. linux swap (4GB or 4096MB)
3. primary partition for your files (/home)
4. extended (here you can make several logical partitions for other OS).

Gparted or PMagic are free bootable partitioning tools which you can use.

I am about to make this move myself.  Of course after doing a good thorough back up.  However, when I first installed Jaunty I did not create a separate home partition.  I have now reduced the size of my windows partition and have an open spot, unallocated space, on my hard drive which I would like to partition as my home partition.  The attached screen shot shows my hard drive setup.  

Question being, will the placement of the free space/unallocated space be an issue?  Or does it not matter?  What do I create in that free space/unallocated space for the home partition?  A primary partition?  Do I label it anything?

Thanks in advance!

[IMG]http://ubuntuforums.org/picture.php?albumid=1154&pictureid=7298[/IMG]

Would be nice to be ready when I get my NAS to get this upgrade done.

---

### Post by dBuster on 2011-01-05
bumping this up to the front again...

---

### Post by dBuster on 2011-01-07
> **dBuster said:**
> bumping this up to the front again...

Nobody has any input?

---

