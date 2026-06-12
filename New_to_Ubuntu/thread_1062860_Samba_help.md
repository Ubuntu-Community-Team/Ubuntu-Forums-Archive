---
title: "Samba help"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2009-02-07
Hello everyone I am new to Ubuntu server and I was asked to set up a samba server for someone. I set up the server using this guide: 
[http://students.ceid.upatras.gr/~mpakoyan/Samba/Build%20a%20Samba%20File%20Server.htm](http://students.ceid.upatras.gr/~mpakoyan/Samba/Build%20a%20Samba%20File%20Server.htm) 

now my question is how do I connect my Ubuntu client to it. I want to make it so that each user can view all shares, but all other shares except their own is read only. Any tips?

---

### Post by superprash2003 on 2009-02-07
well those samba permissions can be setup in your /etc/samba/smb.conf file .. you would also need to add users to the /etc/samba/smbusers file .. you can connect a ubuntu client to a samba share by going to nautilus and typing smb://x.x.x.x ..[http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Indian_Guy101 on 2009-02-07
well how do you edit the file to set the permissions, create a new user and what is nautilus? Thank you for the help

---

### Post by Alterax on 2009-02-07
> **Indian_Guy101 said:**
> Hello everyone I am new to Ubuntu server and I was asked to set up a samba server for someone. I set up the server using this guide....how do I connect my Ubuntu client to it? I want to make it so that each user can view all shares, but all other shares except their own is read only. Any tips?

Well, there are multiple ways (both the curse and the blessing of Linux).  As far as read-write access goes, those permissions should be set on the samba server; the client gets the permissions that the server gives it.  I'm assuming that all of these are set correctly, for brevity's sake.

One way you can go about this would be going to PLACES > CONNECT TO SERVER.  Then change PUBLIC FTP in the dropdown list to WINDOWS SHARE (which is really what Samba is).  Give it the information it needs, and add a bookmark for it.

What may help (and save a lot of duplicated efforts) is to put the shared folders all under one directory on the server, with basic read/no write access.  Then on the individual folders, give the read/write permissions to the student that "owns" it.  Then all you have to do is make ONE bookmark on each student's account on the client to the main shared folder.  Beats having to add a share for each student.

---

### Post by Alterax on 2009-02-07
> **Indian_Guy101 said:**
> well how do you edit the file to set the permissions, create a new user and what is nautilus? Thank you for the help

I'd use NANO to set the permissions if I were working from the server.  Nautilus is the name of the window browser in ubuntu, kind of like Windows' Explorer.exe.

As far as the modifying of the smb.conf file, it's been *many* years since I have used it (since we moved completely to Linux here, I've relied exclusively on sshfs), so before I lead you astray, it may be best for me to brush up on the particulars.

I'll see what I can come up with.

---

### Post by superprash2003 on 2009-02-08
to edit the samba file type sudo gedit /etc/samba/smb.conf .. this tutorial should help you .. [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) .. steps 3,4,5

---

### Post by HermanAB on 2009-02-08
...and if you still cannot get things to work, read this:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

It may help!

Cheers,

Herman

---

### Post by c-m on 2009-02-08
> **superprash2003 said:**
> to edit the samba file type sudo gedit /etc/samba/smb.conf .. this tutorial should help you .. [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) .. steps 3,4,5



I had a look at this, but why don't I get a GUI for sharing drives?

---

