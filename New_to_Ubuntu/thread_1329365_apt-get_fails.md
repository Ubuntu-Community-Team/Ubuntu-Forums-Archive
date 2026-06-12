---
title: "apt-get fails"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by spearo on 2009-11-17
Hello all
I am using Ubuntu 9.10
Still being fairly new to Linux, when i go to terminal and do sudo apt-get install (application) i always get the following reply:
[I]
liam@liam-desktop:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtonezone1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  thunderbird-gnome-support
The following NEW packages will be installed
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.6MB of archives.
After this operation, 39.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  thunderbird
Install these packages without verification [y/N]? y
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main thunderbird 2.0.0.23+build1+nobinonly-0ubuntu1
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_amd64.deb)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I]


I'm not sure if this is a common problem or not. I am on a proxy, but have all the network proxy setting set up, and have access to the internet via firefox, and emails. Synaptic package manager as well does not really work.

Any ideas as to what is causing this, or get around it will be greatly appreciated. Having Linux without the apt-get feature makes me feel almost crippled.

---

### Post by Paqman on 2009-11-17
Looks like it's definitely your proxy settings. Do you have your proxy set up system-wide, and for all protocols?

---

### Post by ukripper on 2009-11-17
Additional to Paqman's comment are you using privoxy?

And before installing can you try below command:```
sudo apt-get update
```

---

### Post by spearo on 2009-11-17
Yep, my proxy settings are system wide and for all protocols.

When i run sudo apt-get update this is the response:

[I]liam@liam-desktop:~$ sudo apt-get update
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/main Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/restricted Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/universe Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Packages
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-security/multiverse Sources
  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

---

### Post by nperry on 2009-11-17
Sorry unable to help with proxies - Might I suggest when you next copy an output could you enclose it within QUOTE tags. Makes it easier for people to look through the topic.

Thanks
Neil Perry

---

### Post by nitstorm on 2009-12-31
i have had a similar issue with my sudo apt-get update as well... some of the packages weren't getting updated, said " failed to retrieve package from the server" please do help out , have subscribed to this thread

---

### Post by Paqman on 2009-12-31
> **nitstorm said:**
> i have had a similar issue with my sudo apt-get update as well... some of the packages weren't getting updated, said " failed to retrieve package from the server" please do help out , have subscribed to this thread

Was it actually a proxy problem, or did it just fail to fetch the packages?

Try switching to a different server in System > Admin > Software sources. It can even search for the best server automatically.

---

### Post by nitstorm on 2009-12-31
Paqman that worked man :D my apt-get download speeds have improved to the maximum as well, i thought since i am in india the indian server would be best, seems the singapore server works best for me :D thanks a mil Paqman :D

---

