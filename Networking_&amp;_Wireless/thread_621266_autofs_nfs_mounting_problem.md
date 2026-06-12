---
title: "autofs nfs mounting problem"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by fga on 2007-11-23
Hello, this is my first post, so I apologize for any weird formatting this post may have. I am setting a home server running nfs and would like to have all our client machines mount several directories from the server using autofs. I have followed the guide  at [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")  . 
I know that my nfs server has been set up correctly because I can manually mount the nfs shares onto the clients, but I have not been able to get autofs to mount my nfs shares. Has anyone done this before? all that I get when autofs is started are the mount points without any files or directories inside. 

this is my /etc/auto.master file:
[INDENT]
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc  /etc/auto.misc --timeout=60
#/smb   /etc/auto.smb
#/misc  /etc/auto.misc
#/net   /etc/auto.net
/home2  /etc/auto.home
/content /etc/auto.content

[/INDENT]

this is my /etc/auto.content file:
[INDENT]
* server:/content/&
[/INDENT]

and this is my /etc/auto.home file
[INDENT]
* server:/home/&
[/INDENT]

I would like to eventually mount /home from the server but for now I am trying to mount it at /home2 to make sure it works.
I have an alias for server in my /etc/hosts file, so it should be able to resolve the name. 

any help will be greatly appreciated :).

---

### Post by fga on 2007-11-24
I have finally figured out what is going on. autofs was doing what it is supposed to do, but I never tried to access anything that was to be mounted onto the mounting point, so the mounting point appeared empty in nautilus. simply issuing cd /home2/fga mounted fga at the moment and made the directory appear in /home2 in the nautilus browser. ](*,)
I hope that someone else in a similar situation will benefit from this.

---

### Post by tr3s on 2008-07-01
hi! mine is working perfectly. this is my settings:

server:/etc/exports
```
/files 192.168.0.0/24(rw,async)
```

client:/etc/auto.master
```
/mnt/nfsmount /etc/auto.nfsmnt --ghost
```

client:/etc/auto.nfsmnt
```
files 192.168.0.99:/files
```

the directory /files in the server is automatically mounted to /mnt/nfsmount/files in the client. /mnt/nfsmount should be existing in the client.

hope this could be a help to others who are still in difficulty

regards

---

