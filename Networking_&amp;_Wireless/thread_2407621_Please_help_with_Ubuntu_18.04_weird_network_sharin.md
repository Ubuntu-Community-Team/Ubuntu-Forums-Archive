---
title: "Please help with Ubuntu 18.04 weird network sharing issues"
date: 2018-12-06
forum: Networking &amp; Wireless
---

### Post by pechius on 2018-12-06
So I have an Ubuntu 18.04 installed on an ssd and I have one 4tb drive(ext4). I've mounted that drive to /mnt/hdd and I have a few folders that I'm sharing with the network, which I need to access and write to from a Windows 10 pc. 
Long story short, I've setup network shares via GUI file manager, and everything seemed to be working fine(I've transferred about 1tb of data), but then I've lost write permissions(I get a message in windows: "You don't have permissions" when trying to copy a file), but then regained them, but now I've lost write permissioms to another folder... 

I don't see any entries related to my shared folders in smb.conf so I'm guessing this works differently?

Does anybody now what could be the problem here?

---

### Post by Morbius1 on 2018-12-06
>  I don't see any entries related to my shared folders in smb.conf so I'm guessing this works differently?
Please post the output of the following command:
```
net usershare info --long
```

---

### Post by pechius on 2018-12-06
```
info_fn: file /var/lib/samba/usershares/bandau is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[share1]
path=/mnt/user/share1
comment=
usershare_acl=Everyone:F,
guest_ok=n

[share2]
path=/mnt/user/share2
comment=
usershare_acl=Everyone:R,GROUP\user:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/labadiena is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/dalinuosi is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[share3]
path=/mnt/user/share3
comment=
usershare_acl=Everyone:R,GROUP\user:F,
guest_ok=n
```

Now I can access /mnt/user/share1 again. I wonder how long until another folder breaks.

---

### Post by Morbius1 on 2018-12-06
There's nothing wrong with the share definitions as long as:

** User django is the one writing to the share.
** You added that user to the samba password database: 
```
sudo smbpasswd -a django
```
** And that user has write permissions - Linux write permissions - to the /mnt/plex1/filmai folder.

Why it would work one moment and not the other I cannot explain either.

---

### Post by pechius on 2018-12-06
Yes, that's how it's set up.

---

