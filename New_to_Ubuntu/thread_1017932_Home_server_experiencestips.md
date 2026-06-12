---
title: "Home server experiences/tips"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-12-21
So there is a great tutorial here for setting up a server for an isp here:
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

That's great and all, but I just need a file/media server for my home.  Can you share your server setup information and what you installed to suit their home file/backup/media needs?  Last year there was talk about about creating a variant for home servers, but it never went anywhere.  I ask because there really doesn't seem to be a good tutorial for home servers, just for advanced servers that do a lot more than a home user needs.

Thanks

JTS

---

### Post by chrisamiller on 2008-12-21
If you're not looking for a development box, there isn't much configuration required.  Use samba shares to set up a few folders for your media.  Rsync can be run over ssh quite easily for backups.  What specifically are you having problems setting up?

---

### Post by jimmy the saint on 2008-12-21
no reall problems.  I actually have a server set up that works pretty well, but I just blindly followed the tutorial. I was just wondering if anyone had a set up they liked and wanted to share.  I'm always looking for tips!!

---

### Post by Kellemora on 2008-12-21
Hi JTS

I'm in the process of building a new file server myself, but will be actually implementing it in REVERSE!

Without getting into a lengthy dissertation on why I'm working in Reverse, suffice it to say it has to to with PUT and FETCH permission problems we've never seemed to get resolved.
And honestly, the office runs much faster this way too!
Everyone DRAWS (Fetches) their work from the server, but they NEVER save (PUT) their completed work back to the file server.  The file server will Fetch their completed work from their computers.  Thus permissions stay intact, and they can Fetch it back from the server the next day.

Shortly after Fetching all the work, another Mirror Fetches everything on the File Server for off-site storage.

Or simply stated, nothing is ever UPLOADED and Everything is ALWAYS a Download.  EG:  Worker at Computer B fetches their Documents from the File Server, when they reach a stopping point (like at lunchtime) or finish the job, it gets put either into the Computer B working folder or the Computer B finished folder.
The File Server will Fetch those files and store them.  When they get back from lunch, the Fetch their working folder back from the File Server, or they can use the one that still resides on their machine after lunch too.  At 3pm all the folders will be Fetched again, and then after quitting time.

So the file server works as a mirrored backup, so we don't have to look all over the place to find out who has what anymore.  Everything is in one place.

On the Home Front, each computer is designated as the file server for certain things, and the actual file server itself is just a mirror of everything all in one place.  You CAN Fetch something from the server instead of going to the machine the original is stored on too.

Things are changing slowly and hopefully soon I will have two file servers and the off-site backup as well.

Everyone likes their own computers set up a certain way and their files in a certain place.  By using the file server in Reverse, they can do that, yet all the files are where they belong on the server as well, in a more logical place.

In fact, I use the exact SAME Broad Classification Schedule for everything, whether it's paper, inventory or electronic data.
My house, office, storage facilities, land and electronic storage media all have the exact same filing systems.
The only thing that changes is the final location of the item.
It's either in a bin, in a file in cabinet or on a Hard Drive.
Simple!

The hardest part of anything is remembering where you put it and WHY.....  And the bigger hard drives get, the easier it is to loose something.  So, be sure to index EVERYTHING and you'll never lose anything.  

Good Luck

TTUL
Gary

---

### Post by CarolinaGuy on 2008-12-21
jimmy,

I followed this link

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

Has everything you need.

CarolinaGuy

---

