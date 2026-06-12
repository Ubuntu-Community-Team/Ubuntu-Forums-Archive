---
title: "files read only over SFTP"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-01-10
I'm running a brand new install of ubuntu 8.10 64.  On 8.04 I was able to connect to the server at work and edit php files thru gedit.  It was incredibly straightforward:  bookmark the location on the server, edit, save, done.

Now, whenever I try to edit a file remotely it opens as read only.

I'm logging in as root.  It's not a permissions issue (i don't think).  I've been reading up...may have something to do with gvfs?

Anybody know about this or know of a workaround?

---

### Post by jman6495 on 2009-01-11
I may Have Missinturpreted You But :
If You Are Logging On To YOUR Pc As Root That Will Not Give you Full Access To A Remote FTP Server.
What Are You Logged On As On The FTP Server?
If Not Just Save The File To Your Pc Then Re Upload it To The FTP Server!

Hope This Helps
         JMan6495

---

### Post by ja660k on 2009-01-11
sftp is secure file transfer protocol it doesnt really allow for editing of files, its main purpose is to put/get files off the server

ssh into your server andthen try it. try using a terminal text editor too.
like vim ... all the cool kids use it

as for the permission do ls -l of the dir and see if there is any changes from a file you have edited and one that you have not.

i hope it helps?

---

