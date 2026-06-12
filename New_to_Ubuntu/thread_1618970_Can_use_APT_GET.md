---
title: "Can use APT GET"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by zi0nee on 2010-11-11
Hey

when i try to use apt get update i get this error:

> Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  404 Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  404 Not Found [IP: 91.189.92.167 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
  404 Not Found [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/b](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/b)                                                                                                 inary-amd64/Packages.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-amd6](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-amd6)                                                                                                 4/Packages.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restri](http://security.ubuntu.com/ubuntu/dists/hoary-security/restri)                                                                                                 cted/binary-amd64/Packages.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/s](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/s)                                                                                                 ource/Sources.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binar](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binar)                                                                                                 y-amd64/Packages.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sour](http://archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sour)                                                                                                 ces.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restri](http://security.ubuntu.com/ubuntu/dists/hoary-security/restri)                                                                                                 cted/source/Sources.gz  404 Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/sourc](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/sourc)                                                                                                 e/Sources.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-](http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-)                                                                                                 amd64/Packages.gz  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/universe/source/](http://archive.ubuntu.com/ubuntu/dists/hoary/universe/source/)                                                                                                 Sources.gz  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used                                                                                                  instead.
and i can neither upgrade or install programs..

any ideas?

Martin.

---

### Post by bioterror on 2010-11-11
Answer is this.

> Ubuntu 5.04 (Hoary Hedgehog), released on 8 April 2005,[11][12] was Canonical's second release of Ubuntu. Ubuntu 5.04's support ended on 31 October 2006.

---

### Post by atomizer on 2010-11-11
never mind my anwser

---

### Post by ibizatunes on 2010-11-11
You version is WELL out of date!
Download ubuntu 10:04 lts and install that!

---

### Post by coffeecat on 2010-11-11
Ah! A trip down memory lane. Hoary Hedgehog. :nostalgic sigh: :wink:

> **zi0nee said:**
> any ideas?

Yes. That version of Ubuntu was released in 2005 and went end-of-life (=unsupported) over 4 years ago. 

If you want to run a more recent and supported version of Ubuntu, have a look here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

And don't forget to ask any questions you need. Good luck!

---

### Post by toekneewood on 2010-11-11
If you are behind a proxy and are trying to install from the command line then you need to have a go at one of the following.  You will need to edit the (domain,user,password,IP and port number)

How to use apt-get behind proxy server
OPTION 1
```

export http_proxy=http://username:password@192.168.1.1:8080
export ftp_proxy=http://username:password@192.168.1.1:8080/

```

OPTION 2
```

sudo gedit /etc/bash.bashrc
#proxy 
export http_proxy=http://MYDOMAIN\user:password@192.168.1.1:8080/
export ftp_proxy=http://user:pass@192.168.1.1:8080/

```

OPTION 3
```

sudo gedit /etc/apt/apt.conf, I added the line:
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"

```

OPTION 4
```

in /etc/apt/apt.conf 
or
in /etc/bash.bashrc
 
ACQUIRE {
http::proxy “http://172.16.1.71:8080/”
}
 
#If you need to authenticate use
 
ACQUIRE {
http::proxy “http://DOMAIN\username:Password@FQDN.or.IP:8080/”

```

---

### Post by bioterror on 2010-11-11
> **toekneewood said:**
> If you are behind a proxy and are trying to install from the command line then you need to have a go at one of the following.  You will need to edit the (domain,user,password,IP and port number)

How to use apt-get behind proxy server
OPTION 1
```

export http_proxy=http://username:password@192.168.1.1:8080
export ftp_proxy=http://username:password@192.168.1.1:8080/

```

OPTION 2
```

sudo gedit /etc/bash.bashrc
#proxy 
export http_proxy=http://MYDOMAIN\user:password@192.168.1.1:8080/
export ftp_proxy=http://user:pass@192.168.1.1:8080/

```

OPTION 3
```

sudo gedit /etc/apt/apt.conf, I added the line:
Acquire::http::Proxy "http://MYDOMAIN\MYNAME:MYPASS@MY.PROXY.COM:MYPORT"

```

OPTION 4
```

in /etc/apt/apt.conf 
or
in /etc/bash.bashrc
 
ACQUIRE {
http::proxy “http://172.16.1.71:8080/”
}
 
#If you need to authenticate use
 
ACQUIRE {
http::proxy “http://DOMAIN\username:Password@FQDN.or.IP:8080/”

```

And you really didnt read my posting which was post #2? ](*,)

---

### Post by toekneewood on 2010-11-11
> **bioterror said:**
> And you really didnt read my posting which was post #2? ](*,)
That's because I was reading the comment "and i can neither upgrade or install programs.." at  #1.  So I take it the user will not be able to do a UPGRADE from an out of date version.  I think [zi0nee]("http://ubuntuforums.org/member.php?u=1185694") was hoping that it would replace the OS by doing an upgrade.  As I have never had to do this myself I and you comment #2 did not actually say that it is NOT possible to upgrade from out of date versions, i was attempting to fix the 404 error.__

---

### Post by zi0nee on 2010-11-11
Thanks for all the great answers :),

Is there anyway to upgrade the system to newest(10.10 i think?) without  reinstall of the system, its because its an rented server so i don't have physical contact to the server :)

- zi0nee

---

### Post by kroq-gar78 on 2010-11-11
this is how you update:

press ALT-F2 and type
```
update-manager -d
```

there should be an option saying "upgrade to latest version" or something like that at the top of the window. It will take some time and 1 reboot, but that's it.

---

### Post by mcduck on 2010-11-11
> **zi0nee said:**
> Thanks for all the great answers :),

Is there anyway to upgrade the system to newest(10.10 i think?) without  reinstall of the system, its because its an rented server so i don't have physical contact to the server :)

- zi0nee

yes, there is, but it's going to require a few tricks and lots of work since you can't jump versions when upgrading (apart from LTS version to next LTS version). Instead you'd have to do a bunch of upgrades.

5.04->5.10->6.06LTS->8.04LTS->10.04LTS ->10.10

(6.06 is still supported on servers until next June, so things get a bit easier once you get to that version)

In the end a fresh install is still most likely easier way to go. But if you wish to go for the upgrade route, here's a guide for upgrading out-of-support releases: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

