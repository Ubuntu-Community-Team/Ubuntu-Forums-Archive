---
title: "Windows/Ubuntu partition filesharing"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Gelegenheit on 2010-12-19
I write and I game.  I love to listen to music while I write and game.  Problem is, I want to manage my music (tagging, storage, etc.) from Ubuntu, seeing as that is the OS that I always have open and Windows cannot read Linux files.  I tried storing music and editing by leaving the music in the Windows partition and accessing it from the /host.  There was something about not being able to journal or edit tags or something to that effect (I don't have it in front of me because I am going back to square one with a clean Windows XP install and my iPod Nano 4G at 1.04.  I want to start fresh so that I don't realize that I screwed up horribly and have to go back and delete all of my partitions and set up Windows XP again because, stupid me, I don't know how to change partitions after they have been established.)

What will allow me to transfer files between Ubuntu and Windows in the same manner that I would transfer between folders or between my USB drive and my computer?

Don't feel obligated to answer all of these questions.  These are just the ways that I tackled the problem in my head last night, aside from "holding Bill Gates hostage to for him to create a bridge between Linux and Windows" or "going into Apple headquarters and DEMANDING that the iPod's file management system be open-sourced and available for third party usage."  Nevermind that it would probably be easier to just go into a store and buy a different MP3 player that has more Linux friendly software.  And nevermind that Bill Gates is no longer CEO of Microsoft and probably knows about as much as, if not less than, I do about bridging NTFS and Ext4.  Part of it is principle and the other part is "$118 for the same freaking thing I already have?".

Thanks in advance for your help and tolerating my stupid questions and pity-party.

1.0 Would I go about using a certain-bootloader or partition manager?
1.1 What is this I keep reading about programs like explore2fs and ext2read?
1.2 What are the risks that come with them and could I mitigate these risks?
2.0 Would formatting all of my partitions on a single filesystem work?  i.e. Formatting both in FAT32 or NTFS (If, and a big if, possible).
2.1 How would that change my experience?
2.2 Would I lose the ability to run the programs that I love so much if I formatted with FAT32?
2.3 Would I still be able to download, install and run the big games like Vindictus?
2.4 If I formatted Ubuntu in NTFS or FAT32, would I lose the aspects of Ubuntu that I love in Ext4, such as speed, stability, and the ability to easily install programs through the Ubuntu Software Center?
3.0 Would adding another hard drive do anything or would that just act as a separate partition and the problem lies in reading?
3.1 Advice: I have a 120 GB PATA hard drive that has the following S.M.A.R.T. report via Speccy in the attachment.  Guess who has no clue how to read this.  This guy :P.  Is this good or bad?  If it is bad, could someone please tell me if it is worth replacing now if I am getting a laptop this summer?

---

### Post by vegetarianshrimp on 2010-12-19
A Comprehensive Guide to Sharing Your Data Across Multi-Booting Windows, Mac, and Linux PCs (Lifehacker.com):

[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

---

### Post by sandyd on 2010-12-19
> **Gelegenheit said:**
> I write and I game.  I love to listen to music while I write and game.  Problem is, I want to manage my music (tagging, storage, etc.) from Ubuntu, seeing as that is the OS that I always have open and Windows cannot read Linux files.  I tried storing music and editing by leaving the music in the Windows partition and accessing it from the /host.  There was something about not being able to journal or edit tags or something to that effect (I don't have it in front of me because I am going back to square one with a clean Windows XP install and my iPod Nano 4G at 1.04.  I want to start fresh so that I don't realize that I screwed up horribly and have to go back and delete all of my partitions and set up Windows XP again because, stupid me, I don't know how to change partitions after they have been established.)

What will allow me to transfer files between Ubuntu and Windows in the same manner that I would transfer between folders or between my USB drive and my computer?

Don't feel obligated to answer all of these questions.  These are just the ways that I tackled the problem in my head last night, aside from "holding Bill Gates hostage to for him to create a bridge between Linux and Windows" or "going into Apple headquarters and DEMANDING that the iPod's file management system be open-sourced and available for third party usage."  Nevermind that it would probably be easier to just go into a store and buy a different MP3 player that has more Linux friendly software.  And nevermind that Bill Gates is no longer CEO of Microsoft and probably knows about as much as, if not less than, I do about bridging NTFS and Ext4.  Part of it is principle and the other part is "$118 for the same freaking thing I already have?".

Thanks in advance for your help and tolerating my stupid questions and pity-party.

1.0 Would I go about using a certain-bootloader or partition manager?
1.1 What is this I keep reading about programs like explore2fs and ext2read?
1.2 What are the risks that come with them and could I mitigate these risks?
2.0 Would formatting all of my partitions on a single filesystem work?  i.e. Formatting both in FAT32 or NTFS (If, and a big if, possible).
2.1 How would that change my experience?
2.2 Would I lose the ability to run the programs that I love so much if I formatted with FAT32?
2.3 Would I still be able to download, install and run the big games like Vindictus?
2.4 If I formatted Ubuntu in NTFS or FAT32, would I lose the aspects of Ubuntu that I love in Ext4, such as speed, stability, and the ability to easily install programs through the Ubuntu Software Center?
3.0 Would adding another hard drive do anything or would that just act as a separate partition and the problem lies in reading?
3.1 Advice: I have a 120 GB PATA hard drive that has the following S.M.A.R.T. report via Speccy in the attachment.  Guess who has no clue how to read this.  This guy :P.  Is this good or bad?  If it is bad, could someone please tell me if it is worth replacing now if I am getting a laptop this summer?
Just store stuff on the windows partition.

If you want, I can make it automount so that all your docs and stuff are automatically stored on windows instead of ubuntu.,

---

### Post by JC Cheloven on 2010-12-19
> **sandyd said:**
> Just store stuff on the windows partition.
This is ok if you'll only read data from that partition when using ubuntu. But it's a bit risky to write systematically in other OS's partitions, in my experience. I'd say that creating a dedicated ntfs data partition is better for the sake of having your files accesible from both windows and linux.

As sandyd says, it can be automounted at startup if you like.

---

### Post by Bucky Ball on 2010-12-19
NTFS data partition as suggested. Easy.

---

### Post by mastablasta on 2010-12-20
starting it all fresh?
 
if so i would do it like this:
make 1 partition as C: drive size 25-30 GB, NTFS file system,  this will be for windows and all the programmes.
make another partition D: drive size 70 GB - this will be NTFS file system, this will be data partition for all the data. if somethign goes wrong with windows you can easilly resintall them or simply format C: and install windows fresh while leaving data intact.
 
the rest 20 GB will be unallocated space for now. you will use it later for Ubuntu.

---

