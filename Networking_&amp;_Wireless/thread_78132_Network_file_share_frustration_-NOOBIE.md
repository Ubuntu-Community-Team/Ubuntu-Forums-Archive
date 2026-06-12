---
title: "Network file share frustration -NOOBIE"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by imagictech on 2005-10-17
Ok, I'm a noob.  I have taken up Linux in the effort to learn a new and better system. I am a Network tech by day but a frustrated Linux user by night.

My issue is trying to get Windows to be able to access files on a Linux share. i have installed Samba and can see the Linux box and get prompted for a user / password. i use either my account or the root account credentials to no avail.  I can clearly see that this is a permissions issue but I also am unable to edit the smb.conf file.  I have also tried this with Red Hat 9  and bought a book on noob linux admin to no avail. I seem to be unable to obtain / install SWAT either.

Concerning the smb.conf, it is flagged as ready only and states that i am not the owner.  I understand that you need admin perms to edit the file but i log in at the root terminal and try to edit as well with the same results.  A whoami verfies that I was root.  I read much about editing the file to enable share access but I cant even get that far.

Any ideas

Robert

---

### Post by byourg on 2005-10-18
In a terminal enter "sudo gedit /etc/samba/smb.conf" (without the quotes), enter your user password when prompted and it should open the samba config file that you can save changes to. Hope this helps!

---

### Post by ProPilot on 2005-10-18
Try this link
[http://ubuntuforums.org/showthread.php?t=73679](http://ubuntuforums.org/showthread.php?t=73679)

---

