---
title: "how to connect from Windows to Ubuntu"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by lulon on 2007-12-11
Hi!

This is my situation:

I have one computer with Ubuntu. In this computer I have an application with a Web Server, an Application Server and a DataBase.

I have another computer, a laptop, with Windows XP.

And now, this is my question:

How can I connect to the computer (with Ubuntu) from the laptop (with Windows XP) for doing operations like these: delete, create, modify files from the Application Server, stop and start the Web Server, etc.?

I hope that I have explain well, I'm not an English speaker...

Thanks a lot.

---

### Post by cemptor on 2007-12-11
Install Samba on the Linux machine (can be found using synaptic)
Add the folders you want to share using System>Administration>Shared Folders
Add a Samba username and password using smbpasswd
Ensure that Samba is running (default start)
Ensure thar Firestarter allows connections from your Windows machine
You can then connect to your Linux machine from Windows. Will ask you for your username and password.

---

### Post by mpokrywka on 2007-12-11
I think ssh server would be a better solution.
There would be no problem with username/password
and you don't need specify which folder to share and what permissions.
On ubuntu install openssh-server.
On windows use free [**PuTTY**]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") ssh client to log in to your server and start/stop services and maintenance.
To transfer/manage files you can use [**WinSCP**]("http://winscp.net/eng/download.php").

---

