---
title: "Feisty -&gt; Feisty... so why windows network?"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by Docter on 2007-04-27
Hullo gurus.

I've never really been much of a networker. I used to make up my own parallell and serial cables for a null modem connection but that's it. 

OK

So I used to share files between two windows machines using a CAT5 crossover LAN. Easy.. just click the wizard. I then changed my main machine to ubuntu and set it up using SAMBA. Easy and informative. Then I got rid of windows on the other machine but now I find myself headbuttinga brick wall.

NFS would seem the way to go now and seeing as both machines are on feisty (are sharing a connection over the LAN) it would seem that SAMBA is unnecessary.

I have allowed connections from my network IP's, I have set the sharing permissions on the folder I wish to share but anytime I try to connect to server or browse network all I get is an empty "Windows Network".

Of course, I never used a GUI when I was using samba I got to it from a terminal:

```
smb://192.168.0.1/Music
```

or whatever... I may need to set a username and password or somesuch for NFS. It's all GNOME ubuntu btw.

Also.. how the bloody hell do I stop my ubuntu as identifying itself as MSHOME? On edgy it was the same problem so I took a meat clever to it and removed samba entirely (but that didn't get rid of "Windows Network" or "MSHOME" either)


must....destroy.....windoze

---

### Post by chili555 on 2007-04-27
I live, happily, in an all Linux home, too. I feel your pain. Without Samba and Winbind, you will probably not be able to readily browse the network by name. There is a quick and easy way to get to your music server, however, without all that. It does require that you know the IP address of the machine you want to connect to, so you may have better luck setting your server with a static IP address. 

Then go to Places -> Connect to Server -> select SSH. SSH is installed and running by default. Put in the Server (192.168.x.xyz), User name (any user on the machine you want to connect to) and click connect. An icon will appear on your destop. When you right-click the icon, you have the option to browse the folder, put in the password of the user and you will be able to see files, open them, play videos, etc., as well as drag-n-drop files to your home folder.

Perhaps this will help.

---

### Post by Erlander on 2007-04-27
From memory I had to install either SSH server or SSH client.  However with them bot there I have no trouble in browsing from one Feisty pc to the other and vice versa.

Places/Connect to Server and select SSH and type in the IP address of the other pc

Rob

---

### Post by Docter on 2007-04-30
Many thanks.

---

