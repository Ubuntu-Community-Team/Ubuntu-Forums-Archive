---
title: "Cannot add any apps/Packages not found in 9.10"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Bonbon622 on 2009-11-15
Hello, 
I just did a fresh install of 9.10 (running persistently from a flash drive as I did with 9.04). I'm trying to play an MP3 and as expected I need an MP3 decoder, but the search turns up the following result:
No packages with the requested plugins found.

I have tried doing a sudo apt-get update first and that hasn't resolved the issue.  

Just out of curiosity, I tried to install vlc from the terminal:

ubuntu@ubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc

I also have noticed that most of the apps in the software center are unavailable (not available in the current data).  Is this normal?

I did successfully run the update manager and the system is up to date as of 30 seconds ago.

I have no idea what's wrong here.  Any help would be greatly appreciated!  Thanks in advance!

---

### Post by Somme on 2009-11-15
```
cat /etc/apt/sources.list

```

Let us know the output.

---

### Post by Bonbon622 on 2009-11-15
> **Somme said:**
> ```
cat /etc/apt/sources.list

```Let us know the output.

ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

