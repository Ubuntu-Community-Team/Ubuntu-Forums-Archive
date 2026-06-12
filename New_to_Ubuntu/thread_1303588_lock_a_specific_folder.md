---
title: "lock a specific folder"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by jndlsnl on 2009-10-28
hi, i m using ubuntu 9.04. can i lock a particular folder...

if yes then can anyone tell me..how is it possible...

is there any software or package which makes it possible...

thnx

---

### Post by ukripper on 2009-10-28
This may help - [http://aarklonlinuxinfo.blogspot.com/2009/10/encrypted-folder-cryptkeeper-ubuntu-904.html](http://aarklonlinuxinfo.blogspot.com/2009/10/encrypted-folder-cryptkeeper-ubuntu-904.html)

---

### Post by Paresh on 2009-10-28
if by locking, you mean encrypt the folder so that only someone with the password can access it, try [this thread]("http://ubuntuforums.org/showthread.php?t=1226044&highlight=ecryptfs")

---

### Post by grizato on 2009-10-28
When you encrypt files like that, can you tranfer em?:)

---

### Post by Paresh on 2009-10-30
It's the file system that's encrypted, and the files are decrypted as they're accessed.  This is done under the hood, so you would not be aware of it.

If you transfer them to another place, the files will be decrypted as they are copied and will be visible to all.

---

