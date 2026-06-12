---
title: "Wireless connected, but won't load web pages"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by kenney001 on 2008-07-22
After a fresh isntall of Ubuntu hardy, everything worked like a charm. However, the other day I was messing with trying to get ad-hoc working in order to steal my iphones internet in the car, and something got messed up.

Now, I can see all the wireless networks and successfully connect to them, but web pages wont load. Frostwire still connects and functions normally, but firefox/web browsing does not.

I am on my windows HD at the moment and need to switch back to obtain details.

any help is appreciated.

---

### Post by superprash2003 on 2008-07-22
in the terminal type ping google.com and post output here

---

### Post by nickdbliss on 2008-07-22
Seems like DNS problem. Try doing what superprash2003 said.

---

### Post by kenney001 on 2008-07-22
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=13 ttl=239 time=105

---

### Post by superprash2003 on 2008-07-23
open your internet browser and type 72.14.207.99 .. does the google page open?

---

### Post by kenney001 on 2008-07-28
nope. It still does not load. just says "connecting to 72.12.207.99"

---

### Post by brujoand on 2008-07-28
"when all other fails, use brute force."

You could just use synaptics and _completely_ remove firefox and then re-install it, since this will remove all config files, and make new ones. That is _if_ the problem is in the firefox configs. And if firefox is the only program effected(you said p2p still works), it probably is.

Wouldn't hurt to try :)

---

### Post by kenney001 on 2008-07-28
That didnt work. and it also wont download new packages in synaptic. It just sits on the "downloading package files" window with a download rate of "unknown".

---

### Post by brujoand on 2008-07-28
try doing a 

sudo apt-get update

and a

sudo apt-get upgrade

just to straiten everything out with the repos

---

### Post by LuigiAntoniol on 2008-07-28
> **kenney001 said:**
> After a fresh isntall of Ubuntu hardy, everything worked like a charm. However, the other day I was messing with trying to get ad-hoc working in order to steal my iphones internet in the car, and something got messed up.

Now, I can see all the wireless networks and successfully connect to them, but web pages wont load. Frostwire still connects and functions normally, but firefox/web browsing does not.

I am on my windows HD at the moment and need to switch back to obtain details.

any help is appreciated.

I had the same problem with my 3G wireless.  LAN works, but not wireless connection.
In Firefox, I clicked "File" then moved down to "Work Offline" and unchecked the "tick".  I have to do it every time I log in using 3G (Vodafone), but I don't mind.
Same for Evolution email.

---

### Post by kenney001 on 2008-07-28
sudo apt-get update gave me:


```
kenney@kenney-laptop:~$ sudo apt-get update
sudo: unable to resolve host kenney-laptop
[sudo] password for kenney: 
Err http://security.ubuntu.com hardy-security Release.gpg
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://wine.budgetdedicated.com hardy Release.gpg
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://wine.budgetdedicated.com hardy/main Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Ign http://security.ubuntu.com hardy-security Release
Ign http://wine.budgetdedicated.com hardy Release
Ign http://security.ubuntu.com hardy-security/main Packages
Err http://us.archive.ubuntu.com hardy Release.gpg
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Ign http://wine.budgetdedicated.com hardy/main Packages
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Ign http://security.ubuntu.com hardy-security/restricted Packages
Ign http://security.ubuntu.com hardy-security/main Sources
Ign http://security.ubuntu.com hardy-security/restricted Sources
Ign http://security.ubuntu.com hardy-security/universe Packages
Ign http://security.ubuntu.com hardy-security/universe Sources
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://us.archive.ubuntu.com hardy Release
Ign http://us.archive.ubuntu.com hardy-updates Release
Err http://security.ubuntu.com hardy-security/main Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/restricted Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/main Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/restricted Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/universe Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/universe Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/multiverse Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://wine.budgetdedicated.com hardy/main Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://security.ubuntu.com hardy-security/multiverse Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Ign http://us.archive.ubuntu.com hardy/main Packages
Ign http://us.archive.ubuntu.com hardy/restricted Packages
Ign http://us.archive.ubuntu.com hardy/main Sources
Ign http://us.archive.ubuntu.com hardy/restricted Sources
Ign http://us.archive.ubuntu.com hardy/universe Packages
Ign http://us.archive.ubuntu.com hardy/universe Sources
Ign http://us.archive.ubuntu.com hardy/multiverse Packages
Ign http://us.archive.ubuntu.com hardy/multiverse Sources
Ign http://us.archive.ubuntu.com hardy-updates/main Packages
Ign http://us.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://us.archive.ubuntu.com hardy-updates/main Sources
Ign http://us.archive.ubuntu.com hardy-updates/restricted Sources
Ign http://us.archive.ubuntu.com hardy-updates/universe Packages
Ign http://us.archive.ubuntu.com hardy-updates/universe Sources
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Err http://us.archive.ubuntu.com hardy/main Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/restricted Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/main Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/restricted Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/universe Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/universe Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/multiverse Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy/multiverse Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/main Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/restricted Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/main Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/restricted Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/universe Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/universe Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/multiverse Packages
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
Err http://us.archive.ubuntu.com hardy-updates/multiverse Sources
  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  Cannot initiate the connection to 192.168.1.1:8080 (192.168.1.1). - connect (101 Network is unreachable)

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

sudo apt-get upgrade gave me

```

kenney@kenney-laptop:~$ sudo apt-get upgrade
sudo: unable to resolve host kenney-laptop
[sudo] password for kenney: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

and nothing else other than terminal is running at the moment...

---

