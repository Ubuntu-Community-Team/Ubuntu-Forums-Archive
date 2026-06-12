---
title: "Server - what can I do with it at home?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by wep940 on 2011-05-14
I know this is going to sound like a really dumb question, but that has never stopped me before ;)
 
We've got 6 computers here - 1 too old to bother doing anything on the net, the other 5 all wireless.  1 of the 5 is no longer needed so it's free for me do what I want to now.  It's an older desktop - 2.7ghz celeron (I *think*), 512mb memory, cd-rw drive.  The hard disk is old and slow, and I have 2 spare 80gig ata100 drives to use.
 
I've been thinking about installing the server version on it just to play and try to learn something, but I hate to admit I'm so stupid I really don't know what I would/could use a server for here at home.  Right now it would be just be my dual-boot desktop and my dual-boot laptop that would do anything with it.  Once I find a use and understand something about the server I could migrate the remaining 2 computers into using it.
 
Soooo.....for a real novice, what could/would I use a wireless server for at home?
 
Thanks in advance!

---

### Post by dwasifar on 2011-05-14
Most common use is a file and media server.  Set up some NFS shares and connect to them with your workstations and laptops.  You can connect to the shares automatically with entries in /etc/fstab on the client machines, and have access to your files on any machine.

Another common use is a print server.  Share a printer with your whole network.

Or, if you want, you can open http and https ports on your router to that machine, get a domain registration, and run your own web server.  Create a blog.  Put up pictures of your kids and your dog.  Run a neighborhood newsletter.  Advertise your business.  Run a forum.  Whatever you want, without paying extra for hosting.  If you're ambitious you can run your own mail server too.

Does that get you going?

Edit: FWIW, a file server really simplifies your life if you have multiple computers in your house.  My files live in one place, not scattered around all those machines, and I can get them from anywhere.  

Since you have two drives to play with, you might also consider setting them up using software RAID.  Improves your data safety, if you're making the server the central repository for your files.  I use software RAID1 plus an external backup.

---

### Post by mikewhatever on 2011-05-14
Could be a file server for easy access from different computers in the house. It could also be used for backups, and all you really need is install and configure samba.

---

### Post by dwasifar on 2011-05-14
> **mikewhatever said:**
> Could be a file server for easy access from different computers in the house. It could also be used for backups, and all you really need is install and configure samba.
Yes, you're right.  I didn't notice he said the client machines are dual boot.  So the shares need to be Samba and not NFS like I suggested above.

---

### Post by OM NOM NOM on 2011-05-14
oN MY Ubuntu server (well actually using Ubuntu Desktop as a server - I love a GUI so sue me lol) I've got: 

- File sharing through Samba and SFTP (VERY handy when you're on the road and forgot that ONE presentation you thought was on your hard drive)
- Media streaming using Subsonic [http://subsonic.org](http://subsonic.org). They had a /deb package you can just click and go
- Nomachine NX ([www.nomachine.com]("http://www.nomachine.com")). Remote desktop. Comes in handy as a web proxy as well when work starts blacklisting sites for no logical reason. 
- BOINC. Why not donate some unused CPU cycles to better humanity or search for alien life? :-)

Hope this helps! BTW even with a GUI my P4 server idles at about 186MB, so you might want to try using Ubuntu Desktop as your server if you're not too familiar with the command line. Of course a little more memory might help a bit. If you are however, then I'll shut up AND go sit in the corner!

Hope this helps give you a few ideas!

---

### Post by dwasifar on 2011-05-15
> **OM NOM NOM said:**
> 
Hope this helps! BTW even with a GUI my P4 server idles at about 186MB, so you might want to try using Ubuntu Desktop as your server if you're not too familiar with the command line. 

I have two Ubuntu servers; one was built using the Desktop version and one using the Server version.  Usually I administer them from commandline over ssh, but I run GUIs on both so I can connect into them by remote desktop if I happen to be doing something that's easier from a GUI.

If you're sensitive about the GUI increasing the memory footprint on your server, you can cut that down a little by using XFCE instead of Gnome.  The XFCE desktop is in the repos; **sudo apt-get install xfce4** to install it.

---

### Post by Off Topic on 2011-05-15
Mine is a file,  media,  and download server.  Before I made the switch to Ubuntu I had a HP Media Smart Server and all my files,  music,  videos, and downloads where served from there.

I have Ubuntu Server loaded with Gnome Core for the GUI,  my secondary PC and Netbook have similar setups,  my main PC has a full Ubuntu Desktop.

---

### Post by wep940 on 2011-05-15
Thank you all for all your great ideas!  I think I'm going to try the Samba thing for running backups to start and probably also the raid idea so I can see how that works in Ubuntu.  I haven't done anything with raid since the early 90's with setting up shadow volumes and shadow sets when more than 1 drive made up the logical drive.  Should be an interesting experiment.

Thanks again for all the great ideas!

---

### Post by Off Topic on 2011-05-15
Im doing things one thing at a time.  Started with Samba,  and file sharing.  All my downloads no matter what it is downloaded onto the server and can share on the local network or accessed over the web.

Backing up the 2 PCs or Netbook dont really matter because all the data is on the server.  The downside is I dont have a way to back up 2+ TB of stuff,  so Ive Dropboxed anything really important.  Anything minorly important I have on an external HDD.

When I can afford to setup a dedicated media server Ill start playing with RAID on a dedicated file server and Ild like to do it all CLI.  With a file server Ill need the redundancy more then I would the space for my audio video files.

Its nice to be able to get to all of my files and media from anywhere,  main reason I have a server.

---

### Post by Irihapeti on 2011-05-15
If your two Ubuntu machines are running the same release, you could set up apt-cacher-ng, which means that you only have to download each package once (with some exceptions, I think, for security updates). It's a bit like having your own repository.

I did it originally because I was on a limited data connection. That's less of an issue at the moment, but I certainly notice the difference in download speeds for the second machine's updates.

---

### Post by Gone fishing on 2011-05-15
NFS and Samba, I'd go for.

Maybe also a fetchmail and an mail server with IMAP then you could  get your mail from any of the client machines.

---

