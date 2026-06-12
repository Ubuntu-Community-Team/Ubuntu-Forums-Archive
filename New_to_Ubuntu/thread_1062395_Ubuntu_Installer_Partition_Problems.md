---
title: "Ubuntu Installer Partition Problems"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Kawaiii on 2009-02-06
I posted this in a related thread but got no replies.

So I'm a linux noob and am trying to install ubuntu for the first time. I'm a pretty advanced windows user and thought maybe ubuntu would be more flexible (I'm a huge customization fan)

Dual booting Ubuntu from having XP installed.

I have 50 gigs of free space at the end of my hard drive. It's free space that I want to install ubuntu in. I'm installing from the live CD, and all the options that it gives me are wrong.

1) Guided 1 - This is the only option that keeps my two existing partitions in the "after" graphic. But it's resizing my partition to get the space- ignoring free space.
2) Guided 2 - No, I don't want to use the entire disk.
3) Guided Continuous Free Space - Uhm... The after graphic shows Ubuntu as using 100% of my hard drive now.  It's not free space, there's partitions I need to keep! I just want it at the end!
4) Manual - The after graphic shows "manual - 100% of drive". There are no options for it. Not very manual, I guess?

I will add that the "Before" picture shows the correct way my Hard Drive is- The two existing partitions and some free space at the end. But none of the after graphics seem to get it right.

Help? I figured I could just have it resize the partitions then afterward use gparted to extend the partition to use the free space anyway. But this is just silly! How do I get it to use the free space that's there?

Some googling brought up few examples of people with similar problems, but no  helpful solutions. Link: [This problem]("http://en.kioskea.net/forum/affich-38577-ubuntu-installation-and-drive-partition") seems similar.

---

### Post by sailthesea on 2009-02-06
Hi kawaiii
 I,m having the same problem myself partitioning the drive prior to install, so far I,ve found out I need to use a live cd with something like Parted Magic to build the partition manually, can't do it from wihin XP or the installation program then you go ahead I,ll see if I can paste the links I went to It seems tricky but if you can get some machine specific advice I think there shouldn't be problems I still haven't quite worked out the settings I need to use We both seem to be stuck at the same place

---

### Post by drs305 on 2009-02-06
Have you visited psychocat's site? He does an excellent job laying out the options for partitioning. Additionally, if you look at the "Create a separate /home partition" you can see how to use the Partition Editor (gparted).
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

And here is the Ubuntu documentation on partitions during installation. It's not as user-friendly for newbies, but there is some good information:
[https://help.ubuntu.com/8.04/installation-guide/i386/module-details.html#di-partition]("https://help.ubuntu.com/8.04/installation-guide/i386/module-details.html#di-partition")

I don't know why the basic installation isn't working in a comprehensibile fashion for you, but if you plan your partitions, boot the LiveCD and then run gparted (System > Administration > Partition Editor) you can make the partitions before beginning the install. You will need at least a system partition( / ) formatted as ext3 and a swap partition (formatted as 'swap'). Many users create a /home partition as well.

Once you have created the partitions you should be able to start the installation (there is a shortcut on the LiveCD desktop) and use "manual" for partitioning, selecting the partitions you have already created.

---

### Post by mpl34 on 2009-02-06
I'm a little unsure what your problem is exactly. However i had problems creating a partition using the ubuntu live disc. I later found that windows system files were near the end of my drive map and even the i had a large chunk of free space (~30GB) the system files near the end of my drive would not let me create the partition as i wanted. I later found that a defrag on boot should be able to move the data closer to that start of the drive map and yes!! it worked and i was able to partition the 40GB i wanted.

This may not be the same problem as you described but hopefully it is useful in some way.

---

### Post by sailthesea on 2009-02-06
Will that work for me too?? I've an old Dell C640 with Windows 2000 and I'm having a similar problem with install I just can't seem to work out how to partition the drive properly AAny tips 
Cheers!

---

### Post by Kawaiii on 2009-02-06
My problem is such- I have free space on the Hard Drive, but the ubuntu installer won't use that to make its partitions and install to.  I can use gparted to make my own and see how that works.

One thing, reading over the Psychocats thing, 

"Ubuntu now has a pretty reliable mechanism for reading from and writing to NTFS, but some people like to play it extra safe and have a separate FAT32 partition for both Windows and Ubuntu to work from."

My second partition, with all my documents and such, is NTFS. What does it mean by being safe? Should I change this to FAT? What exactly is this risk by keeping it in NTFS?

---

### Post by drs305 on 2009-02-06
sailthesea,

If you aren't sure of the partition sizes, psychocat's site explains it. If you aren't sure how to use gparted, here is a good link:
[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")

Defrag first, as mpl34 recommended, and back up important data before starting the repartitioning.

This site has some pix of the install, including manual partitioning:
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml")

By the way, for both of you: Welcome to the ubuntu forums.

---

### Post by sailthesea on 2009-02-06
Many thanks drs305
  I'm getting there slowly and will prevail Methinks I am being too cautious There was a time in my youth when this kind of meddling with a computer was deemed witchcraft and such!:)

---

