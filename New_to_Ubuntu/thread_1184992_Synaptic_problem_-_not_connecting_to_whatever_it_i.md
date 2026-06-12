---
title: "Synaptic problem - not connecting to whatever it is supposed to connect with!"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by psifunk on 2009-06-11
Hello, I get this message from synpatic when I open it and try to get the updates. I can't install anything at all using either Add/Remove , Synaptic and apt-get from command line. It used to work but something must have gone wrong in the past weeks. I tried to remember if I had changed anything but no luck. Is there any way to restore the settings to default? Instructions to set up synaptic from scratch will be useful if reasonably simple.

the message i get for everything is this

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 192.168.0.20:8080 (192.168.0.20), connection timed out

I have ubuntu 8.10 . In synpatic I have main,universe,multiverse and restricted repositories enabled. 

Thanks

---

### Post by Celauran on 2009-06-11
It's trying to resolve archive.ubuntu.com to a private IP. That's really strange. Have anything weird in /etc/hosts?

---

### Post by psifunk on 2009-06-11
in file hosts :

127.0.0.1    localhost
127.0.1.1    psifunk

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



in file host.conf:

# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on



in file hostname there is only my user name



in files hosts.allow and hosts.deny there is only commented text

cheers for the quick reply!!

---

### Post by Steelmourne on 2009-06-11
In software sources, make sure the first four boxes are ticked, from multiverse to restricted, then in terminal try this option: "sudo apt-get update -o Acquire::http::No-Cache=True" without the quotes.

If the connection is timing out, you could also switch to a server closer to where you live in software sources, too.

---

### Post by drs305 on 2009-06-11
You can also check System, Administration, Network Proxy and see if  'Direct internet connection' is enabled.

As Steelmourne suggested, also try another server: Software Sources or Synaptic, Settings, Repositories, Download from, and choose another server or select 'Best Server'.

---

### Post by psifunk on 2009-06-12
> **Steelmourne said:**
> In software sources, make sure the first four boxes are ticked, from multiverse to restricted, then in terminal try this option: "sudo apt-get update -o Acquire::http::No-Cache=True" without the quotes.

If the connection is timing out, you could also switch to a server closer to where you live in software sources, too.

I have done as you said but no luck. I stille get the could not fetch message for every file

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.0.20 8080:

@drs305  The "direct iternet connection" option is enabled. I tried choosig the best server and after all the tests it replied tha it could not find one ad that I should check my internet connection. Any ideas?

Thanks everyone

---

### Post by philinux on 2009-06-12
Post your sources list.

```
cat /etc/apt/sources.list
```

Dont forget to wrap code tags around the output.

---

### Post by sinnadyr on 2009-06-12
Can you think of anything you might have done before this problem occured? Like adding repos, updating something, changed network settings? Do you have this problem regardless of what network you are on?

---

### Post by psifunk on 2009-06-12
@philinux

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid main restricted universe
deb-src http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-updates main restricted universe
deb-src http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid multiverse
deb-src http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid multiverse
deb http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-updates multiverse
deb-src http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-security main restricted universe
deb-src http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-security main restricted
deb http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-security multiverse
deb-src http://ftp.ntua.gr/pub/linux/ubuntu/ intrepid-security multiverse

```


@sinnadyr Yes I have this problem in every network. It is very possible that i have done something without really knowing but I can't remember any useful information.. Everything else related to my internet connection works fine.. Btw ftp.ntua.gr is the server of my university and I live in the dorms so I am on the same network with this server and it used to work fine and very fast. I also tried other servers too.

---

### Post by psifunk on 2009-06-12
Hello again, after some search it seems tha other people too experience the same problem. A lot of users reported tha synaptic just stopped working and was searching for the repos in local IPs (i hope this make sense). I tried to rename all the files in /etc where the string  "192.168.0.20" (this is the ip synaptic is trying to connect to) existed but nothing changed. Any ideas people?

---

### Post by psifunk on 2009-06-14
Problem not solved yet although I have tried several things I could pick up in various forums! 

What is your opinion about uninstalling and reinstalling synaptic?  Ubuntu is useless to me if I can't install things and update so I really need to solve this.

---

