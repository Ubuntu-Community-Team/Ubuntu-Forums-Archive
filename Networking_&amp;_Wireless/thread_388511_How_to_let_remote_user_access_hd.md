---
title: "How to let remote user access hd?"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by rich.bradshaw on 2007-03-19
Hi,

I am planning to set up an old computer as a home server - everything seems like it will be ok, but I have one question.

My father is a wedding photographer, and wants an offsite backup for his files. I live about 100 miles away, so I have suggested that he gives me a large disk (prob external) and I can let him backup his files to this disk over the internet.

What can I use to do this? I want it to be secure, so want to use sftp/ssh. He is using Windows, and isn't very technically minded, so I want it to be simple for him to backup. Something like rsync would be good - can this be used from Windows?

To summarise:

1. How do I create a user that can only access specific folders?
2. What can my father use from Windows to synchronise files with the disk on my computer?
3. How can I ensure that this happens securely?

Is using something like winSCP + ssh the best solution? I would really like rsync like capabilities. 

Thanks!

---

### Post by rich.bradshaw on 2007-03-20
Anyone?

---

### Post by rich.bradshaw on 2007-03-21
OK, well does anyone know how to create a user that can only access one folder? In this case I want to restrain him to accessing only the external drive, so that he doesn't accidently wipe out my files - how do you do that?

---

### Post by thelinuxguy on 2007-03-21
> **rich.bradshaw said:**
> OK, well does anyone know how to create a user that can only access one folder? In this case I want to restrain him to accessing only the external drive, so that he doesn't accidently wipe out my files - how do you do that?

When you create a new user and don't give that user root privileges, that user can read most of the files but write only to his/her home directory. Wouldn't that suffice to avoid accidental damage to your files by your father?

Could you possibly mount your external drive as a folder under /home and make that as the home folder for a new user?

---

### Post by rich.bradshaw on 2007-03-21
Ok, I didn't realise that they could only edit files in their home dir. That makes it simpler.

Do you know what software they can use from windows to easily synchronise files?

---

### Post by thelinuxguy on 2007-03-21
> **rich.bradshaw said:**
> 
Do you know what software they can use from windows to easily synchronise files?

1) pureftp server on the Ubuntu machine with the external HDD. It is available in the repos. You will need pure-ftpd and pure-ftpd-common. In addition, you may want pureadmin which is a graphical configuration tool for pureftpd.

pureftpd lets your Ubuntu system users login from a remote location and serves them their home folders by default. I did not have to do any additional configuration. So your father would see his home folder when he connects to the FTP server at your end. And it supports SSL. 

2) For accessing it from Windows, use any FTP client like CoreFTP Lite.
Or Start >> Run >> ftp://ubuntu_username@ubuntu_machine_address
Windows will ask for the password and present you with an explorer view of the FTP location.


There is also vsftpd (Very secure FTP Daemon) for better security. I haven't used it though.

Let me know if this works for you.

---

### Post by rich.bradshaw on 2007-03-23
Ok, sounds good - I'll take a look - just waiting to get a second computer to use as a server... good old freecycle!

---

