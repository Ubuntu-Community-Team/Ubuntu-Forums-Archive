---
title: "File sharing risk to ubuntu from windows computer"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by ed67 on 2007-12-08
A slightly different samba question that doesn't seem to be addressed anywhere....

My laptop runs ubuntu 7.10.  My desktop (main computer) runs windows xp home.  File sharing works fine both ways, to and from each computer.

Here's the problem.  I usually leave both computers on and use ubuntu most of the time on my laptop.  I can lock the screen on my laptop which requires me to type in my password to resume.  Fine and good.  However, anyone using the win xp machine can simply go to my network places and have full access to my ubuntu laptop.

Here's what I'd like:  on the xp machine, when someone clicks to open my laptop in network places, it should ask for the password.  I typed in the samba pwd when I set it all up.  I know this can be a windows issue as well, but i was thinking there might be a way to have ubuntu require a password for this kind of access.

More info:  I have xp using a different username than I am, called office.  I granted permission in ubuntu to the folder I want to share with "other users".  This is how I want it, easy access to files on either machine from either machine, but a password would be nice when trying to come in from the xp side.

Sorry this is a bit wordy, but any advice is appreciated.

---

### Post by santosh_gr on 2007-12-08
try changing security=user to security=share.  You will have to setup you share again with the correct options with the smb.conf file.

---

### Post by ed67 on 2007-12-08
> **santosh_gr said:**
> try changing security=user to security=share.  You will have to setup you share again with the correct options with the smb.conf file.

Just a little too new to Linux..... where do I change this setting?  and where do I find the smb.conf file?  I set the username and password in terminal with the smbpasswd command.

---

### Post by santosh_gr on 2007-12-09
You will find these options under smb.conf file.  Its a long file and if you were to read through it correctly there is a section which will look something like.


; security=user

You will need to uncomment is and change to 

security=share

---

### Post by santosh_gr on 2007-12-09
The smb.conf file is located in /etc/samba directory.

---

