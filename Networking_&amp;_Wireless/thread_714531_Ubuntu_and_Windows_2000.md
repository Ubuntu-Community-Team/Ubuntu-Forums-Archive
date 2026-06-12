---
title: "Ubuntu and Windows 2000"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by starkriverfell on 2008-03-03
I have shared a folder on my Win 2008 professional pc.  From Ubuntu I can see the PC and see the shared folder, but cannot access the folder itself.  I have created a username on the Windows PC but still cannot access the files within the shared folder.  Ubuntu asks for a username, domain name (I am only on a workgroup setup) and a password, but no password was set on the win 2000 pc.

---

### Post by jrusso2 on 2008-03-03
Maybe you should set one on the windows pc.  I have Windows 2000 server here and it works.

I use smb4k for the samba client.  This always seems to work.

Use the windows user name and password when accessing the share on the windows 2000 box.

---

### Post by Eiríkr on 2008-03-04
And as I've found researching the issues for [thread=705983]this thread[/thread], no-password Windows accounts present particular problems for Samba access.  Reading around on the mailing lists, it sounds like a combination of a change in the Samba client codebase in the shift from smbfs to cifs, and changes in how Windows responds to share client requests.  Your best bet is to set a password on the Windows account and then use that username / password combination, as noted by jrusso2.  It can be even more convenient when the Win and Lin usernames and passwords match.  

HTH,

Eiríkr

---

