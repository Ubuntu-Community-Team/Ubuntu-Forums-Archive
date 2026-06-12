---
title: "How can I see shared files on my laptop from this computer?"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by Jamface on 2010-12-09
I have Ubuntu 10.04 installed on this computer (desktop) and Puppy Linux installed on my laptop.  I have installed Samba on this Ubuntu desktop machine and set one directory as a Samba share.  Using Pnethood Samba Shares on the Puppy laptop I can see (on the laptop) the Ubuntu shared directory.  I have used Places>Connect to Server on the Ubuntu machine to try to set up access to my laptop from Ubuntu using SSH and the laptop IP address.  But access was denied and the bookmark name in Places now seems to do nothing.  I have openssh-server installed on the Puppy Linux laptop.
What am I doing wrong.  Access seems to work from Puppy to Ubuntu but I haven't sorted out how to get access to Puppy from Ubuntu.

---

### Post by anthr6x on 2010-12-09
if you don't have ssh service running from your laptop, there is no way you can connect to it using ssh. samba is the service you use for file sharing. ssh is for secure shell. these are two different services.

---

### Post by pricetech on 2010-12-09
Have you restarted SSH, or the computer, since you installed ssh-server ??

Unless you're sharing to windows machines, you won't need samba.

---

### Post by Jamface on 2010-12-09
I have now restarted both machines, but when I use Places > Connect to Server in Ubuntu and select SSH and put in the laptop IP address I get the message 'Cannot display location "sftp: //192.168.1.101" Connection refused by server'

It seems as if Ubuntu is finding the laptop via the network but the laptop won't give Ubuntu access.

What could I try now?

---

