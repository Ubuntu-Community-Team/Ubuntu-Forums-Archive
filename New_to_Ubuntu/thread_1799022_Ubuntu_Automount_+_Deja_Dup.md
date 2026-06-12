---
title: "Ubuntu Automount + Deja Dup"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by Mars11 on 2011-07-07
I want to mount an external HDD connected to a computer running Windows 7. I've shared it and can access it, but I have to mount it manually every time. I also want to backup to it with Deja Dup. And if it's at all possible, have it show up on the Unity taskbar.

Info: Windows 7 computer name = Family-PC, Windows 7 computer network location = 192.168.0.2, HDD = Arthur's Stuff, Ubuntu Version = 11.04 64-bit.

---

### Post by jtarin on 2011-07-07
How are you mounting it ? Command-line? What command?

---

### Post by Mars11 on 2011-07-07
> **jtarin said:**
> How are you mounting it ? Command-line? What command?
Navigating to it using the Natilus.

---

### Post by jtarin on 2011-07-07
> **Mars11 said:**
> Navigating to it using the Natilus.
You'll have to excuse my ignorance about your filemanager, but could you tell me under what directory it is mounting? /media? It's own directory? If so what is the name?

---

### Post by Jagoly on 2011-07-07
Sorry I misread your post. I thought you were sharing from your computer to a windows 7 machine:oops:

---

### Post by Mars11 on 2011-07-07
No, it doesn't mount it there. It's mounted at smb://family-pc/arthur's%20stuff

---

### Post by jtarin on 2011-07-07
I assume then that this is a USB drive? Is it connected all the time eg;24/7?

---

### Post by Mars11 on 2011-07-07
I did say it was an external HDD, and yes it's connected 24/7.

---

### Post by jtarin on 2011-07-07
[Fairly simple]("http://www.liberiangeek.net/2011/03/mount-partitionsdrives-ubuntu-pysdm/")
[A little work]("http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/")

---

### Post by Mars11 on 2011-07-07
Thanks! I now have two of the things accomplished. Do you know a way to add it to the Unity Launcher/Taskbar?

---

### Post by Jagoly on 2011-07-07
You could try [this]("http://mrjovanovic.posterous.com/pinning-folders-to-unity-launcher-in-ubuntu-n")

But I don't know if it works for network locations.

---

### Post by Mars11 on 2011-07-07
> **Jagoly said:**
> You could try [this]("http://mrjovanovic.posterous.com/pinning-folders-to-unity-launcher-in-ubuntu-n")

But I don't know if it works for network locations.
It's not really a network location anymore, it's at /media/Storage. That won't let me select "Storage."

---

### Post by jtarin on 2011-07-07
> **Mars11 said:**
> Thanks! I now have two of the things accomplished. Do you know a way to add it to the Unity Launcher/Taskbar?
I don't use Unity so I'm no help there but if you mark this thread as solved and make another post with that topic or search the forums.....I know the answer is here.

---

### Post by Jacobonbuntu on 2011-07-07
> **Mars11 said:**
> It's not really a network location anymore, it's at /media/Storage. That won't let me select "Storage."

Hi Mars11, doing that is quite easy, I will show you, but how would you like it to show up? seperately or as a directory in /home/yourname?

---

### Post by Mars11 on 2011-07-07
> **Jacobonbuntu said:**
> Hi Mars11, doing that is quite easy, I will show you, but how would you like it to show up? seperately or as a directory in /home/yourname?
I don't think I quite get what you're saying. I want it to show up in the Unity Launcher/Taskbar.

---

### Post by Jacobonbuntu on 2011-07-07
I understand! ;) but you can make it an entry in you home-folder icon, like this [http://dl.dropbox.com/u/1155139/Schermafdruk.png](http://dl.dropbox.com/u/1155139/Schermafdruk.png)
or you can make it a separate icon in the launcher.

---

### Post by Mars11 on 2011-07-07
I'd rather have a separate icon on the launcher.

---

### Post by Jacobonbuntu on 2011-07-07
> **Mars11 said:**
> I'd rather have a separate icon on the launcher.

Ah, too bad, :D

No seriously, then indeed make a starter, give it the name you want. At the command, type: nautilus /media/Storage

move it to the /home/"yourname"/.local/share/applications -directory (it will work from any directory, but this is the most "proper" location) and drag it onto the launcher. you might also want to give it another icon :)

P.S. the starter should be an "application", not a "location"

---

### Post by Jagoly on 2011-07-07
That's exactly what I linked to...

---

### Post by Jacobonbuntu on 2011-07-07
> **Jagoly said:**
> That's exactly what I linked to...

and it does not work????
by the way, I just noticed the starter-launcher conflicts if there is already another nautilus window open (then it just doesn't work). That is not the case if you make it an entry in the "personal folder icon" in the launchbar. 

To check the mountpoint of your network-folder: if you open the Storage-folder; what is the path you can see at the top?

---

### Post by Jacobonbuntu on 2011-07-07
> **Jagoly said:**
> That's exactly what I linked to...

Ah funny!
Jagoly, I didn't see your name, I thought mars11 wrote the post! 

:biggrin:
...kind of a mix up....

---

### Post by Jacobonbuntu on 2011-07-09
.....I guess OP has left the building...

---

