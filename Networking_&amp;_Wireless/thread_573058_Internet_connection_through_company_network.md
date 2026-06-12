---
title: "Internet connection through company network"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by Morat on 2007-10-11
I'm trying out a few linux distro's in VMWare on my works machine. I'm not sure if the problem is due to being on the company network (with many protocols being blocked by firewalls etc) or running the distros un VMWare but I have the following situation:

I can set up firefox to browse the web in all distros - I'm currently writing this in the Ubuntu virtual machine.
I don't seem to be able to use the supplied package managers. For instance, in Ubuntu I am trying to install EnemyLines3 using "Add/Remove Programs" but I get the following error dialog:

========================================================
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
     ------------------------------------------------------------------------------------------------------------
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
========================================================

The network connect is ok as far as I can tell and Firefox (going through a proxy server) works so I have some kind of connection. Do the various package managers use a protocol that might be blocked?

Btw, I'm not an experienced Linux user though I'm happy with the command line and have used unix systems in the past.

--- Morat

---

### Post by devilears on 2007-10-11
have a look at your /etc/apt/apt.conf file, inside a corporate you probably need to authenticate to the proxy server. Edit your file to look something like this:

APT::Cache-Limit 100000000;
// Options for the downloading routines
Acquire
{
  // Retries "1";
   http::Proxy "http://yourusername:yourpassword@proxyIPaddress : proxyport/";
};

// Inhibit mirror-select
Apt::State::FirstRun "true";

---

### Post by Morat on 2007-10-11
Thanks for the quick response. Unfortunately, there is no apt.conf file in /etc/apt!...

[FONT="Courier New"]alistair@alistair-desktop:/$ ls -al /etc/apt
total 32
drwxr-xr-x   4 root root 4096 2007-10-09 20:51 .
drwxr-xr-x 106 root root 4096 2007-10-09 20:53 ..
drwxr-xr-x   2 root root 4096 2007-10-04 11:50 apt.conf.d
-rw-------   1 root root    0 2007-04-15 12:49 secring.gpg
-rw-r--r--   1 root root 2370 2007-10-04 11:29 sources.list
drwxr-xr-x   2 root root 4096 2007-10-10 03:00 sources.list.d
-rw-------   1 root root 1200 2007-04-15 12:49 trustdb.gpg
-rw-r--r--   1 root root 2393 2007-04-15 12:49 trusted.gpg
-rw-r--r--   1 root root 2381 2007-04-15 12:49 trusted.gpg~
alistair@alistair-desktop:/$ 
[/FONT]
Is there anywhere else that this file may be? Can I just create a new apt.conf file and put those lines straight in with nothing else?

--- Morat.

---

### Post by Morat on 2007-10-12
I created a new file and pasted in what you suggested and it seems to work. Hurrah!

However, it's not ideal to have my password in there in plain text. I'll have to look through the man-page for apt.config and see if there is an option to get it to prompt for a login & password.

Unless someone who knows is able to tell me?...

Morat.

---

