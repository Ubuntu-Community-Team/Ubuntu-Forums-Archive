---
title: "Browsing Windows Domain"
date: 2005-06-23
forum: Networking &amp; Wireless
---

### Post by CrippledFsck on 2005-06-23
I have had Ubuntu Hoary installed for approximately 4 months. My Ubuntu username and password are the same as my Windows2000 domain username and password. Up until about a week ago I could select Places -> Network Servers and once I clicked on the Windows Network Icon I would get a listing of all the computers in the domain. Double clicking on the computer would show me the shares and double clicking on a share would prompt me for username, domainname, and password, i.e. everthing worked perfectly. 

I installed linpopup and everything continued to work. Shortly after that I installed samba so that I could share directories to windows clients. Once I did this, I am no longer getting any computers listed in the "network places" dialog and the gnome foot icon does not even animate like it is trying to locate any other computers. I can still access windows shares using smbclient from the command line. 

I have uninstalled linpopup and samba server but the "network places" dialog is still blank. I am an advanced user and have used LInux as my primary desktop at home for more than 3 years.

Any help would be greatly apprieciated.

---

### Post by intangible on 2005-06-27
I have a bit of experience working with samba, what does your /etc/samba/smb.conf look like?

samba-common still uses that config file, installing samba (the server) may have changed some settings for you.

---

