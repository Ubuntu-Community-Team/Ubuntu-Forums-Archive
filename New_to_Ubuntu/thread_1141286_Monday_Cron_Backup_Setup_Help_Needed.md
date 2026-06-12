---
title: "Monday Cron Backup Setup Help Needed"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by jedimonkey on 2009-04-28
Im new to Ubuntu. Ive been snooping around these forums and found most of the answers Ive needed over the past few weeks..... This is my first post. 

Ive been struggling to get my head round cron jobs.
I want to have a compressed copy of the /home/user1/ directory made every monday at 7.30pm. I would also like a copy of the compressed file from 'user1backup' to be forwarded to another folder.....

here was my half hearted attempt
30 19 * * 1 cd /home/user1/;tar -cvf - * | tar -C /home/user1backup/ -xv

If anyone can help..... it would be appreciated. Ive been learning so much about Ubuntu lately... Im almost Ubunted-all-out !!!!  
thanks
jm

---

### Post by unutbu on 2009-04-28
This crontab entry should backup /home/user1 to /home/user1backup.

```
30 19 * * 1 rsync -a --delete --exclude=.gvfs /home/user1/ /home/user1backup/ 
```

It does not compress /home/user1. Are you sure that is what you want? Although compression saves space, it has two disadvantages: If you want to restore a single file, you have to extract that file from a potentially huge tar.gz file. This requires uncompressing the tar file, then extracting the file. It's a rather slow process.

The other disadvantage is that if for some reason there is an error which corrupts the tar.bz2 file, then you lose everything. In contrast, if you use rsync to mirror your directory, a single error will cause you to lose a single file, not your entire backup.

Nevertheless, if a tar.bz2 backup is what you want, then try 
```
30 19 * * 1 tar cjf /home/user1backup/backup.tar.bz2 --exclude /home/user1/.gvfs /home/user1/ 
```

---

### Post by jedimonkey on 2009-04-29
Thanks you for your help - disadvantages taken on board - cant get is to work yet.... will have a bash at it today, should be ok!!!!!
made my day :)

---

