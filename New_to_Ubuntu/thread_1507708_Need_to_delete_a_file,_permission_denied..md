---
title: "Need to delete a file, permission denied."
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Beta.v.2 on 2010-06-11
Okay, so I've been trying to get familiar w/ using bash a little better and I wanted to move a file from my Downloads folder to my Documents. I messed up and typed this...
```

mv filename /Documents

```Instead of doing what I was supposed to do...
```

mv filename ~/Documents/filename

```So now in my filesystem I have a file named "Documents" that's not supposed to be there and I need to delete it. However, because it's in filesystem every time I try to delete it I get this message.
> 
Error removing file: Permission denied


---

### Post by akelsall on 2010-06-11
I think your thinking about Windows here (re: Documents is a default folder in Windows).

If you are SURE you don't want the file, and it's giving you a permissions error, try placing the word "sudo" in front of it. You'll be prompted for 
your password. Enter your password and that should take care of it. For example:

sudo rm *filename*

Andy

---

### Post by pizza-is-good on 2010-06-11
go to the directory where the file is, and then 
```
sudo rm -f filename
```

if you are interested in learning bash, check [this book]("http://gd.tuwien.ac.at/linuxcommand.org/tlcl.php") out. (It's free)

~pizza

---

### Post by flick on 2010-06-11
Just preface the rm command with sudo, being very careful with typing this time. You don't want typos when using "sudo rm FILE I WANT TO DELETE".

---

### Post by kennedyvelez on 2010-06-11
> **akelsall said:**
> I think your thinking about Windows here (re: Documents is a default folder in Windows).

If you are SURE you don't want the file, and it's giving you a permissions error, try placing the word "sudo" in front of it. You'll be prompted for 
your password. Enter your password and that should take care of it. For example:

sudo rm *filename*

Andy



Also check file system and permissions. It might be a read-only file system...

---

### Post by Beta.v.2 on 2010-06-11
Thank you 'pizza-is-good', I had to cd to / then do the rm. Plus, I already know a lot of bash but I'm trying to use it more often.

---

