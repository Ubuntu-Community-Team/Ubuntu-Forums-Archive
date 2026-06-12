---
title: "Samba Client issue"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by ecfitzgerald on 2008-08-24
I am having an issue reading data from a Thecus NAS.  I am trying to map the shares from the NAS on my Kubuntu box.  I can get the shares mounted in smb4k, and can navigates the directories and see all of the files.  But I cannot use the files.

If I try to open pictures the viewer opens, no erros, but the picture reports 0x0 for size.  I cannot copy the files to the Kubuntu box.  But I can see and use the files from my Windows laptop, and copy the files.  I think I must have a setting slightly wrong.

Also, how would I try to map the shares without smb4k?

---

### Post by bab1 on 2008-08-24
First off I'm not a Kubuntu user.  I use Ubuntu and Samba.  Samba is not used as a client of a Windows share.  I assume that smbk is the client that used to talk to the Windows server.  Yes there is a server built into the Windows share.  

But I believe your problem is a permissions problem.  Is your kubuntu user in the smbusers database?  Is it EXACTLY like the Kubuntu users?  Is there a NAS user database?  What are the permissions on the files in the share?

Hope this helps

---

### Post by ecfitzgerald on 2008-08-24
The error I get is "cannot read" the file I try to copy.

The server is a linux derived NAS, not Windows.  I have it set as a public browsable folder in the basic config page the NAS provides.  I don't have any users setup on the NAS, and my windows machines work fine.

I have tried CIFS and SMBFS, both have identital symptoms.

In smb4k, which is the KDE samba client gui, there is a user it tries to use.  user 1000 group 1000.  It won't take blanks, or guest.

---

### Post by ecfitzgerald on 2008-08-24
Update:

I used Konquor with smb://ipaddress/pictures

And was able to view and copy, using default smb4k settings, so it looks like the issue is with Dolphin.

---

