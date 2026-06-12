---
title: "Can I Torrent without Trackers"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-23
Is there any way to torrent without using a tracker? I want to send a file from my desktop to my laptop, but I don't want any one else to be able to download the file either.

---

### Post by Rolcol on 2009-01-23
Not with the default Transmission application.  You will need a client with DHT, I think.  In other words, yes.

---

### Post by emarkd on 2009-01-23
I don't really know the answer to your question, except to offer that there are easier ways to transfer a file between two computers.  scp, for instance, is very quick and easy to use.  Or you could go with samba or sshfs...

---

### Post by Cypher on 2009-01-23
If your laptop and desktop are on the same network, you can use FTP, SFTP, SCP and so on to easily transfer the files.

If the machines are connected through the Internet, then you can still use SFTP/SCP over SSH through the Internet.

This is going to be a far more straightforward solution than torrenting.

Another alternate to avoid having to setup anything at all is to check out [Dropbox]("http://getdropbox.com"). YOu install the daemon on your laptop and desktop. A directory will be created for you automatically, dump a file in that directory from your laptop and it will be automatically created for you on your desktop and vice-versa.

Since you have to login to access the files, you can use this to transfer the files..

---

### Post by markharding557 on 2009-01-23
you could transfer a file from one computer to another using an internet messenger prog like pidgin,you will need to install encryption if you want to keep it secure

---

### Post by cb951303 on 2009-01-23
> **Rolcol said:**
> Not with the default Transmission application.  You will need a client with DHT, I think.  In other words, yes.

yep, there is a bug ticket opened 3 years ago about DHT support in transmission but still they keep ignoring it.

---

### Post by Sup3r3g0 on 2009-01-24
Thanks. What if I want to send a very large file (around 3 gigs) to multiple people? How would I do that? 

I use Ktorrent and deluge.

---

### Post by Sup3r3g0 on 2009-01-24
bump

---

### Post by cb951303 on 2009-01-24
3gigs is not large for torrent. just google for creating torrents. there are millions of documents.

---

### Post by Sup3r3g0 on 2009-01-24
I googled it and all I've seen include using a tracker. I don't want other people (besides the ones I'm giving it to) to be able to download the file. So how do I do it?

Thanks for all your help.

---

### Post by Big_astur on 2009-01-24
Can't you create a FTP server on your computer and make that only some IPs (your friends ones) connect to it using the FTP client to download the file?

---

### Post by DirtDawg on 2009-01-24
If the computers in question are on the same network and all run Linux, you may want to check out [Giver]("http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/"). It's a simple way to share files and it's in the repos.

---

### Post by cb951303 on 2009-01-24
> **Sup3r3g0 said:**
> I googled it and all I've seen include using a tracker. I don't want other people (besides the ones I'm giving it to) to be able to download the file. So how do I do it?

Thanks for all your help.

well, torrent is not designed for what you're asking. it's file *sharing* protocol. your best bet is to fire up your own private tracker.

---

### Post by billgoldberg on 2009-01-24
Just install a ftp server.

It's easier.

---

### Post by 3rdalbum on 2009-01-24
Break the file up into 3 parts and use a service like Megaupload. ([www.megaupload.com](www.megaupload.com))  At the end of your upload, it gives you a URL to the file you uploaded; just send this URL to the people who need to recieve the file.

---

### Post by Efros on 2009-01-24
If you install webmin, you not only get a really great browser interface for configuring many aspects of Ubuntu but it also has a facility to upload and download files from the Ubuntu box.

---

### Post by Sup3r3g0 on 2009-01-24
> **billgoldberg said:**
> Just install a ftp server.

It's easier.

What ftp server do you reccomend? Like proftp? Something with a GUI would be nice. 

Are FTPs faster than torrents? I thought that torrents were faster because it shared peoples bandwith, and would get faster as I send it to more people.

---

### Post by Cypher on 2009-01-24
Proftp is a nice FTP server indeed and you don't need a GUI for the server. Your users can use any FTP client they like to access your server.

FTP is obviously limited by your bandwidth and is a one-to-one connection, so each individual will be downloading the file one at a time. With P2P, you get bits and pieces from lots of other people that have the same file and this makes it easier to get large files in shorter amounts of time.

---

### Post by Sup3r3g0 on 2009-01-24
Okay thanks. I think for now, I'll stick with P2P, but definately look into ftps for later on.

---

