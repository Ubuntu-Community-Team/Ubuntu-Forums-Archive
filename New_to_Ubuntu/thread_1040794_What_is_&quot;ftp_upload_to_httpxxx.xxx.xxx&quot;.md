---
title: "What is &quot;ftp upload to http://xxx.xxx.xxx&quot;?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by paker on 2009-01-15
I was told to ftp upload files to [http://xxx.xxx.xxx](http://xxx.xxx.xxx).
Exactly what does "ftp upload to http" mean? I searched this forum but all questions were too advanced for me. I tried ftp in terminal, but I don't know what command to use after ftp. The files are in my hard disk.

PS: If this matters, I am setting up a forum. I registered a domain name. I am using friend's server space to host the forum. My friend did all the work and told me to "ftp upload phpbb files to http://xxx.xxx.xxx" I know I can ask him again, but I gotta do something. Once I am done with uploading, he is going to pretty-up the place for me. So this uploading is the only thing I am going to do. Please help.

8.04 32 bit

---

### Post by spiderbatdad on 2009-01-15
generally this is done with a user account like:```
sftp user@serverdomain.com
```
then if you have the publickey or password you will be logged in, and get a prompt
stfp>

you can the use pwd to see where you are and cd to navigate. the put command will upload the file from pwd of your machine or use complete paths.

```
put filename.php
```

lets say I had a directory called MyFavs in my Music folder full of great tunes. I might do:
```
 put /home/spiderbatdad/Music/MyFavs/* 
```

---

### Post by GregA on 2009-01-15
Many people use a graphic ftp client to upload files to a ftp server - - a commonly used one is gftp - which is available via Synaptic or by using this code in a terminal:  sudo apt-get install gftp

---

### Post by spiderbatdad on 2009-01-15
> **GregA said:**
> Many people use a graphic ftp client to upload files to a ftp server - - a commonly used one is gftp - which is available via Synaptic or by using this code in a terminal:  sudo apt-get install gftp
I forgot about that...lol...Also look under your Places menu: "connect to server" is a graphical sftp client.

---

### Post by the.phantom on 2009-01-16
another easy to use ftp client is
fireftp a plug in for firefox ;-D

---

### Post by Paqman on 2009-01-16
> **spiderbatdad said:**
> I forgot about that...lol...Also look under your Places menu: "connect to server" is a graphical sftp client.

^^This.

Nautilus does a perfectly good job of ftp transfers. I find it really handy to be able to bookmark the server.

---

### Post by spcwingo on 2009-01-16
You can also try filezilla.  It's also in the repos.  I used this one on Windows before I made the switch to Ubuntu.  I have never had any problems with either the Windows or Linux versions.

---

### Post by paker on 2009-01-18
Thanks. I found gFTP easy to use. Using it, I uploaded files to [http://www.xxx.com](http://www.xxx.com). Please help me with the next step.

I have to open web browser (Firefox) at [http://www.xxx.com](http://www.xxx.com) and put the cursor on one of the uploaded files. How can I access the files? Where are the files?
Thanks.

---

