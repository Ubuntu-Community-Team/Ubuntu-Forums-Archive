---
title: "Deleted all users"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by jmeister67 on 2010-01-02
I was having problems with certain applications starting when I was logged in as the user created when I installed Ubuntu. I decided to log in as root and delete any users (there was only 1). I then tried to add users through System/Admin/Users and Groups. I then deleted these users. The problem now is that I have no users listed in Users and Groups, but I still see the usernames at the login window. I have also deleted the user home folders. My goal is to have only the root user at login. 

Thanks

---

### Post by Zeedok on 2010-01-02
Probably not a good idea to have only a root user (I'm no expert).  However, an ordinary user can install programs, delete files, make changes etc with root privileges.  When you try to enter synaptic (for example) you are asked to provide the password and away you go.  

It is a safer way to go, otherwise you could inadvertently make a whole bunch of changes to your system with unforeseen consequences.

My suggestion:  Quick reinstall, create an ordinary user account and go from there.

---

### Post by jbrown96 on 2010-01-02
Bad idea. There's no reasonable need for this...

Unless you can give an extraordinarily good reason for this, I'm not going to help.

---

### Post by jmeister67 on 2010-01-02
Thanks for the advice. When I do the reinstall, will I lose any existing data? (I'll backup of course) 

Thanks

---

### Post by Zeedok on 2010-01-02
You will lose your data.  After a few years of installing (and reinstalling) linux systems I have learned to back up frequently!!!

There is a terrific command line program to copy files called rsync.  If the command line is a little much to handle, try Grsync (in the repos, find it in synaptic), which just gives you a few windows etc to control your backup.  Use (G)rsync to copy the data you want to keep to an external hard drive or USB stick.  Once you get your system the way you like it, use (G)rsync to backup your whole /home partition.

---

### Post by jbrown96 on 2010-01-02
You don't need to reinstall, just re-add the users/groups that you deleted. I will help you do that. If you can post your /etc/group, /etc/shadow, and /etc/passwd, then I can help you get everything working again, but it may just be easier to reinstall. If you have deleted your home directory, then you have already lost everything and there's nothing to back up.

---

### Post by 3rdalbum on 2010-01-02
In future: If you have trouble with specific applications, try removing their preferences files. They are stored inside hidden folders in your home directory, so hit Control-H in your file browser to see them.

Or you could have created a new user account and seen if the problem exists in the new user account.

---

