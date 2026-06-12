---
title: "Linux connected to WinXP"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by timohnani on 2007-08-07
Hi,

I've been searching through the forums and using the advice I've found i've tried to setup a simple home network. My aim is to have my Kubuntu (feisty) laptop connect to my WinXP professional desktop computer simply using a network cable so that I can transfer files from one computer to the other. This worked fine when both machines had WinXP. All I had to do was run the "home network" wizard on both computers and set the shared folders.  Now since I am new to Linux (networking has never been my strong point either) I am having some trouble understanding how to get things going. 

I've read around and found three options: samba, smbfs and cifs. From what I've read I've understood that Samba is the "highway" and smbfs or cifs is the "vehicle". Is this a correct concept? If this is correct then I assume I will have to have Samba running in all cases. 

I've heard that smbfs is old and has stopped being developed. Is ths true? If so I guess cifs would be the way to go. 

Once I get the linux side of stuff running e.g. samba and cifs do I need to do anything on my WinXP computer? Ultimately it would be enough for me to be able to see the harddisk of my WinXP so that I can copy files from it and send files to it. 


I would appreciate any help. I am trying to understand the concepts so that maybe I can properly understand the instructions all over the forums and howtos. 

Thanks

Timo

P.S. So far I am loving Kubuntu. If I can get all things setup it will be good bye to Windows FOREVEEEEEEER!!!!!

---

### Post by forgeuk on 2007-08-07
I do something similar here, I have a linux box upstairs and a XP box downstairs, hooked up with a network cable. I don't quite understand what its really doing, but this worked for me:

```
sudo apt-get install samba smbfs
```

then I added a line to /etc/fstab:
```
//PVR/Multimedia /media/PVR cifs rw,user,userid=xxxxx,password=xxxxx1 0 0
```

and created a folder /media/PVR

then do a...
```
sudo mount -a
```

and a "PVR" icon appears on my desktop, which shows the "Multimedia" share on my XP machine downstairs.

So, you do need a password protected user set up on your XP machine, and a network share.


Also, Have a look at this part of the ubuntu guide, it shows a slightly different method...

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

---

