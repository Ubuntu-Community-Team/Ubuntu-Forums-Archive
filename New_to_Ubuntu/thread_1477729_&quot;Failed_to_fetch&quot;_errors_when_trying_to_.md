---
title: "&quot;Failed to fetch&quot; errors when trying to install software"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Zeophlite on 2010-05-09
I've just installed Ubuntu Server 10.04 onto my machine, and whenever I've tried to install just about anything, I get "Failed to fetch" errors.

Last night while [trying to install openssh-server]("http://ubuntuforums.org/showthread.php?t=1476877"), and then mysteriously it worked for no reason!

sudo apt-get install apache2
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap ssl-cert
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap ssl-cert
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,462kB of archives.
After this operation, 11.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)'
in the drive '/cdrom/' and press enter

Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main libaprutil1 1.3.9+dfsg-3build1
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main libaprutil1-dbd-sqlite3 1.3.9+dfsg-3build1
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main libaprutil1-ldap 1.3.9+dfsg-3build1
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main apache2.2-bin 2.2.14-5ubuntu8
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main apache2-utils 2.2.14-5ubuntu8
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main apache2.2-common 2.2.14-5ubuntu8
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main apache2-mpm-worker 2.2.14-5ubuntu8
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main apache2 2.2.14-5ubuntu8
  File not found
Err cdrom://Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)/ lucid/main ssl-cert 1.0.23ubuntu2
  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-3build1_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apr-util/libaprutil1-dbd-sqlite3_1.3.9+dfsg-3build1_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apr-util/libaprutil1-ldap_1.3.9+dfsg-3build1_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apache2/apache2.2-bin_2.2.14-5ubuntu8_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apache2/apache2-utils_2.2.14-5ubuntu8_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apache2/apache2.2-common_2.2.14-5ubuntu8_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apache2/apache2-mpm-worker_2.2.14-5ubuntu8_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/a/apache2/apache2_2.2.14-5ubuntu8_amd64.deb  File not found
Failed to fetch cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/pool/main/s/ssl-cert/ssl-cert_1.0.23ubuntu2_all.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```


The weird thing is, I've opened the CD on my windows laptop and the file exists.

pool/main/a/apache2/apache2.2-bin_2.2.14-5ubuntu8_amd64.deb (2,729,732 bytes)

---

### Post by wojox on 2010-05-09
Why don't you comment out the CD part from /etc/apt/sources.list

---

### Post by Zeophlite on 2010-05-10
That's an option to get everything to work, but I'd rather fix this problem then ignore it.

---

### Post by s4nt on 2010-05-10
It happened to me today when installing mysql-server package on ubuntu server 10.04 on a machine with no network.

**1st- check if /cdrom exists**

```
$ ls /cdrom
```

On my laptop running 9.04 is a link to /media/cdrom0, but on this ubuntu server 10.04 install it was an empty folder.


**Mounting the cdrom on /cdrom directory fixed the issue for me:**

```

$ sudo mount /dev/cdrom /cdrom

```

- cdrom device might be different, if /dev/cdrom does not work try: /dev/sr0, /dev/scd0 or /dev/sg0 too

- /cdrom directory was already there for me on this server. On my 9.04 laptop, /cdrom links to /media/cdrom0. You can do this too easily.

**-Alternate fix- **
```

$ sudo ln -s /media/cdrom0 /cdrom

```

good luck!

---

### Post by Zeophlite on 2010-05-11
sudo mount /dev/cdrom /cdrom
That worked brilliantly!

Thanks for your help

---

