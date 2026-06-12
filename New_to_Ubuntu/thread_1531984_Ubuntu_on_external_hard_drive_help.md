---
title: "Ubuntu on external hard drive help"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by CJ-1990 on 2010-07-15
Hello fellow strayers of the herd ^-^
 
I'm just very new to linux, wanted to see what all the fuss is about, tried the live cd and I was amazed, Ubuntu 10.04 is awesome, but I have some problems that I thought if anywhere, could be solved here.
 
I have a WD External 160GB My passport Hard drive, which is used via any free usb port on my computer, my questions are:
 
Is it possible to make two seperate partitions on this external hard drive and format them to different drive types ie, linux compatible and NFTS? Specifically to use NFTS for 30GB of space for general storage outside of Ubuntu and to use the Linux compatible partition for the Ubuntu operating system with the full capacity minus the 30GB of NFTS.
 
How well do external hard drives cope with running operating systems? Specifically linux ubuntu 10.04. This was an essential question to ask as I don't know too much about computers, only learning, but I don't want my hard drive to stop working after 100,000 writes to the disk because the operating system puts too much strain on it ^-^
If the separate partitions are impossible or hard to achieve then one question remains; If any, what are the file types that can be associated with both linux and windows ie, what file types are compatible with both? and how do I achieve integration of those file types to my external hard drive reffered to at the beggining of this post?

---

### Post by JustinR on 2010-07-15
Hi,

Answering your first question, it is possible to partition your external hard drive like this using the Ubuntu live-cd. To do this you can use one of two programs on it, both are found in System > Administration. The first one is GParted and the other is Disk Utility.

To your second question, external hard drives are just like regular internal hard drives - they will last you for a couple million writes (most likely more). I've put Linux and other operating systems on one of my USB external hard drives and it works fine.

Fat32 and NTFS are both fully supported in Windows and pretty much completely compatible with Linux.

---

### Post by CJ-1990 on 2010-07-15
Hi JustinR ^-^ I'm really new to this site so if this is not the correct way to respond to a thread reply then please notify me, thankyou.
 
Thankyou for the reply dood, so I can format separate partitions to different drive types? And it won't cause undue strain on my drive? That is awesome, have been waiting to install Ubuntu for too long (2 weeks) haha, I was worried that I wouldn't be able to install linux on an external drive, and as for the file types, just have another question sorry.
 
I am going to use linux ubuntu 10.04 for my computing, totally disregarding windows on the internal drive, my question is, If I format the extra 30GB of space to NFTS will it still show up and be usable on linux? Because when I formatted my other drive to linux compatible windows said that there was no drive there 8(
 
Thankyou for the help dood, if there is any way to show my gratification further please let me know ^-^

---

### Post by emoguitarist06 on 2010-07-15
> **CJ-1990 said:**
> ..my question is, If I format the extra 30GB of space to NFTS will it still show up and be usable on linux? Because when I formatted my other drive to linux compatible windows said that there was no drive there 8(

First Question: Yes, I just like having an internal drive with dual boot, Linux can read and write in practically all formats including NFTS.

Second Comment: That is because windows is not compatible and cannot read or write in EXT4/3

Good Luck! Maybe you'll soon been 100% Ubuntu :)

---

### Post by CJ-1990 on 2010-07-15
Thankyou for the help dood, all but one of my questions have been answered ^-^ Sorry if I seem like a noob, but I just want to make sure I can become 100% Ubuntu as you have said haha.
 
Just one final question if you wouldn't mind answering; 
 
When I boot from the live cd do I create the two partitions (Full linux with spare 30GB NFTS partition) mentioned earlier from the Ubuntu installation, or do I use the whole disk to create a linux partition with Ubuntu installed and then create the NFTS partition within Ubuntu to form the extra windows compatible 30GB storage? (So I can store information on the NFTS partition when on windows and get the information off that storage when I boot Ubuntu)
 
How do I add you as a "Friend" on this site? and how do I create the message that comes up with every post ie, the line above -------------- and the quote or saying I want to write, because I would like to use what you said earlier "Hopefully soon I will become 100% Ubuntu"
 
You have been very helpful with my questions, thankyou ^-^

---

### Post by ubunterooster on 2010-07-15
You will want to have the NTFS partition done during install

As for the "signature" > [Edit  Signature]("http://ubuntuforums.org/profile.php?do=editsignature")

As for friends see the screenshots

Edit: Kiwi did not really edit my post; that's just my idea of a funny signature

---

### Post by emoguitarist06 on 2010-07-15
I second the Ubunterooster!

if you want to use someone's text in your replay just click QUOTE right below their post and just delete what you don't mean to quote

You're Welcome

---

### Post by CJ-1990 on 2010-07-15
Thanks doods ^-^ you've all been awesomely helpful with my questions

---

### Post by ubunterooster on 2010-07-15
> **CJ-1990 said:**
> Thanks doods ^-^ you've all been awesomely helpful with my questions
No problem! :D We like to be helpful; it is why we are here.

---

### Post by CJ-1990 on 2010-07-15
That's the kind of mindset that I like ^-^ one question, although not related to this topic;
 
Is there a writing program like microsoft word that I can use on Ubuntu? I already have acrobat 9

---

### Post by ubunterooster on 2010-07-15
If you go to Applications>Office>Open Office, you get the main   Ubuntu equivalent of MS Word (although there are others)

---

### Post by CJ-1990 on 2010-07-15
Awesome, that will come in handy for assignments ^-^ Thankyou dood, you've been really helpful

---

### Post by ubunterooster on 2010-07-15
No problem ;)

---

### Post by JustinR on 2010-07-15
> **CJ-1990 said:**
> Thankyou for the help dood, all but one of my questions have been answered ^-^ Sorry if I seem like a noob, but I just want to make sure I can become 100% Ubuntu as you have said haha.
 
Just one final question if you wouldn't mind answering; 
 
When I boot from the live cd do I create the two partitions (Full linux with spare 30GB NFTS partition) mentioned earlier from the Ubuntu installation, or do I use the whole disk to create a linux partition with Ubuntu installed and then create the NFTS partition within Ubuntu to form the extra windows compatible 30GB storage? (So I can store information on the NFTS partition when on windows and get the information off that storage when I boot Ubuntu)
 
How do I add you as a "Friend" on this site? and how do I create the message that comes up with every post ie, the line above -------------- and the quote or saying I want to write, because I would like to use what you said earlier "Hopefully soon I will become 100% Ubuntu"
 
You have been very helpful with my questions, thankyou ^-^

Hi again,

You only have to make the Linux partition at least 4 gigabytes to install but a recommended would be at least twenty gigabytes, if you used the whole disk for linux then there would be no room for the NTFS partition! So make sure that both partitions (one for Linux and one for Windows) are reasonable sizes, (like 50/50). In Ubuntu you can "mount" the NTFS partition and access data off of it like music/pictures, etc.

---

