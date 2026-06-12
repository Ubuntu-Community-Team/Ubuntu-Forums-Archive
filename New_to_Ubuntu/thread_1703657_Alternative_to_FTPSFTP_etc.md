---
title: "Alternative to FTP/SFTP etc?"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by thegreatlion on 2011-03-09
I'm having a ubuntu server in my basement, I got a website etc, and I'm currently testing FTP, and I know it's insecure, so I want something secure. SFTP didn't just work..

Criteria:

[LIST=1]
[*]Windows users can download/upload files to it.
[*]Somewhat easy to configure
[*]I don't relly want a GUI. CLI is good enough.
[/LIST]
I want to know if there is any good and secure alternative to FTP and SFTP. I will use it as a online file server (not only on my LAN).

---

### Post by turtle153 on 2011-03-09
Tried SSH?

---

### Post by thegreatlion on 2011-03-09
> **turtle153 said:**
> Tried SSH?

I got a openssh server installed, but I dont know how to download and upload files from the windows client..

You know how?

Thanks,

---

### Post by GWBouge on 2011-03-09
Check out [WinSCP]("http://winscp.net/eng/index.php") and [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")

---

### Post by thegreatlion on 2011-03-09
> **GWBouge said:**
> Check out [WinSCP]("http://winscp.net/eng/index.php") and [PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")

I got PuTTY on my machine at work, and I'm tunneling my http with it.

But how on earth do I copy files?

---

### Post by bodhi.zazen on 2011-03-09
You use a program called "winscp"

[http://winscp.net/](http://winscp.net/)

---

### Post by thegreatlion on 2011-03-09
> **bodhi.zazen said:**
> You use a program called "winscp"

[http://winscp.net/](http://winscp.net/)

How can I limit so i can only view my /opt/lampp/upload directory?

Is it possible to use this in a cmd?

---

### Post by GWBouge on 2011-03-09
> **thegreatlion said:**
> How can I limit so i can only view my /opt/lampp/upload directory?

I think (I'm no expert) you'll have to jail/chroot users on the server side, so it won't allow them access to various parts of the filesystem.

> **thegreatlion said:**
> Is it possible to use this in a cmd?

If you're looking for just a one-liner (I assumed more of a 'client'), then you might be looking for one of PuTTY's tools called [PSCP]("http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter5.html").  You can find it in the downloads page if you didn't download the archive with all the tools included.

---

### Post by thegreatlion on 2011-03-09
> **GWBouge said:**
> I think (I'm no expert) you'll have to jail/chroot users on the server side, so it won't allow them access to various parts of the filesystem.



If you're looking for just a one-liner (I assumed more of a 'client'), then you might be looking for one of PuTTY's tools called [PSCP]("http://the.earth.li/%7Esgtatham/putty/0.60/htmldoc/Chapter5.html").  You can find it in the downloads page if you didn't download the archive with all the tools included.

I tried the PSCP but it failed to connect to my server, and got a fatal error :S

---

### Post by GWBouge on 2011-03-09
Hmm ... ok, I'll ask the obvious ... are you sure the server is allowing connections on port 22?

---

### Post by thegreatlion on 2011-03-09
> **GWBouge said:**
> Hmm ... ok, I'll ask the obvious ... are you sure the server is allowing connections on port 22?

My SSH-server is running on port 6923.. :P

---

### Post by thegreatlion on 2011-03-09
pscp.exe -p myport lion@TheIP:"Full_path_to_File"

Got this error:

More than one remote source not supported.

---

### Post by GWBouge on 2011-03-09
> **thegreatlion said:**
> pscp.exe -p myport lion@TheIP:"Full_path_to_File"

```
Options:
  -p        preserve file attributes
  -P port   connect to specified port

```

Capital 'P' ?  (I'm just guessing here, lol ... I'm not all too familiar with PSCP, was just hoping it was a simple, obvious fix  =oD )

---

### Post by matt_symes on 2011-03-09
Hi

> SFTP didn't just work..

Just interested, what were your issues with sftp ?

Kind regards

---

### Post by bodhi.zazen on 2011-03-09
> **thegreatlion said:**
> My SSH-server is running on port 6923.. :P

Change back to port 22 and use keys (and disable passwords) for your ssh server.

[http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

You will need to import the keys to putty (see the link on the  above page).

---

### Post by thegreatlion on 2011-03-12
> **matt_symes said:**
> Hi



Just interested, what were your issues with sftp ?

Kind regards

I used vsftpd and tried to configure it, so it would be secure, but I got a lot errors. When I googled them there was nothing to find.

---

### Post by thegreatlion on 2011-03-12
> **GWBouge said:**
> ```
Options:
  -p        preserve file attributes
  -P port   connect to specified port

```Capital 'P' ?  (I'm just guessing here, lol ... I'm not all too familiar with PSCP, was just hoping it was a simple, obvious fix  =oD )

Thanks, I'm just too used to ssh I forgot I was really working with remote cp. :)

---

