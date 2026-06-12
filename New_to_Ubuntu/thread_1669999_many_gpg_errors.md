---
title: "many gpg errors"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by beew on 2011-01-18
I get these errors when trying to update my sources.

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: BADSIG F9A2F76A9D1A0061 Opera Software Archive Automatic Signing Key 2010 <packager@opera.com>
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


Please help. Thanks.

---

### Post by philinux on 2011-01-18
[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

---

### Post by beew on 2011-01-18
I followed the link and used the commad 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192 54422A4B98AB5139 F9A2F76A9D1A0061 40976EAF437D05B5 2EBC26B60C5A2783 A8A515F046D7E7CF
```

But it didn't work.

These are the outputs for the command above:

> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192 54422A4B98AB5139 F9A2F76A9D1A0061 40976EAF437D05B5 2EBC26B60C5A2783 A8A515F046D7E7CF
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: requesting key 98AB5139 from hkp server keyserver.ubuntu.com
gpg: requesting key 9D1A0061 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: requesting key 46D7E7CF from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 98AB5139: "Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>" 6 new signatures
gpg: key 9D1A0061: "Opera Software Archive Automatic Signing Key 2010 <packager@opera.com>" 6 new signatures
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 20 new signatures
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" 12 new signatures
gpg: key 46D7E7CF: public key "GetDeb Archive Automatic Signing Key <archive@getdeb.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 6
gpg:               imported: 1  (RSA: 1)
gpg:              unchanged: 1
gpg:         new signatures: 44


---

### Post by beew on 2011-01-20
I have no idea what happened. I added the key for getdeb.net and did "sudo update", lo and behold all the gpg errors (save one) are gone. I guess I should mark the thread as solved, though it would be nice if someone could explain what happened!

---

### Post by dhaneshr on 2011-10-26
Try doing this. It worked for me...
```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

---

### Post by ckankiewicz on 2012-01-30
> **dhaneshr said:**
> Try doing this. It worked for me...
```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

Thanks! This fixed me issues.

---

### Post by Macr237 on 2013-01-07
> **dhaneshr said:**
> Try doing this. It worked for me...
```

$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```

This fixed my issues as well. It took many searches #-o to come up with an answer that worked! 
Thanks for the solution.

---

