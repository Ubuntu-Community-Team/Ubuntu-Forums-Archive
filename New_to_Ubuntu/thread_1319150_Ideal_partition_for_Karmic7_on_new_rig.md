---
title: "Ideal partition for Karmic/7 on new rig"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by needastick on 2009-11-08
Hi Guys,
           I'm about to buildmy first machine based on an AMD 785 chipset. I want to install windows 7 and ubuntu to dual boot. I've read the beginners guides on partitioning but I can't find all the answers.

Can I use a live cd, set the partitions, then install windows?

Do I then put the cd back in for Karmic? I'm worried about a new motherboard having the right drivers, the mb came with its own driver installation disc, I don't know at what stage to load that.

I can't seem to find any advice (other than swap file) for how big to size partitions. I'll be using one 500 gig and want to access storage from both os's.

Any advice for an old codger would be appreciated.

---

### Post by durand on 2009-11-08
I don't think windows 7 can access ext3 or ext4 partitions, which are the default on ubuntu. However ubuntu can see ntfs partitions that vista creates so you could use that one as a go between. Basically, you can just install 7 onto the whole hard drive, then put the ubuntu disk in and either let it automatically resize 7's partition to  accomodate ubuntu or manually partition it yourself.

If you have a 500GB drive, you could use 200GB for ubuntu home, 50GB for ubuntu / and for swap, you could use the same size as that of your RAM, unless your RAM is under 2GB. The proportions all depend on how much you intend to use either operating system. I personally would only use 7 as a backup so I would only give it a maximum of 30GB and the rest for ubuntu but its completely your choice.

---

### Post by needastick on 2009-11-08
Thanks for your guidance, it is really the formatting issue that confuses me. Would it be best to install the default file system on each os and then create a further primary partition in say FAT32 that both could access.

---

### Post by louieb on 2009-11-08
Separate the data from both OS.
If I had a new 500GB hard drive I might slice it up something like this


[LIST]
[*]50GB -Win install - NTFS
[*]25GB  - Ubuntu install - ext4 (lots of good choices here)
[*]25GB - Upgrade testing (optional but nice to have) -Ubuntu does put out a new release every 6 months)  - some have not gone that smooth - nice to have.
[*]2GB - Linux swap
[*]whatever is left - data - ntfs or ext4 - What do you plan to use Windows for?
[/LIST]
>  the mb came with its own driver installation disc, Probably windows drivers for sound and networking - install after installing windows - may not need them.

> Would it be best to install the default file system on each os and then create a further primary partitionI normally use Gparted (on the live CD) to create all my partitions before installing the any OS.  Both Win and Ubuntu give you the option of choosing a partition to install in.

---

### Post by Zoot7 on 2009-11-08
> **needastick said:**
> Hi Guys,
           I'm about to buildmy first machine based on an AMD 785 chipset. I want to install windows 7 and ubuntu to dual boot. I've read the beginners guides on partitioning but I can't find all the answers.

Can I use a live cd, set the partitions, then install windows?

Do I then put the cd back in for Karmic? I'm worried about a new motherboard having the right drivers, the mb came with its own driver installation disc, I don't know at what stage to load that.

I can't seem to find any advice (other than swap file) for how big to size partitions. I'll be using one 500 gig and want to access storage from both os's.

Any advice for an old codger would be appreciated.
What I'd recommend you do is to boot off the Karmic liveCD first, launch gparted (system -> administration -> gparted) and create an ntfs partition (however big you want) for Windows 7, but leave some space unallocated for Karmic.

Then install Windows 7 on this ntfs partition
After that boot up the liveCd in Karmic again, and tell it to use the most continuous free space on your hard drive when you're installing Ubuntu. It'll then occupy the rest of the Hard drive along with Windows 7.

For the storage hard drive your best bet is to use ntfs as both OS's can read and write from it.

Also forget about installing drivers; all the drivers are already in the Linux kernel itself so you won't have to install anything in the line of drivers. It'll automatically find all the hardware and configure it appropriately. the only driver you'll have to install is either an ATi or nVidia driver if you've such a card.
So you won't have to worry about drivers for Karmic; Windows of course is a different story.

---

### Post by needastick on 2009-11-08
Good answers guys, thanks for your help, I feel as though I'm going in the right direction now. Just waiting for a bit of hardware, tomorrow hopefully, then the big day...

---

### Post by durand on 2009-11-08
You don't really need to create a separate fat32 partition to share between the two. Ubuntu can read and write to vista's partition easily enough so you can just use that to share files.

---

### Post by Zoot7 on 2009-11-08
> **durand said:**
> You don't really need to create a separate fat32 partition to share between the two. Ubuntu can read and write to vista's partition easily enough so you can just use that to share files.
The only thing with that is Vista is known to kick up a hissy fit if something writes to it's partition without it knowing. There's been cases of where it even refused to boot afterwards. XP doesn't suffer from this problem.
For this reason I'd say the FAT32 or separate ntfs partition is the best option.

---

### Post by durand on 2009-11-08
> **Zoot7 said:**
> The only thing with that is Vista is known to kick up a hissy fit if something writes to it's partition without it knowing. There's been cases of where it even refused to boot afterwards. XP doesn't suffer from this problem.
For this reason I'd say the FAT32 or separate ntfs partition is the best option.

Fair enough. Thats never happened to me but then I don't use vista much at all.

---

### Post by Zoot7 on 2009-11-08
> **durand said:**
> Fair enough. Thats never happened to me but then I don't use vista much at all.
It's never happened to me either, when I was dual booting Gutsy with Vista for about a month. But it seems it has happened to others.
Oh they joys and irregularities of Windows! :rolleyes:

---

### Post by The Funkbomb on 2009-11-08
I had a similar issue except I'm using a 750gb HDD.

Mine turned out to be like this:

200gb for Windows 7
200gb for Ubuntu
5gb for a swap
The rest was an NTFS shared partition.

Install windows 7 and it installs a 100mb Windows Boot Manager.

Install Ubuntu.  Leave X amount for Windows.  I'd say 120gb would be sufficient.  The rest for Ubuntu.

Boot the live CD and resize the Ubuntu partition down to whatever you think you need.

---

### Post by needastick on 2009-11-08
It would seem that NTFS would be best for storage then. I read I think that there was a file size limitation on FAT32. I don't know whether that would affect storing movies.

To summarise then I'm looking at partition one - NTFS. I take it windows will content itself with one partion.

Second partition -extended and then split into two for /home and swap.

Third partition, remainder of space - NTFS. 
Sounds much the same as yours Funkbomb.

---

### Post by olalaaa on 2009-11-14
needastick,

better make a partition for **/** and another one for **home**. And, of course, a third one for **swap** . This as per Ubuntu installation.

---

