---
title: "file system permissions issue"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by ubscott on 2010-09-26
hi,
 
after receiving excellent advice on how to install LAMP:
[http://ubuntuforums.org/showthread.php?t=1579465](http://ubuntuforums.org/showthread.php?t=1579465)
 
i made what appears to be a mistake and installed the latest version of Ubuntu. in short, after i got LAMP i brought down the latest Ubuntu.
 
i'm now having a permissions issue with the File System/var/www folder. I wish to install Drupal; to do this i am trying to copy Drupal files that I downloaded (into the Documents directory) and move them to File System/var/www. (this is so i can run Drupal's install script via Apache, which is running.) 
 
When i attempt to move the files to \var\www, i get an error message saying this is not possible because of a permissions issue. I write-click on this folder, choose permissions and it says that the root is the owner. Also, 'You are not the owner, so you cannot change these permissions.'
 
however, i'm logged in under the administrative account. so, i should be the owner of this folder.
 
does anyone have an idea how to set the permissions on the var/www folder so that i can copy my Drupal files to it?
 
should i reinstall LAMP? it was such a pain in the **** to get it working that i'm hesitant to do this.
 
by the way, if this topic is familiar, i did search for 'permissions' but found nothing similiar to my problem:
[http://ubuntuforums.org/search.php?searchid=76188950](http://ubuntuforums.org/search.php?searchid=76188950)
 
thanks for the help so far.

---

### Post by jtarin on 2010-09-26
As "sudo" you need to change to the directory in a terminal and [change permissions through the terminal.]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by ubscott on 2010-09-27
jtarin, thanks for the info.  however, i'm having difficulty finding the File System folder from the terminal.  i have found my way to /home$ .   How do i navigate into the File System?
 
thanks in advance.

---

### Post by ubscott on 2010-09-27
uh, nevermind my last question.  i just found this:
[https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html](https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html)
 
use, **"cd /var/www"** to go directly to the /www subdirectory of /var/.

---

### Post by ubscott on 2010-09-27
jtarin, thanks.  problem solved.

---

### Post by jtarin on 2010-09-27
You can also open Nautilus file manager and navigate to the directory/folder indicated from your search if you would like a visual, but learning the command line is the fastest way. Did you find it?

---

### Post by jtarin on 2010-09-27
> **ubscott said:**
> jtarin, thanks.  problem solved.
Excellent!

---

