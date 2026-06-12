---
title: "trying to get the software sources working"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by sanitarium616 on 2010-05-01
hey
i instlled ubuntu 10.04 last night & i just got round to setting everything else up but stumbled on this problem i went to software sources to enable the resporitories but when i go to reload i get an error. 
the error is:
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release)  

could someone please help me
sani
ps
it seems to happen when i try to reload the update manager too

---

### Post by wojox on 2010-05-01
Run:

```

gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -; gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -; sudo apt-get update


```

---

### Post by sanitarium616 on 2010-05-01
kool all sorted 
thanks 
sani

---

### Post by wojox on 2010-05-01
Your Welcome.

---

