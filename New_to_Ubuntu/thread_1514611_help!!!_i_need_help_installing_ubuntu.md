---
title: "help!!! i need help installing ubuntu"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by the juman on 2010-06-21
helllo !!!):P

i am veryy new to ubuntu. i have 2 partitions from which one has w7 and other one has xp . xp drive has about hundred gb free. so i wanted to try ubuntu . i downloaded a alternative 9.10 ubuntu. it dosen't start a graphic installation but a text based installations. it is veyyyyyyy confusing for me.:confused::confused:

so any one who is out there to help me plese tell me how in can install it with out loosing my **important data** on both drives.

step by step is **ok**

thank you any one who is ready to hep me

---

### Post by wojox on 2010-06-21
Put in the CD and when you get to partion use the free partion. or install side by side

---

### Post by marin123 on 2010-06-21
first of all if you want a fresh ubuntu install you need 1 partition. you can get that partition by resizing one of the existing partitions... i dont know if you can resize xp partition but you CAN resize 7 partition (if you have enough free space)...

or you can download WUBI (ubuntu windows installer) and install ubuntu (or kubuntu etc...) inside xp (just like any other program) and if you dont like it just go to add/remove in xp and get rid of it...

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

just follow the link above and you shouldnt have any problems... when you turn on your computer you will get to choose if you want ubuntu, 7 or xp, just like you have now (just ubuntu added to the boot menu)...
if you need any additional help, feel free to ask...

---

### Post by diablo75 on 2010-06-21
What you are wanting to do is shrink the partition that contains Windows XP to create a gap of unallocated space which your Ubuntu installation will need to go into.  Because you have multiple partitions on your hard drive you won't be able to do a Guided partitioning of your hard drive and you'll need to do it manually.

So the first step is to shrink your XP partition.  You should be able to do this with the Alternate CD, but it might take a little poking around (wouldn't know what to tell you myself; I use the graphical Live CD more often).

Once the partition is shrunk you'll need to create two new partitions in the area you just cleared one.  Or rather, at LEAST two partitions.  One will have to function as your swap space; this is typically set to be something around twice the amount of RAM you have.  Another partition will need to be set to function as the / partition (also called root partition).  These two should do the trick.

I gotta go.... sorry....

---

### Post by ronnielsen1 on 2010-06-21
>  downloaded a alternative 9.10 ubuntu I'm not sure what you mean by you downloaded an alternative download? Everything besides Ubuntu 10.04 would be considered an alternative download from the get ubuntu site. You might have downloaded a server installation or something. 

This will get you Ubuntu 10.04 desktop
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

This will get you Ubuntu 9.10 desktop
[http://mirror.csclub.uwaterloo.ca/ubuntu-releases/9.10/ubuntu-9.10-desktop-i386.iso](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/9.10/ubuntu-9.10-desktop-i386.iso)

>  i have 2 partitions from which one has w7 and other one has xp . xp  drive has about hundred gb free. 
You need at least 2 more partitions (one swap and one for Ubuntu) which means you'll have to defrag your xp and then use the linux cd to repartition 
[https://help.ubuntu.com/10.04/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/10.04/installation-guide/i386/non-debian-partitioning.html)
>   If you currently have one hard disk with one partition (a common setup for desktop computers), and you want to multi-boot the native operating system and Ubuntu, you will need to:    
                                
[LIST=1]
[*]                       Back up everything on the computer.  
[*]                       Boot from the native operating system installer media such as CD-ROM or tapes.    
[*]                       Use the native partitioning tools to create native system partition(s). Leave either a place holder partition or free space for Ubuntu.  
[*]                       Install the native operating system on its new partition.  
[*]                       Boot back into the native system to verify everything's OK,     and to download the Ubuntu installer boot files.  
[*]                       Boot the Ubuntu installer to continue installing Ubuntu.  
[/LIST]

              


#1 is important

---

