---
title: "How do I identify the repository certain software comes from?"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by 3rr0r on 2010-09-28
Hi all.  I'm trying to setup Ubuntu Server 10.04 but I have a major issue... I can't connect the system to the internet.

I am going through the trials and tribulations of using apt-mirror to copy the repo's to an external drive.  Then the joy of mounting it to the server and editing the sources.list file only to be told that the "package you specified cannot be found" when I want to install certain software.

I need to install
[LIST]
[*]gnome-core
[*]mysql-server libdbd-mysql-per
[*]rt3.8-apache2 rt3.8-db-mysql
[*]postfix
[*]request-tracker3.8 rt3.8-clients 
[/LIST]

I tried installing ubuntu-desktop or gnome-core and it could not find the package.  Not sure how I missed it but I imagine I'll have to review the sources I mirrored.  That's why I need to identify what repo's have the software listed above.

Thank you so much for your help!  I've been going at this for 2 weeks now...

---

### Post by Cowboybebop79 on 2010-09-28
I would imagine that they would be in universe as they are all packages provided by groups external to Canonical.

---

### Post by 3rr0r on 2010-10-04
So what should I add to my 

mirror.list file?

```

############# config ##################
#
# set base_path    /var/spool/apt-mirror
 set base_path	   /media/NIX/repo
 set mirror_path  /media/NIX/repo/mirror
 set skel_path    /media/NIX/repo/skel
 set var_path    /media/NIX/repo/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse

clean http://archive.ubuntu.com/ubuntu

```

---

### Post by Zero++ on 2010-10-04
Can you edit the file in Nano?

or check here 
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by 3rr0r on 2010-10-04
I have no problem editing it.  I just need to know what to specifically add.

That's why I was asking which repo's that software was located at.

[COLOR="Red"]EDIT[/COLOR]:  Ahh, I see what you mean now.  I'll add the following

```

deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

```

[COLOR="red"]EDIT2[/COLOR]: Are these two redundant in terms of downloading the universe files?

```
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
```

---

