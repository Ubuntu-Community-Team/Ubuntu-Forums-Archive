---
title: "samba - share only home directories?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by rolfbeethoven on 2007-06-22
Can one only share the directories off of the home directory with Samba???  I know that isn't right but I can't get Samba set up to access any share that isn't off of my home directory.

Here's my /etc/samba/smb.conf file

--------------------------------------------
workgroup = NOTMSHOME
netbios name = Samba
encrypt passwords = yes

[homes]
read only = no
browseable = no

[fileserver1]
path = /home/fileserver1
browseable = yes
read only = no

[fileserver2]
path = /storage/fileserver2
browseable = yes
read only = no
--------------------------------------------

I have identical user and pswd set up in XP, Ubuntu Feisty and SMB.

fileserver1 and fileserver2 are owned by rolf:rolf and have 777 privledges.   (/storage is also rolf:rolf, 777)

I can see all three shares in XP (via Network Neighborhood) but, I can't get into fileserver2.  Clicking on rolf or fileserver1 brings me directly into the respective folder.  Clicking on fileserver2 gets me a user/pswd prompt and then after inputting username and passwd I get another user/pswd prompt where the username has the netbios name added in front of it (SAMBA\rolf).  I put the pswd in again, but get directed to the same 2nd log in screen indefinitely.

/home is on the same partition as / which only has 10 Gig.
/storage is the mount point for another partition with 185 Gig.  I need to connect to it.

I've reviewed the smb.conf file and several tutorials and I can't find anyone who has had this same problem.   Hopefully it will be something simple (It usually is right?).

What can I do to locate the error?

Thanks for your expertise.

---

### Post by dmizer on 2007-06-23
use the tutorial located in the first link of my sig.

---

