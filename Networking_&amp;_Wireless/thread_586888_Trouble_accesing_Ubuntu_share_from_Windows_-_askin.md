---
title: "Trouble accesing Ubuntu share from Windows - asking for a user/pass?"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Fireblend on 2007-10-22
I recently set up my computer to work with a network on Windows XP, however although I can enter the windows share fine, it won't let me enter my Ubuntu share from the windows machine, asking for a username and password. I'm pretty sure it's not window's username and password since we don't have a password and inputting the machine's name doesn't work. It actually seems to be asking for a user that starts with "Abulafia/" (Abulafia is the name of my computer with Ubuntu), so I'm sure it's something to do with Samba.

Does Samba has some user/pass related configuration somewhere? On Feisty this didn't happen, and Windows had never asked me for a password before when trying to connect to it, so I'm pretty sure Samba's at fault here.

Thanks in advance.

---

### Post by Hero of Time on 2007-10-22
Check your /etc/samba/smb.conf file for an entry called 'guest ok = yes/no*' on your share. There could be a change there since Feisty. Have you tried your Ubuntu logon name and password?

*one of these options is set, it needs to be yes for guest logon to be possible.

---

### Post by Fireblend on 2007-10-22
I have tried using my Ubuntu's name/pass already. I'll check on the conf file and edit this post with an update.

---

### Post by nalmeth on 2007-10-22
I had to create a user on the system, and then create a samba user aswell. 

This page details how to create a samba user:
[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

---

### Post by Fireblend on 2007-10-22
> **nalmeth said:**
> I had to create a user on the system, and then create a samba user aswell. 

This page details how to create a samba user:
[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)

Yup, this definitely worked. Thanks a lot!

---

