---
title: "ssh network mounting"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-01-04
Hi everyone,

Ive been trying to get a network drive to auto mount on login / boot with ssh.
im getting a fuse error. not really sur what to do about it.

heres my input/output

```
romanhtpc@romanhtpc-desktop:~$ sudo sshfs romanmain@192.168.1.102: /mnt/sda "/mnt/sdamain"
The authenticity of host '192.168.1.102 (192.168.1.102)' can't be established.
RSA key fingerprint is 75:65:ef:2b:0b:74:9d:cc:46:7e:b2:e8:69:59:fd:03.
Are you sure you want to continue connecting (yes/no)? yes
romanmain@192.168.1.102's password: 
fuse: invalid argument `/mnt/sdamain'
romanhtpc@romanhtpc-desktop:~$ 
```

i dont really know what to do here.

also, does anyone know how to make this drive automount without password on startup.

thanks alot everyone.

---

### Post by stderr on 2009-01-04
Sorry, I don't have experience of mounting filesystems with sshfs (although I really should have... might look into it later). But it would appear to me, as a regular ssh user, that there shouldn't be a space after the colon...

```
sudo sshfs romanmain@192.168.1.102: /mnt/sda "/mnt/sdamain"
```
=>
```
sudo sshfs romanmain@192.168.1.102:/mnt/sda "/mnt/sdamain"
```

---

### Post by Archer Troy on 2009-01-04
no i still get the same error as before. ](*,)

---

### Post by albinootje on 2009-01-04
> **stderr said:**
> 
```
sudo sshfs romanmain@192.168.1.102:/mnt/sda "/mnt/sdamain"
```

Are you in the group "fuse" ?

Make that :
```

mkdir ~/sdamain
sshfs romanmain@192.168.1.102:/mnt/sda /home/romanmain/sdamain

```
Assuming that your Ubuntu desktop username is romanmain.
If not, change it accordingly in the /home/romanmain/sdamain part.

---

### Post by HermanAB on 2009-01-04
"fuse: invalid argument `/mnt/sdamain'"

Are you sure that the mount point /mnt/sdamain exists?  If not, create it:
$ sudo mkdir /mnt/sdamain

Cheers,

Herman

---

### Post by Archer Troy on 2009-01-05
Thanks for the reply guys

The mount point exists.

Im not sure if im in the "fuse group" - how would i find out?

---

### Post by albinootje on 2009-01-05
> **Archer Troy said:**
> 
Im not sure if im in the "fuse group" - how would i find out?

Type in the command :
```

groups

```

If you're not in the fuse group, then add your username to that, and make sure you log out (GUI or CLI) for your user, then log in again.
Check again with "groups" and check whether it works.

By the way, if you're the only one using sshfs, then it doesn't make sense at all to use sudo for that, hence my suggestion to make a mountpoint directory in your home directory in the example.

---

### Post by lazyart on 2009-01-05
try it without the quotes?

---

