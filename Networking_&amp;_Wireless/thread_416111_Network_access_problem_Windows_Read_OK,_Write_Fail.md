---
title: "Network access problem: Windows Read OK, Write Fail"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2007-04-20
For some reason on my windows box, when i try to paste an MP3 to the box, it says access denied.

I have this in my smb.conf

```
[public]         
  comment = Public Folder
  path = /share
  public = yes
  writable = yes               
  create mask = 0777
  directory mask = 0777     
  force user = nobody            
  force group = nogroup  

```


ls -l s*
share:
total 20
drwxr-xr-x  2 hansoffate hansoffate 4096 2007-04-03 16:40 Computer
drwx------  2 root       root       4096 2007-04-02 18:56 lost+found
drwxr-xr-x  2 hansoffate hansoffate 4096 2007-03-25 18:56 Misc
drwxr-xr-x  1 root       root       4096 2007-04-03 21:16 Musik
drwxr-xr-x 33 hansoffate hansoffate 4096 2007-04-01 12:06 Videos

Any Ideas?  
Thanks,
Hans

---

### Post by bnuytten on 2007-04-21
It looks like the force user/group options collide with the permissions set on your files. When you access \\yourlinuxbox\public from windows you will be seen as user nobody/nogroup trough Samba on the linux file system.

Thus: you can access the Samba share but you do not have local file system rights to write to the /share directory. Check the permissions of that directory (and the files within). chmod 777 /share should surely do ;-)

---

### Post by hansoffate on 2007-04-21
#-o DOH!  Hehe.  Thanks, that did the trick.

---

