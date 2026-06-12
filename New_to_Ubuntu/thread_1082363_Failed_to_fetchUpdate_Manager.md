---
title: "Failed to fetch/Update Manager"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by fincorenn on 2009-02-27
I'm getting the following errors when I run the Update Manager.Any ideas why this is?



W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://ppa.launchpad.net/wellington-team/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/wellington-team/ubuntu/dists/hardy/Release.gpg)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://ppa.launchpad.net/wellington-team/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2](http://ppa.launchpad.net/wellington-team/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://ppa.launchpad.net/wader/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/wader/ubuntu/dists/hardy/Release.gpg)  Could not resolve ‘e9c38cce6c’

W: Failed to fetch [http://ppa.launchpad.net/wader/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2](http://ppa.launchpad.net/wader/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘e9c38cce6c’

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2009-02-28
In applications>accessories>terminal type

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by forger on 2009-03-01
If it's not fixed, post the output of:
```
apt-config dump
```

---

### Post by fincorenn on 2009-03-01
Still didn't work.

The output is

pc@ubuntu:~$ apt-config dump
APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "0";
APT::Install-Suggests "0";
APT::Acquire "";
APT::Acquire::Translation "environment";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT::Install-Recommends-Sections "";
APT::Install-Recommends-Sections:: "metapackages";
APT::Install-Recommends-Sections:: "restricted/metapackages";
APT::Install-Recommends-Sections:: "universe/metapackages";
APT::Install-Recommends-Sections:: "multiverse/metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Update "";
APT::Update::Post-Invoke-Success "";
APT::Update::Post-Invoke-Success:::: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu hardy-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then  touch /var/lib/update-notifier/dpkg-run-stamp; fi";

---

### Post by forger on 2009-03-01
> Could not resolve &#8216;e9c38cce6c&#8217;
This means that you've probably set a network proxy.

Check menu System > Preferences > Network Proxy

Also check the output of:
```
cat /etc/environment
ls -l /etc/profile.d/
```

---

### Post by forger on 2009-03-01
Can you also post the output of:
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

---

### Post by fincorenn on 2009-03-01
pc@ubuntu:~$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
pc@ubuntu:~$ ls -l /etc/profile.d/
total 0
pc@ubuntu:~$

---

### Post by fincorenn on 2009-03-01
pc@ubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/wellington-team/ubuntu](http://ppa.launchpad.net/wellington-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/wellington-team/ubuntu](http://ppa.launchpad.net/wellington-team/ubuntu) hardy main
deb [http://ppa.launchpad.net/wader/ubuntu](http://ppa.launchpad.net/wader/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/wader/ubuntu](http://ppa.launchpad.net/wader/ubuntu) hardy main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
pc@ubuntu:~$ ls -l /etc/apt/sources.list.d/
total 16
-rw-r--r-- 1 root root 110 2009-03-01 18:39 wader.list
-rw-r--r-- 1 root root 110 2009-03-01 18:39 wader.list.save
-rw-r--r-- 1 root root 130 2009-03-01 18:39 wellington.list
-rw-r--r-- 1 root root 130 2009-03-01 18:39 wellington.list.save
pc@ubuntu:~$

---

### Post by forger on 2009-03-01
Do this:
```

sudo sed -i 's#http://\S*archive.\ubuntu\.com#http://archive.ubuntu.com#' /etc/apt/sources.list

```
And then:
```

sudo apt-get update
sudo apt-get autoclean
sudo apt-get -y --purge autoremove
sudo apt-get -y upgrade

```

Post the output. I think it's the gb.archive.ubuntu.com

---

### Post by fincorenn on 2009-03-01
Still not working

pc@ubuntu:~$ sudo sed -i 's#http://\S*archive.\ubuntu\.com#http://archive.ubuntu.com#' /etc/apt/sources.list
pc@ubuntu:~$ sudo apt-get update
Err http://ppa.launchpad.net hardy Release.gpg
  Could not resolve ‘e9c38cce6c’
Err http://ppa.launchpad.net hardy/main Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://ppa.launchpad.net hardy Release.gpg
  Could not resolve ‘e9c38cce6c’
Err http://ppa.launchpad.net hardy/main Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy Release.gpg         
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy/main Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy/restricted Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy/universe Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy/multiverse Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy-updates Release.gpg 
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy-updates/main Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy-updates/restricted Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy-updates/universe Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not resolve ‘e9c38cce6c’
Err http://security.ubuntu.com hardy-security/restricted Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://security.ubuntu.com hardy-security/main Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Err http://security.ubuntu.com hardy-security/universe Translation-en_GB
  Could not resolve ‘e9c38cce6c’
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://ppa.launchpad.net/wellington-team/ubuntu/dists/hardy/Release.gpg  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://ppa.launchpad.net/wellington-team/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://ppa.launchpad.net/wader/ubuntu/dists/hardy/Release.gpg  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://ppa.launchpad.net/wader/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  Could not resolve ‘e9c38cce6c’

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
pc@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pc@ubuntu:~$ sudo apt-get -y --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pc@ubuntu:~$ sudo apt-get -y upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pc@ubuntu:~$

---

### Post by forger on 2009-03-02
Post the output of this:
```

ping -c 5 google.com
ping -c 5 74.125.45.100
host google.com

```

---

### Post by fincorenn on 2009-03-02
pc@ubuntu:~$ ping -c 5 google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=242 time=124 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=242 time=125 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=242 time=123 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=242 time=123 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=5 ttl=242 time=124 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 123.528/124.322/125.030/0.585 ms
pc@ubuntu:~$ ping -c 5 74.125.45.100
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=242 time=124 ms
64 bytes from 74.125.45.100: icmp_seq=2 ttl=242 time=124 ms
64 bytes from 74.125.45.100: icmp_seq=3 ttl=242 time=125 ms
64 bytes from 74.125.45.100: icmp_seq=4 ttl=242 time=124 ms
64 bytes from 74.125.45.100: icmp_seq=5 ttl=242 time=123 ms

--- 74.125.45.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 123.640/124.509/125.612/0.787 ms
pc@ubuntu:~$ host google.com

---

### Post by forger on 2009-03-02
And this?
```
cat /etc/hostname
cat /etc/hosts
```

I'm actually trying to figure out just where that "e9c38cce6c" is mentioned :)

OK if the above commands don't return "e9c38cce6c", execute this:
```
sudo grep -r "e9c38cce6c" /
```
It will search inside all files about that string. Hopefully it will return a file (or files). It will take some time to finish, so let it run and go for a walk. :)

**[COLOR="Red"]WARNING![/COLOR]** The above command might show some private documents and information. Please send the output of the above command in a PM.

---

### Post by fincorenn on 2009-03-03
pc@ubuntu:~$ cat /etc/hostname
ubuntu
pc@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
pc@ubuntu:~$

---

### Post by plucky on 2009-03-03
Please post output of ```
cat /etc/apt/sources.list.d/wader.list
cat /etc/apt/sources.list.d/wellington.list
```

Thank you

---

### Post by forger on 2009-03-04
> **fincorenn said:**
> pc@ubuntu:~$ cat /etc/hostname
ubuntu
pc@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
pc@ubuntu:~$

what about the last command? :)

