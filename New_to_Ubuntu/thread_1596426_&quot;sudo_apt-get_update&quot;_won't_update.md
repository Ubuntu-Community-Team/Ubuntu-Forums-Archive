---
title: "&quot;sudo apt-get update&quot; won't update"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by MathMcC on 2010-10-14
Hi

When I try the above in a terminal I get the following error messages, so that basically I'm not able to dl anything:

```
Err http://security.ubuntu.com lucid-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (110: Connection timed out)
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
  Unable to connect to security.ubuntu.com:http:
Err http://archive.canonical.com lucid Release.gpg                             
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB       
  Unable to connect to archive.canonical.com:http:
Ign http://archive.canonical.com lucid Release                                 
Ign http://security.ubuntu.com lucid-security Release    
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://archive.canonical.com lucid/partner Packages  
Err http://gb.archive.ubuntu.com lucid Release.gpg       
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Ign http://gb.archive.ubuntu.com lucid Release
Ign http://gb.archive.ubuntu.com lucid-updates Release
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Ign http://archive.canonical.com lucid/partner Packages
Ign http://gb.archive.ubuntu.com lucid/main Packages
Ign http://gb.archive.ubuntu.com lucid/restricted Packages
Ign http://gb.archive.ubuntu.com lucid/main Sources
Ign http://gb.archive.ubuntu.com lucid/restricted Sources
Ign http://gb.archive.ubuntu.com lucid/universe Packages
Ign http://gb.archive.ubuntu.com lucid/universe Sources
Ign http://gb.archive.ubuntu.com lucid/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid/multiverse Sources
Ign http://security.ubuntu.com lucid-security/main Packages
Ign http://security.ubuntu.com lucid-security/restricted Packages
Ign http://security.ubuntu.com lucid-security/main Sources
Ign http://security.ubuntu.com lucid-security/restricted Sources
Ign http://security.ubuntu.com lucid-security/universe Packages
Ign http://security.ubuntu.com lucid-security/universe Sources
Ign http://security.ubuntu.com lucid-security/multiverse Packages
Err http://archive.canonical.com lucid/partner Packages
  Unable to connect to archive.canonical.com:http:
Ign http://gb.archive.ubuntu.com lucid-updates/main Packages
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://gb.archive.ubuntu.com lucid-updates/main Sources
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://gb.archive.ubuntu.com lucid-updates/universe Packages
Ign http://gb.archive.ubuntu.com lucid-updates/universe Sources
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com lucid/main Packages
Ign http://gb.archive.ubuntu.com lucid/restricted Packages
Ign http://gb.archive.ubuntu.com lucid/main Sources
Ign http://gb.archive.ubuntu.com lucid/restricted Sources
Ign http://gb.archive.ubuntu.com lucid/universe Packages
Ign http://gb.archive.ubuntu.com lucid/universe Sources
Ign http://gb.archive.ubuntu.com lucid/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid/multiverse Sources
Ign http://gb.archive.ubuntu.com lucid-updates/main Packages
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://gb.archive.ubuntu.com lucid-updates/main Sources
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://security.ubuntu.com lucid-security/multiverse Sources
Err http://security.ubuntu.com lucid-security/main Packages
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/restricted Packages
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/main Sources
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/restricted Sources
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/universe Packages
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/universe Sources
  Unable to connect to security.ubuntu.com:http:
Ign http://gb.archive.ubuntu.com lucid-updates/universe Packages
Ign http://gb.archive.ubuntu.com lucid-updates/universe Sources
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://gb.archive.ubuntu.com lucid/main Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/restricted Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/main Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/restricted Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/universe Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/universe Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/multiverse Packages
  Unable to connect to security.ubuntu.com:http:
Err http://security.ubuntu.com lucid-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to gb.archive.ubuntu.com:http:
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (110: Connection timed out)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_GB.bz2  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.gz  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  Unable to connect to security.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-amd64/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by MathMcC on 2010-10-14
I tried this suggestion: [http://ubuntuforums.org/showthread.php?p=9929861#post9929861](http://ubuntuforums.org/showthread.php?p=9929861#post9929861) But was told no suitable server was found. It seems that apt-get doesn't recognise my internet connection even though I have one and am surfing the net without a problem.

---

### Post by MathMcC on 2010-10-14
Oh [this]("http://ubuntuforums.org/showthread.php?t=1093272") seems to have worked. In fact the guy goes to the same university as me.

---

### Post by akumarb2010 on 2011-05-31
Hi,

I got into similar issue while doing "apt-get update"
root@AP-BGLR-UBUNTU02:/home/sysadmin# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (91.189.92.161). - connect (111: Connection refused) [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (91.189.92.161). - connect (111: Connection refused) [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.161 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

Can anybody suggest me abt this.
I did apt-get clear and all which suggested above

---

### Post by dazz100 on 2011-07-02
Hi

I get a similar problem with:

unable to connect to secuirty.ubuntu.com connection refused

I also had problems connecting to the ubuntu mirrors.  I had to try three (by editing /etc/apt/sources) before I could complete an installation.

I can't connect to get the security updates.  I don't have a web proxy.  I do have a normal internet connection that is able to connect to some mirrors, but not all the time.

This type of connection problem seems to be very common with Ubuntu apt.  Has someone raised a bug report????

---

### Post by wolfen69 on 2011-07-02
> **dazz100 said:**
> Hi

I get a similar problem with:

unable to connect to secuirty.ubuntu.com connection refused

I also had problems connecting to the ubuntu mirrors.  I had to try three (by editing /etc/apt/sources) before I could complete an installation.

I can't connect to get the security updates.  I don't have a web proxy.  I do have a normal internet connection that is able to connect to some mirrors, but not all the time.

This type of connection problem seems to be very common with Ubuntu apt.  Has someone raised a bug report????

Post the result of:
```
cat /etc/apt/sources.list
```

---

### Post by shuttleworthwannabe on 2011-07-03
> **MathMcC said:**
> Oh [this]("http://ubuntuforums.org/showthread.php?t=1093272") seems to have worked. In fact the guy goes to the same university as me.
Thanks for the pointer--I see you are using lucid; do you know if this would work for natty? I do not see why not, but just checking.```
acquire::http::proxy "http://username:password@wwwcache.university.ac.uk:8080
```
Why I ask, from maverick, I think, editing /etc/xx gave me trouble. I think it was editing xorg.conf (it does not have it in fact).

---

### Post by dazz100 on 2011-07-13
Hi

OK Here is the contents of my Sources.list

{code}
:/etc/apt$ cat sources.list
#
# Modified to get files from citylink.co.nz DFC  1/7/11
# deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid main restricted
deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-updates main restricted
deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid universe
deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid universe
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-updates universe
deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid multiverse
deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-updates multiverse
deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

{/code}

Took me a while because I was having problems with mounting a usb drive.

---

### Post by dazz100 on 2011-07-18
I found the problem.  I run IPCop firewall and the proxy server was enabled.  Once that was disabled, everything worked.

Dazz

---

