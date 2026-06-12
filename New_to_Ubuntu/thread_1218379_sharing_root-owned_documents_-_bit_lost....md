---
title: "sharing root-owned documents - bit lost..."
date: 2009-07-20
forum: New to Ubuntu
---

### Post by liquidus219 on 2009-07-20
I do seem to remember getting this to work previously :s.

Anyway, I have ubuntu 9.04 installed, but all my data on a separate HDD. I want to share a folder of data with another computer  on the network, but root is apparently the owner of the files. Is a quick fix for this?

---

### Post by Wickd on 2009-07-20
Well if I do recall the simplest way to do this is to change the owner of the file to yourself and then do a simple share

chown *username* -R *Directory path*

Will change the ownership of the folder and then you can just use nautilus to set share permissions on the directory (Similar to Windows)

Dont know if this helps

Cheers

---

### Post by liquidus219 on 2009-07-20
I tried, didn't work though :(.

---

### Post by niteshifter on 2009-07-20
Hi,

Try the below instead:
```
sudo chown -R <user_name>:<group_name> </path/to/mounted/drive>
```
Change <user_name> to your login name. Unless you've an odd setup that will be what you need to replace <group_name> with. Replace </path/to ...> with the path to the drive. Example: User login name of 'joe', path is /media/disk:
```
sudo chown -R joe:joe /media/disk
```

---

