---
title: "Recommended partition sizes"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by japhyr on 2010-08-07
I am about to install 10.04, and I want to do a dual-boot setup.  I want to be able to install 10.10 this fall alongside 10.04, and from then on flip-flop new versions.  So I want to make the following partitions:
Partition 1 - OS 1 (10.04)
Partition 2 - OS 1 home
Partition 3 - OS 2 (will be 10.10)
Partition 4 - OS 2 home
Partition 5 - data (will be linked to each home partition)
Partition 6 - swap?

I have a 500G hard drive and 4G of RAM.  Can someone recommend sizes for these partitions?

---

### Post by Elfy on 2010-08-07
If you are going to be storing data outside of home then I wonder if it is actually worth having seperate homes - I don't have a seperate home - I just make sure to backup the conf files for any app I need the data for.

My media are all symlinked to the home music folder for instance.

But you will get both sides of this argument I am sure.

So as far as sizes go - I would make the OS partitions 10Gb or so, home depends on how you go about the data.

Swap - if you wish to use memory intensive apps then have some, if you wish to hibernate then swap should be equal to or greater than RAM.

---

### Post by japhyr on 2010-08-08
I want to have separate home partitions to keep clean configuration files.  I think this approach will allow me to keep using my existing setup during the time it takes to clean up new installations.

If I am planning to keep all data outside of the home partitions, how big do the home partitions need to be?  Is 10G big enough for home?

---

### Post by Elfy on 2010-08-08
I would say so

---

### Post by japhyr on 2010-08-08
I just installed 10.04, but I'm not sure I did the partitioning correctly.  This is the first time I have partitioned manually.  I am not sure if I did the mount points correctly.  I wanted:
[LIST=1]
[*]Root for OS 1 (10.04).  This was straightforward, I just selected "/" for the mount point.
[*]Home for OS 1.  This was straightforward as well, I selected "/home" for the mount point.
[*]Root for OS 2 (10.10, obviously just reserving space right now).  I put in "/os2/" for the mount point.
[*]Home for OS 2.  I put "/os2/home" for the mount point.
[*]Swap, which was straightforward.
[*]Data.  I put "/data" for the mount point.
[/LIST]
Can someone tell me if I did this right?  I can see all of these mount points in Nautilus, and I'm not sure I should be able to.  Also, if this is incorrect, will I need to reinstall?  That would be no problem at this point.

---

### Post by oldfred on 2010-08-08
I would expect that doing it as part of the install, it added all the partitions to fstab, saving you from having to manually add them.

I found my /home is only 1GB when all my data is in /data. When I created my /data I moved all my folders in home that were just data like documents, music, PDF etc, so then I just link all those partitions back into my /home.

Since I have at least 3 versions of Ubuntu, old, current, & beta/future I created a bash script from the first time I manually did it by listing history & copying to a bash file.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
[http://ubuntuforums.org/showthread.php?t=1411482](http://ubuntuforums.org/showthread.php?t=1411482)

Because I only have folders in my /data I link them all with this command run from home so it is the default (to) location.

for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

/usr/local/fred is where I mount my /data partition. Then I do not see it in Nautilus (except thru links).

I originally did this but had too many folders:
rm -rf Documents/
rm -rf Downloads/
etc, & then
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Downloads

---

### Post by japhyr on 2010-08-08
I will take a little time to digest some of that, but I follow it for the most part.  Can you, or someone else, reassure me that I should be able to use my "/os2/" and "/os2/home" partitions for another ubuntu version at some point?  I haven't done anything to mess that up, have I?

---

### Post by oldfred on 2010-08-08
When you want to install another system, use manual install and choose your / (root) and /home, it will auto find swap. Just remember which partition is which. I have a lot and created one for beta and one for data and initially installed beta Ubuntu into the data partition. Fortunately I had no data in it yet so I just changed the labels.

Also with a second install you have to decide which bootloader (grub) you want. If you are primarily using the old one use the advanced button on the last install screen to not install grub. You can reinstall later if/when you fully switch. Or let the new one install to the MBR and it will add a choice for you older install. The only real difference is which is the first/default boot.

---

### Post by japhyr on 2010-08-09
Thank you very much for the help in this process.  It's exciting to be making a more interesting setup than just the default installation!  I teach my high school students how to install linux, and many of them are interested in dual-boot setups.  This understanding will certainly be passed along, and experimented with by many of them.

---

