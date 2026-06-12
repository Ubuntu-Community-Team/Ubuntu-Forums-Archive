---
title: "Mount Windows file share during startup"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by rats54 on 2008-07-06
Hi,

I am new to Linux and am having a problem mounting a Windows file share on a Ubuntu box during startup.  

I have a wired LAN with 9 computers on it.  One of the Windows boxes has a file on it that I want all of the other computers to access and have read/write permission automatically during their startup process. 

I  have found four ways to mount the share. The problem is none of them does the complete job. Three of the processes do not mount during startup. They require running *sudo mount -a*  from the terminal after they have finished booting. They do give me the permissions (760) I need.

The forth method automatically mounts the share during startup, but over-rides the permissions to a 744 level. That is not good.

I started by creating the mount point on an Ubuntu box (*/home/user/mount/point).* I did this as user. Then I did a chmod to set the permissions *(sudo chmod 760 /home/user/mount/point).*

Next I edited the /etc/fstab file to mount the share. These are the four processes I have that almost work:
1. ```
//192.1.1.30/share /home/user/mount/share smbfs rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0
``` 
2. ```
//192.1.1.30/share /home/user/mount/share smbfs credentials=/root/.smbcredentials,dmask=764 0 0
```
3. ```
//192.1.1.30/share /home/user/mount/share smbfs rw,default 0 
0
```
4. ```
//192.1.1.30/share /home/user/mount/share smbfs default 0 0
```

Methods 1-3 will not mount automatically during startup,but have the correct permissions when mounted manually.  Method 4 mounts automatically, but has the wrong permissions.

For method 2 I created a */root/.smbcredentials*  file that contains username and password information.

I would appreciate any suggestions or help that is offered to resolve this problem.

Thanks,

---

### Post by rats54 on 2008-07-10
This has been posted for over a week with no reply, but 70 lookers. Apparently there are others with the same problem, but no one with an answer.

Thanks for the help.

---

### Post by Efros on 2008-07-10
//192.168.1.199/e /media/pimage cifs auto,credentials=/etc/samba/creds,uid=1000,gid=100 0 0

I use this, the file credentials should contain your username and password. In the credentials file put two lines
username=username
password=password
make the file owned by root and ro by root (sudo chown root.root /etc/samba/creds && sudo chmod 400 /etc/samba/creds)

once you've entered this into fstab save and sudo mount -a

Hope that helps

---

### Post by rats54 on 2008-07-11
Thanks for the reply Efros, but that does not work either.

---

### Post by dmizer on 2008-07-11
see the second link in my sig.

---

