---
title: "http network"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by zefiriss01 on 2009-11-02
hi, when first intalling ubuntu, it will ask about http network, kind like umm i forgot, but it says put it blank if you don't know about it. But i insert what i think its my http login, my username and password, but i think i make mistake, and now the software update can't be use.

but i can use firefox, i mean when firefox start, it will ask my http username and password, i use LAN here.

so, how to fix it? thx

---

### Post by Little Girl on 2009-11-02
When you do software updates, use the same [s]username and[/s] password that you use to log in to Ubuntu. I'm not sure how to get rid of an http login username and password since I'm not sure what those are. Hopefully the updates will work now, though. ;)

---

### Post by NickJones on 2009-11-02
You should only have to enter your password.

---

### Post by zefiriss01 on 2009-11-03
it says like this

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve ']host:10.0.0.1'

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

i think, i made mistake on earlier networking stuff on installation.

btw i still able to use firefox for browsing the internet

---

### Post by Little Girl on 2009-11-03
What do you get if you type this in a terminal window?
```
cat /etc/hosts
```

---

### Post by zefiriss01 on 2009-11-03
```
zefiriss@ubunturedi:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubunturedi

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by cariboo on 2009-11-03
Could you paste a copy of /etc/apt/sources.list in your next post?

---

### Post by running_rabbit07 on 2009-11-03
I understand what you did wrong, but I don't know the fix other than reinstalling, which you shouldn't do if someone here has a fix.

"Started install and when prompted for network info, you entered the wireless info, instead of leaving blank?"

---

### Post by zefiriss01 on 2009-11-03
> **cariboo907 said:**
> Could you paste a copy of /etc/apt/sources.list in your next post?

```
# 
# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main multiverse restricted universe

# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://id.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://id.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

> **running_rabbit07 said:**
> I understand what you did wrong, but I don't know the fix other than reinstalling, which you shouldn't do if someone here has a fix.

"Started install and when prompted for network info, you entered the wireless info, instead of leaving blank?"
yah, maybe, it said, on installation, something like "your network may pass http something, bla bla bla, ..., enter ... [[username][pass]@[port], ..., you can leave it blank , this can configured later" like that, i think i made mistake on port section, but i think something like this can be fixed later, so i try to enter it.

btw i just notice i also can't use pidgin, it won't connect, firefox is the only one works.

---

### Post by zefiriss01 on 2009-11-03
> **zefiriss01 said:**
> btw i just notice i also can't use pidgin, it won't connect, firefox is the only one works.
sorry my mistake, pidgin works well, it just takes time to load, i just can't use updates from ubuntu

---

### Post by zefiriss01 on 2009-11-03
hi, i found the problem, looks like this is what is called "http proxy"
```
sudo nano /etc/apt/apt.conf
```
delete the line, or put the right one, done

thanks everyone.

---

### Post by Little Girl on 2009-11-04
I'm glad you got it sorted out, zefiriss01. I don't even have /etc/apt/apt.conf on my system, so it must get put there if you fill in those blanks during installation. :D

---

