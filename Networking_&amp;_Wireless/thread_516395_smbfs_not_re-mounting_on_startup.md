---
title: "smbfs not re-mounting on startup"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by scaaryfast on 2007-08-03
Hi

I am trying to mount a windows share on a uni network using fstab.

I have made the following entry in fstab:

```

//<server> /media/share/ smbfs auto,credentials=/path/to/credentials,uid=1000,gid=1000,umask=000   0 0
```

Obviously, I've changed the server and password entry in the real thing.

If I enter that line in a fresh fstab and save it, I can mount the drive manually using:

```
mount /media/share/
```
If the machine has been rebooted with that line in fstab, then attempting to manually mount the drive waits for about 30 seconds before outputting:

```
Could not resolve mount point /media/homes/
```
Any ideas?

---

### Post by callan79 on 2007-08-03
> **scaaryfast said:**
> ```
//<server> /media/share/ smbfs auto,credentials=/path/to/credentials,uid=1000,gid=1000,umask=000   0 0
```

Howdy,

This reply might be totally useless, but I thought I'd post my fstab line, so you can try this and see if it works. This is in my home computer, to mount the smb share at work :

```

//server.mycompany.com/share        /media/officeshare      smbfs   noauto,defaults,username=callan,password=pass,dmask=0777,fmask=0777     0     0

```


So I guess the only two things that are different :

1. No trailing slashes ( / ) at the end of share and mountpoint names. I can't see this making a difference, but try it...

2. Try putting user/pass in the mount line like above - at least if that works, you know it might be an issue with the credentials line


Good luck!

Cheers
Callan

---

### Post by scaaryfast on 2007-08-06
Sorry, that was a typo - still no change!

Thanks for your reply.

---

