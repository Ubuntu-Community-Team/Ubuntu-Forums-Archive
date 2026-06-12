---
title: "Undelete - Removed file using 'rm'"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by mr_luksom on 2010-09-23
Hey,

I've deleted a file using rm in bash, is there a way to 'undelete' it (like the DOS command of old)?

Not a massive deal if I can't, but I think it would still be handy to know.

---

### Post by da burger on 2010-09-23
rm deletes a file completely. It doesn't move it to a trash folder or anything like that. The only way to recover it would be to use a file recovery program like photorec. That's quite a lot of effort though if the file isn't that important. If you want to do this and need help post back here so we can give you a hand.
Angus

---

### Post by mr_luksom on 2010-09-23
I think I'll pass on that - I've had to use photorec previously when I accidentally repartitioned the wrong drive; it is certainly not worth that effort.

---

### Post by Rubi1200 on 2010-09-23
You might want to consider using the ```
mv
``` command next time; that way if you mess things up you can always restore the file.

See```
 man mv
``` for details.

---

### Post by PriceChild on 2010-09-23
I've used tools like photorec in the past to recover data and yes it can be a hassle but it got me everything back.

There are other *easier* ways though depending on what filesystem you are using? Did you immediately shut down or are you using the machine/disk still? If so, the data might (probably has been) overwritten.

---

### Post by Mark Phelps on 2010-09-23
> **da burger said:**
> rm deletes a file completely. 
Technically, it does not delete a file "completely". If it did, tools like photorec could not recover the file.

> It doesn't move it to a trash folder or anything like that. Now, this is true.

If you want to delete a file "completely", meaning, so that it can not be recovered, then use "shred".

Yeah, I'm nitpicking ... but folks need to be made aware that to completely remove files and their contents, they need to use something other than "rm".

---

### Post by da burger on 2010-09-23
> **Mark Phelps said:**
> Technically, it does not delete a file "completely". If it did, tools like photorec could not recover the file.

 Now, this is true.

If you want to delete a file "completely", meaning, so that it can not be recovered, then use "shred".

Yeah, I'm nitpicking ... but folks need to be made aware that to completely remove files and their contents, they need to use something other than "rm".

What I meant by that, and what I think can be reasonably inferred from what I said, was that it is totally removed from the file system. The only way to get it back is to have a program inspect the blocks that are not in use by the file system (like photorec). Depending on your definition of delete, what I said was perfectly accurate.

---

### Post by Diametric on 2010-09-23
> **Rubi1200 said:**
> You might want to consider using the ```
mv
``` command next time; that way if you mess things up you can always restore the file.
 
See```
 man mv
``` for details.
 
+1 here - Especially if you're not used to working within a command prompt.  YOu can create a directory and move files there that you want to delete (it would work like a trash bin) then come back at the end of your session and make sure you want to run the rm command.

---

### Post by mr_luksom on 2010-09-24
Using mv as in moving it to another directory? That would require a designated 'trash' directory, and a conscious effort to keep it clean. 

In the event that I'm not sure I should be deleting the file, I usually use mv to rename the file to .backup, test what I need to test and then delete that.

---

### Post by mastablasta on 2010-09-24
> **Mark Phelps said:**
>  
Yeah, I'm nitpicking ... but folks need to be made aware that to completely remove files and their contents, they need to use something other than "rm".
 
 
makes sense, but why there is no command to undue the deleting? surely it should be easier in Linux since there is less disk fragmentation, yet we all know that DOS undelete can do it. as could unformat (or similar) back in the days return data from formated drive.

---

### Post by Rubi1200 on 2010-09-24
> **mr_luksom said:**
> Using mv as in moving it to another directory? That would require a designated 'trash' directory, and a conscious effort to keep it clean. 

In the event that I'm not sure I should be deleting the file, I usually use mv to rename the file to .backup, test what I need to test and then delete that.
That is also a sensible option in my opinion.

---

