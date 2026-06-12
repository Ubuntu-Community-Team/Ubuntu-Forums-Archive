---
title: "Files from Windows to Ubuntu?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by noseshark on 2010-01-18
[FONT=Century Gothic][SIZE=2]Is it possible for me to transfer some of my files eg. Music, Video, ect from Windows to Ubuntu?

**[COLOR=YellowGreen]I have Dualboot[/COLOR]**[/SIZE][/FONT]
[FONT=Century Gothic][SIZE=2]
If so how would I go about doing this? **[COLOR=DarkOrchid]simplest way possible?[/COLOR]**[/SIZE][/FONT]

---

### Post by 1packer on 2010-01-18
I setup an extra partition formatted to FAT 32 with most of my hard drive space, then leave all the files on it, both operating systems can access it that way. Not sure if it is the easiest way after a fresh install though.

---

### Post by audiomick on 2010-01-18
Can't you see the windows partition in the file manager from Ubuntu? I think you should be able to. If so, you should be able to just drag and drop into a folder in the Ubuntu partition.

---

### Post by werecatomega on 2010-01-18
the easiest way to transfer files in dual boot is when in ubuntu, go to Places/OS. it will ask for your password and then you can enter your windows filesystem

---

### Post by thatguruguy on 2010-01-18
Or, just leave them where they are, and access them straight from the windows partition as needed.

---

### Post by noseshark on 2010-01-18
Hum, I tryed but all it says under **Places** is

**Home Folder, Desktop, Documents, Music, Pictures, Videos, Computer, Floppy Drive, Office 10, Network, Connect To Server, Search For Files, Recent Documents**

I went to **Networks** and It says **Windows Network**, But when I try opening it 

"**Unable to Mount Location**
Fail to retreive share list from server"

I checked the properties and they all say unknown, Im not sure how to fix this

**** And I don't want to restart my computer to listen to my music or watch a movie, I want to remove windows completely after I get used to Ubuntu**

---

### Post by warfacegod on 2010-01-19
Check in Synaptic and make sure you have ntfs-progs installed. As well as a few other related packages.

---

### Post by PenguinInside on 2010-01-19
> **noseshark said:**
> Hum, I tryed but all it says under **Places** is

**Home Folder, Desktop, Documents, Music, Pictures, Videos, Computer, Floppy Drive, Office 10, Network, Connect To Server, Search For Files, Recent Documents**

I went to **Networks** and It says **Windows Network**, But when I try opening it 

"**Unable to Mount Location**
Fail to retreive share list from server"

I checked the properties and they all say unknown, Im not sure how to fix this

**** And I don't want to restart my computer to listen to my music or watch a movie, I want to remove windows completely after I get used to Ubuntu**

Do you have your Windows installation on a disk on the same computer as Ubuntu?

On a default installation of Ubuntu Karmic, Ubuntu can read (and write) to Windows partitions.

Like the poster above said, just leave your music files where they are and play them from Ubuntu.

Give some more information, and folks will be able to help you out.

---

