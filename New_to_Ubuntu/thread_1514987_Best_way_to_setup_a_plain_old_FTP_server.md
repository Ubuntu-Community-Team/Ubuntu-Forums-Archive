---
title: "Best way to setup a plain old FTP server?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by diablo75 on 2010-06-21
I want to host an FTP server from a computer I have (and specifically, I don't want to use any encryption/SSH/SFTP).  I'm trying to do an experiment with my Nexus One Android phone because I like to use this program called AndFTP to connect via SSH to this computer and download files over the wireless LAN but the downstream is always slow (usually no faster than about 70 Kb per second).  Strangely I am able to upload at almost ten times that speed, I am also able to download files from the web via HTTP at about the same speed too, so I'm trying to find an alternative way to download files from this computer at a faster rate.  If found, I'll never connect to a computer with a USB cable again (if I can help it).

---

### Post by bodhi.zazen on 2010-06-21
[https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)

---

### Post by -kg- on 2010-06-21
@ bodhi.zazen

You beat me to it by ***_that_ _much_!***:p

---

### Post by bodhi.zazen on 2010-06-21
> **-kg- said:**
> @ bodhi.zazen

You beat me to it by ***_that_ _much_!***:p

LOL, I was going to go on an on re: security and FTP , but I decided to forgo the obvious as the OP seems interested in speed over security, lol.

---

### Post by 11hjpphty76lkjj on 2010-06-22
I personally would recommend that you look into installing webmin if you are going to be setting up a server. It makes configuration a LOT easier, IMV.

Plus, you can do a lot of cool things with it.

---

### Post by lkraemer on 2010-06-23
You might also try vsftp.
[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

And for your Client run Filezilla.  Works wonderful.

If you want a copy of my document of how I did it PM me.

lk

---

