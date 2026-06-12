---
title: "Question about GRIP..."
date: 2009-11-02
forum: New to Ubuntu
---

### Post by TheMustangZone on 2009-11-02
Hello all,
    I'm still fairly new at using Ubuntu, but I'm starting to get the hang of it.  I recently added GRIP as an application, but I can't for the life of me figure out where it is storing the files it rips down.  How do I change the path so the files will go into the folder I created on my desktop?  Thanks in advance.
 
Rob

---

### Post by streed on 2009-11-02
Applications go to "/usr/share/applications" and just create application-launchers and move them into whatever folder path you want. I don't know if you can change where apps go when they download.

---

### Post by TheMustangZone on 2009-11-03
Thanks for the info, but what I'm trying to figure out is how to tell GRIP to put the "ripped" MP3s into the folder I created.  According to their help menu this is possible, but it doesn't tell you how to do it?  Any other ideas?  Thanks.
 
Rob

---

### Post by plh on 2009-11-07
Hi,
In the "config / rip / ripper tab you can set the directory as well as the file name in the "Rip file format" textfield.

As of me, I wrote "~/mp3.d/%A/%d/%n.wav" and files go to mp3.d under my home dir.
Do the same for the "Encode / encoder" tab : I wrote "~/mp3.d/%A/%d/%n.%x" and my mp3 files end up in mp3.d too

Hope it helps

---

### Post by TheMustangZone on 2009-11-08
> **plh said:**
> Hi,
In the "config / rip / ripper tab you can set the directory as well as the file name in the "Rip file format" textfield.

As of me, I wrote "~/mp3.d/%A/%d/%n.wav" and files go to mp3.d under my home dir.
Do the same for the "Encode / encoder" tab : I wrote "~/mp3.d/%A/%d/%n.%x" and my mp3 files end up in mp3.d too

Hope it helps

THANK YOU!!! That solved my problem.  I do have one other question you might know the answer to, though.  Is there a way to make GRIP create just one folder in the desired location rather than a folder in a folder?  For example, it now creates a folder with the artists name and another folder inside of that one with the album name.  I would like it to just create one folder with the artists name and album name together.  Is that possible?  Thanks again.

Rob

---

### Post by plh on 2009-11-08
Yes I think so: the pattern I gave you indicates "~/mp3.d/%A/%d/%n.%x", the idea is to get something like "~/mp3.d/%A-%d/%n.%x" instead, that should create a unique directory named after the artist AND album names...

Didn't try it yet, but that sould work...

let me know!

---

### Post by TheMustangZone on 2009-11-08
> **plh said:**
> Yes I think so: the pattern I gave you indicates "~/mp3.d/%A/%d/%n.%x", the idea is to get something like "~/mp3.d/%A-%d/%n.%x" instead, that should create a unique directory named after the artist AND album names...

Didn't try it yet, but that sould work...

let me know!

Well, it almost worked.  It created yet another folder with the song name.  I printed off a list of the switches, so I will keep trying different combinations until I get the one I'm looking for, now that I know how they work.  Thanks so much for showing me how to use them.  Take care and God bless.

Rob

---

### Post by jamesisin on 2009-11-13
You may appreciate my post on configuring Grip.  I use flac but it should be pretty obvious what you need to adjust for other formats:

[http://www.soundunreason.com/InkWell/?p=1220](http://www.soundunreason.com/InkWell/?p=1220)

---

