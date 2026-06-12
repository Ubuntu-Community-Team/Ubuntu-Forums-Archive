---
title: "Update Manager Error"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by Shellbak3 on 2010-12-16
I get an error when Update Manager runs.  When I click on "Check" I get the error below.  


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by oldos2er on 2010-12-16
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

---

### Post by Shellbak3 on 2010-12-17
Thanks, another little nagging thing resolved!  :p

(Like your photo)

---

