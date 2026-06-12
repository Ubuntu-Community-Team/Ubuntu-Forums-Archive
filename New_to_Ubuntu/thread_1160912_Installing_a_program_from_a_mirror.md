---
title: "Installing a program from a mirror"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by gemm on 2009-05-16
Hi,

I am trying to install a program (R for statistical computing). I have added this line:

deb [http://cran.at.r-project.org]("http://cran.rakanu.com/")[/bin/linux/ubuntu]("http://%3cmy.favorite.cran.mirror%3e/bin/linux/ubuntu") intrepid/

in my /etc/apt/sources.list file. However when I "Reload", I get the following Error message:
[W: GPG error: http://cran.at.r-project.org intrepid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821]("http://cran.rakanu.com/")

I have tried different mirror sites, but the result is the same. There is nothing written about public keys on the download of the program:
[http://cran.at.r-project.org/](http://cran.at.r-project.org/)

Then, I have tried after I added the line to the /etc/apt/sources/list file not pressing "Reload", but "Close", and I have written in the console:
sudo apt-get update
but I received similar message again:

....
Reading package lists... Done
W: GPG error: [http://cran.rakanu.com](http://cran.rakanu.com) intrepid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821
W: You may want to run apt-get update to correct these problems

Do you know what the problem is, and what should I do? Thanks in advance.

---

### Post by spiderbatdad on 2009-05-16
```
gpg --keyserver keyserver.ubuntu.com --recv D67FC6EAE2A11821
gpg --export --armor key_id | sudo apt-key add -

```

---

### Post by gemm on 2009-05-16
> **spiderbatdad said:**
> ```
gpg --keyserver keyserver.ubuntu.com --recv D67FC6EAE2A11821
gpg --export --armor key_id | sudo apt-key add -

```

Thanks, it worked :).

---

### Post by spiderbatdad on 2009-05-16
small mistake i trust you figured out:
```
gpg --keyserver keyserver.ubuntu.com --recv D67FC6EAE2A11821
gpg --export --armor **D67FC6EAE2A11821 **| sudo apt-key add -
```

---

### Post by gemm on 2009-05-16
> **spiderbatdad said:**
> small mistake i trust you figured out:
```
gpg --keyserver keyserver.ubuntu.com --recv D67FC6EAE2A11821
gpg --export --armor **D67FC6EAE2A11821 **| sudo apt-key add -
```

Yes, I have done this exactly like that, when it didn't happen with the first try :).

---

