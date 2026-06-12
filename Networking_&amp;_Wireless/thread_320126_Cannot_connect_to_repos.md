---
title: "Cannot connect to repos"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by Squrdel on 2006-12-16
For the last 2 weeks I have not been able to connect to the repos/archives. Synaptic is trying to connect to 1.0.0.0 and times out on each archive. My DSL is fine and I connect through a D-Link router which works fine on both WinXP and Dapper. Aptitude and Automatix no better.

Please help!!!!

---

### Post by taurus on 2006-12-16
Is your network working at all?  Can you surf the web with firefox?

---

### Post by Squrdel on 2006-12-17
Yes, all my internet access is fine, in fact I can connect to the archive FTP directories with Firefox.

---

### Post by maxamillion on 2006-12-17
would you mind opening /etc/apt/sources.list in a text editor and pastebin-ing them and posting the link?

---

### Post by Squrdel on 2006-12-17
Here is the last one I tried. I have commented/uncommented all entries one at a time with no luck. I have tried removing the "gb" from the URL and also adding "us" to see if that worked. As you will see Automatix2 keeps adding lines each time I reload if I have commented them out.

Here goes the source.list file

# 
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)] dapper main restricted

# Line commented out by installer because it failed to verify:
 deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted multiverse

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted multiverse
#AUTOMATIX REPOS END

---

### Post by taurus on 2006-12-17
How about removing the "gb." from your repos and run these two commands again?  Paste the exactly error here is there's one...

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Squrdel on 2006-12-17
Here is the error message;

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done

Thanks for the help, I hope you can find the solution.

---

### Post by Squrdel on 2006-12-18
The problem is fixed. I found a solution on another thread which I edited for my system. I am posting it here for the benefit of others.

I edited my sources.list file to remove the country key in the URLs - 'us' or 'gb' or whatever.

Edit dhclient-script directly. Prepend or supersede the resolv.conf file with your known good isp nameservers. I used prepend with the prefered DNS server IP from my routers setup.

Edit /etc/dhcp3/dhclient.conf

(sudo gedit /etc/dhcp3/dhclient.conf) and just before the "request" line, add this if you want to prepend your isp nameservers and have your routers dns address at the bottom of the list in resolv.conf:

prepend domain-name-servers 127.0.0.1,139.175.55.224; 
(These are my systems IPs, for multiple addresses, separate with a comma and don't forget the semicolon at the end)

Reboot or just bring your interface down and up again:

sudo ifdown eth0
sudo ifup eth0

---

