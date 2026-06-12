---
title: "How do you fix sudo &quot;rm -rf /*&quot;??"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by nevets04 on 2009-10-20
I'm new to Linux and someone was helping me setup a local apache server so i could test my python web apps. This person had been helping me for maybe 15 minutes when he told me to now run sudo rm -rf /*. Apparently I shouldn't have done this. I'm sure you are all aware of the effects of this. Now, I am trying to reinstall ubuntu (By the way I'm on Acer aspire 3680), but it doesn't work, I get a black screen with a bunch of white writing, then when I reboot, and it try's to load grub, it fails. I'm thinking if there is a way to reformat from the disk I can do that. So now my questions:
1. How do you reformat from the Ubuntu 9.04 install disk?
2. Is there an easier way you can think to fix my problem?

If you don't know the effects of sudo rm -rf /*: [http://www.youtube.com/watch?v=wWOjmvWPRvQ](http://www.youtube.com/watch?v=wWOjmvWPRvQ)
This is not my video

---

### Post by Bachstelze on 2009-10-20
All you can do is reinstall. You can format your partitions during the installation process.

---

### Post by nevets04 on 2009-10-20
> **Bachstelze said:**
> All you can do is reinstall. You can format your partitions during the installation process.

Once I choose install, I got errors. Is there anyway I can format from that menu that says like:

. Try Ubuntu without any changes to your computer
. Install Ubuntu
. Test disk for defects
. Boot from first disk

---

### Post by Bachstelze on 2009-10-20
> **nevets04 said:**
> Once I choose install, I got errors. Is there anyway I can format from that menu that says like:

. Try Ubuntu without any changes to your computer
. Install Ubuntu
. Test disk for defects
. Boot from first disk

No, but you can choose the "Try" option, and when you're in the live environment, run GParted to format your partitions.

---

### Post by benj1 on 2009-10-20
if you have any data on there you *may* be able to recover it, im not an expert so ill leave others to make recommendations, but dont reinstall or partition your hard drive if you want anything back.

---

### Post by nevets04 on 2009-10-20
> **benj1 said:**
> if you have any data on there you *may* be able to recover it, im not an expert so ill leave others to make recommendations, but dont reinstall or partition your hard drive if you want anything back.

I don't really mined losing data, as long as my computer works.

I tried using the "Try ubuntu without any changes to your computer"
and now this is happening:
[IMG]http://i36.tinypic.com/2uhn2ar.jpg[/IMG]

---

### Post by Marlonsm on 2009-10-20
There is no way to get the data back after that command, as far as I know.


I've submitted an idea about it to Ubuntu Brainstorm, but some people doesn't seem to like it very much...

