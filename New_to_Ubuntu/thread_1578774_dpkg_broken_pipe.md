---
title: "dpkg broken pipe"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by bpogi on 2010-09-20
I'm about at my wit's end with this. I've searched the forums and Google and tried everything I could find in order to fix this, but I can't get apt and dpkg working correctly. Having already cleared the package cache and I keep getting the error:```
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

Sometimes it is accompanied by an error about a broken pipe. I would very much like to avoid forcing a purge or removal since the present package with which I have this issue is base-files. If I open aptitude and attempt to fix the currently broken dependencies, I get an error about a missing file in base-files. I'm not an absolute beginner, but I could really use some help right now.

---

### Post by NightwishFan on 2010-09-21
Give me the output of:
```
sudo apt-get update
```
and
```
sudo apt-get -f install
```

---

### Post by bpogi on 2010-09-21
"apt-get update" appears to work correctly. Doesn't give me any errors.

However:

```
# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  base-files
The following packages will be upgraded:
  base-files
1 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
1 not fully installed or removed.
Need to get 70.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main base-files 5.0.0ubuntu20.10.04.2 [70.2kB]
Fetched 70.2kB in 0s (91.5kB/s)
(Reading database ... 73498 files and directories currently installed.)
Preparing to replace base-files 5.0.0ubuntu20.10.04.1 (using .../base-files_5.0.0ubuntu20.10.04.2_i386.deb) ...
Unpacking replacement base-files ...
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

---

### Post by NightwishFan on 2010-09-21
It seems you will have to purge it somehow. Though I would wait for a second opinion before doing so.

---

### Post by bpogi on 2010-09-21
I tried purging the package cache by removing the *.bin files in /var/cache/apt and also I manually deleted the downloaded *.debs in /var/cache/apt/archives, which caused apt-get to redownload the files, but still ended in errors.

---

### Post by bpogi on 2010-09-21
Just took a look at /var/log/dpkg.log.

An excerpt:

```
2010-09-21 15:52:50 startup packages configure
2010-09-21 15:56:20 startup archives unpack
2010-09-21 15:56:20 upgrade base-files 5.0.0ubuntu20.10.04.1 5.0.0ubuntu20.10.04.2
2010-09-21 15:56:20 status half-installed base-files 5.0.0ubuntu20.10.04.1
2010-09-21 15:56:21 startup packages configure
```

I'm thinking it is very bad that base-files is half-installed.

---

### Post by NightwishFan on 2010-09-21
Reinstalling will not help I am sure, not by that manner. It is installing the package that is broken somehow, something is missing that it needs.

---

### Post by bpogi on 2010-09-21
Well, I just FUBAR'd the system by attempting a forced removal of base-files, which as I expected, had very negative consequences on the functionality of the system. I don't even know what state it's in since I was using SSH to administer it and I apparently rendered that non-functional.

---

