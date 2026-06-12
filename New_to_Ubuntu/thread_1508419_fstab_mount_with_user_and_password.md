---
title: "fstab mount with user and password"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-12
i know for a guest it is
//192.168.#.#/folder /home/user/folder cifs guest,auto 0 0

how do I add a user name and password? and still have it auto mount? not planing to write to it just want to see it and be able to copy from it.

---

### Post by apjone on 2010-06-13
```

gkduso gedit /root/cred-file

```

Add the following

```

username=windowsuser
password=windowspassword

```

Save & close, then add the following to fstab

```

//192.168.x.x/share /where/to/mount smbfs user,credentials=/root/cred-file,uid=linuxusername,gid=users,fmask=0770,dmask=0770 0 0

```


But putting the file under /root only super users will be able to see the saved username & password.

---

### Post by lance bermudez on 2010-06-13
why are you using smbfs? I was told that it was out dated and I should be using cifs. Was I told wrong?

---

### Post by lance bermudez on 2010-06-13
lance@bermudezl:~$ sudo mount -a
bad user name "linuxusername"
 
what did I do wrong?

---

### Post by lance bermudez on 2010-06-13
lance@bermudezl:~$ sudo mount -a
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.

i changed the uid to my uid because im the only user on this computer

---

### Post by lance bermudez on 2010-06-14
gkduso gedit /root/cred-file

needs to be

gkduso gedit /root/.cred-file

//192.168.#.#/music /home/acer/music       cifs auto,credentials=/root/.cred-file 0 0

thank you all for all your help. I did not know where to begine

---

