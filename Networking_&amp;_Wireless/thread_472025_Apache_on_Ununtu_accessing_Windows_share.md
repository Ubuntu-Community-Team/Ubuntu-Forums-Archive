---
title: "Apache on Ununtu accessing Windows share"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by corman420 on 2007-06-12
I've tried quite a few things to get this to work but I have no idea where to start.

Basically I have Apache2 installed on Ubuntu and I want to map a network drive FROM my Windows Vista machine to my Apache installation on my Ubuntu machine.

I want to be able to type in [www.myserver.com/downloads/](www.myserver.com/downloads/) and the /downloads directory will point to my Windows Vista share.

Can it be done?

All I need to know is how to get my windows share into my apache installation - the rest I can figure out.. I think.. lol

---

### Post by stchman on 2007-06-12
> **corman420 said:**
> I've tried quite a few things to get this to work but I have no idea where to start.

Basically I have Apache2 installed on Ubuntu and I want to map a network drive FROM my Windows Vista machine to my Apache installation on my Ubuntu machine.

I want to be able to type in [www.myserver.com/downloads/](www.myserver.com/downloads/) and the /downloads directory will point to my Windows Vista share.

Can it be done?

All I need to know is how to get my windows share into my apache installation - the rest I can figure out.. I think.. lol

Have to use Samba.  Install Samba and share the Apache folder (usually /var/www).

---

### Post by corman420 on 2007-06-12
How is Samba going to Map a windows share to a web server though?

---

### Post by stchman on 2007-06-13
> **corman420 said:**
> How is Samba going to Map a windows share to a web server though?

So you want to be able to access your files through the internet.

I was assuming that your machine that has Apache and your Windows machine were on the same network.  My bad.

---

### Post by dmizer on 2007-06-13
samba is a protocol designed for local network file sharing only.  you should NOT use it for sharing files across the web.

if you want to share files across the web, you should use a protocol designed for sharing files across the web ... like ftp, or better yet sftp or ftps.  take a look at the third link in my sig for how to configure a ftp server.

---

### Post by corman420 on 2007-06-14
No, my Ubuntu machine and Windows machine are on the same network.  I know about FTP, but thats not what Im trying to do.  I want to have my Apache server setup with a Virtual directory pointing to a windows share.

---

