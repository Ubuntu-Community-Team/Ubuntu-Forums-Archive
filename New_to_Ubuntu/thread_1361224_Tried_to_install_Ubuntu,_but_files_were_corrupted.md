---
title: "Tried to install Ubuntu, but files were corrupted"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2009-12-21
Hi everyone :) I'm a totally newbie and need help desperately. I have two HD with C: having windows xp on it and J: with just data. I tried to install ubuntu on J: from a cd I downloaded from your site and as it was installing it came up with messages that the files were corrupt and I quit the install. I then tried to put mint on and it said ubuntu was installed on the drive. Anyway I've made a big mess. What I wanted to do was format both drives so I can keep the J drive in this machine and dual boot ubuntu with win xp and take the other drive (with winxp on it) out and put it in another computer. I have my capabilities confused with my possibilities and just have no idea what I'm doing :lolflag: Does this make sense? How do I do this? do I use the windows disk and format both drives first? Help!

---

### Post by itang sanjana on 2009-12-21
Hello, [s]welcome to the community ..[/s] See the big picture below:
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs).

Enjoy ..

---

### Post by audiomick on 2009-12-21
Hallo.
It sounds like the cd is corrupted. The best thing would be to get another one, and let it check itself before you use it. When you boot into the cd, i.e. put the cd in the drive and re-start the computer, it is one of the options in the menu that appears.

The cd drive needs to be in the boot devices list. This can be changed, if necessary, in BIOS.

I suspect you might have problems when you put the intact drive with xp on it in another machine. As far as I know, xp has "security" (read: annoying) measures to prevent piracy that take note of the computer hardware at installation and complain if it changes. If should run, I think, but you will more than likely have to re-activate it. I am afraid I can't tell you how to do that. Maybe someone else know better on this subject.

When you have removed the drive that you want to put in the other computer, install xp in the one you are leaving in that machine.
Then, boot from the cd and run the Ubuntu install.
This will give you some instructions:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Iowan on 2009-12-21
I haven't used Mint, but I suppose I'd have expected it's installer to give you the option to format the partition (formerly known as Ubuntu) before it tried to install Mint.

---

### Post by ThePinkWitch on 2009-12-21
[QUOTE=audiomick;8539515]Hallo.


I suspect you might have problems when you put the intact drive with xp on it in another machine. As far as I know, xp has "security" (read: annoying) measures to prevent piracy that take note of the computer hardware at installation and complain if it changes. 

Thankyou so much for answering but you mis understand. I don't want to put the drive in the other machine and use the windows, I want to format it and put it in the other machine :) The other computer has it's own legal copy of windows so I'll put that back on. I need to format both drives and take one out. Then put Ubuntu and win xp back on the second drive. I tried to put Ubuntu then mint on the second drive so is it ok to format both drives with the windows disk or do I need a boot disk or something? Thnkyou so much for answering guys :)

---

### Post by audiomick on 2009-12-21
Ooooooh.... (light bulb lighting up...)
Ok.
On the live cd, there is a thing called gparted in system> administration> gparted. That is a linux partitioning tool that you can use to re-format the disc that is coming out. You need to put an ntfs partition on it for it to be useful to xp.

You can use the same tool to set up the other one before you start your installs, but I am a bit shaky on the exact procedure. I think, if you create a partition the size that you want to have for the xp install and leave the rest un-allocated, that's the easiest way. You then install your xp, then install your Ubuntu into the unallocated space.


I have to hit the sack now. We're 10 hours behind Australia here, so it's about 3.15 a.m. I'll look back in tomorrow, this evening for you.

---

### Post by ThePinkWitch on 2009-12-21
Thankyou Soooooooo much Michael :)

---

### Post by juancarlospaco on 2009-12-21
Maybe you got Virus, then it eats the ISO.

---

### Post by audiomick on 2009-12-22
> **juancarlospaco said:**
> Maybe you got Virus, then it eats the ISO.
This could be possible, I spose. You are burning your CDs from a windows machine, aren't you? How long since you did a complete scan on it?

Also, by the way, I've seen several people mention that using CD-RW blanks, the ones you can erase and use again, often doesn't work for the Live CD. You should use a CD-R blank.

---

### Post by ThePinkWitch on 2009-12-23
> **audiomick said:**
> This could be possible, I spose. You are burning your CDs from a windows machine, aren't you? How long since you did a complete scan on it?

