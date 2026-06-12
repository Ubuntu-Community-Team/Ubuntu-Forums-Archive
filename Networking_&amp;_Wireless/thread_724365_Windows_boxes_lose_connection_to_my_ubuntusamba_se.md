---
title: "Windows boxes lose connection to my ubuntu/samba server"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by qwert231 on 2008-03-14
If I enter \\192.168.0.xxx from a Windows box to connect to my linux box after entering my user/pass. I'll connect, then go into one of my shared folders to look at pictures. All of a sudden, the share will be inaccessible, and I have to go back to the IP address and re-enter my password.

If I try to enter \\192.168.0.xxx\sharename I can't connect unless I've entered my username and password. I'd like to be able to enter my user/pass once, and not have it lose connection while I'm doing a slideshow, or working with files.

---

### Post by dca on 2008-03-14
What happens if you use the 'Map Network Drive' option.  Right-click on the network neighbor hood and select that option.  Selecyt any drive letter from the drop-down and  enter the path \\xxx.xxx.xxx.xxx\sharename
 
...then login... Be sure to uncheck the 'reconnect on start-up' button before doing so...
 
...if it fails after using that method, check the /var/log/messages file on the samba box to see if it indicates anything...

---

### Post by qwert231 on 2008-03-14
Hmm... could be the key.

---

### Post by qwert231 on 2008-03-14
Hmm... I think I'm having a larger issue... Right now, I can't connect from my box to the linux box.

---

### Post by dca on 2008-03-14
Generally, if you run Ubuntu Server you just need to install 'samba' package.
 
Configure the /etc/samba/smb.conf file adding the share info
 
Then from CLI:
 
sudo smbpasswd -a username
sudo smbpasswd -e username 
 
...then restart samba daemon...

---

### Post by qwert231 on 2008-03-17
Samba works... I think this is actually  a network issue with the box.

I have a web site hosted off this box, and looking through pictures on the box (in a slideshow) goes well for a while, but randomly disconnects, forcing us to restart the slideshow.

---

