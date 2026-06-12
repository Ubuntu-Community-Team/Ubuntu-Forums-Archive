---
title: "Partitioning? For Dual Boot, Grub 18 Error"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by winjas on 2009-10-24
Hiya

So i have an old Toshiba laptop that i had XP on, and i been trying out Ubuntu with Live CD, i today went to fully install it and dual boot my laptop. Yup you guessed it, i ended up with the Grub error 18 and my laptop was little use again. 

Now doing much googling i can find solutions for partitioning when only installing Linux, such as create a small boot partition etc etc, but how do i setup and partition my drive (150gb) so i can dual boot ok? My bios seems to have no settings for hard drive either and it is the latest version of bios!

So i sat here right now freshly formatted laptop (had backups ofc) with a blank 150gb drive, a XP cd and a Ubuntu CD in my hands.. and want to dual boot it ok.

-Do i boot Live CD and use parition editor to build all partitions and if so can you recommend what to create for both OS?
-Do i install XP first? or Linux

I like to think i am a pretty good computer geek, but that said new to linux.. but disappointed ever guide i found to setup ubuntu neglects to mention old machines and the grub 18 error, so i now sat here stuck...

Thanks

---

### Post by Ravernomina on 2009-10-24
Do this (:


1. Boot up Partitioner
2. Make 3 new partitions. 1 for swap, 1 for Linux, 1 got XP
3 make the new partitions these sizes
      Swap - 1024 MB (1gb)
      Linux as much as you want (EXT4)
      Windows as much as you want (NTFS)
        _** REMEMBER THAT 1gb IS 1024mb!!**_
4. restart and install Windows XP
5. Install updates for windows XP
6. Install ubuntu.
7.update ubuntu DONE!

---

### Post by winjas on 2009-10-24
Thanks for fast response, but its the problem of HD size with my bios thats causing me headaches.
So with your suggestion, lets say i do these sizes and this order:

1-1gb swap
2-40gb EXT4
3-109gb NTFS

If i then install XP, i assume i tell it to use part 3 yes?
Then when i run ubuntu install which do i tell it  part 2 i assume?
And with that partition table will Grub work ok on my 150gb hard drive? As the current error is 18, which i believe means cylinder is past size my bios can see or aomthing?

Thanks again, just want to be sure before i sit through 2 installs all over again...

---

### Post by mapes12 on 2009-10-24
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by oleoleo2 on 2009-10-24
> **winjas said:**
> Thanks for fast response, but its the problem of HD size with my bios thats causing me headaches.
So with your suggestion, lets say i do these sizes and this order:

1-1gb swap
2-40gb EXT4
3-109gb NTFS

If i then install XP, i assume i tell it to use part 3 yes?
Then when i run ubuntu install which do i tell it  part 2 i assume?
And with that partition table will Grub work ok on my 150gb hard drive? As the current error is 18, which i believe means cylinder is past size my bios can see or aomthing?

Thanks again, just want to be sure before i sit through 2 installs all over again...

Hey did you get the problem fixed? (as I'm in the EXACT same situation with an old Toshiba and have fought with it in a couple of days)

---

### Post by SaRJe on 2009-10-27
This is my first post, and I suck at Grub 18.  I've read posts, and I'm at my wit's end.  Feels like I missed a Bingo by 1 number.

Before I begin, please advise if I should be adding to this thread, or if there's a way I can start my own thread.  I am totally green at asking for support.

Thanks

---