Also, by the way, I've seen several people mention that using CD-RW blanks, the ones you can erase and use again, often doesn't work for the Live CD. You should use a CD-R blank.

Possibly you guys are right. I was having huge issues with my machine so that was one reason I wanted to format. I have now partitioned with gparted and put two partitions on. I put windows in one and thought Ubuntu would install on the other. Dunno what I did wrong but it has windows on 100g about 80g on an empty drive and Ubuntu is on about 4gig. What the? lol. How do I uninstal ubuntu and put it on the empty partition? Do I need to put this in a new thread?

---

### Post by audiomick on 2009-12-23
Hallo.
That sounds like a bug I have seen mentioned, that the installer creates a tiny partition and puts ubuntu into it and leaves the rest empty. 

The solution, if I remember rightly, is to install again and do your partitions manually during the install.

How had you intended the partitions to be? All (ubuntu) in one, or had you wanted to put /home separate? I would guess not.

Are you familiar with the linux file system structure?

If you don't specify diffently, ubuntu will install into one partition. The top of the pyramid (or base of the tree, if you prefer) is called /

Within that, there are a number of directories called things like /root , /etc , /var and /home , amongst others.

/home is of particular interest, because that is where all your data lands by default, and where all your personal configuration stuff is stored. If you have a separate /home partition, if you ever have to re-install, you can simply re-mount the /home partition in the new install and thereby retain all your data and settings. Good Thing!

Don't be fazed by this, I know it sounds daunting when you are first confronted with it, but it is pretty self explanatory when you get down to setting it up. You have already successfully used gparted, so you are half way there... :)



Most people recommend the following scheme.

a partition about 10 GB mounted a /
a swap partition a small amount bigger than your swap.
a partition with the rest of the space mounted at /home

Re size of /  : a fresh install will (with a separate /home) put about 2.7 GB in /  . The system will grow with time. I had to expand the / for someone recently because it was full at 5GB (and it was a pain.. ). My system, after 2 and a half years of updating and indiscriminate installing, is up to about 6GB. 10 GB is a good compromise between leaving enough room to grow for the next few years and not occupying disc space for no good reason.


Re swap: swap is where the system puts stuff "for now" when the RAM gets full. If you have a decent amount of RAM ( upwards of 1GB) your system may never access the swap, depending on what you do with it. Photo editing, for instance, is RAM intensive, as is having 5 applications open at once, and 35 web sites open in firefox (do it all the time...:))

BUT the hibernate function writes the contents of RAM to the swap space. The is why it should be as big as your RAM. If you know you will never want to hibernate, you can make your swap smaller. 1GB is ok.

The system will run without a swap partition, but this is not recommended.

As I said, looks confusing, but it is pretty self explanatory when you are sitting in front of it. I managed it the first time on a wing and a prayer with no pre-knowledge. The most important thing is to know where the windows install is, so you don't accidently install over it, but given that you set up the partition for it yourself, you should know that.

---

### Post by ThePinkWitch on 2009-12-23
Thankyou so much for your help :) I have just done what I think you said lol..hopefully it turns out ok..its installing now. It was confusing when it asked what type of file system it was for each one, I just guessed ex2 except for the swap. It also said it had 6 partitions, I thought there would be only four. Oh well I'll see what happens when it finishes installing. Thanks again Michael :) oh I forgot..it asked me if I wanted primary partitions or logical..I didn't know that either..If I screwed up I'll just have to do it all AGAIN! :D

---

### Post by audiomick on 2009-12-23
Sorry, I should have mentioned the file system, I spose.

9.10 actually uses ext4 by default, which is a newer development of ext2, but I believe that ext2 will also work without a problem.

I'd be interested to know what the 6 partitions are...

Edit:
Primary and logical:
you can only have 4 primary partitions on a disc. logical partitions were developed to get around this. If a disc has 3 partitions already, or if the total number will exceed 4, you have to create and extended partition within which you can create logical partitions. Logical partitions always get a number above 5. 1 to 4 is reserved for primary partitions.

I'll attach a picture of my first disc.

---

### Post by ThePinkWitch on 2009-12-23
Thanks Michael. I actually just used the Ubuntu installer to redo the aprtitions not gparted. It seems to have worked. Can't get my internet to work now I reinstalled Ubuntu. I was so surprised it worked right away in the first install. Totally refuses now. Go figure. Anyway thanks for all your help :) Off to network forum now :D

---

