---
title: "/home/alex/Desktop/thunderbird-2.0.0.21.tar.gz"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Alex82 on 2009-03-31
Ok I have the above mentioned tar file on my desktop, but I am having real problems extracting and installing it.  I just cant get it to work? I have tried moving it to opt and home but with no success, I would also like to replace the evolution tab with a thunderbird tab on my task bar.
cheers

---

### Post by PukingPenguin on 2009-03-31
Is there a reason you don't want to use the version in the repos? (pretty sure t-bird is there, correct me if I'm wrong...)

---

### Post by sisco311 on 2009-03-31
yep, thunderbird 2.0.0.21 is in the repos.
[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")
[uhelp]community/InstallingSoftware[/uhelp]

---

### Post by Alex82 on 2009-03-31
It's there but not sure if its the newest version and have always just downloaded straight from Mozilla in the past so I guess its a habbit.

---

### Post by PukingPenguin on 2009-03-31
> **Alex82 said:**
> It's there but not sure if its the newest version and have always just downloaded straight from Mozilla in the past so I guess its a habbit.

Well, then this should be old hat...


```
sudo mv /home/alex/Desktop/thunderbird-2.0.0.21.tar.gz /opt/thunderbird-2.0.0.21.tar.gz && tar -zxvf /opt/thunderbird-2.0.0.21.tar.gz
```
From there it's just a matter of finding the installer (probably /opt/thunderbird/thunderbird installer) and running it.

---

### Post by sisco311 on 2009-03-31
> **Alex82 said:**
> It's there but not sure if its the newest version and have always just downloaded straight from Mozilla in the past so I guess its a habbit.

Your package manager should show the version of the package.

In a terminal you can run:
```
aptitude show thunderbird
```

Or you can check it out here:
[http://packages.ubuntu.com/hardy/thunderbird]("http://packages.ubuntu.com/hardy/thunderbird")

---

### Post by Alex82 on 2009-03-31
> **PukingPenguin said:**
> Well, then this should be old hat...


```
sudo mv /home/alex/Desktop/thunderbird-2.0.0.21.tar.gz /opt/thunderbird-2.0.0.21.tar.gz && tar -zxvf /opt/thunderbird-2.0.0.21.tar.gz
```
From there it's just a matter of finding the installer (probably /opt/thunderbird/thunderbird installer) and running it.

Its a habit from windows days. I'm pretty new to ubuntu.

---

### Post by PukingPenguin on 2009-03-31
> **Alex82 said:**
> Its a habit from windows days. I'm pretty new to ubuntu.
Ah. That makes more sense....Seriously, i'd recommend using the package manager, at least to start. It really is one of the best things about Linux and Ubuntu. All your software is updated by one application!

---

### Post by Alex82 on 2009-04-02
> **sisco311 said:**
> Your package manager should show the version of the package.

In a terminal you can run:
```
aptitude show thunderbird
```

Or you can check it out here:
[http://packages.ubuntu.com/hardy/thunderbird]("http://packages.ubuntu.com/hardy/thunderbird")

That command opens thunderbird.
How do I now get an icon to run it on the ubuntu bar?

---

