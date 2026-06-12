---
title: "Update problems (connection problems !)"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by alihmohd on 2009-10-09
[B]Am new to Ubuntu 9.04 and am trying to update or install new packages and this message is shown, can any one help:

Regards,

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/B]

---

### Post by alihmohd on 2009-10-09
Thx ppl Found the solution. :D
Cheers

---

### Post by taavikko on 2009-10-09
> **alihmohd said:**
> Thx ppl Found the solution. :D
Cheers

1. Please tell the solution, if others suffer from the same issue, it could help them also.

2. Please then mark the thread solved by using thread tools. so others could see, look 1.

---

### Post by alihmohd on 2009-11-07
Sorry for the Delay, 
the solution was that our University ?Network has a Proxy Connection to the Internet therefore, I've add the Proxy settings to the Network Proxy found in :
systems -> Preferences -> Proxy settings, then depending on the tech. info. I 've added the details in the automatic proxy configuration and Wallah  ... it worked perfectly :)

Cheers, all

---

