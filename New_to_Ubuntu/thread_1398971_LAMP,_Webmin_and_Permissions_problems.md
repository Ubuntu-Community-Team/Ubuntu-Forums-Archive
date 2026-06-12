---
title: "LAMP, Webmin and Permissions problems"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by DarkKoopa on 2010-02-05
Hi,

After not having used Ubuntu for several years (and my knowledge back then was rather basic), I've bought myself a new box for Ubuntu.

I've installed Ubuntu Server with LAMP, ProFTPd, phpmyadmin and Webmin so I can just access it remotely (also setup the remote desktop so I can use a VNC tool to access the desktop, as I love the GUI as opposed to the terminal).

The LAMP server is working OK, however I completely forgot that Linux is much more secure than Windows with file and directory permissions.  

I have dumped 3 different Joomla backups that I have in three different directories in /var/www

If I use another computer to access the ubuntu installation (or type in localhost in a browser), I get the default "It works page".

Excellent, I know that Apache is working.  I also know that mySQL is also functioning as I can access it via phpmyadmin.

My issue is that if I type localhost/directory1 (or 2 or 3), the browser goes back and downloads a file, instead of displaying it.

The permissions are for user root in group root.

Can anyone explain what I've done wrong and what I can do to rectify it?

---

### Post by jken146 on 2010-02-05
First, make sure that the files you've put in /var/www/ are readable by apache. Apache runs as the user www-data

---

### Post by DarkKoopa on 2010-02-05
> **jken146 said:**
> First, make sure that the files you've put in /var/www/ are readable by apache. Apache runs as the user www-data
Thanks for the info re apache.

How do I check that?

My experience with permissions in Linux is minimal.  From what I can gather, it's all owned by root in the group root.  This is the problem I face as if I VNC into the box and look at the permissions of the files/directories, as I'm not user 'root', I can't change them.

---

