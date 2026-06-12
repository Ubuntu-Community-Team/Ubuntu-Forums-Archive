---
title: "How can i make ubuntu &quot;use&quot; delete button as always send to trash"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Dr.Fritz on 2009-01-07
[SIZE="2"]Actually the tilte pretty much says it all.
I think that delete button works in a kinda "frustrating" by : sometimes sending the file to trash,some others completely deleting it.

I like having a trash and using it, it seems :)[/SIZE]

[SIZE="3"]P.s.[/SIZE]
[SIZE="1"]If it has already been answered excuse my double post as i did some research but i havent actually scanned the net for some hours, anyways just point me to the thread answered, i wouldnt like wasting anyones time in already answered questions at least :P[/SIZE]

---

### Post by Malalo on 2009-01-07
Open a File Browser, then Edit -> Preferences

Behaviour tab, look at the last 2 options... this is the best I could find that come close to what you're looking for...

---

### Post by Tony Flury on 2009-01-07
can you check on what occassions the delete button does not send to trash ?

the only time i have seen that is when i am browsing and deleting files from non-ext type file systems.

---

### Post by Captain_tux on 2009-01-07
Pressing **Shift** & **Delete** simultaneously permanently deletes whatever you're deleting (meaning it does not pass go, does not collect $200, does not go to the trash bin)...

---

### Post by JohnLM_the_Ghost on 2009-01-07
I always do shift+delete, so I worry not.
Except when I delete something needed, but that happens extremely rarely.

As for topic... I don't think it is actually possible... at least not in painless way!
Deleting (to trash) usually moves file in the **same** partitions trash folder.
There is no such folders in non-linux partitions. (ie. FAT and NTFS)
And it completely would defeat deleting (to trash) files on removable media, cause it won't free space.

---

### Post by Dr.Fritz on 2009-01-07
guys thanks for your replies, 
I have the first option checked as the 2nd one is useless for me as captain tux says i can use shift and delete to completely delete a file all i want is when i press delete to have the files sent to trash.

Oh and by the way tony i think you are right it does delete whatever is in a non ext2 drive the file i lost actually was in a NTFS drive as i share it with my windows(i need em for some programs) but i dont know if thats the only time it happens , i think it pretty much does it some other times too.. maybe for some certain kind of files..

---

### Post by Dr.Fritz on 2009-01-07
john LM i didnt see your post till i already post mine but are u sure it is impossible to somehow create .Trash folder in NTFS ?
oh and what u said for removable media isnt true in my experience , when i connect my cellphone there is a .Trash file in my memory cards storage same for usb sticks(FAT ones)

---

### Post by Dr.Fritz on 2009-01-07
i am pretty sure that there is a simple way to write a script that will be executed whenever i press delete button so that it moves to trash even if it is in a NTFS volume.. i dont know anything about programming but i guess someone from all of you Linux gurus can help me :p

anyways
thanks in advance for your replies

---

### Post by JohnLM_the_Ghost on 2009-01-07
> **Dr.Fritz said:**
> oh and what u said for removable media isnt true in my experience , when i connect my cellphone there is a .Trash file in my memory cards storage same for usb sticks(FAT ones)

Well technically, NTFS has slightly different inode and journal system, but now as you say it it seems pretty possible to create Trash... I'm note exactly sure how Trash works or what metadata it saves.
As for removable media... I dunno... it is possible, but moving to trash doesn't free space. So not very useful on removable media.

> **Dr.Fritz said:**
> i am pretty sure that there is a simple way to write a script that will be executed whenever i press delete button so that it moves to trash even if it is in a NTFS volume.. i dont know anything about programming but i guess someone from all of you Linux gurus can help me :p

anyways
thanks in advance for your replies

That wouldn't really classify as painless, but yeah that's also what I thought.
But I'm not exactly material to make such script. (Partly cause it won't be any use for me) :D

---

### Post by -kg- on 2009-01-07
Maybe a *slight* PITA, but I can think of a workaround. Create a special "Trash" folder (and call it what you want) then when you try to delete something and it won't send it to the regular trash (as on an NTFS or whatever drive, or for whatever reason), instead of deleting it just move it to the special folder you created.

That will save it and, if necessary, you can transfer it back if you find you actually needed it.  Of course, once in a while you will need to "empty" your special trash folder, either into the regular trash or permanently delete it, as you wish.

---

### Post by Dr.Fritz on 2009-01-08
> Create a special "Trash" folder (and call it what you want) then when you try to delete something and it won't send it to the regular trash (as on an NTFS or whatever drive, or for whatever reason), instead of deleting it just move it to the special folder you created.

yea but if i accidentaly press delete... then i'll lose my files :(
or is there any way i can "link" delete to send to "trash" folder i have created if i am browsing an ntfs drive?

all this started cause i moved some files to my NTFS shared drive as i was going to format my ubuntu partition and do a clean install, i accidentally pressed delete and then without any confirmation i lost all the files i moved there (including several projects for my university)

---

### Post by JohnLM_the_Ghost on 2009-01-08
Hmm...
Most simplest script would be this line!
```
mv -t /your/new/trash $1
```

if you were also to save some metadata in file... would go something as
```
echo $PWD > .meta_file_something
```
what would be useful if you'd make restore script as well...

something like
```
mv -t `cat .meta_file` $1
```
($1 in both examples is command line arg. for your deletable/restorable file)


Well these are quite lame commands, but it might show a quick idea of what to do. I don't have any idea how to assign scripts to nautilus commands or *Del* button for that matter.

---

