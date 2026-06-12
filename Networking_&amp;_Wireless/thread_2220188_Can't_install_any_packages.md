---
title: "Can't install any packages"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by ahmad6 on 2014-04-27
Hello,

I have installed a fresh copy of Ubuntu server 14.04 on vmware esxi but for some reason I cannot install any updates by issuing the following command:

```
sudo apt-get update
```

When I do issue the above command, i get the following erros:

```
[FONT=Menlo]Err http://security.ubuntu.com trusty-security InRelease[/FONT]

[FONT=Menlo]Err http://security.ubuntu.com trusty-security Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'security.ubuntu.com'[/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty InRelease[/FONT]

[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-updates InRelease[/FONT]

[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-backports InRelease[/FONT]

[FONT=Menlo]Err http://us.archive.ubuntu.com trusty Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-updates Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-backports Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]

```

Could someone help me solve this problem?

Thanks.

---

### Post by kakar on 2014-04-27
Maybe its a slow mirror problem. . . Try this ? - [http://blog.ubuntulinuxguide.com/2013/03/sudo-apt-get-update-error-slow-mirror.html](http://blog.ubuntulinuxguide.com/2013/03/sudo-apt-get-update-error-slow-mirror.html)

---

### Post by ahmad6 on 2014-04-27
> **kakar said:**
> Maybe its a slow mirror problem. . . Try this ? - [http://blog.ubuntulinuxguide.com/2013/03/sudo-apt-get-update-error-slow-mirror.html](http://blog.ubuntulinuxguide.com/2013/03/sudo-apt-get-update-error-slow-mirror.html)

I tried your suggestion, but looks like now I receive even a bigger error:

```
[FONT=Menlo]Err http://security.ubuntu.com trusty-security InRelease[/FONT]
[FONT=Menlo]  [/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty InRelease[/FONT]
[FONT=Menlo]  [/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-updates InRelease[/FONT]
[FONT=Menlo]  [/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-backports InRelease[/FONT]
[FONT=Menlo]  [/FONT]
[FONT=Menlo]Err http://security.ubuntu.com trusty-security Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'security.ubuntu.com'[/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-updates Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]Err http://us.archive.ubuntu.com trusty-backports Release.gpg[/FONT]
[FONT=Menlo]  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty InRelease[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates InRelease[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports InRelease[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security InRelease[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty Release.gpg[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates Release.gpg[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports Release.gpg[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security Release.gpg[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty Release[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates Release[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports Release[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security Release[/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/main amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/restricted amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/universe amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/multiverse amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/main i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/restricted i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/universe i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty/multiverse i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/main Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/main Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/multiverse Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/multiverse Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/restricted Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/restricted Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/universe Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty/universe Translation-en[/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/main amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/restricted amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/universe amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/multiverse amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/main i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/restricted i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/universe i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-updates/multiverse i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/main Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/main Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/multiverse Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/multiverse Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/restricted Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/restricted Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/universe Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-updates/universe Translation-en[/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/main amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/restricted amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/universe amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/multiverse amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/main i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/restricted i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/universe i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-backports/multiverse i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/main Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/main Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/multiverse Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/multiverse Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/restricted Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/restricted Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/universe Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-backports/universe Translation-en[/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/main amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/restricted amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/universe amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/multiverse amd64 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/main i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/restricted i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/universe i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Err mirror://mirrors.ubuntu.com trusty-security/multiverse i386 Packages[/FONT]
[FONT=Menlo]  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/main Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/main Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/multiverse Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/multiverse Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/restricted Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/restricted Translation-en[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/universe Translation-en_US[/FONT]
[FONT=Menlo]Ign mirror://mirrors.ubuntu.com trusty-security/universe Translation-en[/FONT]
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/main/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/restricted/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/universe/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/multiverse/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/main/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/restricted/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/universe/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/multiverse/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-updates/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/main/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/restricted/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/universe/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/multiverse/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-backports/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/main/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/restricted/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/universe/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/multiverse/binary-amd64/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/trusty-security/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]

```

---

### Post by kakar on 2014-04-28
u tried to change to a different mirror?
-------------

Ok I see you did.

---

### Post by ahmad6 on 2014-04-28
Hate to do this; BUMP.

I tried installing a fresh one on vmware fusion, i still get the same error. why can't I install anything?

the only thing I have done is to assign a static IP and renaming the vm by editing the following files: **hostname**, **hosts**, and **interfaces**

here is what each file look like:

File: /etc/hostname
```
ubuntu
```

File: /etc/hosts
```
[FONT=Menlo]127.0.0.1    localhost[/FONT]
[FONT=Menlo]192.168.1.50    ubuntu[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# The following lines are desirable for IPv6 capable hosts[/FONT]
[FONT=Menlo]::1     localhost ip6-localhost ip6-loopback[/FONT]
[FONT=Menlo]ff02::1 ip6-allnodes[/FONT]
[FONT=Menlo]ff02::2 ip6-allrouters[/FONT]

```

File: /etc/network/interfaces
```
[FONT=Menlo]# This file describes the network interfaces available on your system[/FONT]
[FONT=Menlo]# and how to activate them. For more information, see interfaces(5).[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# The loopback network interface[/FONT]
[FONT=Menlo]auto lo[/FONT]
[FONT=Menlo]iface lo inet loopback[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# The primary network interface[/FONT]
[FONT=Menlo]auto eth0[/FONT]
[FONT=Menlo]iface eth0 inet static[/FONT]
[FONT=Menlo]    address    192.168.1.50[/FONT]
[FONT=Menlo]    network 192.168.1.0[/FONT]
[FONT=Menlo]    netmask 255.255.255.0[/FONT]
[FONT=Menlo]    broadcast 192.168.1.255[/FONT]
[FONT=Menlo]    gateway 192.168.1.1[/FONT]

```

Can someone help out?

---

### Post by ian-weisser on 2014-05-03
Do you have any network connectivity at all?
Can you ping out to the internet?

---

### Post by ahmad6 on 2014-05-04
> **ian-weisser said:**
> Do you have any network connectivity at all?
Can you ping out to the internet?

I have 2 vm installed on this esxi server, on my other vm (Debian) I can ping out and have network connectivity, however, on this vm (ubuntu 14.04) I have no internet connectivity to the internet. I can ssh to it via my local network.

---

### Post by claracc on 2014-05-04
I observe, you don't have any dns-nameservers in the /etc/network/interfaces, try to add a line as ```
dns-nameservers 8.8.8.8
```, which are the google's one.

Please see this link: [http://draalin.com/setting-up-a-static-ip-address-in-ubuntu/](http://draalin.com/setting-up-a-static-ip-address-in-ubuntu/)

---

### Post by claracc on 2014-05-04
> **ahmad6 said:**
> So many linux users and no one knows what is wrong with this?

I think the question is not asked in the appropriate subforum, I think it would be better in the Networking & wireless one since I think the problem is the assignment of static ip.

---

### Post by mörgæs on 2014-05-04
Moved.

---

### Post by smss on 2014-05-04
In virutal machines, you have to set IP protocols in that icon (usually in right bottom of virtual window this appear).
Then, you should be able to ping [www.google.com](www.google.com) or 4.2.2.2 or 8.8.8.8 or your getway.
So, Could you ping google.com? if NOT, go for set the virtual network settings, otherwise you have to see your ubuntu version for checking supported or not.
So, open a terminal and type this command and paste the output here:
```

uname -a

```
Then, If everything is ok, this is possible that your sources.list gone with the wind and you have to clean temporary apt and set it from the first. Google it.

---

