---
title: "Creating /home partition: should I move files first?"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by amanchesterman on 2011-04-17
A simple question from a beginner.

I have set up my laptop with Ubuntu 10.10 and I am very impressed with it. However when I installed it I created a single partition across the whole hard drive (120 GB), and having read several posts in these forums since then I now realise that it would have been better to create one partition for the OS and another for my /home folder. (Makes it easier to upgrade the OS in future.)

I have read some tutorials on the net which suggest that it's quite easy to create another partition at this stage, using gparted on the Ubuntu installation disk. But what the tutorials don't say is whether I need to do anything to the files in my /home folder first. If I am going to move them around, do I need to somehow group them together first, making sure that they aren't scattered all over the disk -- or does Ubuntu take care of that for me?

(If this was Windows I would be asking about defragmenting, but I realise that Linux is very different.)

Also, if I create another partition, will Ubuntu automatically recognise that as my new /home folder? Will I see two partitions in the File Manager, like two drives in Windows Explorer?

For info, the disk usage analyser reports that I am currently using about 20 GB out of a total filesystem capacity of 105 GB, so I should have plenty of space to create the new partition.

(And yes, before you say it, I have read the warnings and I understand about the need to back up my data safely before attempting this.)

Thanks,
John

---

### Post by Bucky Ball on 2011-04-17
You might want to start here:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Or even here:

[http://au.altavista.com/web/results?fr=altavista&itag=ody&q=create+new+%2Fhome+partition+ubuntu&kgs=0&kls=0]("http://au.altavista.com/web/results?fr=altavista&itag=ody&q=create+new+%2Fhome+partition+ubuntu&kgs=0&kls=0")

In short, you are going to need to boot Ubuntu from the installation disk and that way all your partitions will be unmounted. You need to shrink your one large partition leaving free space as big as you want the new /home to be. Once you have that done, create the /home partition using the free space and follow further instructions from the links.

It's not quite as simple as creating a separate partition and moving your files. All user settings are also in /home directory/partition so you need to tell the system where they are once moved. ;)

---

### Post by amanchesterman on 2011-04-18
Thanks for your helpful reply. Evidently the process isn't quite as simple as I had thought, but I will probably try it: the instructions in some of the links you sent me seem clear enough.

Thanks again
John

---

### Post by Bucky Ball on 2011-04-18
Should be straight forward. Just make sure you have the space freed up to create a /home the size you want using the LiveCD and all should be good. ;)

---

