---
title: "Cannot connect to Windows Shares"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Luggy on 2006-09-18
My roomate runs Windows and has some folders shared over the network. I'm having trouble seeing and connecting to those shares.

From what I can tell I should just be able to see them by going to Places -> Network Servers and then clicking on the Windows Network. But when I click on the Windows Network I don't see anything.

Can someone please help me out.

---

### Post by andb on 2006-09-18
Since I know my local network, I choose to mount using the command line. For example:
```
sudo mount -t smbfs //192.168.1.111/SHARENAME /media/MOUNTPOINT/ -o uid=1000,user=USERNAME,password=PASSWORD
```
Often the username and password are unimportant, depending on the windows share type. The uid should match your account and enables you to write to the share without using sudo. Its also possible to add the net share in your fstab file, so itll mount automaticaly on boot. Sorry Ive never used the network browser, so cant help on that...

---

