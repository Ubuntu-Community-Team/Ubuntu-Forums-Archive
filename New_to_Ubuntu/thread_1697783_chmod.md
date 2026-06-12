---
title: "chmod"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by expatCM on 2011-03-01
I have a data drive.  It holds a lot of directories and under those directories there are sub-directories and files. Some of the directories and files have 0700 permissions and others have 0755.

I would like to run a command to change all directories and files to have 0755 permissions.

Would "chmod -R 755" be the correct approach to this?

---

### Post by TeoBigusGeekus on 2011-03-01
> **expatCM said:**
> Would "chmod -R 755" be the correct approach to this?

I believe so, yes.

---

### Post by Tabu.it on 2011-03-01
> **expatCM said:**
> I have a data drive.  It holds a lot of directories and under those directories there are sub-directories and files. Some of the directories and files have 0700 permissions and others have 0755.

I would like to run a command to change all directories and files to have 0755 permissions.

Would "chmod -R 755" be the correct approach to this?

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

sudo chmod -R 755 folder

---

### Post by TeoBigusGeekus on 2011-03-01
> **Tabu.it said:**
> [http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

sudo chmod -R 755 folder
If he uses sudo, won't it change the ownership of the drive?

---

### Post by expatCM on 2011-03-01
but also the command "sudo chmod -R 755 folder" says folder at the end.  This would be impossible since there are hundreds of folders.  If folder is required would it not be better to add * as a wild card?

The owner / group is root / root without exception so as long as I execute a command at the root terminal I can do away with sudo.

---

### Post by Tabu.it on 2011-03-01
> **TeoBigusGeekus said:**
> If he uses sudo, won't it change the ownership of the drive?

Tested:

drwxrwx--- 2 ale  sharing  4096 2011-02-28 18:42 Films
tech@Ubuntu:/media$ sudo chmod 775 Films
tech@Ubuntu:/media$ ls -l
drwxrwxr-x 2 ale  sharing  4096 2011-02-28 18:42 Films

owner is still ale, or i made a mistake?

> 
If folder is required would it not be better to add * as a wild card?


yes

---

### Post by mcduck on 2011-03-01
> **TeoBigusGeekus said:**
> If he uses sudo, won't it change the ownership of the drive?

No, chmod doesn't change ownership. On the other hand, if you are already the owner then *there's absolutely no need to use sudo with chmod*, you already have permission over your own files... ;)

---

### Post by TeoBigusGeekus on 2011-03-01
> **mcduck said:**
> No, chmod doesn't change ownership. On the other hand, if you are already the owner then *there's absolutely no need to use sudo with chmod*, you already have permission over your own files... ;)

Thanks.

---

### Post by Morbius1 on 2011-03-01
Instead of:
```
 sudo chmod -R 755 folder     
```You might consider:
```
sudo chmod -R a+rwX,go-w folder
```The first one will make every folder and file have permissions of 755. That's good for directories but it just made all your files executable.

The second way will make directories and all those files that are already marked as executable - executable ( that's what the big "X" does ). All other files will not be marked as executable.

Just a thought.

---

### Post by expatCM on 2011-03-02
Gosh.  So pleased I asked.

So it looks like being 

```
sudo chmod -R a+rwX,go-w *
```

Thank you everyone for your contributions on this thread.

---

### Post by expatCM on 2011-03-02
the curious thing  is that attempting  to run the command generates the following...

chmod: invalid mode: 'a+rwX,'

---

### Post by Morbius1 on 2011-03-02
> **expatCM said:**
> the curious thing  is that attempting  to run the command generates the following...

chmod: invalid mode: 'a+rwX,'
One of the most irritating responses to posts like the one above is: " Well, it works for me".

I just did this on one of my own directories and did not receive that error. I hate to contribute to the great volume of bad information on the Web concerning Linux so I will try to reproduce your error.

---

