---
title: "Need help making full image of my Ubuntu Karmic installation."
date: 2010-02-16
forum: New to Ubuntu
---

### Post by inameiname on 2010-02-16
Having no luck resolving issues with Remastersys, specificially problems with ubiquity, the Ubuntu Live CD Installer, I am looking for any other way to make a full backup of my Ubuntu Karmic computer, so that I can have an image of it for restoration use, as well as using it to put on a couple other computers, which all have different hardware.

Remastersys worked great up until recently, but due to the problem, not a Remastersys one mind you, I need alternatives.

Does anybody have a good, basic script, or idea which would work. I've tried QuickStart, but that didn't work on another computer as it gave out an error due to wrong hardware. I also found a script online somewhere, which would give me a Tar file, but it wouldn't get restored onto another computer, which was first installed with a fresh installation of Ubuntu Karmic from the live cd, downloaded from [www.ubuntu.com]("http://www.ubuntu.com").

Any help would be great. :)

---

### Post by Girya on 2010-02-16
checkout partimage its always worked for me. its included on the system rescue live cd. [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by inameiname on 2010-02-16
Thanks for the suggestion. I didn't know it was part of that SystemRescue CD. Thanks for that. 

However, I've looked at Partimage, and from what I've been able to understand of it, it won't allow me to backup, say, my computer, and restore it on another that isn't exactly the same hardware, which is one thing having a custom Live CD made from Remastersys does well. Oh, and from that link you gave me, it seems it doesn't work with ext4 file systems, which is what Karmic's. Though, I may be mistaken.

---

### Post by inameiname on 2010-02-17
Finally, after lots of testings and analysis, I have figured out the problem. It is indeed a PPA repository that had some sort of update which messed with 'ubiquity'. So what I did was reinstalled the entire computer again, but then went through each PPA to see which was causing the problem. 

There is something updated about two weeks ago or so in the following which conflicts with 'ubiquity' (as well as 'nautilus-actions' too actually) which will mess it up to the point where it cannot even open, thus not being able to back up:

deb [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/janvitus/ppa/ubuntu](http://ppa.launchpad.net/janvitus/ppa/ubuntu) karmic main 

So to those who have a similar problem, I suggest checking to see if you have 'janvitus' repository in your sources.list.

Thus, Remastersys seems to work just fine now. But it's always nice learning about other ways to back my system up.

---

### Post by gdonwallace on 2010-02-17
I would suggest clonezilla.  Its an Opensource disk image program.  It works similar to Ghost.  If you ever get to that point where you want to backup your entire system and move it to another computer, clonezilla is a go way to go.

I also know that there is a Ghost clone out, saw it in softpedia's website but I don't remember what it was called or if it was open source / FOSS.

---

### Post by inameiname on 2010-02-17
Clonezilla, I am not familiar with that one. Thanks, I'll check it out.

---

