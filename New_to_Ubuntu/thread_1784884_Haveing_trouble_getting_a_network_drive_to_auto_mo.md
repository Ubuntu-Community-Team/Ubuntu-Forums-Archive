---
title: "Haveing trouble getting a network drive to auto mount on ubuntu 11.04"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by jpayne21 on 2011-06-17
Hello i built a samba file server a while ago and it worked flawlessly with sharing with my two windows 7 computers. However i recently converted one of my windows 7 computers to Ubuntu 11.04. the install went fine and the computer works fine and when i go into network in my computer and click on my work group i can view the server and mount the drive how ever when i try to edit fstab and make the network drive auto mount. when i use the camand mount -a it returns with```
Mounting cifs URL not implemented yet. Attempt to mount smb://SERVER NAME.NETWORK NAME.com/sdb

``` and then nothing happens. i have tried multiple variations of what i enter in fstab and they all return with an error like the one above. what am i doing wrong

---

### Post by cariboo on 2011-06-17
Have you tried smbfs instead of cifs?

---

### Post by jpayne21 on 2011-06-17
i did and now im getting the error ```
Warning: mapping 'guest' to 'guest,sec=none'
Warning: ignoring deprecated smbfs option 'codepage=unicode'
Mounting cifs URL not implemented yet. Attempt to mount smb://192.168.1.104/sdb
```

---

### Post by Morbius1 on 2011-06-17
Do you actually have the expression "smb://....." in fstab? THat's not the correct syntax. Please post the output of the following command:
```
cat /etc/fstab
```

---

### Post by jpayne21 on 2011-06-17
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
smb://192.168.1.104/sdb  /data  smbfs  guest 0 0

```

i forgot to mention i removed the "codepage=unicode" but it dident help

---

### Post by Morbius1 on 2011-06-17
Give this a shot instead:

```
//192.168.1.104/sdb /data cifs guest 0 0
```

---

### Post by jpayne21 on 2011-06-17
now i get the error ```
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

``` the server in on a homegroup could that be effecting anything?

---

### Post by Morbius1 on 2011-06-17
You know I really should read original posts more carefully. You had an all Win7 lan and now you introduced a Ubuntu machine. And you're using homegroup as well.

Lordy, lordy..........

One question: you are asking specifically about automounting but can you mount the remote share through Network in Nautilus?

---

### Post by jpayne21 on 2011-06-17
i can i go in and click computer --> network --> windows network --> MSHOME --> SVR1 --> sdb

---

### Post by Morbius1 on 2011-06-17
I'll be darned.

OK, unmount the remote share and try this in a terminal:
```
 gvfs-mount smb://192.168.1.104/sdb
```What should happen is a mount icon will appear on your desktop and a mount point will be created in:
> /home/your-user-name/.gvfs/sdb on 192.168.1.104Can you confirm if that's what happens?

And is this an acceptable mount location?

---

### Post by jpayne21 on 2011-06-17
terminal says gvfs-mount is currently not installed so i installed it and ran that cammand it returned wit ```
Error mounting location: volume doesn't implement mount

```

---

### Post by Morbius1 on 2011-06-17
gvfs-mount is not installed? I don't know how that could happen.

Why do I feel like I'm going down a rat hole. If gvfs-mount was not installed then I'll bet that this wasn't either:
```
gvfs-fuse
```And I'm betting you are not a member of the fuse group either so fix that as well:
```
sudo gpasswd -a your-user-name fuse
```You're going to have to logoff ( not a reboot ) and logon again I'm afraid for the group memebership to change. Then run the gvfs-mount command again.

---

### Post by jpayne21 on 2011-06-17
gvfs-fuse was installed and it returned with the same error as before

---

### Post by Morbius1 on 2011-06-17
Are you sure 192.168.1.104 is the right ip address? That might explain this for both methods.

What happens when you access it with the hostname:
```
  gvfs-mount smb://SVR1/sdb
```Or maybe this ( don't remember how MS handles caps ):
```
gvfs-mount smb://svr1/sdb
```

---

### Post by jpayne21 on 2011-06-17
it replyed with the same error and the host name is in caps

---

### Post by Morbius1 on 2011-06-17
Is the remote share still mounted in nautilus?

---

### Post by jpayne21 on 2011-06-17
no, should it be?  is there a way to veiw how nautilus is connecting and repeat that in fstab

---

### Post by Morbius1 on 2011-06-17
Your corrected fstab entry should work as it is .
gvfs-mount should work as it is.

Right now the only thing that seems to be working is essentially this:
```
 nautilus smb://192.168.1.104/sdb
```

And I have no idea why.

---

### Post by jpayne21 on 2011-06-17
could it be a server problem? it shouldent be though because the server is formated to share the drive with anyone who connects to the network

---

### Post by Morbius1 on 2011-06-17
If it were a server problem then you could not access the share using this command:
```
  nautilus smb://192.168.1.104/sdb
```
But that' what you do when you go though Nautilus.

Actually what you are doing is:
```
  nautilus smb://svr1/sdb
```

---

### Post by jpayne21 on 2011-06-17
hmmm well if u get any ideas let me know

---

### Post by jpayne21 on 2011-06-17
hmmm well if u get any ideas let me know are there any packages that fstab and gvfs goes through or talk to about networking?

---

