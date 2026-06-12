---
title: "adding public key"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-05-22
this always confuses the heck out of me how do i add this public key. error report is from the update mgr

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
tks

---

### Post by kpkeerthi on 2009-05-22
In brief, run this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5

```

Detailed instructions can be found here:
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

---

### Post by rburkartjo on 2009-05-22
kp tks for your quick response that did the trick

---

### Post by clhsharky on 2009-05-22
Go here

[https://answers.launchpad.net/ubuntu/+question/71767](https://answers.launchpad.net/ubuntu/+question/71767)

---

### Post by mrhhug on 2011-05-24
> **kpkeerthi said:**
> In brief, run this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5

```

Detailed instructions can be found here:
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

+1 kpkeerthi

---

