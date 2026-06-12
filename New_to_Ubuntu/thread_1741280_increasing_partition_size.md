---
title: "increasing partition size"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-04-27
My ubuntu partition is only 10 GB. I need more space. I have 7 sda's ie sda1, sda2 and so on. ubuntu is in sda 7. can i add hard disk space?

---

### Post by garvinrick4 on 2011-04-27
> **RobikShrestha said:**
> My ubuntu partition is only 10 GB. I need more space. I have 7 sda's ie sda1, sda2 and so on. ubuntu is in sda 7. can i add hard disk space?
 Take a screen shot of gparted and post here. Add the screenshot with attachments (the paper clip).
If do not have gparted in System/Admin add:
```
sudo apt-get install gparted
```

---

### Post by RobikShrestha on 2011-04-28
Here is the screenshot. If there is a solution please explain it too I am really eager to learn about these stuffs.

---

### Post by garvinrick4 on 2011-04-28
Well you are out of space is the bad news:
Good news is if you want to you can shrink sda6 if you want about 8 gig or so then move
sda7 over to fill that space.
You got 25 gig or so in sda5 that you can move sda6 over if you want to get more room
in sda6 which means you can get more room in sda6 to give to sda7.
Takes a little time since you are moving data over.
Have to use Live Cd and gparted to do it. Cannot play with a mounted partition and when you
use a live cd (install CD using Try Ubuntu) nothing is mounted. See keys on your screenshot that means that partition is mounted. This link has a bit of a tutorial on gparted to shrink partitions. 
##Make sure you have backups because you are messing with your drive. It works I have done it many times and used the World over but always nice to have backups in case you 
lose focus or something go's awry.

[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

---

### Post by RobikShrestha on 2011-04-28
Thank you, but I do not have a live cd. May be i will create one with iso file then try it. Thanks a lot.

---

### Post by RobikShrestha on 2011-04-28
Even if i have a live cd how would i run gparted?? Can't i add to linux partition from windows?? The website seems to be about fresh installation of ubuntu. How do I just shrink one drive and add that part to another?

---

### Post by An Sanct on 2011-04-28
If you have a spare 1gb (or more) USB flash drive, you can create a Live USB. It is faster, needs no has no spin-up time and is reusable.

---

### Post by An Sanct on 2011-04-28
> **RobikShrestha said:**
> Even if i have a live cd how would i run gparted?? Can't i add to linux partition from windows??

Windows does not recognize linux partitions, so you cannot do that under windows (unless you have an advanced partitioning tool)

---

### Post by RobikShrestha on 2011-04-28
If I want to create iso of ubuntu on another parition, what should I do? I mean I do not have an empty CD/DVD and want an iso file.

---

### Post by RobikShrestha on 2011-04-28
I created an iso file using remastersys. Then live usb with system>administrator>live usb disk creator. When I try to boot from pen drive, it says, 
"could not find ram disk image /casper/initrd.gz"
What do I do now?

---

### Post by An Sanct on 2011-04-28
For Live USB creation, you should use official ISOs, downloaded from canonical ([www.ubuntu.com](www.ubuntu.com)) or a real installation CD.

---

### Post by RobikShrestha on 2011-04-28
Isn't there a way to create live USB with iso files created from remastersys or aptonCD or something. My bandwidth is limited downloading would take long. If I had to download I would download ubuntu 11 but can I upgrade my ubuntu 10.04 to ubuntu 11.04 (after doing disk partition with live USB of ubuntu 11.04)??

---

### Post by An Sanct on 2011-04-29
Upgrades between non Long Term Support versions are sequential
(9.04 -> 9.10 -> 10.4 -> 10.10 -> 11.04)

And are sequential between LTS versions, 10.04 is LTS and you will be able to upgrade it directly to the next LTS version.

I looked up remastersys and it seems to be the right tool, to make a Live ISO of Ubuntu (any Debian distribution) Maybe you can tell us what went wrong with the remastersys option? (I will take a look at your previous posts, maybe you already did and I missed it...)

PS. Before downloading 11.04 or upgrading to it, take a look at the forums "general help" and "absolute beginner" talk, to see what problems people have with this version (released about 20 hours ago, when I am writing this)

PS2. To my knowledge creation of a Live CD/USB with 11.04 has some major problems, this might be due to the fact, that the desktop and netbook versions have been merged ... just a guess ...

edit: found the problem with initrd.**gz** you mentioned in post #10 ... take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1525367") in short, initrd.**lz** is the default naming for the file, so take a look at that usb key, open /casper/ and if you find initrd.(lz/gz), make a copy of that file to the same location and rename it so, that you will have both "initrd.**gz**" and "initrd.**lz**". The file is only 11Mb big, so size should be no concern...

after doing that, try to start the Live USB again

---