[http://brainstorm.ubuntu.com/idea/21957/]("http://brainstorm.ubuntu.com/idea/21957/")

---

### Post by nevets04 on 2009-10-20
Updated Pic:
[IMG]http://i38.tinypic.com/2dc66g3.jpg[/IMG]
Its pretty much following this pattern, but occasionaly changing numbers between the brackets at the beginning.

---

### Post by theozzlives on 2009-10-20
Try using the gparted live CD and put it on a flash drive with unetbootin. Delete all partitions and start from scratch. NEVER use that command again, geeze a little common sence.

---

### Post by Sef on 2009-10-20
You could try [photorec ]("http://www.cgsecurity.org/wiki/PhotoRec")for recovering your data or even better, try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") for recovering your partitions.

---

### Post by yeats on 2009-10-20
> I'm new to Linux and someone was helping me setup a local apache server so i could test my python web apps. This person had been helping me for maybe 15 minutes when he told me to now run sudo rm -rf /*.

Sorry, but I have to ask... who was this person?  What was the venue you were using for support?  Not these forums, right? 

So sorry to hear about your problems... what an *expletive* thing to do to somebody just starting out!:mad::mad:

---

### Post by zerhacke on 2009-10-20
> **nevets04 said:**
> Updated Pic:
[IMG]http://i38.tinypic.com/2dc66g3.jpg[/IMG]
Its pretty much following this pattern, but occasionaly changing numbers between the brackets at the beginning.

That's a hardware error, meaning either your CD or your DVD/CD ROM is bad.  Try burning another disk at a slower speed.  If this doesn't work you're looking at getting another drive.

---

### Post by nevets04 on 2009-10-20
I was able to boot from a fadora live cd. Is there anyway I can reformat from here?

---

### Post by nevets04 on 2009-10-20
accident double post

---

### Post by nevets04 on 2009-10-20
> **zerhacke said:**
> That's a hardware error, meaning either your CD or your DVD/CD ROM is bad.  Try burning another disk at a slower speed.  If this doesn't work you're looking at getting another drive.

k, I will try reburning

---

### Post by nevets04 on 2009-10-20
> **chrissharp123 said:**
> Sorry, but I have to ask... who was this person?  What was the venue you were using for support?  Not these forums, right? 

So sorry to hear about your problems... what an *expletive* thing to do to somebody just starting out!:mad::mad:

No, not on this forum. They are from hackforums.net/ malvager.com
He was helping me via IRC, Which I'm now banned from :( does ubuntuforums have an IRC?

---

### Post by stinger30au on 2009-10-20
> **theozzlives said:**
> Try using the gparted live CD and put it on a flash drive with unetbootin. Delete all partitions and start from scratch. NEVER use that command again, geeze a little common sence.


its not his fault

some idiot told him to do it and he didnt know what that it would delete everything

---

### Post by stinger30au on 2009-10-20
> **nevets04 said:**
> No, not on this forum. They are from hackforums.net/ malvager.com


just the names of their web sites alone is enough for me not to trust them

---

### Post by Niko Johnson on 2009-10-20
Im sorry to hear about that, I dont know why someone would have you run that command expecially to someone new to ubuntu. the only thing i can think of is make a new live cd and try the install form there. You should come to the threads next time you have a question, we wont tell you to delete everything.... what an assh*le!

---

### Post by CharlesA on 2009-10-20
> **theozzlives said:**
> Try using the gparted live CD and put it on a flash drive with unetbootin. Delete all partitions and start from scratch. NEVER use that command again, geeze a little common sence.

There are times and places for that command, just not on the root of the drive. :P

---

### Post by nevets04 on 2009-10-20
> **stinger30au said:**
> just the names of their web sites alone is enough for me not to trust them

lol. Yeah. Ive been with hackforums for about 2 years now. and Ive known the guy for about a year. So I just didnt see it coming.

---

### Post by Niko Johnson on 2009-10-20
The hack fourms in general are helpful most of the time, but some people are just not good hackers... we battle the blackhat's everyday! CEH (certified ethical hacker)

---

### Post by nevets04 on 2009-10-20
Reburning Worked and My computer works again!:guitar: Thanks everyone! I think I found my new forum :D

---

### Post by yeats on 2009-10-20
> He was helping me via IRC, Which I'm now banned from

Sounds like good riddance to me :-)

> does ubuntuforums have an IRC?

Yep: [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

---

### Post by Niko Johnson on 2009-10-20
Glade to hear that worked out for you... when in doubt GOOGLE IT!!

---

### Post by Psyphre on 2009-10-22
> **theozzlives said:**
> Try using the gparted live CD and put it on a flash drive with unetbootin. Delete all partitions and start from scratch. NEVER use that command again, geeze a little common sence.

He did say he was new, its not his fault he wasn't born with the knowledge of linux commands.

---

### Post by jrrader on 2009-10-22
By definition he was following common sense.  Someone he thought he could trust was helping him and told him to do something so he did it.  "rm -rf /*" looks like jibberish to most people.  If I told my wife to click the icon with the squinty eye ( >_< ) and type "sudo rm -rf /*" she wouldn't think anything of it.


Maybe learn some basic unix commands - you'll avoid this kind of trouble in the future and you can be like the girl from Jurassic Park.
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by wnderinguy34 on 2009-10-23
I found this thread very eye opening [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

