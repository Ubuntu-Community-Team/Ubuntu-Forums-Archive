---
title: "What file sharing do you use? SMB/NFS/SSHFS"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by sitedesign on 2008-06-25
Do you set-up Linux file servers for multiple users?
If so, what do you prefer for your file sharing service.

1) SMB (Samba)
2) NFS (Linux native)
3) SSHFS (again Linux native and secure)
4) Other (Please specify)

I will edit this post to add links to my other posts about my findings for each.

I have been working on setting up Ubuntu file servers for several years now and tended to use Samba due to the networks having Windows clients.

Now I am starting to find customers asking for Linux clients so the networks are pure Ubuntu.

This poll should hopefully provide some insight to what is required to start making Ubuntu the perfect company desktop and server OS of choice. With simple HowTo's and tools for simple deployment and management.

---

### Post by earthmeLon on 2008-06-25
I like using Samba because it's really simple and works well with /etc/fstab mounting :D

When setting up samba, I do the following:
```

sudo adduser foo
sudo vim /etc/passwd

```

Then change the **/home/foo:/bin/bash** to **/home/foo:/bin/false**

```
sudo smbpasswd -a foo
vim /etc/samba/smb.conf

```

Edit this config file to your liking, but as an example I'll show you something in mine:

```
[Media]
    path = /media/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = foo
    force group = foo

```


Now, to add a samba server to your bootup, add something similar to your /etc/fstab file.

```

//Server/Downloads /media/Server/Downloads smbfs username=foo,password=bar

```

Hope this helps :D

**Edit:**
Haha, this doesnt help you at all, but, I still vote SAMBA

---

