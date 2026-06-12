---
title: "[sudo nautilus] error message"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-15
wheni try to go ```
 sudo nautilus OR gksudo nautilus i get the following 
message:
nigel@nigel-laptop:~$ sudo nautilus
[sudo] password for nigel: 
Initializing nautilus-share extension
seahorse nautilus module initialized
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6599): WARNING **: Unable to add monitor: Operation not supported

```
but nautilus stil opens and allows me to perform actions not permitted in normal file manager etc.   then when i close the nautilus window the error continues with some extra word - as follows
```
--- Hash table keys for warning below:
--> file:///root

(nautilus:6599): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6599): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-share extension
nigel@nigel-laptop:~$ 

```
is this right?  have i set something up wrong?
to continue, i recently had to reinstall the whole ubuntu set up because i broke it and i couldn't get the backup to work for me.  
i was also wondering if these nautilus 'issues' are related to the way i have my partitions set up.  please ask if you need any information about this and i will post it.  i thought i would eliminate the question of nautilus first before moving on to the partition/directories point.
thanks for any help
cheers
nigel

---

### Post by Elfy on 2009-01-15
No I think that it's still a bug - I don't look for it anymore.

I've had it since I started using ubuntu.

Edit I came back :) - I see you say sudo nautilus OR gksudo nautilus, best not to use sudo anyway :)

---

### Post by theozzlives on 2009-01-15
try hitting ALT+F2 and type the command

---

### Post by capnthommo on 2009-01-15
hi there.  thanks for the replies, i shall ignore this one then and look further for the thought s i have about my directory structure.  thanks particularly for the Alt F2 suggestion, it certainly reduces desktop clutter when opening apps doesn't it?  and i shall take note of the gk advice, i am so clumsy i need all the safeguards i can get to stop me wrecking the system - and even then i manage it.  ho hum, 3 steps forward 2 steps back - atleast the end result is 1 step in the right direction.  and we can consider this particular one solved as well, i shall open a new thread to look at my dir/partition structure.
thanks again, v much
nigel
):P

---

