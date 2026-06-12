---
title: "Unable to log into a Shared Folder on Ubuntu from XP"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by KhaiJB on 2008-06-02
to start off :

Delenn - Running 8.04
Cerberus - Running XP Pro

now.. I followed the instructions to setup Samba from here - [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) all good so far. Delenn talks fine to Cerberus and windows server Merlin.

buuuuut when I try to logon to a shared folder on Delenn, I get asked for Username and Password.

which I enter (they are identical on both machines) and bing... I'm asked again... and again... and again...

so. I went back and checked everything over.. twice.

I just can't seem to log in!

---

### Post by Iowan on 2008-06-02
Is the user valid on Ubuntu? (username and password in **passwd** file?
Have you set up the user in Samba using **smbpasswd -a**?

---

### Post by KhaiJB on 2008-06-02
yup and yup.
User is on Delenn and Cerberus, Identical user Names and Passwords.

---

### Post by Iowan on 2008-06-02
I had that happen when I was trying to login to a "home directory" as a different user - Samba showed a directory that didn't exist - I hadn't built the directory for my login name.
 But I digress... User has access rights to shared directory? (I suspect this is one of those things you already checked twice.)

---

