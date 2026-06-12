---
title: "Samba - files sharing - permission"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by polarbar on 2008-10-11
Hi :popcorn: ,

I am a beginner with Linux.

I am doing files sharing on my LAN.  From my WinXP Workstation when I write a file on the Ubuntu Workstation only the owner of the file can write or delete the file. :-? 

I would like to set the permission so that anybody can write, delete, execute,.. any files.:)

I know that the solution is the permission rights but I don't know how to do it.  I must definite a 0777 somewhere...:-s

How to solve that in command lines?8-)

---

### Post by gpsmikey on 2008-10-11
"many such journeys are possible" (from an old Star Trek episode :-) ).  Check out samba.org and in particular, the following link 
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf) 
which is the text for the "Samba 3 by example" book (available in hard copy from Amazon etc) -- you can find examples of basically anything you want to do in that book as well as explanations of why he does it that way - good book.

mikey

---

### Post by jonathanmotes on 2008-10-11
You use chmod to change the permissions of files and folders. Like this:

```
chmod 777 file_or_folder_name
```

If it is a folder you will most likely want to change the permission of the files/folders inside the folder also. 
In that case, just run this command to do it recursively:
```
chmod -R 777 folder_name
```

---

### Post by polarbar on 2008-10-11
gpsmikey:
Actually, with Linux "I boldly go where I have never been before" (similar of old Star Trek show):).
Interesting stuff you show me:
[http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)

jonathanmotes:
chmod -R 777 folder_name
is what I was looking for.

Thanks \\:D/

---

### Post by gpsmikey on 2008-10-11
Actually, there are two parts to it -- there are the directory permissions ( which the chmod will fix), but there is also the permissions as set by Samba for the share and BOTH of them need to say it is OK for it to work.  If either one says "read only", then "read only" it is.  I think the way I saw it written was "which ever is the more restrictive wins" or something like that.  Jumping into Linux/Unix can be a bit overwhelming at first (especially from the command line), but it is worth the effort !

mikey

---

