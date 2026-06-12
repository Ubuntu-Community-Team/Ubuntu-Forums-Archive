---
title: "issue with worng settings"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by nnamdi on 2009-08-12
hello friends i gave my laptop to a friend but when he brought it back i found out that where he used the laptop they hada proxy there i have change everything i can change but i still have issue updating my synaptics manager. when i try to update i get this error

```

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

this is the proxy ‘proxy.aust-abuja.org’

---

### Post by LowSky on 2009-08-12
go to system>admin>sources

under a tab there will be an option for selcting your server.

sorry doing this from memory as im on a windows pc

---

### Post by fooman on 2009-08-12
well i don't know anything about proxys...but have you tried changing the server in synaptics repositories?

open synaptic (system > administration > synaptic package manager).
 
click on settings > repositories > ubuntu software tab

in the bottom section,  uncheck the cdrom option.

then just above that,  click the arrow at the end of the "download from:" box and try another server.  you can try the main server,  or click other > select best server...and ubuntu will try and find the best server for you.

like i said,  don't know if that will help with the proxy problem or not.

---

### Post by nnamdi on 2009-08-12
hello friends i gave my laptop to a friend but when he brought it back i found out that where he used the laptop they hada proxy there i have change everything i can change but i still have issue updating my synaptics manager. when i try to update i get this error

```

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-proposed/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘proxy.aust-abuja.org’

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

this is the proxy ‘proxy.aust-abuja.org’ how do i resolve these thank you

---

### Post by nikhilbhardwaj on 2009-08-12
its unlikely to help
he'll have to remove the proxy entry

---

### Post by nnamdi on 2009-08-12
No one has said anything yet about it still waiting

---

### Post by fooman on 2009-08-12
> **nnamdi said:**
> No one has said anything yet about it still waiting

this is a duplicate thread...there were a couple of responses in the other one:

[http://ubuntuforums.org/showthread.php?t=1238548](http://ubuntuforums.org/showthread.php?t=1238548)

---

### Post by nnamdi on 2009-08-12
the problem is that when ever i try updating it trys to connect via the proxy again after removing it from everywhere

```

. .bashrc
bash.bashrc

.profile


```


sudo apt-get update

```

pradeep@pradeep-laptop:~$ sudo apt-get update
0% [Connecting to proxy.aust-abuja.org] [Connecting to proxy.aust-abuja.org] [Co

```

---

