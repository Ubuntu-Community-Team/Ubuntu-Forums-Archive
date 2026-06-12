---
title: "Share directory over internet"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by petri on 2011-07-19
Is there any easy and secure way to share one directory over internet for streaming purpose? I want to share my movies to my children but I don't want them to be able to browse whole hard drive just that one specific directory.

I tried ftp but it doesn't allow streaming, I tried VNC but that one requires port 5900 to be open on my router and that doesn't sound so safe to me. Anyway it didn't wokr either. Once I read a comment there this guy created own VPN which his friends could join and then they were able to watch movies with XBMC though the files was still in .rar packages. He never replied to my question how he did it.

Sending DVD:s to three diffrent locations costs some money and takes time. There must be an easier way, right?

---

### Post by eriktheblu on 2011-07-19
SSH is probably the best answer but I haven't gotten far enough with it to offer instructions.

> requires port 5900 to be open on my router and that doesn't sound so safe to me.

Anything you wish to allow others to see on your computer is going to require port forwarding from your router. 

I would actually suggest a service like Ubuntu One or Dropbox.

---

### Post by petri on 2011-07-21
Thank you for responding.

Ubuntuone and Dropbox are really not an alternative. SSH is an easy way to connect but how to restrict browsing anywhere else than the users directory?

---

### Post by aktiwers on 2011-07-21
I would also suggest SSH. 
To restrict access, you could create a system user that only has read access to the folders you want to share. 


If you feel like experimenting, you could try:
[http://www.oneswarm.org/](http://www.oneswarm.org/)

I tried it when it was in extreme alpha , so it was a little unstable. Maybe it got more mature now?
Its about 1-2 years since I tried it.

---

### Post by MrWES on 2011-07-21
You can install denyhosts, to help protect yourself on the fowarded port.

[http://www.ubuntugeek.com/securing-ssh.html]("http://www.ubuntugeek.com/securing-ssh.html")

---

### Post by petri on 2011-07-22
> **aktiwers said:**
> ...
To restrict access, you could create a system user that only has read access to the folders you want to share. 
...

Yes exactly what I want to do. Just still don't know how.

---

### Post by halitech on 2011-07-22
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by petri on 2011-07-24
[QUOTE=halitech;11074763][https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)[/QUOTE

And which way will that howto help me restrict acces to more than one folder?

---