Also, post the output that plucky requested, I forgot about those two!

---

### Post by fincorenn on 2009-03-04
I have run sudo grep -r "e9c38cce6c" / as requested. It is still running after 24 hours. Is this normal?

---

### Post by forger on 2009-03-04
Well.. probably, it basically scans all your files (system and home directories) for that text string.

1) Give it one more day, stop it and see if there's anything in the output.

2) One more thing, do you have a network proxy, a firewall, squid, or a local apt mirror or something connected to apt running? like debtorrent ?
Anything that would interfere between you and the internet?

3) Can you lastly post the output of:
```

cat /etc/apt/sources.list.d/wader.list
cat /etc/apt/sources.list.d/wellington.list
sudo ufw status
sudo iptables -L

```

---

### Post by fincorenn on 2009-03-09
I don't know how to stop the output from  sudo grep -r "e9c38cce6c" /
It appears to be stuck in a loop.

I'm not aware of any firewall in use. I am accessing the internet by a wireless router. Would this have any effect?


pc@ubuntu:~$ cat /etc/apt/sources.list.d/wader.list
deb [http://ppa.launchpad.net/wader/ubuntu](http://ppa.launchpad.net/wader/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/wader/ubuntu](http://ppa.launchpad.net/wader/ubuntu) hardy main
pc@ubuntu:~$ cat /etc/apt/sources.list.d/wellington.list
deb [http://ppa.launchpad.net/wellington-team/ubuntu](http://ppa.launchpad.net/wellington-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/wellington-team/ubuntu](http://ppa.launchpad.net/wellington-team/ubuntu) hardy main
pc@ubuntu:~$ sudo ufw status
[sudo] password for pc: 
Sorry, try again.
[sudo] password for pc: 
Sorry, try again.
[sudo] password for pc: 
Firewall not loaded
pc@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
pc@ubuntu:~$

---

### Post by forger on 2009-03-10
To stop the loop, just kill it or reboot:
```
kill `pgrep grep`
```

1) Try these two and reply with the output:
```

ping -c5 archive.ubuntu.com
wget --save-headers --verbose http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg -O -
wget --save-headers --verbose http://fr.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg -O -

```

2) After that, I want you to attempt to download a package for ubuntu 8.04 (hardy heron):
```
arch=`dpkg --print-architecture`
wget http://fr.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.12-1_${arch}.deb -O traceroute_2.0.12-1_${arch}.deb
sudo dpkg -i traceroute_2.0.12-1_${arch}.deb

```

