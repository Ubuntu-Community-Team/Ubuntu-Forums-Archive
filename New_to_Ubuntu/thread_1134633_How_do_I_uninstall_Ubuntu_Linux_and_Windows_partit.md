---
title: "How do I uninstall Ubuntu Linux and Windows partition?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by sashag on 2009-04-23
Hi!

I'd just like to know how I can delete the Ubuntu OS and the Windows XP partition to get a 'clean' hard drive? Hopefully, I can get an answer in the next half hour or so, as I don't have any internet connection on the laptop I'm working on for my friend. I can print out the (hopefully) easy directions and then start erasing the hard drive to have it ready for my friend. Thanks!:)

---

### Post by ugriffin on 2009-04-23
Do you have a live CD? If so, boot up with it, and open "GParted". It's somewhere in the system menu. 


Partition your HD as you please, and enjoy having a completely wiped computer when you shut down from the LiveCD.

---

### Post by j_zhill on 2009-04-23
Try booting into a live CD or USB, then using the partition editor to remove everything you see on the hdd.

Either way, you need to be booted on a different device if you want to format the entire hard drive.

---

### Post by sashag on 2009-04-24
> **ugriffin said:**
> Do you have a live CD? If so, boot up with it, and open "GParted". It's somewhere in the system menu. 


Partition your HD as you please, and enjoy having a completely wiped computer when you shut down from the LiveCD.

Hi!

I tried finding 'GParted' in the 'System' part of Ubuntu, but after installing Ubuntu, I couldn't see 'GParted' anywhere! Did it just disappear? Also, when I boot with the Live CD, I get the same screen I did when I first put in the Ubuntu CD, which has all the options, like starting Ubuntu without messing up the current OS, etc. I tried doing things both ways, the first using the first selection on the screen, and then using the last selection, by booting from the hard disk, which already has Ubuntu as the main OS. 

I even used the 'Help' file in Ubuntu, which basically told me to
click on System, then Admin, then Gnome Partition Editor, which
I can't find any more. As mentioned, I've tried using the Live CD
disk to find GParted, and I've tried using Ubuntu in the 'test' mode, but neither with any luck in finding GParted. I know that GParted is on the Ubuntu OS as I've used it the very first time
I put in the Live CD. After the first time, the Gnome Partition Editor doesn't show up anywhere in the System drop down menu. How can I find it? Thanks.

---

### Post by bodhi.zazen on 2009-04-24
What do you mean by "clean" ?

boot any live Linux CD and use dd to write all 0's to your hard drive if you wish.

You can simply re-install Windows or Ubuntu and use the entire disk, or format the partitions.

---

### Post by zakirs on 2009-04-24
you will find gparted in live cd by the name "Partition editor" in system-->administration menu .. after going into it delete all the partitions .. ( u will have to install it if u already installed ubuntu .. it will only be available in the live cd .. in the installed os u will have to install it seperately)

---

### Post by oldos2er on 2009-04-24
> **sashag said:**
> Hi!

I tried finding 'GParted' in the 'System' part of Ubuntu, but after installing Ubuntu, I couldn't see 'GParted' anywhere! 

 Open a terminal and enter
```
gparted
```

---

### Post by ssdt on 2009-04-24
I had deleted my harddrive memory and the information of both Ubuntu and Windows. Now my computer only has a black screen. Don't know what to do with that old computer.

---

### Post by bodhi.zazen on 2009-04-24
> **ssdt said:**
> I had deleted my harddrive memory and the information of both Ubuntu and Windows. Now my computer only has a black screen. Don't know what to do with that old computer.

Install a new OS ;)

---

