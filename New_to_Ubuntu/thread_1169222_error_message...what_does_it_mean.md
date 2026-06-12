---
title: "error message...what does it mean"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by SLEEPER_V on 2009-05-24
> E: openafs-modules-dkms: subprocess post-installation script returned error exit status 3
Thats the error message i get when I try to install virtualbox or anything really. Any ideas?

---

### Post by lisati on 2009-05-24
What happens when you run the following from the terminal?
```
sudo dpkg --configure -a
```

---

### Post by SLEEPER_V on 2009-05-25
> Setting up openafs-modules-dkms (1.4.9.dfsg1-0+ubuntu3) ...

Error! DKMS tree already contains: openafs-1.4.9
You cannot add the same module/version combo more than once.
dpkg: error processing openafs-modules-dkms (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 openafs-modules-dkms this

---

### Post by Didius Falco on 2009-05-25
Here is a bug report listing a possible fix:

[https://bugs.launchpad.net/ubuntu/+source/openafs/+bug/288743](https://bugs.launchpad.net/ubuntu/+source/openafs/+bug/288743)

Here is a PPA linked from that bug report that claims to have a fix for it.

[https://launchpad.net/~anders-kaseorg/+archive/ppa]("https://launchpad.net/%7Eanders-kaseorg/+archive/ppa")

Note: I don't use this, I don't know if this fix works, I don't take any responsibility, I just know how to google bug reports. <G>

Good Luck!!

Regards,

Didius

---

### Post by SLEEPER_V on 2009-05-25
I fixed it.  Apparently in my zeal to set up virtualbox I downloaded open afs - modules - dkms and it was throwing that error.  I removed that program and reinstalled dkms and viola.

Thanks for the suggestion, though.  If I read the error message more thoroughly this wouldnt have happened

---

