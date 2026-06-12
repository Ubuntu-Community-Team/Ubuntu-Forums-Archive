---
title: "FTP character set"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by blackliteon on 2007-04-20
Hi all!
Yesterday install Ubuntu 7.04
Great work! Fantastic! In couple of hours my Windows XP partiion goes down!
But I have some FTP trouble: My internet provider has FTP server, i Think it base on Windows, because when I connect to this server by "connect to server" in Ubuntu desktop all folders contained Russian letters shown as
"??? Invalid Unicode sequence ???"
I think character set of folders is CP-1251
What I need to do to make folders names shown good ?

---

### Post by morningboat on 2007-04-20
You should choose one decent international FTP client that supports selecting of the FTP server's character encoding. I'd recommend you to have a try on [CrossFTP]("http://www.crossftp.com"), [FileZilla]("http://filezilla.sourceforge.net/"), or VirgoFTP. Take CrossFTP as an example, you can select the Server's character encoding at Sites -> Site Manager -> Options -> Server Encoding. After configuring of this option, reconnect to the server and refresh, you should be able to see the correct words.

---

### Post by blackliteon on 2007-04-21
So there is no any method to fix this problem in gnome ?

---

### Post by morningboat on 2007-04-23
Yes, I don't think there is any easy way to fix it in the gnome's default browser currently.

---

