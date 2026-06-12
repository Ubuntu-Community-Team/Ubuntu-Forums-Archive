---
title: "partioning problem"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-02-13
I am trying to install windows and ubuntu side by side on my system. I am facing problem in partitioning. I want to install ubuntu with a separate home folder. So i have to make 3 primary partitions for - home folder, ubuntu and linux swap. Another primary partition would be for windows. Now I cannot make any other partition for D and E drive....
can anyone suggest how can make it possible!!

---

### Post by Linyx on 2011-02-13
> **amitpokhrel said:**
> I am trying to install windows and ubuntu side by side on my system. I am facing problem in partitioning. I want to install ubuntu with a separate home folder. So i have to make 3 primary partitions for - home folder, ubuntu and linux swap. Another primary partition would be for windows. Now I cannot make any other partition for D and E drive....
can anyone suggest how can make it possible!!

You can't make primary partitions more then 4, You have to make an extended Partition and make more partitions as a logic...it very easy to do with Gparted(Linux tools for Partitioning) , you can run in from live-cd (System>Administration>Gparted),

Follow the link to know how to do it > [http://www.dedoimedo.com/computers/gparted.html#mozTocId801746](http://www.dedoimedo.com/computers/gparted.html#mozTocId801746)

Edit:- Basically in Extended Partition you can make as many partitions as you want....that will depend on your Extended partition Space, 
It is Important to note that Extended-Partition is a kind of Primary partition, so if you want to make Extended Partition, then you will remaining Primary Partitions will be 3 (the 4th one will be **Extended**), and in Extended you can make more partitions.

Good Luck

---

### Post by amitpokhrel on 2011-02-13
can i install windows in extended partition??
and can I make one extended partition and within it make all three partition( home, ubuntu and linux swap)???

---

### Post by amitpokhrel on 2011-02-13
I am thinking of partitioning my system as:
1. primary partition- for windows(C)
2. primary partition for ubuntu (os)
3. Extended partition
    1. home folder for ubuntu
    2. linux swap
    3. D drive
    4. E drive
Would this work???

---

### Post by Quackers on 2011-02-13
Windows (or at least its boot files) must be installed to a primary partition.
Your last proposition could be changed slightly.
1. primary partition for Window (C: )
2. primary for D:
3. primary for E:
4. Extended partition using all remaining disc space
5. logical partition for Ubuntu root (/)
6. logical partition for Ubuntu /home
7. logical partition for swap space

D: and E: could possibly also be logical partitions within the extended partition (depending on what you would be using them for).
Linux systems do not need to be in a primary partition in order to boot (like Windows does).
As the extended partition is a type of primary partition, the above layout would leave you with 4 primary partitions. This must never be exceeded!

It is normally easier to install Windows first. After installation, make sure it boots ok, and also make sure Windows has only used one primary partition! Windows 7 may want to create 2 (one for boot files).

---

### Post by klytu on 2011-02-13
> **amitpokhrel said:**
> I am thinking of partitioning my system as:
1. primary partition- for windows(C)
2. primary partition for ubuntu (os)
3. Extended partition
    1. home folder for ubuntu
    2. linux swap
    3. D drive
    4. E drive
Would this work???

This should work, but I think a better plan would be to install Windows in a primary partition, and separate the rest of your hard drive into logical partitions within an extended partition. (Reason: Windows can only boot from a primary partition, but Linux can boot from a logical partition.) Something like this (assuming you don't plan to install other versions of Windows on the D and E drives ...):

1. primary partition for windows (C)
2. extended partition
   1. ubuntu /
   2. ubuntu /home
   3. linux swap
   4. D drive
   5. E drive

This way, if you decide to install other versions of Windows side-by-side with what you already have installed, you can still make three additional primary partitions later on. Just my opinion, but no big deal - your idea should be fine as well.

---

### Post by klytu on 2011-02-13
> **Quackers said:**
> Windows (or at least its boot files) must be installed to a primary partition.
Your last proposition could be changed slightly.
1. primary partition for Window (C: )
2. primary for D:
3. primary for E:
4. Extended partition using all remaining disc space
5. logical partition for Ubuntu root (/)
6. logical partition for Ubuntu /home
7. logical partition for swap space

D: and E: could possibly also be logical partitions within the extended partition (depending on what you would be using them for).
Linux systems do not need to be in a primary partition in order to boot (like Windows does).
As the extended partition is a type of primary partition, the above layout would leave you with 4 primary partitions. This must never be exceeded!

It is normally easier to install Windows first. After installation, make sure it boots ok, and also make sure Windows has only used one primary partition! Windows 7 may want to create 2 (one for boot files).

Sorry, I didn't see your post when I was typing mine. I duplicated some stuff you already mentioned.

---

### Post by Quackers on 2011-02-13
Lol, no problem! Two heads are usually better than one :-)  We seem to be suggesting the same things. No confusion there :-)

---

### Post by amitpokhrel on 2011-02-13
thank you both of you!!

---

### Post by Linyx on 2011-02-13
> **amitpokhrel said:**
> can i install windows in extended partition??
and can I make one extended partition and within it make all three partition( home, ubuntu and linux swap)???

I Hope your Problem is solved, but its a Good idea to install Windows in  primary so you won't have problem, because once i have tried that,and  after that i face many Problems and then i Recreate my Partition table,  so the Good Suggestion will be to install Windows in Primary and Ubuntu/Swap etc  in Logic Partitions,

See my own thread for Confirmation > [http://ubuntuforums.org/showthread.php?t=1669219](http://ubuntuforums.org/showthread.php?t=1669219)

Moreover it will be Good to mark **thread-as-Solved** in **thread tools** above once the Problem is Solved :P

---

