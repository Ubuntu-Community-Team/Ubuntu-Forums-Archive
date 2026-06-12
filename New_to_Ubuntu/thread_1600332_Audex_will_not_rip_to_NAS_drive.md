---
title: "Audex will not rip to NAS drive"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by KPJ on 2010-10-18
I have installed Audex and it works great for ripping to my local drives, but I am having issues with it ripping to my NAS. I have mounted the network drives so they show when selecting where to save the files. I can create new directories using Audex on my NAS. I checked all file rights on the NAS operating system to ensure everyone can modify. But when I try to rip to the NAS I get what is in the attachment.."unable to create directory"  This is confusing because I can create a directory manually from within Audex???

Any suggestions is appreciated.
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by perrti-y02 on 2010-10-19
It could be that you are trying to rip it to a directory that the program doesn't have permissions to write to. If you made the folder as your desktop user it will probably be the case that you are the owner of it and only you and the root user can fiddle with it. Audex might be running in some way that doesn't allow it to write to that folder.

What you can try is changing the permissions. The command is chmod and will look something like

```
sudo chmod -R 777 /music
```

I don't know if it has to be run as sudo but I always do, the -R applies it recursively and the 777 means that everyone has read, write and execute permissions.

Hope that works for you.

---

### Post by KPJ on 2010-10-20
> **perrti-y02 said:**
> It could be that you are trying to rip it to a directory that the program doesn't have permissions to write to. If you made the folder as your desktop user it will probably be the case that you are the owner of it and only you and the root user can fiddle with it. Audex might be running in some way that doesn't allow it to write to that folder.

What you can try is changing the permissions. The command is chmod and will look something like

```
sudo chmod -R 777 /music
```I don't know if it has to be run as sudo but I always do, the -R applies it recursively and the 777 means that everyone has read, write and execute permissions.

Hope that works for you.


Thanks for the feedback, I believe you are on the right track. I permanently mounted the dirve with the following command in /etc/fstab: //IOMEGA-0A41DA/music    /home/ken/IOMEGAmusic        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

The NAS is visible on my desktop. I can write to it by dragging and dropping files. I can modify folders within Audex. When I tried to rip an album, the top directory of the CD (artist) is made then it fails to create or write any other data and stops. What is even more interesting is that the directory Audex made has a lock symbol in the bottom right corner of the folder icon. 

I loaded another ripping software and discovered that it had the same results as Audex so it has to be a file setting.

I attempted to run the chmod command but was unable to find the directory????? The command I entered was "sudo chmod -R 777 /home/ken/IOMEGAmusic"   Have I listed the file structure incorrectly?

---

### Post by perrti-y02 on 2010-10-21
I am not sure what else to suggest.

Maybe try to find the folder through the terminal to double check it is where you think it is and not somewhere subtly different. Beyond that I am not sure.

---

### Post by perrti-y02 on 2010-10-21
Are you using SAMBA on the NAS? That might complicate things and it certainly takes it beyond my knowledge.

---

### Post by KPJ on 2010-10-21
> **perrti-y02 said:**
> Are you using SAMBA on the NAS? That might complicate things and it certainly takes it beyond my knowledge.

I am using SAMBA on NAS. It has to be a rights issue with the mounting of the drive.  Thanks for your help perrti.

---

### Post by perspectoff on 2010-10-21
I'm having the same problem with some DVD / video manipulation programs. 

I used to be able to do it, so perhaps something changed in Samba or permissions or something.

There is some mystery to me about permissions, anyway. When I change permissions from the command line ( chmod / chown ), they do not appear when I check using a File Manager (Nautilus or Dolphin), and vice versa.

It is as if there were two permission paradigms in Ubuntu, somehow, and Samba is in limbo somewhere in between.

---

