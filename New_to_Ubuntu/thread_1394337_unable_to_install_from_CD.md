---
title: "unable to install from CD"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Nygel on 2010-01-30
According to the book, when I try to install ubuntu from the CD I should have 3 options available:- 1. Partion the disc to enable dual boot 2. Clear the disc and only have Ubuntu 3. Something else more complicated!  Well I only have the last 2 options, why do I not have the option to partion the disc (which is what I want to do)???  I have defragged the hard disc and have loads of free space available.
All help gratefully appreciated, thanks
Nygel

---

### Post by ubudog on 2010-01-30
What are the two options?

---

### Post by Nygel on 2010-01-30
The 2 options are:-
"Erase and use the entire disk"
"Specify partitions manually (advanced)"
 
Nygel  (most definitely not "advanced"!)

---

### Post by oldfred on 2010-01-30
Some computers come with all 4 primary partitions used?

run this from liveCD and post results:

sudo fdisk -l  (el not 1 or I)

---

### Post by Nygel on 2010-01-30
> **oldfred said:**
>  
run this from liveCD and post results:
 
sudo fdisk -l (el not 1 or I)
 
Sorry to be so thick but can you explain what this means - in simple language!!
Thanks
Nygel

---

### Post by reaper308 on 2010-01-30
type that command in the terminal and it will give you the results of how your harddrive is partitioned. This will give everyone a better idea of how to solve your problem

---

### Post by Ji Ruo on 2010-01-30
To be precise:

-Boot up the live CD and choose 'Try Ubuntu Without Making Any Changes to Your Computer'

-There is a program called terminal. It opens a window where you can type in commands instead of pointing & clicking, just like the DOS prompt in Windows.

To get to it, click Applications>Accessories>Terminal

- Brief explanation of commands:

sudo - 'Super User DO' This allows you to perform admin functions in Linux.
fdisk - A program that gives you information about your hard drive and its partitions. -l is a flag that gives you a 'long' description ie more info.

- to copy from the terminal window, you have to press <CTRL>+<SHIFT>+<C>. Then you can paste it into a reply in your browser.

HTH

---

### Post by Ji Ruo on 2010-01-30
> **Nygel said:**
> According to the book, when I try to install ubuntu from the CD I should have 3 options available:- 1. Partion the disc to enable dual boot 2. Clear the disc and only have Ubuntu 3. Something else more complicated!  Well I only have the last 2 options, why do I not have the option to partion the disc (which is what I want to do)???  I have defragged the hard disc and have loads of free space available.
All help gratefully appreciated, thanks
Nygel

Reading this again, I'm wondering if you've opened the CD while you're inside Windows. This will install Ubuntu using WUBI as opposed to a dual boot.

The advantage of a WUBI install is that you don't have to muck around with the partitions on your hard disk. It will install Ubuntu on the Windows partition just like a program, then you can choose Ubuntu or Windows when you start the computer up. To remove it, just go to 'Add/Remove programs' while you are in Windows and you can uninstall Ubuntu.

If you want to do a proper dual boot, you will have to boot from the CD. When your computer starts up, on the first screen or two you will have 'setup' and/or 'boot options'. You want to go into this and choose CD, or put CD before the hard disk. Then, when you have the Ubuntu CD in the drive when the computer starts up, it will boot that instead of Windows. Then you will have the normal install options like you have on paper.

Just guessing but I think that's your problem.

Good website on installing - [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by Nygel on 2010-01-30
Thanks for all your replies and the precise description, thats what I needed!
 
> **Ji Ruo said:**
> Reading this again, I'm wondering if you've opened the CD while you're inside Windows. 

 
No, I'm definetly installing from the boot CD - nothing to do with windows.
 
> **Ji Ruo said:**
>  .... -l is a flag that gives you a 'long' description ie more info.
 
 
How do I type the "-l" symbol? Is it 1 or 2 keys? I assume it's the minus sign and then the key that's in the bottom left of the keyboard??? but when I use that key i get the "more than" & "less than" symbols, not what is printed on the keyboard. Or maybe it's nothing to do with that key!!!?????
Thanks
Nygel

---

### Post by harrisonk on 2010-01-30
[SIZE=4]Hello

It is the minus sine (-) plus the "L" key it is not a "T" on its side.

Harrisonk
[/SIZE]

---

### Post by oldfred on 2010-01-30
The easy way to run commands is to just copy and paste them. You can from the browser highlight and right click to copy and open a terminal and right click paste.

It is the small letter L (el phonically) not  1 number one, nor I capital letter I. Most times on screen users think it is one or i.

so copy and paste

sudo fdisk -l

---

### Post by Nygel on 2010-01-30
[SIZE=4]plus the "L" key [/SIZE]
[SIZE=4][/SIZE] 
[SIZE=2]Yes! Of course it is! Obvious when you know the answer! How bloody stupid can I be!!! (Note, no question mark - I don't need an answer to that!)[/SIZE]
[SIZE=2]Right, now I'll go away and get the info originally requested.[/SIZE]
[SIZE=2]Thanks[/SIZE]
[SIZE=2]Nygel[/SIZE]

---

### Post by Nygel on 2010-01-31
> **oldfred said:**
> Some computers come with all 4 primary partitions used?
 
run this from liveCD and post results:
 
sudo fdisk -l (el not 1 or I)
 
The results I get are as follow:-
 
Device Boot Start End Blocks ID System
 
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 22386 179767350 7 HPFS/NTFS
/dev/sda3 22387 29982 61014870 7 HPFS/NTFS
/dev/sda4 29983 30393 3301357+ db CP/M/CTOS/....
 
 
I am sort of assuming as there are four lines of info that the disc has already got 4 partions??? There is a C drive and a D drive but I've no idea what the other two are.
So where do I goto from here??? I really do not want to mess up the existing disc so I'm think that just adding a second hard drive may be the easiest and safest option, that way I think I can keep Windows and Ubuntu completely seperate. Any thoughts???
Thanks
Nygel
 
PS when I typed this it all looked very readable, now I've previewed it I see it has taken all the spaces away from the disk info, hope you can still understand it!!!!

---

### Post by oldfred on 2010-01-31
I always prefer multiple hard drives each with an operating system and the MBR set to boot that system. If one fails you can in BIOS set the other first and still boot.

Most windows computers do not have an install CD. The recovery partition often lets you write a CD that will erase your entire drive and reinstall to "factory new" with all the cr*pware(and erasing all your files & settings). Some may only work if the partition is still there. Also some Dell computer have media software that boots directly. Some of that software can interfer with grub and makes one more reason to have a separate drive.

I would install the new drive and set it as first in BIOS. When you install Ubuntu it will find your windows install and allow you to boot it. If you ever have issues, your windows boot is still configured so you can still set it first in BIOS and boot. Not sure if you have the media direct software what it does with a second drive booting first.

---

### Post by Nygel on 2010-02-01
Thanks Fred, I will install another hard drive and then get back to you all with my next set of problems!!!
Nygel

---

