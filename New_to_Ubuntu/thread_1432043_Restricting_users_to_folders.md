---
title: "Restricting users to folders"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Jloser on 2010-03-17
I have a user I would like to restrict file access.  Basically I only want the user to be able to see files in their home directory, and also some folders under /var/www.  Let's say I have 5 websites all in 5 different folders:
/var/www/1
/var/www/2
/var/www/3
/var/www/4
/var/www/5

I want this new user to ONLY be able to view/edit 4 & 5 along with the files in their home directory.  I don't want them to see or do anything else.

---

### Post by marbertone on 2010-03-17
Hi,
I've never done this specific thing, but IMHO I think it should be something like this:

```

sudo chmod -rwx[perhaps more options] [folder] 

```

try 
```

man chmod

```

you should find what you are looking for!

Cheers,
Mario Alberto

---

### Post by mikemelen on 2010-03-17
type the below command in terminal. First try to change the ownership, For ex

username is test

#chown test:test /var/www/4
#chmod 750 /var/www/4

---

### Post by Jloser on 2010-03-17
I understand how to give the user access to the folders, but how do I restrict access to everything else?  As of now if I login as the user and ls I see the names of all folders and files.

---

### Post by mikemelen on 2010-03-17
this [link]("http://omgili.com/mailinglist/debian-user/lists/debian/org/2b265c5a0809021318r3eddbbecx701fd955ec3c4657mailgmailcom.html") may be help

---

### Post by bodhi.zazen on 2010-03-17
> **Jloser said:**
> I understand how to give the user access to the folders, but how do I restrict access to everything else?  As of now if I login as the user and ls I see the names of all folders and files.

You have several options.

One option is to use Apparmor. Take a look at jailbash :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash)

Another option is to use a chroot, depending on how you give them access. You can chroot ssh and / or ftp.

---

### Post by sublimation on 2010-03-17
are you trying to restrict access from someone who sits down at the computer using a graphical session, or are we talking someone using SSH for a console?

---

### Post by Jloser on 2010-03-17
This would be for ssh and/or ftp.  I am looking into chroot now.

---

### Post by sublimation on 2010-03-17
You can do most of what you're looking for from within the sshd config files. For example:
editing /etc/ssh/sshd_config
after the line
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
toss in
```
Match Group sftp
    ChrootDirectory %h
    ForceCommand /usr/lib/openssh/sftp-server
    AllowTcpForwarding no
```
this chroots the user to the directory specified. They won't be able to do anything to the root directory (here %h means /home/username, and you could change that to /var/www/) just make sure they own their particular website's folder, so they can enter that folder, make what directories they want, upload & download, but not much else. 
All users you add to the group sftp will get this restriction. So if you wanted, you could make groups for website_1 website_2 and give each site it's own Match Group website_# section. Then each site could be restricted to just their site's folder, too. 

You need a fairly recent OpenSSH for this to work, I think it started with OpenSSH 5.0

I've only experimented lightly with this, so I'm not certain how cleanly multiple Match Group calls would work.

---

