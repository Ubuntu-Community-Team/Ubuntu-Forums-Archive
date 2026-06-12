---
title: "Help with mounting problems."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by rbgCODE on 2008-12-07
Well I have a centOS server that is my media share and it is setup with samba  

\\xshare\other\tv 
or 
\\xshare\other\movies  

has files in it right..

now I have a different server I use as a download server (Ubuntu 8.10 server with sabnzbd), and when a download is complete it moves it to a folder say /home/downloads/complete/tv : I want to mount that TV folder to my centOS machine so that when it moves it to TV, it is actually transferring it over the network.

Sadly my attempts to mount it always fail, and when I tried to smbmount it, it worked great but wouldn't for the life of my delete or create files or copy files to it even after chmod.  Now the CentOS share, if I visit from any windows machine, i can drag and drop files, make new files and delete.  Here is the smb share info from CentOS.

```

[other]
         path = /home
         admin users = rBg
         read only = No
         guest ok = Yes

```

Anyone have any ideas?

---

### Post by cmnorton on 2008-12-09
You should be able to mount the drive from your CentOS system using smbmount. 

Here's a link:

[http://tldp.org/HOWTO/SMB-HOWTO-8.html](http://tldp.org/HOWTO/SMB-HOWTO-8.html)

---

