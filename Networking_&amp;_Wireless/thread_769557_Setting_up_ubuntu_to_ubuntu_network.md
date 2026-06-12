---
title: "Setting up ubuntu to ubuntu network"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by LeeU on 2008-04-26
I have Ubuntu 7.10 on a laptop. I just installed 8.04 on a desktop and cannot figure out how to network the two. I assumed they would see each other. I have searched this forum and the Internet and am not able to find this particular problem. Most of them are for Ubuntu and XP, and Internet connections. I can get on the Internet, I just can't connect the two computers. I am using a router, though which each computer also accesses the Internet. I don't have the slightest idea of where to start. Any ideas?

---

### Post by LeeU on 2008-04-26
bump

---

### Post by superprash2003 on 2008-04-26
are the pcs able to ping each other?

---

### Post by LeeU on 2008-04-26
Yes, they can do that.

---

### Post by kgriff on 2008-04-27
Use Synaptic Package Manager to ensure you have openssh-server installed on both computers.
Once you have that going, as least as far as Hardy is concerned, use the Places>Connect to Server to connect to other computer by name or IP.

This link provides additional ssh information.
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by LeeU on 2008-04-27
That works now. Thanks! I just wished I could get it working in GNOME Commander. But I can always open two windows in Places. Thanks again. I thought I would have to share all the directories I wnated to access. I'm guessin that this is safe .... right?

---

### Post by kgriff on 2008-04-27
It should be as secure as your password.  Any time you connect to once computer from the other using Places, you should be required to login.  I believe (if memory serves) that you have several ¨password remember¨ options.  As long as you don´t ever select an option that doesn´t require password entry, anyone that were trying to access your computer would have to enter the correct password.

I´m not sure about using Gnome Commander, but I will look into that.  Presumably, if I can find where the network share is mounted, Gnome Commander should be able to access it.

---

### Post by LeeU on 2008-04-28
> **kgriff said:**
> I´m not sure about using Gnome Commander, but I will look into that.  Presumably, if I can find where the network share is mounted, Gnome Commander should be able to access it.

That would be great. Thanks again.

---

### Post by kgriff on 2008-04-28
I haven´t seen any way to use Gnome Commander with ssh.  However, you can use Gnome Commander if you set up an ftp server on the remote computer.  Use Synaptic to install pure-ftpd and pureadmin or vsftpd.
I haven´t used vsftpd, so I don´t know how it works.

Using pure-ftpd (basic).  For more info see [www.pureftpd.org/](www.pureftpd.org/)
Start pureadmin from terminal.
When you start the program, the server will be running.  Use the PureFTPd menu to stop the server, then configure the server for new users.
*Edit>Preferences>External tab.
  *Set default password file (the default is /etc/pureftpd.passwd.  Not sure why they refer to this as ¨default¨ since you have to enter it yourself)
  *Set default puredb file. (the default is /etc/pureftpd.pdb.  Again, it is initially blank.)
*Close the Preferences window and click on Manage Users.  You will be presented with two pop-up windows.  Click OK to both.
*In the window that opens, click Add new user, then enter a user name and password.
* At this point, you have a virtual user created.  You can edit this user to customize thing such as Home Directory, ftp restrictions, etc.

Once you have a user and password setup, and any other configuration done that you want, go to the PureFTPd menu and Start Server.

Back to the local machine and Gnome Commander.  Use Connections>Remote Server to connect to the remote machine.  You will first have to add a connection to the computer that is now running the ftp server.  This can be done by computer name, or IP.

I believe at pureftpd.org they give instructions for starting the server as a service, if you want to have it running all the time.

Hope this works for you.  It´s working well for me.

---

### Post by LeeU on 2008-04-28
Thanks, I'll have to give it a try. I appreciate the help.

---

