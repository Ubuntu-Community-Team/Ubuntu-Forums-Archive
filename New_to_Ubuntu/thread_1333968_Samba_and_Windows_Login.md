---
title: "Samba and Windows Login"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by D_2 on 2009-11-22
I have Ubuntu Server 9.10 and I had to do a fresh install because the HDD died. Before the drive died when I was going to access the shared directories on the server I was prompted to enter a username and password so the server knows who I am. I am not able to do that now and now when I try to save a file, or update a file on the server that has a shared directory I get access denied even tho I have given myself permision to that directory for read and wright, but if the system doesn't know who I really am then it wont know to let me write to a file or make any new files or new directories.
 
How can I have it ask me to enter something so it knows. I would rather have it this way for security reasons. I don't mind having to enter something when I go through My networks or if I have a mapped network path to the share, when I click on that link it should ask me to enter a username and password and remember it untill I reboot my Windows computer.
 
Any help with this will be greatful.

---

### Post by frenchn00b on 2009-11-22
> **D_2 said:**
> I have Ubuntu Server 9.10 and I had to do a fresh install because the HDD died. Before the drive died when I was going to access the shared directories on the server I was prompted to enter a username and password so the server knows who I am. I am not able to do that now and now when I try to save a file, or update a file on the server that has a shared directory I get access denied even tho I have given myself permision to that directory for read and wright, but if the system doesn't know who I really am then it wont know to let me write to a file or make any new files or new directories.
 
How can I have it ask me to enter something so it knows. I would rather have it this way for security reasons. I don't mind having to enter something when I go through My networks or if I have a mapped network path to the share, when I click on that link it should ask me to enter a username and password and remember it untill I reboot my Windows computer.
 
Any help with this will be greatful.


well eventyully screenshot

do you have SSH on your server ? you can acesss it as root

---

### Post by D_2 on 2009-11-22
> **frenchn00b said:**
> well eventyully screenshot
 
do you have SSH on your server ? you can acesss it as root
 
yes I can access it through putty but I am wanting to be able to have programs save files to the ubuntu server and right now I get access denied when saving, I can see the files of the share and I can read so I have 755 access over there but I want something in windows to come up and ask me who I am and my password and then send that information to the server so it then knows who I am and it is ok to wright to the share.

---

