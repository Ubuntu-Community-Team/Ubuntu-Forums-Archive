---
title: "Help with share directory"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by jbraum on 2005-11-30
've created a share winshare and I want to be able to share it (map a drive) across my windows lab but everytime I map the drive it prompts me for a username and password. I just want drive to be there everytime the workstation is login. I setup the following to try to do this.

Share information

[winshare]
comment = Windows Applications and Student Share
path = /home/samba/software
write list = administrator
read only = No

Windows workstation info

username - administrator
passwd - no password to login

Linux

Setup a user called administrator with no passwd.

Permissions on the file are as follows:

File Owner - admin
File Group - students
Owner - read write execute
Group - read write execute
Others - read write execute

I simply want to make the drive/folder accessible with out typing a password

The only way to get in is to type admin and it's password them I in.

---

### Post by schilcha on 2005-12-01
Windows first tries to connect to the samba-server using the username and password you supplied during logging into the win-box. If these don't match, windows asks you to enter username and pwd.

I take care that the usernames and passwords are the same for windows and samba (I don't think that pwd of the linux-account needs to be the same). I have no idea, if you can tell windows to always use a different name/pwd. 

Moreover, I've never tried empty passwords. If there's no pwd, you could try to grant something like "Guest-Access". I think there is some option for samba to control this.

I hope, I understood your problem correctly.

Good Luck!

---

### Post by jbraum on 2005-12-01
Ok I got it.  The security setting in my config file was set to user.  Set it back to share and I'm good.  Don't know how this happened, been beating my head against the wall on this because I knew it was something right in front of me.  

Thanks for the reply

---

