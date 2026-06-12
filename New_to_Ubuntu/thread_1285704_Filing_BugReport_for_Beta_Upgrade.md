---
title: "Filing BugReport for Beta Upgrade"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by thorsten muller on 2009-10-08
I just wanted to install the Kubuntu 9.10 Karmic Koala for Beta testing.
I followed instructions here:
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu)

Everything went fine until it was nearly finished downloading packages.
Then it stopped, telling me that those upgrades could not be found:

 p, li { white-space: pre-wrap; }  Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/a/automoc/automoc_1.0~version-0.9.88-2_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/a/automoc/automoc_1.0~version-0.9.88-2_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano-dev_2.3.0+dfsg.1-2~ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano-dev_2.3.0+dfsg.1-2~ubuntu1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/universe/a/adept/adept_3.0~beta7.2ubuntu3_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/a/adept/adept_3.0~beta7.2ubuntu3_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssrpc4_1.7dfsg~beta3-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssrpc4_1.7dfsg~beta3-1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkdb5-4_1.7dfsg~beta3-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkdb5-4_1.7dfsg~beta3-1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5srv6_1.7dfsg~beta3-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm5srv6_1.7dfsg~beta3-1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dev_1.7dfsg~beta3-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dev_1.7dfsg~beta3-1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/konversation/konversation_1.2~rc1-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/konversation/konversation_1.2~rc1-0ubuntu1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/libm/libmsn/libmsn0.1_4.0~beta6-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/libm/libmsn/libmsn0.1_4.0~beta6-1_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/q/qca2-plugin-ossl/libqca2-plugin-ossl_0.1~20070904-4_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/q/qca2-plugin-ossl/libqca2-plugin-ossl_0.1~20070904-4_i386.deb) 404 Not Found
 Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/q/quassel/quassel_0.5.0~rc2-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/q/quassel/quassel_0.5.0~rc2-0ubuntu1_i386.deb) 404 Not Found
 

My internet connection was working, there is enough diskspace etc.
Seems the packages are plainly not on the server.

No big issue for me, I just tried to test it a bit. But  I wanted to send a bug report, and read the information here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

But I somehow got lost there, since I'm not sure which package is responsible for the problem. So I don't know how or where to report that as a bug.
Can somebody point me to the right place, please?

---

### Post by shafin on 2009-10-08
You should file a bug against Update Manager and Apt/ Packagekit, depending on which one you used to upgrade.

---

### Post by ditsch on 2009-10-13
Seems that this was a temporary issue.

---

### Post by markbuntu on 2009-10-13
The servers get a little backed up at times so the connection fails. This will get worse in the next few weeks and when karmic is released so keep that in mind.

---

