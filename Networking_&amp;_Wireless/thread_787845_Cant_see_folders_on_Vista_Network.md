---
title: "Cant see folders on Vista Network"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by shadow1983 on 2008-05-09
I have just installed the latest version of ubuntu and i most say its brilliant, much better then Windows that i have been using for years. anyway my problem, i am able to view files on windows xp and even transfer files from one computer to my laptop running ubuntu over the network, but when i try and access my main computer which is running vista im unable to see any files which are being shared also vista is unable to transfer files to my laptop but is able to see them. I have downloaded samba, but when i click on it in system-admin it keeps crashing. Im completely new to linux so im probably doing something noobish, any help would be much appreciated thanks in advance Chris.

---

### Post by njparton on 2008-05-09
Ensure that all 3 computers have the same workgroup name, the same username and password.  Remember that linux is case sensitive so bob and Bob are not the same.
 
If that still doesn't work please post your /etc/samba/smb.conf file.

---

### Post by shadow1983 on 2008-05-09
I tried with having all the same names and passwords , that didnt seem to work. but here is a copy of the smb.conf file

[Music]
path = /home/chris/Music
available = yes
browsable = yes
public = yes
writable = no

[global]
wins support = no


.

---

### Post by njparton on 2008-05-09
That's it?

That's not the one that's usually installed by default - have you played around with it?

It should have a lot more generic entries at the top.  Did you install samba from the repositories?

---

