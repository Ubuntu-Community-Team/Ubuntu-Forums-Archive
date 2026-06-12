---
title: "smbmount wont find my share"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by m1 grant on 2007-06-10
I'm trying to setup a backend for mythtv on a headless server to save its recordings on another server that has the most harddrive space. I've used smbmount \\\\\hohenheim\\Volume_2\\mythtv_recordings /mythtv_recordings which is a previously made folder on that servers. For some reason this only works when I don't include \\mythtv_recordings. I really don't want to store all recordings in that volume's main directory because it stores other things in there as well so I would really like to know why it doesnt pick up a folder deeper within the heirarchy

---

### Post by m1 grant on 2007-06-10
BTW the server is an embedded NAS device (DNS 323) which is basically a samba server with each hard drive having a a share named "Volume_x". Don't see why it should matter, but it might help

---

### Post by dmizer on 2007-06-10
please post the output of smbtree

---

### Post by m1 grant on 2007-06-10
> 
marcus@ed:/mythtv_recordings$ smbtree
Password:
MDJ NET
        \\ANETTE                        Mom's Laptop
                \\ANETTE\Printer                hp photosmart 7900 series
                \\ANETTE\hpcolorL               hp color LaserJet 2550 PCL 6 (1)
                \\ANETTE\shared
                \\ANETTE\Morrowind
                \\ANETTE\print$                 Printer Drivers
                \\ANETTE\SharedDocs
                \\ANETTE\IPC$                   Remote IPC
CENTRAL
        \\HOHENHEIM                     Network Server
                \\HOHENHEIM\lp                  USB Printer
                \\HOHENHEIM\ADMIN$              IPC Service (Network Server)
                \\HOHENHEIM\IPC$                IPC Service (Network Server)
                \\HOHENHEIM\Volume_2
                \\HOHENHEIM\Volume_1
                \\HOHENHEIM\web_page            Enter Our Web Page Setting
        \\ED                            Samba 3.0.24
                \\ED\IPC$               IPC Service (Samba 3.0.24)
                \\ED\marcus
marcus@ed:/mythtv_recordings$


CENTRAL is the workgroup all mythtv associated devices reside in.

---

### Post by dmizer on 2007-06-10
first ... install smbfs:
```
sudo aptitude install smbfs
```

then, try this command:
```
sudo mount -t cifs //hohenheim/Volume_2 /tmp/foo -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount --bind /tmp/foo/mythtv_recordings /mythtv_recordings
sudo umount /tmp/foo
```

where "foo" is a subfolder created by you in /tmp.  you should use cifs because otherwise you won't be able to transfer files larger than 2 gig.

---

### Post by m1 grant on 2007-06-10
what do you mean by /tmp/foo?

---

### Post by dmizer on 2007-06-10
> **m1 grant said:**
> what do you mean by /tmp/foo?

you're temporarily mounting the root share in /tmp/foo ... this can actually be any directory you like because it's only purpose is to gain access to the root share so you can bind the desired directory.

so in /tmp add a directory foo:
```
sudo mkdir /tmp/foo
```

again ... "foo" can be anything you like.  for more information ... [http://en.wikipedia.org/wiki/Foo](http://en.wikipedia.org/wiki/Foo)

---

### Post by m1 grant on 2007-06-10
```
sudo mount -t cifs //hohenheim/Volume_2 /tmp/foo -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

when I try this I get
```
 
No ip address specified and hostname not found
marcus@ed:~$ mount error: could not find target server. TCP name hohenheim/Volume_2 not found

```

---

### Post by m1 grant on 2007-06-10
this is after I mkdir'd /tmp/foo BTW

---

### Post by m1 grant on 2007-06-10
actually I managed to mount stuff foo like you said, but I'm still confused, is /myth_recordings now mounted to that network share?

---

### Post by m1 grant on 2007-06-10
NVM I'm an idiot I just figured it out.

Thanks ALOT!!!!!

---

### Post by dmizer on 2007-06-10
lol ... sorry i had to step away for a bit and didn't have a reply for you.  glad you got it nailed down though.

---

