---
title: "Sama Stuff...."
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by tophat2445 on 2007-02-22
I want to access a samba share that is on my ubuntu server.

I can access this share from my windows systems.
I can't access this share from my ubuntu systems.

I need to be able to read/write to this share from multiple computers, some ubuntu some windows. 

again..I can read/write to this share from my windows systems, but I can't from my Ubuntu systems.

Can you help me?

Kenny

---

### Post by gradedcheese on 2007-02-22
Is the account that you're using (on the Ubuntu client side) configured in samba?  It may be that the Windows account is configured but you're using a different account in the other Ubuntu PCs.  If you don't know what I mean (ie: smbpasswd and smb.conf), please take a quick look at [this little guide I wrote]("http://andrey.thedotcommune.com/samba.html")

---

### Post by tophat2445 on 2007-02-22
Okej, heres the deal. 

I have 4 pc's. 1 server

2 pc's are running windows XP.
2 pc's are running Ubuntu 6.06 LTS

My server is running Ubuntu 6.06 LTS.

In my server, I am trying to share one drive (hdb1), which I have named [KSN] accross my entire network. 
I need to be able to read/write to this drive from all of my other pc's at any given moment. 

I can read/write to KSN from all of my Windows machines, but I can't from my Ubuntu machines.

When I go to Places->Network Servers, I see: HOME1, HOME2,KSN

when I'm in my ubuntu macheines, I click on KSN, nothing happens...it dosn't open a share folder or anything. Thats what I need to see, 

I need to accsess (hdb1)[KSN] on my server, from my ubuntu machines.

How can I do this.

I've already confiugred all of the smbpasswd and smb.conf to allow the user kenny to read and write to the share. this works on windows. not ubuntu

please help,
Kenny

---

### Post by gradedcheese on 2007-02-22
and, from these Ubuntu clients, when you're testing you definitely are the user 'kenny'?

---

### Post by tophat2445 on 2007-02-22
Yes. i am kenny on all these machines

---

### Post by gradedcheese on 2007-02-22
hmm... can you post the server's /etc/samba/smb.conf file please?

---

### Post by tophat2445 on 2007-02-23
[global]
 ;general server settings
 netbios name = KSN
 serverstring = 
 workgroup = KSN
 announce version = 5.0
 socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
username map = /etc/samba/smbusers
name resolve order = host wins bcast

wins support = no

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

[print$]
 path = /var/lib/samba/printers
 browsable = yes
 guest = ok
 write list = root
 create mask = 0664
 directory mask = 0775

[printers]
 path = /tmp
 printable = yes
 guest ok = yes
 browsable = no

[hdb1]
 path = /media/hdb1
 browsable = yes
 readonly = no
 guest ok = no
 create mask = 0644
 directory mask = 0755
 force user = kenny

---

### Post by tophat2445 on 2007-02-24
Okej, I've made this a little easier to follow....

I've removed all of my pcs but one from the server...

this pc is dual booted with Ubuntu/Windoze XP

with XP I can do everthing I want to the drive(hdb1) on my ubuntu server!

I can't get ubuntu to even show the drive...although the server (KSN) is shown..

---

### Post by gradedcheese on 2007-02-24
From what I've been reading, it looks like Nautilus doesn't handle Samba (or Windows) shares very well.  Your best bet, for the Linux clients, is to mount the drives normally (using mount, 'smbfs' as the file system) or to share the data using a more Linux-native method like NFS.  NFS and SFTP shares seem to work really well in Nautilus for GUI browsing.  Alternately, the smbfs mount method will mount the drives like a normal disk as the user would expect (similar to "map network drive" in Windows).  Sorry that I can't be of much more help :(

---

### Post by tophat2445 on 2007-02-24
How would I go about using the smbfs mount method? ("map network drive")

thanks alot for all your help so far...

Kenny

---

### Post by dmizer on 2007-02-25
use cifs instead.  to manually mount from the cli, create a directory in your /media folder called something unique to your server.  currently your smb.conf file has KSN as both the server name as well as the domain name.  so, you can create a directory in /media called KSN ...
```
sudo mkdir /media/KSN
```

here's a suggested cifs manual mount command:
```
sudo mount -t cifs //KSN/KSN /media/KSN -o username=***,password=***,iocharset=utf8,file_mode=0777,dir_mode=0777
```

this *should* give you r/w access to your samba shares, as well as provide you with an icon on the desktop.

for more information, and alternative configurations (including fstab) see the second link in my sig.

---

### Post by gradedcheese on 2007-02-25
Excellent!  I was waiting for him to post that information.  Very good stuff.

---

