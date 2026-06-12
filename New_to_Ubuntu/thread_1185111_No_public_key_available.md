---
title: "No public key available"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-06-11
Hai,
   I accidently deleted the public key for the repositaries in synaptic.Now am stucked as i cant get some packages.Pls help me to fix it..

My output when i apt-get update

> W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs




so I cant get the packages from the following server.


> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://in.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.



                 any help is appreciated...

---

### Post by x33a on 2009-06-11
do this
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo aptitude update
```

---

### Post by balachandarlinks on 2009-06-11
> **x33a said:**
> do this
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo aptitude update
```
Thanks a lot x33a..problem solved....;-);-)

---

