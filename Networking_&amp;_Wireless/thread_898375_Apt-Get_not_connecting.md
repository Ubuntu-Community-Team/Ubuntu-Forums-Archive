---
title: "Apt-Get not connecting"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2008-08-23
Hello all!
I tried to use apt today and it sent out a lot of errors ```
root@ubuntu:/# apt-get update
Err http://us.archive.ubuntu.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://ppa.launchpad.net hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://ppa.launchpad.net hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/adnarim/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@ubuntu:/# 

```

now obviously I can see that it is asking my pc for the files on port 4001, but why? I went into Synaptic and checked the settings, it says to "Direct connection to the internet" is enabled. my /etc/hosts has nothing about ubuntu going to localhost either, and my dns settings are fine under /etc/resolv.conf

Any ideas? :confused: also, I am not running any proxy

---

### Post by Sam Lars on 2008-08-23
I use a proxy to connect to my apt-cache server, and it's defined in a file called /etc/apt/apt.conf.d/01proxy, so you could check that directory at least.

---

### Post by davethewave83 on 2008-08-25
> **Sam Lars said:**
> I use a proxy to connect to my apt-cache server, and it's defined in a file called /etc/apt/apt.conf.d/01proxy, so you could check that directory at least.

Thanks for the reply but all I have in that directory are:```
00trustcdrom  05aptitude      20archive		     99update-notifier
01autoremove  10periodic      50unattended-upgrades
01ubuntu      15update-stamp  70debconf
```

I checked them, there is nothing in there about having apt call to local host for the files. :(
how can I fix this please

---

### Post by Paindistributor on 2008-08-25
Are you using a proxy setting in gnome?

Start a terminal and type in:

```
echo $http_proxy
```

Do you get some output? Go to your gnome-proxy settings and set it back to direct internet connection. Or you just type in

```
unset http_proxy
```

before you using apt.

That should fix your problem ;)

---

### Post by davethewave83 on 2008-08-25
> **Paindistributor said:**
> Are you using a proxy setting in gnome?

Start a terminal and type in:

```
echo $http_proxy
```

Do you get some output? Go to your gnome-proxy settings and set it back to direct internet connection. Or you just type in

```
unset http_proxy
```

before you using apt.

That should fix your problem ;)

Thanks! You rock:guitar: I needed to unset a proxy I never knew I had installed :confused: I tried everything else.. even purged apt itself and reinstalled it with dpkg, now synaptic isn't working :( 

Thanks again!

**edit** got Synaptic working again =D (had to add a source to my sources.list)

---

