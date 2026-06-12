---
title: "Mounting network share errors"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2007-11-07
I'm trying to mount a shared folder on a server at school, but I'm getting an error. The server runs Fedora Linux and has Samba. This is what I'm trying:```
mount -t cifs -o //xxx.xxx.xxx/home/username /media/taz username=username,password=password,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I've also tryed adding this to the fstab file:```
#taz folder
//xxx.xxx.xxx.xxx/home/username /media/taz cifs username=username,password=password,iocharset=utf8,file_mode=0777,dir_mode=0777
```Then I run "mount -a". 

Either way, I get this error:```
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

Anyone know what could be causing this?

Thanks!

---

### Post by jonathanmotes on 2007-11-08
Anyone?

---

### Post by jonathanmotes on 2007-11-14
I've made some progress.

This is what I'm trying:
```
sudo mount.cifs -o user,sync,domain=MYDOMAIN,user=myusername,uid=1000,gid=1000,file_mode=0600,dir_mode=0700 //xxx.xxx.xxx.xxx/home/myusername /media/taz/
```

This is what I'm getting:```
Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found
```

Typing the IP in a web browser pulls up the website (since this server is both a file and a web server). I can also easily create ssh and samba connections, so I'm not sure what the problem is.

Any help is appreciated!

---

### Post by jonathanmotes on 2007-11-16
Someone has got to know how to use mount.cifs! Come on guys!

Well, I've made little progress. I noticed that I was doing things in the last post in the wrong order. I entered mount.cifs in the terminal. This is the Usage line:```
mount.cifs <remotetarget> <dir> -o <options>
```

So now I am trying this:```
sudo mount.cifs //xxx.xxx.xxx.xxx/home/myusername /home/myusername/Desktop -o user,sync,domain=MYDOMAIN,user=myusername,uid=1000,gid=1000,file_mode=0600,dir_mode=0700,noperm
```

But now I am getting this:```
myusername@myusername-laptop:~$ sudo mount.cifs //xxx.xxx.xxx.xxx/home/myusername /home/myusername/Desktop -o user,sync,domain=MYDOMAIN,user=myusername,uid=1000,gid=1000,file_mode=0600,dir_mode=0700,noperm
[sudo] password for myusername:
Password: 
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

I'm sure this is something simple, please help!

---

