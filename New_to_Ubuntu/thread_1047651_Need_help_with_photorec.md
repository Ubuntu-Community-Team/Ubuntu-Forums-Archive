---
title: "Need help with photorec"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by zabien1970 on 2009-01-22
I have a lg venus phone I've been taking pics/vids with and storing them to a SD card then transfering to my laptop, last time I removed the card and put it in my phone it said blank and do I want to format, I was using the cp command, put in back in my computer and there its blank too.
 I started up photorec and it only shows my harddrive available. I do get an icon on my desktop so I believe its mounting.
 What could be the prob?

---

### Post by blueridgedog on 2009-01-22
My guess would be that the card became corrupt during removal.  Did you eject it via the eject button in nautilus?  If you let the phone format it again, you may be able to have it automounted in Ubuntu again.

---

### Post by zabien1970 on 2009-01-23
That is pretty much what I was thinking, I didn't unmount it and corrupted it, my phone does want to reformat it but I'm trying to recover my data which is why I'm using photorec, but I dont know how to get photorec to find it.

---

### Post by zabien1970 on 2009-01-27
Bump,  Still need help with this

---

### Post by phd7 on 2009-01-30
How about putting the card in a USB card reader. This may show up on the photorec list in "select drive"

---

### Post by buffy^ on 2009-01-30
[http://www.recuva.com/](http://www.recuva.com/)

---

### Post by phd7 on 2009-01-30
> **buffy^ said:**
> [http://www.recuva.com/](http://www.recuva.com/)

screenshot from Recuva.com:
System requirements 

[B]Recuva will run on any PC running Microsoft Windows 98 or later:

Windows Vista (all editions, including 64-bit) 
Windows XP (Home, Professional, Media Center, Tablet Edition, 64-bit) 
Windows 2003 and 2008 Server (all editions). 
Windows 2000 
Windows NT4 
Windows ME (Windows Millennium) 
Windows 98 (Note: Windows 98 does not support secure deletion) 
Recuva is a small program that runs fast. There are no minimum memory or hard drive requirements.

Note: Recuva works on both NTFS and FAT-formatted drives.[/B]


are you sure it works with Linux? I was wondering why I hadn't seen it mentioned before.

---

### Post by buffy^ on 2009-01-30
Sorry didnt think that one though, I run many differnt OS's so I dont think about that kinda of thing.

---

### Post by mkvnmtr on 2009-01-30
Recuva is a Windows utility. Why would someone post that as a resource to help someone on a Ubuntu site when there are several apps that work for linux?

---

### Post by buffy^ on 2009-01-30
Some times getting the files back is more important that just using ubuntu. Also said person may not know about linux apps, but as you didnt post the link one wonders if you do either.

Other than that your comment was supportive and helpful.

---

### Post by zabien1970 on 2009-01-31
After a little more research I've solved this, I had to run fdisk to find the device name for the card then run photorec /dev/(device), worked great, recovered all pics and a few of the videos.



Edit: Why can't I mark this as solved? I don't see the option under thread tools

---

