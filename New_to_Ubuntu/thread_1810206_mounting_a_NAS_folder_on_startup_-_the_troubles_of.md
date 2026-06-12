---
title: "mounting a NAS folder on startup - the troubles of a newbie"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by Witra on 2011-07-22
Hi.

I got around 9 hours of experience with ubuntu right now(hence the absolute beginner forum), and I'm trying to get it to automatically mount a folder on my NAS(smb://datakori/share, datakori being my NAS at 192.168.0.101) on startup, but having trouble.

I've been searching for answers for the past four hours, but everything I found was above my level of expertise, thus I decided to post here. So far I've figured the simplest way to do this might be with either fstab or rc.local, but that's about as far as I've gotten, since I found myself unable to understand the examples I found with google well enough, even after reading enough man pages to get a headache.

So, I'd really appreciate it if someone could take few minutes and explain just exactly how I could mount the aforementioned folder into my home folder.

Thanks

---

### Post by papibe on 2011-07-22
Which version of Ubuntu are you running?
Did you install samba already?

Regards.

---

### Post by doas777 on 2011-07-22
well, there are a couple options:
1) mount the folder at boot
2) mount the folder at login

to mount on boot, you need to add the share to your /etc/fstab file. 
Check these out:
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

or for login, create a script file with a command like this:
```
[FONT=Courier New]
#!/bin/bash
mount -t smbfs -o username=username,password=password //server/share /local/mount/point/[/FONT]
``` 
(editing each parameter for your system). then call the script from startup applications with a command like: 
```
gksu <path/to/script>
```.

also make sure your script file is executable 
```
sudo chmod u+x <path/to/script>
```

also note that /local/mount/point must exist and be accessible before you can mount to it.

---

### Post by e79 on 2011-07-22
**doas777** is right, however :

> **doas777 said:**
> 
```
[FONT=Courier New]
#!/bin/bash
mount -t smbfs -o username=username,password=password //server/share /local/mount/point/[/FONT]
```
SMBFS is deprecated and CIFS should be used instead

Install CIFS:
```
sudo apt-get install smbfs
```  (odd but yeah, tis will install CIFS)

Mount your share:
```
sudo mount -t cifs -o user=username,password='password' //server/share /local/mountpoint
```

---

### Post by Witra on 2011-07-23
> **doas777 said:**
> 
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)

That was exactly what I was looking for, worked quite well. Raises the question of how I managed to not find it earlier.. Ah well.. 

Thanks, to all three of you. :)

---

### Post by e79 on 2011-07-23
No sweat,

please mark the thread as solved if you feel you don't need any more help.

Regards

---

