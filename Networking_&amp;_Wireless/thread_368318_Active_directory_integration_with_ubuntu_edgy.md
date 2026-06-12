---
title: "Active directory integration with ubuntu edgy"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by eltidi on 2007-02-23
Hi, 

I'm trying to set up my computer to integrate with th domain of my company.
My problems comes when i try to install krb5-user and libpam-krb5.

I get a broken packages error.

this is the output of the command.


The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-9ubuntu1) but 1.4.3-9ubuntu1.1 is to be installed
             Depends: libkadm55 (= 1.4.3-9ubuntu1) but 1.4.3-9ubuntu1.1 is to be installed
E: Broken packages

---

### Post by spd106 on 2007-02-23
You need to add the universe security updates repository. 

Open the /etc/apt/sources.list file and look for the line starting deb [http://security.ubuntu](http://security.ubuntu)... then add 'universe' to the end. Like so
```
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe

```

---

### Post by eltidi on 2007-02-23
> **spd106 said:**
> You need to add the universe security updates repository. 

Open the /etc/apt/sources.list file and look for the line starting deb [http://security.ubuntu](http://security.ubuntu)... then add 'universe' to the end. Like so
```
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe

```


Many thanks, that solved it for me.

---

