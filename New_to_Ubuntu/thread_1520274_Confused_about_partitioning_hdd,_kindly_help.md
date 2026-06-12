---
title: "Confused about partitioning hdd, kindly help"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by John Macnab on 2010-06-29
Hi everyone :)
             I've been reading the page about partitioning the hard disk for installing Ubuntu along with my Win XP and I am a bit confused.(I mean this page: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual](https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual) )
        With my limited knowledge about computers, I cant make out the steps- it tells you to create a root partition as a logical drive? (Well English is not my first language so I maybe just reading it wrong,if so,do forgive me). I'd used Ubuntu for a couple of days a few years back and I think I actually created the root as a primary partition. 
         Next is about home partition-"Creating the home partition
This step is not necessary but will allow you to keep your settings and files in the event you reinstall Ubuntu. Set it up as you would the home partition but choose /home as the mount point."   <<<What does it mean asking someone to set home partition as the same way as home partition but choose /home as the mountpoint? 
        Could someone kindly clear up these two things please?Also, I dont have a clue about console commands,so I had d/lded a linux manual and got  it printed out -will that help with learning Ubuntu or do I need to get an Ubuntu specific book? Please do reply.

---

### Post by madinc on 2010-06-29
wich version of ubuntu do you want to install?

---

### Post by Garthhh on 2010-06-29
> **John Macnab said:**
> Hi everyone :)
             I've been reading the page about partitioning the hard disk for installing Ubuntu along with my Win XP and I am a bit confused.(I mean this page: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual](https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual) )
        With my limited knowledge about computers, I cant make out the steps- it tells you to create a root partition as a logical drive? (Well English is not my first language so I maybe just reading it wrong,if so,do forgive me). I'd used Ubuntu for a couple of days a few years back and I think I actually created the root as a primary partition. 
         Next is about home partition-"Creating the home partition
This step is not necessary but will allow you to keep your settings and files in the event you reinstall Ubuntu. Set it up as you would the home partition but choose /home as the mount point."   <<<What does it mean asking someone to set home partition as the same way as home partition but choose /home as the mountpoint? 
        Could someone kindly clear up these two things please?Also, I dont have a clue about console commands,so I had d/lded a linux manual and got  it printed out -will that help with learning Ubuntu or do I need to get an Ubuntu specific book? Please do reply.

Hi John 

You will probably find this page more useful
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
burn a live CD
during the install process you will be given the option to set up a dual boot
choosing that option will do the actual partitioning

---

### Post by John Macnab on 2010-06-29
madinc:I would like to try and install 10.04 sir.
Garthhh: Ty for the link sir,I'll check it out.

---

### Post by madinc on 2010-06-29
i hope this helps

[http://www.youtube.com/watch?v=m5Jxfj6tu_U&feature=fvw](http://www.youtube.com/watch?v=m5Jxfj6tu_U&feature=fvw)

---

### Post by John Macnab on 2010-06-29
Thank you for the link sir, am watching it :)

---

### Post by John Macnab on 2010-06-29
Uh umm, I am facing some problems with the partitioning. I have 5 WinXP drives on my computer-as far as I know,the C: drive is a primary partition and the rest are logical (is that the word?)drives.I am trying to install Ubuntu to the space now occupied by G: drive.I am  trying to create one additional primary drive for root and a logical drive for /home and a swap space. Problem is, after I create the root and swap,the partition manager shows the rest of the free space as unusable.Also,I have tried creating /home partition and root, but I dont get an option to make /home as a logical drive- if I select to make root as the primary partition then the rest of the partitions that I make are automatically primary??? I cant understand why I am running out of primary partitions? I thought you could have 4 primary partitions on a hdd, and if c: is a primary partition then I have 3 open slots for creating primary partition dont I? So shouldnt I be able to create root, /home and swap even if these 3 are for some reason created as primaries? Could someone kindly tell me why I am facing this problem and what the solution could be please? I have a feeling that something about my assumption about c: being primary and d,e,f,g being extended partitions is wrong, so will be really thankful if someone would take the time to correct me about my false notion.

---

### Post by bodhi.zazen on 2010-06-29
> **John Macnab said:**
> Uh umm, I am facing some problems with the partitioning. I have 5 WinXP drives on my computer-as far as I know,the C: drive is a primary partition and the rest are logical (is that the word?)drives.I am trying to install Ubuntu to the space now occupied by G: drive.I am  trying to create one additional primary drive for root and a logical drive for /home and a swap space. Problem is, after I create the root and swap,the partition manager shows the rest of the free space as unusable.Also,I have tried creating /home partition and root, but I dont get an option to make /home as a logical drive- if I select to make root as the primary partition then the rest of the partitions that I make are automatically primary??? I cant understand why I am running out of primary partitions? I thought you could have 4 primary partitions on a hdd, and if c: is a primary partition then I have 3 open slots for creating primary partition dont I? So shouldnt I be able to create root, /home and swap even if these 3 are for some reason created as primaries? Could someone kindly tell me why I am facing this problem and what the solution could be please? I have a feeling that something about my assumption about c: being primary and d,e,f,g being extended partitions is wrong, so will be really thankful if someone would take the time to correct me about my false notion.

Partitioning is a bit confusing at first.

See this link : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

After reviewing that, if you have questions, please ask.

I would suggest you understand the terminology before you start changing things.

You also should back up your data as, although rare, if something goes wrong during the install data loss can occur.

You can also see the gparted documentation:

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Last, the install CD should to some extent automate the process for you ...

---

### Post by John Macnab on 2010-06-30
Thank you for the links sir, and yes I know I need to learn from the basics, and that link about partitioning seems to be just what I needed,I am reading it slowly and carefully. Well ummm,I have installed 10.04 on my machine and looks like I didnt break anything with my clumsy efforts hehe.*touch wood*

---

### Post by bodhi.zazen on 2010-06-30
> **John Macnab said:**
> Thank you for the links sir, and yes I know I need to learn from the basics, and that link about partitioning seems to be just what I needed,I am reading it slowly and carefully. Well ummm,I have installed 10.04 on my machine and looks like I didnt break anything with my clumsy efforts hehe.*touch wood*

W00t !!!

---

