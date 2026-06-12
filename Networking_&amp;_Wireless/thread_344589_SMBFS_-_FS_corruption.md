---
title: "SMBFS - FS corruption??"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by reech on 2007-01-23
Have a strange problem with smb mounts here on dapper server :

I am able to mount a network mount fine manually like so: 
```

smbmount //server01/fshare /root/newmount -o username=xxx,password=xxx
```


However when I add the mount to fstab it simply refuses to mount.  If I do ```
mount -a
``` once I have rebooted though it seems to corrupt the mount  point - giving the error :

```
unable to resolve mount point /root/newmount
```

I am then unable to list the dir that the mount point is located in or it shows up something like this:

```
?___?___?                newmount
```

my fstab entry looks like this:

```
//server01/fshare    /root/newmount  smbfs  auto,credentials=/root/.credentials      0      0
```

---

### Post by streeto on 2007-01-23
I turned to CIFS module because of some charset problems. Maybe you should try it.

Here is the entry in fstab:

//machine_name/mp3  /mnt/mp3        cifs   rw,auto,iocharset=iso8859-1,credentials=/etc/smbcredentials,file_mode=0666,dir_mode=0777       0       0

Hope this helps.

-st.

---

