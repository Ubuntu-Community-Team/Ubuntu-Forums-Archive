---
title: "Padlock on Mp3/Data Files"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by SILLAT on 2009-02-24
Hi y'all 
I Got a Mp3 Cd from a friend and wanted to copy the music off the Cd and store it on my hard drive in my music folder. 
After i copy the songs from the Cd to my hard drive i notice all the Mp3 files have a Padlock on them ! if i right click on them an go to permissions i notice they are read only but i also notice that i can change it to read and write I'm able to play them and the padlock is gone.
How can i get my Mp3 or data files copied from a Cd normal and not having to change permissions on each single file ?? i hate coping files off Cd and see Padlock on them afterwards :mad: ! !

---

### Post by llamabr on 2009-02-24
When you copy them they'll be whatever permission they are.  If you don't want them to be that permissions, you can change it.

Move to the directory where you store them, in terminal, and issue:

chmod 755 *mp3

---

### Post by llamabr on 2009-02-24
I don't quite know what you mean by 'protect'.  What do you want to protect them from?

And I don't quite know what you mean by 'stream not copied'.

But yes, there is a solution.

---

### Post by SILLAT on 2009-02-25
> **llamabr said:**
> When you copy them they'll be whatever permission they are.  If you don't want them to be that permissions, you can change it.

Move to the directory where you store them, in terminal, and issue:

chmod 755 *mp3 Thanks llamabr worked like a charm ):P

---

### Post by Dougie187 on 2009-02-25
> **u.lover said:**
> how can I protect mp3's in ubuntu? I want to secure my mp3's so, that these files only stream not copied. Is there any solution?

You should probably start your own thread to get some help with your issue. Also you should work on explaining your issue more clearly as this is not very easy to understand.

---

### Post by llamabr on 2009-02-25
Yes, instead of changing the thread and adding new details at the bottom, you might want to start a new thread.

This one has changed so many times in the last 2 days I have trouble following the question.

---

