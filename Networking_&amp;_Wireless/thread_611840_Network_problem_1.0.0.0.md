---
title: "Network problem 1.0.0.0"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by ram zu on 2007-11-13
Hi people.

Try to find an answer for my problem in the forum but without results.

I have an AMD 64 that was running 7.04 with no problems, everything working fine (ethernet/wireless). Now I upgraded to 7.10 and my problems start to appear.

1- Can't get acess to the repos. But when I was looking in th sources file, all the repos were commented. - FIXED.

2- My Firefox does't go anywere. Searching this forum I understand that is a problem with IPv6. Using "about:config" and set the line "network.dns.disableIPv6" to "true" it fixes my problem.

But now I have anouter problem. When I run the "Update Manager" or the "Add/Remove..." it stays try to download files but in the end gives an error. When I try to run "apt-get update/upgrade" I  get a network error like:

"0% [Connecting to pt.archive.ubuntu.com (1.0.0.0)]"
and after some time it result in:
"Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) gutsy Release.gpg
Could not connect to pt.archive.ubuntu.com:80 (1.0.0.0), connection timed out"

Don't know what to do more. Eveything worked fine in 7.04 without any hardware change.

Thanks for your atention.

---

### Post by taurus on 2007-11-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

I assume your network still works?

```
ping -c 3 www.google.com
```

---

### Post by ram zu on 2007-11-13
Here is the sources.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Here is the ping

PING [www.l.google.com](www.l.google.com) (64.233.183.147) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (64.233.183.147): icmp_seq=1 ttl=238 time=71.4 ms
64 bytes from [www.google.com](www.google.com) (64.233.183.147): icmp_seq=2 ttl=238 time=75.9 ms
64 bytes from [www.google.com](www.google.com) (64.233.183.147): icmp_seq=3 ttl=238 time=78.2 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 71.423/75.192/78.219/2.823 ms

Ping, trace, nslookup and so on tools work fine

panda@panda:~$ nslookup
> [www.google.com](www.google.com)
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   [www.google.com](www.google.com)
Address: 64.233.183.147
>

---

### Post by jcostom on 2007-11-13
If your DNS is resolving pt.archive.ubuntu.com as 1.0.0.0, it seems pretty clear that you've got DNS problems.

Either change your DNS settings to point somewhere else (I'd recommend OpenDNS - very good), or change to another mirror for your sources.  Specifically, one whose address you can resolve properly.

---

### Post by Lambert on 2007-11-13
If you do a google search for ubuntu 1.0.0.0 you will see this a lot (also other distrubtions have this problem)

It appears a problem with some routers/modems with ipv6

as jcostom said, look into opendns and also disabling ipv6 in both ubuntu and in firefox.

You can search for answers on how to do both of these.

---

### Post by CHFFriday on 2007-11-13
Sense you post, have you been able to do any updates?

This a a IPV6 issue and there is an update to fix this BUT it does not always seam to work so the reason I ask about the update will help me give you directions.

CHFFriday

---

