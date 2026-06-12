---
title: "window server 2003"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by keats4 on 2010-11-01
Yes I really am an absolute beginner  . . .  I have my first Ubuntu system installed on my office network. Is it possible to attach to my windows 2003 server? On a windows system I would MAP and network drive to the directory on the server after I've logged in. 

Is it possible to attach?
How would I attach to the server?
Then map a drive ! ?! ?


Thank in advance
Keats4

---

### Post by luvshines on 2010-11-01
You mean, you want to transfer files across both of them, right ??

Is it just one way or both ways, Ubuntu ---> Win2003 and vice versa ?

---

### Post by Hippytaff on 2010-11-01
You might want to look into Samba, [http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29) SMBCLIENT etc. Not positive it is the 'right tool for the job' though

---

### Post by Zzl1xndd on 2010-11-01
There are tools for connecting Linux/Ubuntu to AD. The one I used in the past was Likewise Open. Its free and makes the process rather easy. I believe there is another option in the software centres partners section that will also do the job.

I seem to remember being able to access mapped drives. Although I don't remember how its been a few years and it was a school project.

---

### Post by keats4 on 2010-11-02
Yes I would like to move files from one to the other and vice versa. I don't even know if ubuntu has "drive letters" like windows does . . . there might be something built into ubuntu I really am that new to this

---

### Post by HermanAB on 2010-11-02
Connecting to a Windows server is usually quite trivial:
Nautilus (the file browser on your desktop), File menu, Connect to Server, SMB protocol...

---

### Post by Hippytaff on 2010-11-02
SMB - Samba - thought so :-)

---

### Post by keats4 on 2010-11-03
Nautilis? I don't see this on my desktop.

Keat

---

### Post by Zzl1xndd on 2010-11-03
> **keats4 said:**
> Nautilis? I don't see this on my desktop.

Keat

Nautilis is a File manger like Windows Explorer. 

You can also just go to Places > Connect to server.

---

### Post by HermanAB on 2010-11-03
The Ubuntu Gnome File Browser is called Nautilus.  You can also do it with Kubuntu KDE Konqueror.

Linux file browsers are like Swiss Army knives and can browse pretty much anything on a computer.

---

