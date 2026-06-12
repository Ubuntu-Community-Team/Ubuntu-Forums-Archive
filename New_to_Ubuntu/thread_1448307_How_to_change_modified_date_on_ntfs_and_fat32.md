---
title: "How to change modified date on ntfs and fat32 ?"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by ubfu on 2010-04-06
I had a folder of file transfer from a window xp to an external drive.The problem is those file transfer from window xp change its' modified date to current transfer date.
When I view those file using ubuntu all of it is today modified dates.It totally mess up those doc and folder date.

Is there anyone can write a script to change all the modified date file back to the current ?

Let say I output a .txt list file modified from window xp using cmd command 
dir /OGN /TC /A- > test1.txt ( cmd command [http://www.computerhope.com/dirhlp.htm](http://www.computerhope.com/dirhlp.htm) )

Then when it had transfer to the external hard disk.Using ubuntu with script or command , I wanted to change the modified timestamps according to the test1.txt output modified timestamps.Files and folder together.

Some files & folder are transfer to a NTFS and Fat32 partition.

Is it possible ? hope you can understand , though it might be hard.
Thanks for reading :)

---

### Post by ubfu on 2010-04-07
What about script to modified timestamps? in a batch ?

---

### Post by ubfu on 2010-04-09
How to change to modified date in ntfs will it work ?

---

### Post by ubfu on 2010-04-11
What about ls list change in batch using script ?

---

### Post by ubfu on 2010-04-13
will changing modified date crash with window xp viewing ?

---

### Post by ubfu on 2010-04-14
What about changing modified date one by one ? since it's so hard to change it in a batch

---

### Post by lisati on 2010-04-14
The "touch" command might be of some help. See **man touch** for more informaiton.

---

