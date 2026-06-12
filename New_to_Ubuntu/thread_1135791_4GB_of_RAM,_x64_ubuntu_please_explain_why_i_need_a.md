---
title: "4GB of RAM, x64 ubuntu please explain why i need a swap partition n question installs"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-04-24
Ok i have 4GB of RAM on my laptop in Windows 7 i barely use more than 1.5GB of RAM. I had already set up my HDD which is 320GB as such. first time i did it 100GB 7, 60 UBuntu, remainder Media files and such. Now i resized it as 76GB 7, 60GB Ubuntu, and the remainder is for all of my multimedia files. So can anyone explain to me how to properly install ubuntu? 

It tells me install right beside the 7 boot loader as the first option. So that would mean in theroy to me atleast that it'd install it on teh 1st partition i have. 

I tried to do the manual paritioning option but can't figure out how to make it install ubuntu on my /sda2. I was just wondering why i'd need swap. I don't hibernate, i have 4GB of RAM. I also won't be using Virtualization software.

Edit:Why i'm using 7 is b/c of my school, their forcing me to use a Window OS to do my hw upon it.

tl&dr?;
Why should i have a swap parition if i have 4GB of RAM don't do virtualization on my laptop, and also don't hibernate. 

PS. If anyone can explain to me why my Fans are working properly in my laptop that'd be great too. In ubuntu 9.04 my fan never kicks on yet in 7 i can feel it kick on if i'm doing something.

edit2:messed up on the releases.

---

### Post by James_Lochhead on 2009-04-24
You don't really need one. I have only actually needed it while virtualizing.

---

### Post by 133794m3r on 2009-04-24
ok can you also explain which option to use in my setup then? which option should i use to make it run properly and use my partitions properly.

---

### Post by Hospadar on 2009-04-24
You'll want to do manual partitioning, then when you get in, select the partition you want to install to (sda2 sounds like?), and set the mount point to "/" (without quotes).  This makes that partition / in your filesystem.  You can set up separate partitions for /home and other folders in the same way.

As above, you don't really *need* a swap on a machine like that, but it's always nice to have if you ever do need it, and it's easier to set up now than at some later date when it turns out you need more memory.

As to your fans, it's probably that ubuntu is just runnin a little cooler than 7

---

### Post by 133794m3r on 2009-04-24
well i had it sitting on my bed and it got really warm and never ran which really worried me and ok i'll set it up then. Thanks for the help :D

---

### Post by jsowoc on 2009-04-24
I would say that having 128 MB of swap would be good. I also have 4 GB of RAM, but I find there are some programs that load up libraries that are never used. They are written out to swap, so I can have more RAM free for disk cache.

As said above, if you choose manual partitioning, you should see a 60 GB partition /dev/sda2. You can then "edit" the partition, set it to be formatted as "ext3", and the mountpoint as "/".

---

### Post by lavinog on 2009-04-24
I would make a seperate thread for your fan issue, and post your system specs (video card especially)
Also knowing if your fan worked in past releases may be good to know.
My laptop can go a long time without the fan kicking in in hardy, but in windows it almost always runs...but at the same time if I reboot from hardy and stay on the grub boot menu, the fan will run at for a couple of mins at a high speed. It is like hardy has different temperature settings than bios.

---

### Post by 133794m3r on 2009-04-24
ok i already made a brand new thread with it in there. Specs etc.

---

### Post by Sir Jasper on 2009-04-24
Hi,

I'm sure that you, in your particular circumstances, don't need a swap file and there are both windows and linux programs that can record temperatures,

My regards

---

### Post by bodhi.zazen on 2009-04-24
As you say , swap is needed if you are low on RAM. With a desktop install and 4 Gb ram this is extremely unlikely.

The only time you will need RAM is if you run a laptop and want to use hibernation, in which case the contents of RAM are written to swap, so you need swap = RAM + say 128 mb .

If you are using RAM heavy apps, such as Virtualization, you may need swap.

---

