---
title: "Can mount one NFS share, but not the other?"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by Ted_Smith on 2007-04-11
Hi

I've got myself into a bit of a pickle and hoping someone can straighten me out, 

I have two drives, both formatted as ext3. I have them mounted in home/ted/Mounts/ext3A and home/ted/Mounts/ext3B on my main unit which has an IP of 192.168.1.2 (192.168.1.1 is the router). 

I setup ext3A months ago as an NFS share with 192.168.0.0 - 255.255.255.0 having access to it and I made an entry in the /etc/exports file as follows : 

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/ted/Mounts/ext3A 192.168.1.0/255.255.255.0(rw)

```

I have been able to mount it from other Linux machines for months with 
```

sudo mount -t nfs 192.168.1.2:/home/ted/Mounts/ext3A ~/localShare

```

I can also map to it in Windows XP on my Windows laptop, although I cannot write to it. 

I then setup my second ext3 drive (ext3B) in the same way (as far as I can tell) and I added a similar line to exports so it now looks as follows : 

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/ted/Mounts/ext3A 192.168.1.0/255.255.255.0(rw)
/home/ted/Mounts/ext3B 192.168.1.0/255.255.255.0(rw)

```

but when I try to do an nfs mount from my other Linux machines I get 
```

mount : 192.168.1.2:/home/ted/Mounts/ext3B failed. Reason given by server : Permission Denied" 
```

Yet, ironically, I can map to it from my Windowx XP laptop without any trouble. What's worse (from a secuirty point of view) is that my entire home/ted folder is browsable from the Windows network which was not the case before (as far as I can remember)! All I want to achieve from the Windows point of view is to be able to browse ext3A and ext3B - I don't want everything open like that. I can't write to any of it, but it is all readable. 

So can anyone help me by explaining 

a) Why my ext3B drive cannot be access via NFS mounts and
b) why my entire home/ted folder is browsable as opposed to just ext3A and ext3B?

Thanks a lot

Ted

---

### Post by Ted_Smith on 2007-04-15
Is anyone able to offer any guidance with this? Thanks a lot

Ted

---

