---
title: "SAMBA Problem"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by putz3000 on 2008-10-04
I have limited Samba experience and it has been a while since the last install plus I wanted to make some changes - not a good recipe for success.  Anyhow, I want a general shared storage location and I want multiple computers to have access with full control.  But I did not want guest access.  I did all this command line and suspect I am missing something basic but not basic enough for me to grab.

Here is what I did:

1) Built my own smb.conf file which currently reads:

[global]
 workgroup = WORKGROUP
 map to guest = Bad User
 netbios name = Evo

[storage]
 comment = Data Storage
 path = /data
 read only = NO
 force user = home
 force group = storage
 guest ok = No
 nt acl support = NO

2) sudo groupadd storage
3) sudo useradd -m home
4) sudo passwd home
5) sudo mkdir /data
6) sudo chmod 770 /data (I wanted user and group to have full but not other)

7)sudo chown -R home:storage /data
8) sudo chmod -R ug+rwxs /data
9) sudo /etc/init.d/samba restart

My server currently shows up online and so does my shared folder.  When I try to connect to the shared folder I am correctly prompted for my user login and password but when I enter it the authentication is rejected.  I have redone the "passwd" in case I screwed up the password the first time, but I still have the same problem.  If I change the "guest ok = no" to "guest ok = yes" then I can get straight into the shared folder...but that is not what I want.

The one thing that I am not sure about is under windows when I go to networking an double click on my server name, the shared folder that shows up is called "storage".  I have gone back through the commands I executed and do not see where I actually created anything called storage with the exception of "[storage]" in my smb.conf file.  I assume that is where it came from?  Plus if I allow guest logons then this "storage" location does not seem to be a problem.  

Is anyone able to easily see what I have missed/screwed up?  I thought once about adding "valid users = %s" to the smb.conf file but the more I think about it, the more I do not think that is what will fix this.

---

### Post by putz3000 on 2008-10-12
Since it does not appear that there are many folks up to speed on SAMBA, does anyone know where a samba based forum is?  Any forums that have a stronger SAMBA background/presance?

---

### Post by gpsmikey on 2008-10-12
Being new to the Samba game myself, my best suggestion is to check out the following three links:
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/index.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/index.html)
[http://us3.samba.org/samba/docs/man/Samba-Guide/](http://us3.samba.org/samba/docs/man/Samba-Guide/)

The first one is the pdf version of the "Samba 3 by example" book - you snoop through it and find one of the examples that is like what you want to do then he has the config information there on how to set it up.  Very good book (I have a hard copy I purchased).  The O'Reilly Samba book (3rd edition) is pretty good too.

Edit - just noticed that you didn't indicate you had used the 
sudo smbpasswd -a username to add that user to the Samba password database - you need to do that so Samba knows who you are in addition to linux.


mikey

---

### Post by gpsmikey on 2008-10-12
Sigh - said it hadn't posted it with a proxy error - it lied.  Sorry for double post.

mikey

---

