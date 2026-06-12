---
title: "Big big problem for a newbie: I cannot install or upgrade new software in Ubuntu 9.10"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by aaricia on 2011-02-02
Hello,

I would really appreciate any help with this problem, because I don't know what else can I don't.

I have Ubuntu 9.10. In the last weeks, and without changing anything (at least consciously), I noticed that the Synaptic Manager couldn't install any upgrade. I thought that it may be the connection, but I tried from different places and I have disabled the proxy for the BT Home Hub connection and it doesn't make any different.

This is the output I get from console:

when I type sudo apt-get upgrade or update:

Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
  Unable to connect to 10.11.0.30 80:
Reading package lists... Done             
W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to 10.11.0.30:80 (10.11.0.30), connection timed out

and when I type  sudo apt-get check:
Reading package lists... Done
Building dependency tree       
Reading state information... Done


You may have noticed that I connect to a Spanish server despite being in the UK. This is because, I thought that it may be caused by a server problem, so I edited source.list and replace the "uk" with "es". It hasn't worked obviously.

When I go to "software sources" to check from which server it would be the best, there is a messages saying that Ubuntu cannot connect to any server.

I know that the problem is caused by some de-synchronization, but I don't know how to fix it.

Any help is very much appreciate.

Thank you very much.

---

### Post by steveneddy on 2011-02-02
I don't think 9.10 is supported anymore.

This version only had six months of support.

It may be time to upgrade to 10.04 (the LTS - supported for three years or so) or to another six month supported version - 10.10.

---

### Post by fabricator4 on 2011-02-02
I would also recommend you upgrade to 10.04 LTS.  The intermediate releases are supported for 18 months, but yes it's past it's UBD.

You should have been able to install new programs though, even if you couldn't upgrade.  It might be time to start with a fresh install of 10.04 and see if your problems go away.

Chris

---

### Post by tekkidd on 2011-02-02
First go to the terminal and type this in ```
sudo apt-get update
```If that does not work then try this: 
Go to System>Administration>Synaptic Package Manager
Then, in Synaptic go to Settings>Repositories
Now under the "Ubuntu Software" tab change the Server where it downloads from

then do a ```
sudo apt-get update
```.

Im trying to promote my blog so please drop by and look around 

