---
title: "windows pc access to ubuntu pc"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by devilgas on 2009-09-28
I have only 1 ubuntu box runing desktop 9.x. I want to remote connect into it with my Windows pc.
 
What do I need to setup on the ubuntu box?
 
What do I need on my windows pc side?
 
Appreciate the help

---

### Post by LewRockwell on 2009-09-28
[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

reading the comments might also provide additional information

.

---

### Post by erilidon on 2009-09-28
you need a vnc program. I like Tight VNC and Real VNC is alright

---

### Post by 3rdalbum on 2009-09-28
When you say you want to "remote connect", what exactly is it that you want to do?

If you want to share files and folders, then you should install the "system-config-samba" package which gives you a GUI to set up Samba file sharing on the Ubuntu machine. Windows already comes with the necessary features to connect to Samba shares, and your Ubuntu share will appear under "Network Neighbourhood". Or you might need to add the share to Windows, giving Windows the following URL:

```
smb://<computername>/<sharename>
```

If you want to be able to remotely control the Ubuntu machine from Windows, then start Remote Desktop on the Ubuntu machine, and then install a VNC client on Windows.

---

### Post by little_penguin on 2009-10-04
For a minimal configuration setup, also take a look at:

[http://www.ntrconnect.com]("http://www.ntrconnect.com/") (multiplatform)
[http://www.yugma.com](http://www.yugma.com) (multiplatform)
[http://www.teamviewer.com](http://www.teamviewer.com) (in Wine on the linux side)

A little bit more configuration is involved, but very fast and secure since it uses SSH and RSA/DSA encryption:

Nomachine NX:
[www.nomachine.com]("http://www.nomachine.com")

---

### Post by Old_Grey_Wolf on 2009-10-04
> **3rdalbum said:**
> If you want to share files and folders, then you should install the "system-config-samba" package which gives you a GUI to set up Samba file sharing on the Ubuntu machine.

I don't remember having to install system-config-samba for the last couple of Ubuntu releases. Maybe I did but have forgotten doing it. All I remember doing is going to the Places menu and navigating to the folder I wanted to share, right click on the folder, select Properties, then select the Share tab, and select how I wanted to share it.

---

### Post by erilidon on 2009-10-04
> **Old_Gray_Wolf said:**
> I don't remember having to install system-config-samba for the last couple of Ubuntu releases. Maybe I did but have forgotten doing it. All I remember doing is going to the Places menu and navigating to the folder I wanted to share, right click on the folder, select Properties, then select the Share tab, and select how I wanted to share it.


If I remember correctly, the first time you do so it downloads samba automatically.

---

