---
title: "407  Proxy Authentication Required"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by chaitu_021 on 2010-02-17
i am using ubuntu9.10. when iam trying to reload in synaptic package manager iam getting following error.plz help me.


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by s.fox on 2010-02-17
Hello,

Welcome to the forum.

I came across [this]("http://ubuntuforums.org/showthread.php?t=400210") old thread which looks similar to your problem.  I would try the suggestions discussed.

-Silver Fox

---

### Post by chaitu_021 on 2010-02-18
my system is not working with proxy.
and i also did the following settings

1. System->Preferences->Network Proxy-> Set : Direct Internet Connection.
2. System->Administration->Synaptic Package Manager->Settings->Preferences->Network-> Set : Direct Internet Connection.

still iam getting problem

---

### Post by misamisa2804 on 2010-02-19
Just open synaptic manager> settings > network> and fill MANUAL PROXY CONFIGURATION...(and don't forget to fill under AUTHENTICATION on the right-if you have password and username!!)

---

