---
title: "can't add google earth"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by bigtiff on 2009-10-17
Hello guys, I am trying to add google earth to my aspire one: I downloaded the link from google earth home page but when i try and add it using K Pakage manager i get the following message: 

smart install -y  /media/disk/Downloads/GoogleEarthLinux.bin ;echo RESULT=$?
Loading cache...
error: Unable to create channel for file: /media/disk/Downloads/GoogleEarthLinux.bin

RESULT=1

Does anyone know what i'm doing wrong please?  I'd really like to add google earth, it's a great tool and my kids love using it.

All help appreciated, I'm pretty knew to Ubuntu so please explain in newbie terms if possible.

Thanks,

Jon

---

### Post by synapsys on 2009-10-17
Open up synaptic package manager and install the google earth package.

---

### Post by oldos2er on 2009-10-17
I know nothing of KPackage manager, but if it's anything like Synaptic, it only looks to the repositories for *deb files, not *bin files on your system.

 Here are a couple different methods of installing GE: [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by philinux on 2009-10-17
> **bigtiff said:**
> Hello guys, I am trying to add google earth to my aspire one: I downloaded the link from google earth home page but when i try and add it using K Pakage manager i get the following message: 

smart install -y  /media/disk/Downloads/GoogleEarthLinux.bin ;echo RESULT=$?
Loading cache...
error: Unable to create channel for file: /media/disk/Downloads/GoogleEarthLinux.bin

RESULT=1

Does anyone know what i'm doing wrong please?  I'd really like to add google earth, it's a great tool and my kids love using it.

All help appreciated, I'm pretty knew to Ubuntu so please explain in newbie terms if possible.

Thanks,

Jon

You need the medibuntu repo's then googleearth will be in the package manager.
[http://www.medibuntu.org/](http://www.medibuntu.org/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by wirate on 2009-10-17
see if this works
download the installer from google's site and type:

```
sh <path and filename of installer>
```

---

