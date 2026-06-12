---
title: "Establishing network connectivity between two computers"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by formyfriend on 2006-10-17
Hello,

I like to post a query on Networking. 

Is it possible to connect two computers directly through the Ethernet, back to back and establish connectivity. 

I tried the same : 

Set the IP Address of Both the Machines as 192.168.0.1 and 192.168.0.2, though Gateway is not needed I set them to common values, Primary and Secondary name servers are also put the same. 

Is it possible to establish the connection. 

The machines are not ping'ing also. 

In the Windows XP i can see limited connectivity. But unable to transfer any files or anything.

Or do I need to use nfs or something like that ?

Regards,

       Dilip

---

### Post by wieman01 on 2006-10-17
The best option is to buy yourself a cheap hub (~20 USD) and connect the computers this way. 

Second best option is to get hold of a so-called cross-over cable so that you can connect both computers directly. In that case you don't need a router and simply have to assign the same IP range. That's all.

But it feels nice to own a hub. :-)

---

### Post by borobudur on 2006-10-17
If you connected the two computers what programm do you recommend to copy files from one to the other pc?  
The best what I got is over the termial with ftp. Is that the only way??
Regards from Zurich
borobodur

---

### Post by mips on 2006-10-17
Depends, if they are both linux use NFS.
If one is Windows then look at Samba.
Another option is via SSH

---

### Post by borobudur on 2006-10-17
it's between two ubuntu computers. 

I set the directory on the server side to be shared with nts but I can't access it on the client. What shall I use there?

---

### Post by mips on 2006-10-18
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)

---