3) If (2) succeeds, execute and post back the output:
```
sudo tracert archive.ubuntu.com
```

---

### Post by fincorenn on 2009-03-10
pc@ubuntu:~$ ping -c5 archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=51 time=35.1 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=51 time=38.4 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=51 time=38.5 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=4 ttl=51 time=33.1 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=5 ttl=51 time=35.5 ms

--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 33.179/36.184/38.554/2.067 ms
pc@ubuntu:~$ wget --save-headers --verbose [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) -O -
--20:59:16--  [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)
           => `-'
Resolving e9c38cce6c... failed: Name or service not known.
pc@ubuntu:~$ wget --save-headers --verbose [http://fr.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) -O -
--21:02:09--  [http://fr.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)
           => `-'
Resolving e9c38cce6c... failed: Name or service not known.
pc@ubuntu:~$

---

### Post by fincorenn on 2009-03-10
pc@ubuntu:~$ arch=`dpkg --print-architecture`
pc@ubuntu:~$ wget http://fr.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.12-1_${arch}.deb -O traceroute_2.0.12-1_${arch}.deb
--21:06:35--  [http://fr.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.12-1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.12-1_i386.deb)
           => `traceroute_2.0.12-1_i386.deb'
Resolving e9c38cce6c... failed: Name or service not known.
pc@ubuntu:~$ sudo dpkg -i traceroute_2.0.12-1_${arch}.deb
dpkg-deb: unexpected end of file in version number in traceroute_2.0.12-1_i386.deb
dpkg: error processing traceroute_2.0.12-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 traceroute_2.0.12-1_i386.deb
pc@ubuntu:~$

---

### Post by forger on 2009-03-10
ok:
1) execute:
```
cd
rm traceroute_2.0.12-1_i386.deb

```
2) download the attached package **and save it in [COLOR="Red"]your home folder[/COLOR]**:
[ATTACH]106029[/ATTACH]

3) install it by typing:
```
sudo dpkg -i traceroute_2.0.12-1_i386.deb
```

4) Then execute:
```
sudo tracert archive.ubuntu.com
```

and leave it to run, it may take several minutes (10-15 maximum?) - then paste the output. use [*quote][/QUOTE] (without the asterisks)

---

### Post by forger on 2009-03-10
Two more:
5) Check menu System > Preferences > Network Proxy
Do you have a network proxy set there?

6) post the output of:
```
ls -l $HOME/.wgetrc
cat /etc/wgetrc
cat /etc/hosts
cat /etc/hostname
```

---

### Post by fincorenn on 2009-03-11
There is an automatic network proxy URL e9c38cce6c

pc@ubuntu:~$ sudo tracert archive.ubuntu.com
traceroute to archive.ubuntu.com (91.189.88.31), 30 hops max, 60 byte packets
 1  dsldevice.lan (192.168.1.254)  67.976 ms  67.227 ms  66.356 ms
 2  lo98.sc-acc-bras-3.as9105.net (212.74.102.3)  37.086 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * xe-9-0-0.lon20.ip.tiscali.net (89.149.185.73)  34.016 ms *
 7  * ge-7-1.core2.London1.Level3.net (213.200.77.130)  36.076 ms *
 8  ae-32-56.ebr2.London1.Level3.net (4.68.116.190)  44.839 ms  36.398 ms  37.696 ms
 9  ae-1-100.ebr1.London1.Level3.net (4.69.132.117)  37.329 ms  36.894 ms  34.393 ms
10  ae-2.ebr2.London2.Level3.net (4.69.132.145)  38.023 ms  35.285 ms  38.241 ms
11  ae-26-56.car2.London2.Level3.net (4.68.117.176)  114.811 ms  202.783 ms  204.952 ms
12  195.50.121.2 (195.50.121.2)  34.772 ms  35.005 ms  35.968 ms
13  leningradskaya.canonical.com (91.189.88.31)  37.363 ms  34.664 ms  34.594 ms
pc@ubuntu:~$

---

### Post by fincorenn on 2009-03-11
pc@ubuntu:~$ ls -l $HOME/.wgetrc
ls: cannot access /home/pc/.wgetrc: No such file or directory
pc@ubuntu:~$ cat /etc/wgetrc
###
### Sample Wget initialization file .wgetrc
###

## You can use this file to change the default behaviour of wget or to
## avoid having to type many many command-line options. This file does
## not contain a comprehensive list of commands -- look at the manual
## to find out what you can put into this file.
## 
## Wget initialization file can reside in /etc/wgetrc
## (global, for all users) or $HOME/.wgetrc (for a single user).
##
## To use the settings in this file, you will have to uncomment them,
## as well as change them, in most cases, as the values on the
## commented-out lines are the default values (e.g. "off").


##
## Global settings (useful for setting up in /etc/wgetrc).
## Think well before you change them, since they may reduce wget's
## functionality, and make it behave contrary to the documentation:
##

# You can set retrieve quota for beginners by specifying a value
# optionally followed by 'K' (kilobytes) or 'M' (megabytes).  The
# default quota is unlimited.
#quota = inf

# You can lower (or raise) the default number of retries when
# downloading a file (default is 20).
#tries = 20

# Lowering the maximum depth of the recursive retrieval is handy to
# prevent newbies from going too "deep" when they unwittingly start
# the recursive retrieval.  The default is 5.
#reclevel = 5

# By default Wget uses "passive FTP" transfer where the client
# initiates the data connection to the server rather than the other
# way around.  That is required on systems behind NAT where the client
# computer cannot be easily reached from the Internet.  However, some
# firewalls software explicitly supports active FTP and in fact has
# problems supporting passive transfer.  If you are in such
# environment, use "passive_ftp = off" to revert to active FTP.
#passive_ftp = off
passive_ftp = on

# The "wait" command below makes Wget wait between every connection.
# If, instead, you want Wget to wait only between retries of failed
# downloads, set waitretry to maximum number of seconds to wait (Wget
# will use "linear backoff", waiting 1 second after the first failure
# on a file, 2 seconds after the second failure, etc. up to this max).
waitretry = 10


##
## Local settings (for a user to set in his $HOME/.wgetrc).  It is
## *highly* undesirable to put these settings in the global file, since
## they are potentially dangerous to "normal" users.
##
## Even when setting up your own ~/.wgetrc, you should know what you
## are doing before doing so.
##

# Set this to on to use timestamping by default:
#timestamping = off

# It is a good idea to make Wget send your email address in a `From:'
# header with your request (so that server administrators can contact
# you in case of errors).  Wget does *not* send `From:' by default.
#header = From: Your Name <username@site.domain>

# You can set up other headers, like Accept-Language.  Accept-Language
# is *not* sent by default.
#header = Accept-Language: en

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
#http_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)
#ftp_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)

# If you do not want to use proxy at all, set this to off.
#use_proxy = on

# You can customize the retrieval outlook.  Valid options are default,
# binary, mega and micro.
#dot_style = default

# Setting this to off makes Wget not download /robots.txt.  Be sure to
# know *exactly* what /robots.txt is and how it is used before changing
# the default!
#robots = on

# It can be useful to make Wget wait between connections.  Set this to
# the number of seconds you want Wget to wait.
#wait = 0

# You can force creating directory structure, even if a single is being
# retrieved, by setting this to on.
#dirstruct = off

# You can turn on recursive retrieving by default (don't do this if
# you are not sure you know what it means) by setting this to on.
#recursive = off

# To always back up file X as X.orig before converting its links (due
# to -k / --convert-links / convert_links = on having been specified),
# set this variable to on:
#backup_converted = off

# To have Wget follow FTP links from HTML files by default, set this
# to on:
#follow_ftp = off
pc@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
pc@ubuntu:~$ cat /etc/hostname

---

### Post by fincorenn on 2009-03-11
I have removed the Network Proxy settings.Everything now appears to be working normally.

Thanks

---

