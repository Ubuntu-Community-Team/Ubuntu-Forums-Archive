---
title: "Questions about moving Wubi to a partition..."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by 11010110 on 2009-03-19
Hi everyone, 

I have been running Ubuntu 8.10 on Wubi for a few months and I love it! I am considering moving it to a partition of its own as to increase the amount of storage i will have (im down to a few hundred megs left!)

I just have a few questions first...

1. Right now i have to ability to communicate with my windows files and filesystem (thats where all of my music and movies etc are). If i do switch to a true dual boot will there be any way possible for me to continue that? It would be a pain and very inefficient to copy it all...

2. How much of a risk would i run by splitting the windows partition in half to make room for my second partition which would house Ubuntu? And is there any way that is safest compared to other options?

3. Will i notice any changes in operation? Such as will i have to startup differently or run any new commands?

4. Will anything change with my Ubuntu when i move it?

5. And finally, there are few if any problems with hardware incompatibilities when I run it through Wubi, will any of this run the risk of changing when I switch over? 


Sorry for the lengthy post I just like to know exactly what i am getting myself into before I jump for it. 

Thanks a lot in advance everyone!

---

### Post by Paqman on 2009-03-19
> **11010110 said:**
> 
1. Right now i have to ability to communicate with my windows files and filesystem (thats where all of my music and movies etc are). If i do switch to a true dual boot will there be any way possible for me to continue that? It would be a pain and very inefficient to copy it all...


A Wubi install and a traditional install are almost indistinguishable on the desktop. They certainly both do the same things.

Your Windows drive will be mounted at a slightly different location though. You might need to update the path to the files in your applications.

> 
2. How much of a risk would i fun by splitting the windows partition in half to make room for my second partition which would house Ubuntu? And is there any way that is safest compared to other options?


Disk partitioning always carries a small risk. It's always a good idea to do a backup before starting. That being said, i'm sure you'd be fine. Just remember to make sure Windows still has at least about 20% free space on it's partition, or it'll get horribly fragmented.

> 
3. Will i notice any changes in operation? Such as will i have to startup differently or run any new commands?

4. Will anything change with my Ubuntu when i move it?

5. And finally, there are few if any problems with hardware incompatibilities when I run it through Wubi, will any of this run the risk of changing when I switch over? 


Nope, you should notice any difference at all, except the above mentioned different path to the NTFS partition.

Glad you're enjoying Ubuntu!

---

### Post by 11010110 on 2009-03-19
Thank you very much for all of the information and the quick reply! I am glad that I will still be able to mount my windows partition. That was the greatest of my worries.

---

### Post by Paqman on 2009-03-19
No problem.

At the moment your NTFS partition is mounted at /host. Once you transfer over to a dedicated partition install the package ntfs-config. That'll give you an easy way to set your NTFS partition into a new mount point so that it'll be mounted automatically when you boot. I'm not sure exactly what mount point it'll choose of the top of my head, most likely /media though.

---

### Post by 11010110 on 2009-03-19
very cool thanks for letting me know about ntfs-config. do I just run it and chose to mount what I want or would it jsut take care of it for me?

Thanks again!

---

### Post by Paqman on 2009-03-19
It can do either. It'll find all your NTFS partitions (there would normally only be one) and you can tell it to sort them out automatically, or you can fiddle with the options. It's pretty straightforward though.

It basically just means you don't have to create the mount point and then edit /etc/fstab manually.

---

### Post by 11010110 on 2009-03-19
Very good!

I see youre testing Jaunty. Hows it looking thusfar?

---

### Post by Paqman on 2009-03-19
> **11010110 said:**
> Very good!

I see youre testing Jaunty. Hows it looking thusfar?

Lot's of little bugs still, but overall it rocks. Hard.

To get the full benefit you're going to want to switch to the new EXT4 filesystem. That means backing your stuff up, burning a CD, and doing some manual partitioning. Best way to get the LiveCD after it's released is through torrents, btw. The servers get pretty swamped around release time so downloading direct from Ubuntu will be sllloooooowwwwww, while the torrents are stupidly fast. I've had 1000Kb/sec off Ubuntu LiveCD torrents on release day before.

---

### Post by 11010110 on 2009-03-19
a new filesystem eh? I wonder why. So youd suggest doing a fresh install for it? Should i just wait on moving to a partition and instead wait for jaunty?

---

### Post by Paqman on 2009-03-19
EXT4 has been in the piepline for a while. Eventually it'll replace EXT3 (just like EXT3 replaced EXT2). The main advantage for desktop users is that it's quicker.

It might be worth waiting for Jaunty, yes. Release date is 23rd April.

---

### Post by 11010110 on 2009-03-20
So I take it that if you were to upgrate instead of do a fresh install you wouldnt get the new filesystem? Will the EXT4 still be able to use and run all of my old programs and such? Any compatability issues?

---

### Post by Paqman on 2009-03-20
Yeah, you have to reformat your partitions with the new filesystem, so an upgrade won't cut it. Even if you do automatic partitioning on a fresh install it still defaults to EXT3. They're just being conservative about how they roll out EXT4, which is sensible.

Compatibility-wise, the only problem you'll strike is that older versions of Linux won't be able to mount any new EXT4 partitions they find.

---

### Post by 11010110 on 2009-03-20
so if i made a live CD and installed it it would use EXT3 automatically? how would i chose EXT4? And if older versions of linux wouldnt recognise it would that be the same with older programs like compiz fusion etc? Or would they all still work with it?

---

### Post by Paqman on 2009-03-20
You'd have to choose "manual partitioning" during installation, then pick EXT4 from the list of options for the partition format. That's the same as any other non-default filesystem like Reiser or JFS.

Your apps will work just the same. Although possibly a bit faster!

---

### Post by 11010110 on 2009-03-20
I cant imagine Ubuntu being any faster than it already is lol. As a recovering Windowsoholic im already blown away lol. Ill probably wait a little whlie to be sure its bug free (for the most part) and completely stable before I make the switch.

Thanks a lot for helping me with everything! Even the off topic things lol.

Also, as fast as EXT4 is supposed to be there could be severe data loss due to the way it delays the writing of files. so I dont know what im going to do yet lol

---

