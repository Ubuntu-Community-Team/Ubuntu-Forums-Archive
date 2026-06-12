---
title: "file permissions on mounted drive"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-15
I just mounted a storage drive on a 8.10 server. I installed samba so I can use this mounted drive from a windows machine. I have edited my samba config to allow writes, and to create directories. How I ever I still get permission errors wen trying to edit files or create files, or try and copy files to the shared drive (mount). How can I tell if this problem is from linux file permissions? Thanks

---

### Post by ja660k on 2008-12-15
i dont know if this will work but do a ls -al of the drive and it should tell you permissions

---

### Post by pshootr on 2008-12-15
> **ja660k said:**
> i dont know if this will work but do a ls -al of the drive and it should tell you permissions

Ok I got this

FS:~$ ls -al
total 28
drwxr-xr-x 3 pshootr pshootr 4096 2008-12-14 06:47 .
drwxr-xr-x 3 root    root    4096 2008-12-11 01:17 ..
-rw------- 1 pshootr pshootr 4057 2008-12-14 20:59 .bash_history
-rw-r--r-- 1 pshootr pshootr  220 2008-12-11 01:17 .bash_logout
-rw-r--r-- 1 pshootr pshootr 3115 2008-12-11 01:17 .bashrc
drwx------ 2 pshootr pshootr 4096 2008-12-14 06:47 .gconf
-rw-r--r-- 1 pshootr pshootr  675 2008-12-11 01:17 .profile
-rw-r--r-- 1 pshootr pshootr    0 2008-12-11 02:15 .sudo_as_admin_successful

---

### Post by pshootr on 2008-12-15
I think the output of ls -al looks ok.

BTW I am using windows explorer from my laptop to access the shared directory on the server. In the smb.conf I have this option set.

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

However, I am not promted to provide a user name to access the share. Something is wacky. Any ideahs?

---

### Post by pshootr on 2008-12-15
It seems no matter how I edit the smb.conf I still can not write to the share? Is this only possible through a smb client or something?

---

### Post by Amorphous_Snake on 2008-12-15
Nothing against Ubuntu, but that's why I left Ubuntu for Mandriva. Since 8.04, sharing things with Windows machines have become very difficult on Ubuntu after they removed the Shared Folders GUI. Of course you can always edit the smb.conf, but why do it when you can control everything from a nice GUI.

I am keeping track of this thread as it's almost the same problem that I had: The Windows client doesn't ask you for a password for the Linux server when you are logging in. Thus, you don't register as one of the smb users, and so you don't have any write rights.

---

### Post by pshootr on 2008-12-15
I found this problem mentioned on another site, and one guy supplied a command to use. And it mostly worked for me. The only issue now is editing a text file. I wish I could remember the command. I will try tommorrow to find the page again.

---

### Post by waspbr on 2008-12-15
whenever I have permission problems on a drive I use a more unorthodox method. 

I do ALT+F2 and type the command

```
gksu nautilus
```

this opens nautilus in root mode, so be careful cos whatver changes you make are going to stick. 

anyway, go to /media and find the drive you want to enable permissions for. 

right click on it and choose the properties menu, there go to the  permissions tab, modify the permissions as you wish and don't forget to check to click on the "apply permission to enclosed files" button.


hope it helps

PS:sometimes I use the same method to copy/cut/paste/delete/edit protected files.

---

### Post by AlanR8 on 2008-12-15
I found:

system-config-samba

in the repos that provides a GUI for samba shares. Give it a go. I don't have any problems saving or writing to my 8.1 "server" from the wife's XP box or my 8.1 laptops

---

### Post by Amorphous_Snake on 2008-12-15
I know this tool. It's from Fedora. I tried it in 8.04 and it didn't even run.

I haven't tried it in 8.10 as I installed it for a few hours or so. I will be installing it to a USB stick and try again.

---

### Post by AlanR8 on 2008-12-15
I noticed it didn't run in 8.04 as well but it does in 8.10

---

### Post by pshootr on 2008-12-15
> **pshootr said:**
> I found this problem mentioned on another site, and one guy supplied a command to use. And it mostly worked for me. The only issue now is editing a text file. I wish I could remember the command. I will try tommorrow to find the page again.

I must have been really tired last night, the command I found was actually from this site lol. Well here it is.


sudo chmod a+wrx dirname

Thanks for all the extra tips guys, as this command still does not let me edit text files. I will have to tinker some more using all the suggestions you guys have provided. Thanks alot guys.

---