[http://tekkidd.tumblr.com/](http://tekkidd.tumblr.com/)

---

### Post by Ctrl-Alt-F1 on 2011-02-02
steveneddy, non LTS versions are supported for 18 months.  Just because a new version comes out every 6 months doesn't mean they stop supporting old versions.  This means that 9.10 should be supported until April.

I agree that if you're going to want software updates it might be worth transitioning to a newer version now, since support expires in April anyway.

---

### Post by steveneddy on 2011-02-02
> **Ctrl-Alt-F1 said:**
> steveneddy, non LTS versions are supported for 18 months.  Just because a new version comes out every 6 months doesn't mean they stop supporting old versions.  This means that 9.10 should be supported until April.

I agree that if you're going to want software updates it might be worth transitioning to a newer version now, since support expires in April anyway.

I couldn't remember exactly, but I knew that it was getting close to end of life - or close to it.

Thanks for correcting me - I have been away from the forums for a while and have forgotten many of the details that I used to know so well.

---

### Post by gmargo on 2011-02-02
> **aaricia said:**
> 
Unable to connect to [COLOR=Red]10.11.0.30 [/COLOR]80:

Could not connect to [COLOR=Red]10.11.0.30[/COLOR]:80 (10.11.0.30), connection timed out


The problem is the IP address. 10.11.0.30 is a [private network]("http://en.wikipedia.org/wiki/Private_network") address, not an internet IP address. Is it a local proxy machine that's currently down?

---

### Post by Golem XIV on 2011-02-03
> **gmargo said:**
> The problem is the IP address. 10.11.0.30 is a [private network]("http://en.wikipedia.org/wiki/Private_network") address, not an internet IP address. Is it a local proxy machine that's currently down?

Correct, the 10.x.y.z range is for private (internal) networks.  You may also want to check your /etc/resolv.conf file to make sure you're not forcing the system to look for the Ubuntu servers on an internal network.

---

### Post by aaricia on 2011-02-05
Thanks for your replies.
I want to upgrade to 10.1 but I can't!!!

sudo apt-get update doesn't work obviously.

I checked that, in the BT Home Hub the firewall is off and that my laptop has a public IP address (just in case) .

I have also opened the file you mention, this is its content:
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.254

Is it correct? What should I write?

---

### Post by cwsnyder on 2011-02-05
The line ```
nameserver 192.168.1.254
``` points to your BT Home Hub as your nameserver for DNS resolving.  Either your BT Home Hub is not pointing to a proper Internet DNS server, or you need to change it to a proper DNS server such as ```
nameserver 208.67.222.222
nameserver 208.67.220.220
``` for OpenDNS or ```
nameserver 8.8.8.8
nameserver 8.8.4.4
``` to use the Google DNS servers. My /etc/resolv.conf also does not list the ```
domain home
search home
``` lines.

---

### Post by fabricator4 on 2011-02-05
Here's my resolv.conf:

```

# Generated by NetworkManager
domain home.gateway
search home.gateway
nameserver 192.168.1.254

```

In any case, the best way to upgrade is to download the iso, burn it to a CD, then boot off the install CD.  Backup up your data if your home is on the boot partition.  Backup your data anyway, it's good policy.  Just copy all of /home/username.

If you're doing a new install anyway you might consider making a separate partition for /home.  I've started doing this and it really simplifies installing a new OS, since none of your important data is on the boot partition which will get formatted.

To download the ISO for 10.04 [go here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and change the download option to 10.04 LTS.  Download the ISO (about 700Mb) and burn it to a CD.  You now have an installer CD that can be used on any computer.

Chris

---

### Post by cwsnyder on 2011-02-05
> **fabricator4 said:**
> Here's my resolv.conf:

```

# Generated by NetworkManager
domain home.gateway
search home.gateway
nameserver 192.168.1.254

```

In any case, the best way to upgrade is to download the iso, burn it to a CD, then boot off the install CD.  Backup up your data if your home is on the boot partition.  Backup your data anyway, it's good policy.  Just copy all of /home/username.

If you're doing a new install anyway you might consider making a separate partition for /home.  I've started doing this and it really simplifies installing a new OS, since none of your important data is on the boot partition which will get formatted.

To download the ISO for 10.04 [go here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and change the download option to 10.04 LTS.  Download the ISO (about 700Mb) and burn it to a CD.  You now have an installer CD that can be used on any computer.

Chris

I double checked: 192.168.1.254 is the default address for a modem and/or router!!!  Your problem is in the setup of your router, not in your computer.

---

### Post by aaricia on 2011-02-06
Thank you for trying to help me.
I changed to the DNS numbers you mentioned but no luck.

I still get the message:

everytime I try to install something via sudo or synatic terminal (the browser is running file):

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-client_1.4.1-5ubuntu2.7_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-client_1.4.1-5ubuntu2.7_all.deb)  Unable to connect to 10.11.0.30 80:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-common_1.4.1-5ubuntu2.7_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-common_1.4.1-5ubuntu2.7_all.deb)  Unable to connect to 10.11.0.30 80:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_7.6.0-1ubuntu4.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_7.6.0-1ubuntu4.1_i386.deb)  Unable to connect to 10.11.0.30 80:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This is the content of my sources.list if this gives you any clue:
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

I don't think that it is a problem of the BT Home Hub, as it happens in other wifi connections.

Thanks you for your help

---

### Post by aaricia on 2011-02-06
I just wanted to let you know that I fixed it!!

For some reason, the addresses of the latest proxy were still in vigour for the connection, although my user profile was configure to have a direct internet connection (that is why I could browse Internet)

I went to Network Proxy, althought it was fixed to a direct Internet connection I reset it, then applied the changes to System wide.

I am able to do update and upgrade now.

I will upgrade to 10.1

Thank you very much to everybody.

---

