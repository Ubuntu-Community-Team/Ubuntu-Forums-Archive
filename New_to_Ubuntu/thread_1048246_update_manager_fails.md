---
title: "update manager fails"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by jfrelin on 2009-01-23
I am a newbie.  I have a Dell mini installed with 8.04.  My update does not run correctly.

I get the following error message:

GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22GPG error: [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9FDA6BED73CDC22GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz)  404 Not Found 
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz](http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz)  404 Not Found 
Some index files failed to download, they have been ignored, or old ones used instead.


Clearly I have done something wrong, but I can't figure out whathttp://ubuntuforums.org/images/smilies/icon_sad.gif.

Thanks

---

### Post by superprash2003 on 2009-01-23
try to change your update server in sys->admin->software sources

---

### Post by cwsnyder on 2009-01-23
As described, your error is that you did not get the encoding key to verify that the updates you are getting from the repository are legitimate and not spoofed.

You will probably have to either go back to the instructions you had for installing the repository, or if installed by the vendor, contact the vendor to get the proper instructions to get the GPG (security) key.

---

### Post by jfrelin on 2009-01-23
thanks for the replies

I  gave up and installed 8.10 that I had wanted to do anyway.

thanks again

---

