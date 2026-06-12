---
title: "Help...cannot update 11.04"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by packrat on 2011-05-31
Advisory says check Internet Connection...obviously, internet connection works...same with two computers over same connection???

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb) 404  Not Found [IP: 91.189.92.166 80]

---

### Post by mdbelt on 2011-05-31
I'm getting this too.  Breaks update & upgrade.

Failed to fetch
[http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_i386.deb)
404 Not Found [IP: 91.189.92.166 80]
Failed to fetch
[http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_i386.deb)
404 Not Found [IP: 91.189.92.166 80]
Failed to fetch
[http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb)
404 Not Found [IP: 91.189.92.166 80]

---

### Post by f37u5g0d on 2011-05-31
Try using different servers.  System -> Admin -> Software Sources in Ubuntu classic.  Power Button -> System Settings -> Software Sources in unity.  Use the 'select best server' tool thingy.

---

### Post by mdbelt on 2011-05-31
Someone really screwed up the entire community.  I see the forums are coming alive with reports.

[http://ubuntuforums.org/showthread.php?t=1772230](http://ubuntuforums.org/showthread.php?t=1772230)

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/790538](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/790538)

---

### Post by stijnblommerde on 2011-06-01
OS: 11.04 natty

problem: could not update my software using update manager either.

solution: i used the suggestion [f37u5g0d]("http://ubuntuforums.org/member.php?u=390299") described above.

power button - system settings - software sources - download from - main server (instead of server for netherlands)

apparently the default "server for the netherlands" was down.

---

### Post by packrat on 2011-06-01
Same problem as yesterday...

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb) 404  Not Found [IP: 91.189.92.166 80]

---

### Post by Rubi1200 on 2011-06-01
I had this problem yesterday, but ran the update now and everything is back to normal.

Try this in the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by packrat on 2011-06-01
Thanks. Kept trying and it finally updated.

---

### Post by Rubi1200 on 2011-06-01
Excellent! Glad you got it sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

