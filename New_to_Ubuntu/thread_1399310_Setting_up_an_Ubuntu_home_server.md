---
title: "Setting up an Ubuntu home server"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by natpondnewbie on 2010-02-05
I am planning on setting up a home server soon, and I intend on using Ubuntu on it. unfortunately as a newcomer to the linux world, I am unfamiliar with many of the programs I will need to give my server the functionality I desire. The following is a list of roles/capabilities i would like my server to play, I was wondering if you lot could help me find the programs necessary to accomplish all (or as many as possible) of these.

-Web server for a wordpress blog/small website with my resume, current projects, etc.
-"exchange" server for my email/calendars/contacts
-data backup/sync
      -back up all of my media/documents/settings for my laptop and desktop
      -keep one unified backup of all my files, taking into account changes i make to files on my 2         other computers, ideally this would sync changes automatically and keep all computers maintaining the same versions of all my files. if i encode a cd and put it in my MP3 collection on my desktop, this should propagate tot he server, and then to my laptop, this sort of idea.
-HTPC connected to my television/stereo (im thinking XBMC)
-give me the ability to log in to my computer and get files remotely (this is just ssh, right?)


thank you for any help/information you can give me.

---

### Post by nothingspecial on 2010-02-05
The key to answering these questions correctly is weather or not the other  computers are running some sort of linux.

---

### Post by lykwydchykyn on 2010-02-05
> **natpondnewbie said:**
> 
-Web server for a wordpress blog/small website with my resume, current projects, etc.

Apache2 is the obvious choice, though you may want to install the "LAMP" role during installation, since most CMS systems require PHP and a database.
> 
-"exchange" server for my email/calendars/contacts

Are you hosting your own email server?  Most things in this category seem like overkill for a home server.  
Anyway, I haven't set something like that up so I won't pretend to know.
> 
-data backup/sync
      -back up all of my media/documents/settings for my laptop and desktop
      -keep one unified backup of all my files, taking into account changes i make to files on my 2         other computers, ideally this would sync changes automatically and keep all computers maintaining the same versions of all my files. if i encode a cd and put it in my MP3 collection on my desktop, this should propagate tot he server, and then to my laptop, this sort of idea.

There are a lot of good backup solutions available.  Bacula is a good place to start, as it's one of the more popular selections.
> 
-HTPC connected to my television/stereo (im thinking XBMC)

Don't know there.  I'm not that high-tech.
> 
-give me the ability to log in to my computer and get files remotely (this is just ssh, right?)

SSH will give you remote access to the server.  You can pipe various services over ssh as well, so it's sort of a swiss-army-knife of remote connectivity.

What sort of things do you want to do remotely?

---

### Post by natpondnewbie on 2010-02-05
@nothingspecial
sorry, forgot to mention. one is a macbook pro running OSX/Windows7 (i need windoes 7 at work, dont ask.) and the desktop is running Kubuntu and Win7.

@lykwydchykyn
remotely i really just want to be able to access my files. For example if i have a song stuck in my head at a friends house i can just downlaod the mp3 from my server, or if i need a document at work i can just grab it remotely.

---

### Post by peace.gangsta on 2010-02-05
Web hosting and file hosting can cost you a bit( I aint sure abt it though)
So why not have a paypall and download from rapid-share , filetube and other popular file-hosting sites.
And infact , if you are ready to compromise with speed you can go for p2p clients like dc++,shareaza(which is perhaps history now),torrent.. etc.
But then again you can always go for a server.
Do you have any previous experience with famous servers like wamp , apache etc on windows platform..??

---

### Post by peace.gangsta on 2010-02-05
I think those people who have had experience with creating/running servers on linux platform can give some ideas.. some tutorial links /e books /videos which can throw some light on the basic of file hosting can help a lot.
Once you get the basics you can go for whatever you want to do :)

---

