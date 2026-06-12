---
title: "Samba problem with Actiontec MI1424wr router"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by richmarchman66 on 2007-06-07
Hello all

I'm having a big problem here with my samba file shares.  This is on ubuntu 7.04.  I have had samba setup to share my media with my other pcs for over a year working perfectly...now that I'm moved to a new ISP (verizon fios) I have no connection to the samba shares from my wireless pcs although I have no other connection issues!  The wireless pcs previously had no problem.

My wired pcs (attached to the router) can still access the shares with no problem.

Static leases for the 2 machines
Server - 192.168.1.4
Wireless client (windowsxp)- 192.168.1.7
Both on the same subnet.

Why all of a sudden with this new router can I not connect to my samba shares?  There are no firewall rules on the router currently.

Samba log for 192.168.1.7 shows no connection attempts since I switched to the new router.

Here's the pertinent (i think) part of smb.conf


[global]
   workgroup = home 
   server string = Ubuntu-Server 
   log file = /var/log/samba/log.%m
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true


When I attempt to connect (192.168.1.4/movies) from the client it hangs for over a minute then prompts username/password but will not connect.

Please give me a hand...and let me know any more info you might need!

Thanks a ton
Rich

---

### Post by richmarchman66 on 2007-06-07
Another piece of information that I should have included with the 1st post. 

I can ping the fileserver machine from the wireless client and vice-versa.  Both by static ip and by machine name.

---

### Post by richmarchman66 on 2007-06-08
RESOLVED - I changed the mediacenter back to it's original static ip (.1.3 instead of .1.7), reloaded samba (sudo /etc/init.d/samba reload  then  /etc/init.d/samba restart) and it works again.

Not sure why the clients static changing would stop it from connecting to the server, but that appeared to be the fix.

Thanks

---

