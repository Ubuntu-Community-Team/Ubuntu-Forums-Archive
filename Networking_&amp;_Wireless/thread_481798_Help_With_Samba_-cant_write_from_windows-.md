---
title: "Help With Samba -cant write from windows-"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by scrupul0us on 2007-06-22
I have a fresh install of 7.04 (CLI only)on my dev server and im tring to setup Samba

i went over to ubuntuguide.org and tried to follow their directions ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server))

1) INSTALL
-sudo apt-get install samba smbfs

2) Add User
-smbpasswd -a scrupul0us
-set password

3) Edit "/etc/samba/smbusers"

ubuntuguide said to to add this: **system_username = "network username"**
so i added: **scrupul0us = "scrupul0us"**

so then i saved the file and restarted samba

4) Edit "/etc/samba/smb.conf"
i uncommented: **security = user**
i added:** username map = /etc/samba/smbusers**
i added:
[B][www]
  comment = WWW
  path = /var/www/
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup[/B]

so then i saved the file and restarted samba

5) From Windows
I hit my ip and can read the directory just fine.. but i cant write... i check the security permissions in windows and **scrupul0us** is no where to be found nor can i add it

ideas please?

---

### Post by scrupul0us on 2007-06-23
bump

---

### Post by dardack on 2007-06-23
I personally use WebMin to manage my samba install.  However, my linux server is a KnoppMyth box, so no idea if WebMin works on Ubuntu.  But basically from my windows box, i put in my Myth Box's ip in firefox, log into webmin and can change what folders are shared and read/write permissions.  Made it a snap to get reading/writing to myth from windows.

---

### Post by scrupul0us on 2007-06-23
while its tempting... id rather learn the CLI than install a FE GUI... i feel like im missing something stupid in the config from ubuntuguide

thanks for the offer tho dardack!

ive also tried this now:

[B][WEBROOT]
path = /var/www/
comment = WWW
valid users = scrupul0us
read only = no
case sensitive = no
msdfs proxy = no
public = yes
writable = yes
create mask = 0777
directory mask = 0777[/B]

now im prompted with a login... i enter my username and password and this time now it just keeps prompting for a password

---

### Post by dardack on 2007-06-23
Ok then 2 suggestions, in your smb file under [www] i think you forgot

valid users = system_username1 system_username2

and also, i've had issues setting r/w properti es on folders with the CL, like i would do chmod/chown on a folder yet it didn't seem to take.  For example, i was trying to back up my WoW directory to my windows partition, and kept getting, you don't have read permission, i had to sudo natulis (or whatever it's called) to fix this problem.  DOn't know why i had issues.  Sucked tho. I would just make sure that that directory has set proper permision to write i guess.

---

### Post by scrupul0us on 2007-06-23
i did actually enter the valid users [see my edited post above]

and i know... its so much easier within X... but im desperate to learn it

hopefully someone can speakup :)

---

### Post by dardack on 2007-06-23
quick thing should it be?:
scrupul0us = "network username"
and not?
scrupul0us = "scrupul0us"
just curious

---

### Post by dardack on 2007-06-23
also i think i found the CL for chown/chmod
sudo chown -R system_username /location_of_files_or_folders

and than

chmod with -R i think to make sure that they have r/w, i'm sorry, i'm not an expert i'm just tryin to help you out.


also did you run:
sudo testparm
sudo /etc/init.d/samba restart
?

---

### Post by scrupul0us on 2007-06-23
i ran the testparm and it was fine... i rebooted the server and it was fine

right now i dont have a r/w issue since i cant even login.... my original config allowed anyone to read the share.... right now i have it tied to just the one username i want to allow and i cant even login... so somehow i have a users issue

---

