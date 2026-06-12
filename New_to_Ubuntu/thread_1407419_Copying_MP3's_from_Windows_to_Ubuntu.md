---
title: "Copying MP3's from Windows to Ubuntu"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by foghornsean on 2010-02-15
Hi Guys,
 
I've installed Ubuntu 9.10 for the first time this weekend and have run into a bit of trouble when it comes to using MP3's
 
I created a partition and mounted it to a folder which was shared over my network. Then from my laptop running XP I accessed the shared folder on my Ubuntu box and copied some MP3's from my XP computer into it.
 
However when I look at the properties of the MP3 files all the fields (artist, title, length etc) are "unknown". These fields are all filled in on the XP system but they don't appear to have been copied across. The main reason I installed Ubuntu was to run it as a server so I could access music/video from it but if the MP3's are missing the tags then I can't organise them properly either on my other windows machine or Xbox.
 
Has anyone got any suggestions on how I can get this information to copy across and still be associated with each file?
 
Thanks in advance guys
 
Sean

---

### Post by AlexDudko on 2010-02-15
Do files have the tags if copied back to an XP computer? Aren't the files corrupted? Is there a difference in checksums in XP and Ubuntu?

---

### Post by foghornsean on 2010-02-15
I haven't tried copying them back from Ubuntu to XP. I'll try that when I get home from work.
 
The files played fine either in Ubuntu or when accessed from my xbox 360 so don't appear to be corrupt.
 
I did however open the files in easyTAG and it was able to find the right information so it looks like it was associated with the files. However, even after clicking to save the information back to the files,Nautilus still returned the fields as "Unknown".
 
Thanks
 
Sean

---

### Post by 3rdalbum on 2010-02-15
> **foghornsean said:**
> I haven't tried copying them back from Ubuntu to XP. I'll try that when I get home from work.
 
The files played fine either in Ubuntu or when accessed from my xbox 360 so don't appear to be corrupt.
 
I did however open the files in easyTAG and it was able to find the right information so it looks like it was associated with the files. However, even after clicking to save the information back to the files,Nautilus still returned the fields as "Unknown".
 
Thanks
 
Sean

There are different versions of ID3 (the tagging format). My guess would be that Windows XP is using an old version, and Gnome expects a newer version. You get the same problem with certain portable MP3 players.

You can set Easytag to use a later version of ID3, in the preferences. Then you can simply get Easytag to "save" all your MP3s, which will convert the tags.

---

### Post by foghornsean on 2010-02-15
I've opened the mp3 file in easyTAG and checked the preferences. The newest ID3 tag version I have is ID3v2.4.

Then clicking save it saves the file but still when I go to the properties of the mp3 file in Nautilus the fields are still "unknown".

Any ideas on where to go from here?

---

### Post by foghornsean on 2010-02-16
Any ideas guys?

---

### Post by Thomas Garman on 2010-02-16
I have a separate partition set up on my HD that I share between Vista Ultimate and Ubuntu 9.04.  I put all of my music and videos on this shared partition.  I wondered if I had the same problem you have after I read your post, so using Ubuntu I chose a random mp3 and right clicked it and chose properties.  Everything was present...  name, file type, etc etc.  I never entered any of that data.  So, my guess is that you lost the tags that you entered manually?

---

### Post by foghornsean on 2010-02-16
The tags that are associated with the files were put in automatically when I ripped the CDs using itunes so they're not tags I've added manually.
 
What's strange is that EastTAG finds the tags without issue but doesn't seem to be able to write them back to the mp3s in a way that any other program can access them.

---

### Post by foghornsean on 2010-02-16
I've managed to sort it out!

I'm not really sure how I did it but just in case it's any help to other people I'll try and tell you what I've done.

I opened the track and by default it opened with Movie Player. Since I'd not opened an .mp3 file since I reinstalled I hadn't downloaded the codex's etc so I auto downloaded them. This however didn't help Nautilus.

I then installed tagtool (sudo apt-get install tagtool) and looked at an mp3 file. Again tagtool was able to read the id3 information but I was still unable to get it to show up in Nautilus.

I then installed id3v2 (sudo apt-get install id3v2) and then restarted Nautulus (killall -s TERM nautilus).

Low and behold, when I now right click on an mp3 and go to properties all the information from the id3 tag is there.

I hope this helps someone else and thanks to everyone above for their efforts.

Sean

-One Happy Ubuntu User :D

---

