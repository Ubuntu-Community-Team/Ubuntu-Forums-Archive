---
title: "linux to linux samba"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by daveyiv on 2006-12-03
I am trying to get samba to work properly, and I can view the files and stuff in the directory shared on my fileserver, however I cannot write to it. I have tried setting its permissions to 777 and I still don't have write access to it. 

I am using this to mount the share

```
//spork/videos /media/shares/spork/videos smbfs auto,credentials=/etc/cred,uid=1000,umask=000,user 0 0
```


And this is my share in smb.conf
```
[data]
        writeable = yes
        path = /media/data
        force group = nogroup
        create mask = 0000
        force user = nobody
        directory mask = 0000
        public = yes
        browsable = yes
        available = yes
```

Does anyone know why I can't write to the directory from another linux machine?

Also, it will let me create a directory, but once it is created I cannot do anything to it, I can't write to it, I can't delete it, nothing.

---

### Post by daveyiv on 2006-12-03
anyone know?

---

### Post by stevieb on 2006-12-03
i'm having the same problem!

---

### Post by daveyiv on 2006-12-04
bump for a solution!

---

### Post by Iowan on 2006-12-05
Any help here?
[http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")
or the 3rd link in my sig?

---

### Post by mozetti on 2006-12-05
If it's for simple file-sharing, you can try using the "force user" option to treat every user that logs into that machine with an existing user on the host machine that does have write permission to the partition.

Or maybe you need to create users with the same username/pw on the host machine, and give those users write permission to the partition.

I'm just throwin' some ideas out here, because I'm dabbling with SAMBA myself. I used the HowTo here on the forums to configure SAMBA on my computer.

---

### Post by daveyiv on 2006-12-05
> **Iowan said:**
> Any help here?
[http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")
or the 3rd link in my sig?

Yeah, I tried both of those and still can't figure it out

---

### Post by dannyboy79 on 2006-12-05
you have force user as nobody, nobody has guest only access which obviously means that you can't write to it. i would think that this is your problem. also, i have heard that nfs is WAY faster than samba, so if you have 2 linux boxes why try to use samba?? also, why does your sahre point state /media/data when you are actually mounting the folder to /media/shares/spork/videos? i would look into these things and you should be set! if not post back and I can help ya somemore. I struggled with samba for a long time but finally have my ubuntu desktop, my xubuntu wireless laptop, my 2 xbox's, and my winbloz desktop all working right now. well except for some reason lately, when i try to view winxp thru xsmbrowser (thru xubuntu since it doesn't have nautilus) it states that it has no available shares but if I mount the folder using cifs it works fine. oh yeah, that's another thing, smbfs is being replaced by cifs, try that instead. it uses a slightly different fstab entry.

---

### Post by daveyiv on 2006-12-05
> **dannyboy79 said:**
> you have force user as nobody, nobody has guest only access which obviously means that you can't write to it. i would think that this is your problem. also, i have heard that nfs is WAY faster than samba, so if you have 2 linux boxes why try to use samba?? also, why does your sahre point state /media/data when you are actually mounting the folder to /media/shares/spork/videos? i would look into these things and you should be set! if not post back and I can help ya somemore. I struggled with samba for a long time but finally have my ubuntu desktop, my xubuntu wireless laptop, my 2 xbox's, and my winbloz desktop all working right now. well except for some reason lately, when i try to view winxp thru xsmbrowser (thru xubuntu since it doesn't have nautilus) it states that it has no available shares but if I mount the folder using cifs it works fine. oh yeah, that's another thing, smbfs is being replaced by cifs, try that instead. it uses a slightly different fstab entry.

Tried changing the force user to an account with admin access and it still didn't work. Anyway I am using samba because I need to share it with windows as well as linux. And as far as the shares conflicting directory names it's because i copied the wrong share out of smb.conf, I actually have 3 shares all the same with the exception of the directory being shared, so I just copied the wrong one.

---

### Post by Iowan on 2006-12-06
Have you tried the "Connect to Server" option from... Places??  For some reason, I have better luck that way - I haven't had to manually mount the share or change **fstab**.  
I'm probably mistaken (again), but I thought the **force user/group** affected only the permissions of the saved file - not whether or not the user has the permission to save the file.

---

### Post by daveyiv on 2006-12-06
> **Iowan said:**
> Have you tried the "Connect to Server" option from... Places??  For some reason, I have better luck that way - I haven't had to manually mount the share or change **fstab**.  
I'm probably mistaken (again), but I thought the **force user/group** affected only the permissions of the saved file - not whether or not the user has the permission to save the file.

Yeah, I tried that, same deal. The weirdest thing is that it works fine when I connect to it in Windows, I can write to it fine.

---

### Post by dannyboy79 on 2006-12-07
what kinf of filesystem is it? because if you do man fstab, uid= and umask aren't vaild options for ext3, those are only options applicable to fat32 also known as vfat. these are my fstab entries for both ext3 and vfat and I can write to them over samba just fine.
/dev/hdd1       /home/daniel/300gb-ext3 ext3    defaults        0       2
/dev/sda1       /home/daniel/400gb-ext3 ext3    defaults        0       2
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=u tf8,umask=0000  0       0

also, here would be important parts from my smb.conf, give them a try.
[global]
    netbios name = UBUNTU
    server string = Dans Linux Desktop
    workgroup = LINUX
    encrypt passwords = yes
#    guest ok = yes
    smb passwd file = /etc/samba/smbpasswd
   domain master = no
    local master = no
    preferred master = no
    os level = 35
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#   passdb backend = tdbsam
    null passwords = true
    username map = /etc/samba/username.map
#   name resolve order = wins lmhosts host bcast
    hosts allow = 127.0.0.1 127.0.1.1 192.168. EXCEPT 192.168.0.20
    hosts deny = 0.0.0.0/0
#   hostname lookups = yes
#   hosts equiv = /etc/samba/lmhosts 
#    map to guest = Bad User   
#    guest account = nobody
#    wins support = yes
#   smb ports = 139
    browse list = yes
    mangled names = yes
    default case = lower
    case sensitive = no
    preserve case = yes
    short preserve case = yes

;These are private shares that only 
[UBUNTUFILES]
    path = /home/daniel
    browseable = yes
    read only = no
    guest ok = yes
    valid users = %U root
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel
    available = yes
    public = yes
    writable = yes

[lptp-backups]
    path = /home/daniel/400gb-ext3/laptop-backups
    available = yes
    browseable = yes
    public = yes
    writable = yes
    read only = no
    guest ok = yes
    valid users = %U root
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel

;These are shares that everyone can access, even guests
[music]
    path = /home/daniel/fat32/music
    browseable = yes
    writable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel
    available = yes
    public = yes

[movies]
    path = /home/daniel/fat32/movies
    browseable = yes
    writable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel
    available = yes
    public = yes

[PICS]
    path = /home/daniel/fat32/pics
    available = yes
    browseable = yes
    public = yes
    writable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = daniel
    force group = daniel

good luck!

---

### Post by daveyiv on 2006-12-07
they are XFS filesystem, does that make much difference as far as how I have it configured?

---

### Post by dannyboy79 on 2006-12-07
well, the same applies regarding what I stated before. those options you have in your fstab only apply to vfat. just do man mount, and you can see the applicable options for each filesytem. also, can you write to the folder normally? are the usernames and passwords the same on both of the machines?? I know mine are. i actually run xubuntu on my old laptop, since it doesn't have nautilus I installed xsmbrowser (a smb browser) and when I start the program from the terminal, I can actually see all the commands in the background and what is failing etc etc. which helped me troubleshoot some of the samba problems I had in the begining. just do sudo apptitude install xsmbrowser, then from a command line, just type in xsmbrowser and it should bring up the gui smb browser. then when you click on samba default, you could move the gui to the side and check out your terminal to see what the messages are about when you try to mount and write to 1 of the shares on your other computer. just a thought.

---

### Post by daveyiv on 2006-12-07
When I am writing to the samba shares from windows it is also ridiculously slow. Any idea what would cause this? FTP is a ton faster. With samba i get about 1MB/s and FTP I get 10MB/s

---

