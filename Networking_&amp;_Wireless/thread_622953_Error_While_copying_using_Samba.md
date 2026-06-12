---
title: "Error While copying using Samba"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by c0reyf on 2007-11-25
I'm using an Ubuntu on my home PC and my laptop. My wife uses XP on her laptop so I need to give her access to the printer and possibly file share on the home PC, I need to have printer access and file share. I right clicked on the folder I wanted to share and used SMB. Now I can see the folders on my laptop(ubuntu) and my home PC(ubuntu) under windows network but when I goto copy files I get an error "file xxx cannot be copied because you do not have permissions to read it". I'm root and can open the files locally. Any suggestions on what is going on? I need to get some files copied over ASAP. TIA

---

### Post by nickpaton on 2007-11-25
Have you configured your firewall on your Ubuntu PC?

To do it:

[http://ubuntuforums.org/showthread.php?t=609989#4]("http://ubuntuforums.org/showthread.php?t=609989#4")

Which I discussed an easy way to set up Samba, as well as Firestarter the Ubuntu firewall.

let us know how you get on.

Nick

---

### Post by c0reyf on 2007-11-25
Ok I've tried the above now I have an access denied problem when trying to copy a folder accross the network. Mind you this is between Ubuntu boxes. Obviously something is wrong with my sharing permissions somewhere. Any other ideas?

---

### Post by nickpaton on 2007-11-25
When networking between two Ubuntu boxes, use NFS.  This is in addition to setting up Samba for the Ubuntu Windows share:

A good NFS HOWTO can be found[ here]("http://ubuntuforums.org/showthread.php?t=249889").

---

### Post by nickpaton on 2007-11-25
To set up prinitng between your Ubuntu box and either the XP or other Ubuntu one, use[ this HOWTO]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu").

Remember to set up your firewall as I've already mentioned.

Have you managed to network your Ubuntu box with the XP one OK?

Nick

---

### Post by c0reyf on 2007-12-08
It seems to work fine on my wifes XP laptop to move files over to my Ubuntu server. I still get access denied while copying from my ubuntu laptop to the Ubuntu server though. Any thoughts.

---

### Post by popch on 2007-12-08
> **c0reyf said:**
> It seems to work fine on my wifes XP laptop to move files over to my Ubuntu server. I still get access denied while copying from my ubuntu laptop to the Ubuntu server though. ***Any thoughts***.

As far as I can remember, Samba manages its own set of userids, passwords and credentials. Thus, even if you are using the same userid both for Linux and Samba, there might be two different passwords attached to those accounts.

It has been a long time since I last read up on Samba, but you asked for thoughts, which you got. I hope it helps.

---

### Post by santosh_gr on 2007-12-08
Here is what you need to check for.

1)  Does the share exist.  i.e.  which ever share you are sharing e.g. /tmp/tmpshare.

2)  Check permissions on the share /tmp/tmpshare.  Check both user and group permissions.

3)  Does the user id you are using have the required permissions.

4)  Whats the permissions that you have set for your share.  Is it read-only?

5)  There is a section for valid users in /etc/samba/smb.conf.  Is the user id listed there?

6)  What is the security level set to is it user or share etc.

7)  Restart samba service on the system.  run  /etc/init.d/samba restart

If you can output your smb.conf file it will be useful.

---

### Post by c0reyf on 2007-12-09
Solved the problem by setting the Samba password to root instead of my user name. Appreciate the help everyone. Thanks,

---

### Post by serhito on 2008-02-05
> **c0reyf said:**
> Solved the problem by setting the Samba password to root instead of my user name. Appreciate the help everyone. Thanks,

How do you do that ?

---

