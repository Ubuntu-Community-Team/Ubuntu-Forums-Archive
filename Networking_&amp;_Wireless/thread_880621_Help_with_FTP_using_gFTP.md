---
title: "Help with FTP using gFTP"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by stoneybroke on 2008-08-05
Hi, Can anyone tell me what I am doing wrong here, I installed gftp (and have Filezilla) I can connect to other FTP Internet sites without any problem at all but when I enter a friends IP address and port to connect to him I can't do it. He has the same problem trying to connect to me, so can anyone please tell me what we need to do to connect to each other.

Thanks,

---

### Post by nbayiha on 2008-08-05
Near the place where you put your password you should change (FTP) who is the default one by local or whatever you are trying to do. 
For example i use to put there ssh cause i need to get to my school server ... I hope you understand what i mean .

---

### Post by tturrisi on 2008-08-05
gFTP is an FTP Client that is used to connect to FTP Servers.  You and friend must both be running FTP Servers to be able to connect to each other using an FTP Client like gFTP.  Do you have the Filezilla Server?

If have the server installed, set the FTP Listen port to a port other than 21 because most ISPs filter port 21 to prevent customers from running FTP Servers.  And if use a router use the router Port Forwarding to forward FTP requests to that port at the LAN IP address of the comp with the server..

---

### Post by stoneybroke on 2008-08-05
Thanks to you all for the reply I have Filezilla, gFTP and vsftpd all installed so as tturrisi suggests we will try a different port than 21 and see what happens this could be our problem as we are both using that port, we will also use ssh as you suggest nbayiha.

I will let you know the results,
Thanks again everyone.

---

### Post by tturrisi on 2008-08-06
Well, if use ssh you will need the sshd installed and running.  No need for an ftp server if use sshd.  The default sshd port is 22.  For security, use a port like 3022 or similar, and use the router port forwarding.  That way, whem script kiddies do bulk scans over the wan your sshd won't show up in a common port scan.

---

### Post by miegiel on 2008-08-06
Try connecting to your own ftp server (use localhost and/or your ip-address).

If you are directly connected to the internet (your ip-address doesn't start with 10. or 192.168.), you might want to check if you firewall accepts traffic on the port you are serving ftp on.

If you aren't directly connected to the internet (your ip-address starts with 10. or 192.168.), then check if your router is forwarding the port to your machine.

---

