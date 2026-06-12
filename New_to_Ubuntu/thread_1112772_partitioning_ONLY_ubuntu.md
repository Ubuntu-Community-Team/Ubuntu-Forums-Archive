---
title: "partitioning ONLY ubuntu"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by D1ZZ4ZZT3R on 2009-04-01
ok, i've searched and searched. i've found tutorials, i've checked in beginning ubuntu linux 3rd edition; everything talks about partitioning WITH windows and only serves to complicate the matter for me.

i'm installing ubuntu on my new laptop, i'm at the part where i can partition the drive. i think i need main, swap, and root partitions. i don't know which to do first, how much space to give each or, what order to do them in.

i've got a 60 gig drive, around 750 megs of ram. will somebody please tell me what and how i should do this? i'd really like to finish this and go to bed. i want a seperate partition so if i mess something up while still learning linux, i can re-install and not lose files. NOTE: i currently have no files so, i don't have any to back up. i just want to partition it correctly.

thank you.

---

### Post by Moop on 2009-04-01
I'd suggest a 10gb root, a 1.5gb swap and the rest for home. You can make them in that order.

---

### Post by D1ZZ4ZZT3R on 2009-04-01
i'll get right on it. thanks. i'll report back.

---

### Post by anitha-h on 2009-04-01
for ubuntu two important partiotions to be done are 
root and swap
where swap can be double the size of ram
root(/) can be 10 to 20 gb
and the rest can be /home

---

### Post by D1ZZ4ZZT3R on 2009-04-01
oh no, i don't have / (root) option. would i use ext3 journaling file system?

---

### Post by Moop on 2009-04-01
Yes use ext3 for the file system. You have the / option. I think you need to click on edit partition to assign the / and home to the partitions.

---

### Post by D1ZZ4ZZT3R on 2009-04-01
shameless bump. don't know if that works here but I-HAVE-TO-TRY-SOMETHING

---

### Post by anitha-h on 2009-04-01
click new partioion and select the type as ext3 and mount point as /

---

### Post by D1ZZ4ZZT3R on 2009-04-01
ok, i think i almost have it. are all three partitions primary or logical? which is which?

---

### Post by D1ZZ4ZZT3R on 2009-04-01
another shameless bump before wild abandonment.

---

### Post by meierfra. on 2009-04-01
Look at [NOPARSE] "DON'T  8)" [/NOPARSE] in 

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by D1ZZ4ZZT3R on 2009-04-01
well, i guess i'll call this case solved and, closed. i'll see what happens. thanks, you two!

---

### Post by D1ZZ4ZZT3R on 2009-04-01
> **meierfra. said:**
> Look at [noparse] "DON'T  8)" [/noparse] in 

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)


thanks! : O

---

