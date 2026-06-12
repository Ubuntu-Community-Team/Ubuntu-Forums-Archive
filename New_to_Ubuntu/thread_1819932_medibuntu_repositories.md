---
title: "medibuntu repositories"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by expatCM on 2011-08-07
Has something changed with medibuntu?

I am getting a 404 error when I try to update and this applies to all my machines.  The repositories used are as suggested in the ubuntu.com page and in the Ubuntu guide as follows

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

I also obtain the same result if I change from the local repositories to United States or Main Server.

Is there any reason why?

---

### Post by gandaran on 2011-08-07
> **expatCM said:**
> Has something changed with medibuntu?

I am getting a 404 error when I try to update and this applies to all my machines.  The repositories used are as suggested in the ubuntu.com page and in the Ubuntu guide as follows

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

I also obtain the same result if I change from the local repositories to United States or Main Server.

Is there any reason why?
medibuntu is working fine here, maybe the servers where down for awhile or could be you have some network problem.

---

### Post by garvinrick4 on 2011-08-07
Medibuntu ppa is below:
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)

Keys if you need them:
Medibuntu key:
```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783

```
```
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by Gone fishing on 2011-08-07
In my /etc/apt/sources.list.d/medibuntu.list I have

```
deb http://packages.medibuntu.org/ natty free non-free
```

Did you follow the instructions on the medibuntu site? run terminal 

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by expatCM on 2011-08-07
This has been a problem for about six weeks so I find it hard to explain.  Especially since it affects multiple machines.

Yes, I have followed the instructions suggested on the medibuntu site.

The keys are already added but until the repository can be accessed there is no need of them.

I am in Thailand and I just hope this is not a new national initiative (a block) for something related to the medibuntu repository contents.

---

### Post by expatCM on 2011-08-07
Just to be thorough I ran the command from the medibuntu site again and then ran sudo apt-get update and the following errors appeared .... 

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

---

### Post by gandaran on 2011-08-07
> **expatCM said:**
> Just to be thorough I ran the command from the medibuntu site again and then ran sudo apt-get update and the following errors appeared .... 

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/user/ppa-medibuntu/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
this PPA is incorrect, it doesn't exist.

---

### Post by expatCM on 2011-08-07
well that explains one machine.  Deleted the ppa and apt-get returns to happiness.

Thank you for pointing out the obvious.

---

