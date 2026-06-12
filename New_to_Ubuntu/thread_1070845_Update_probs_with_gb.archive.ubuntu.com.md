---
title: "Update probs with gb.archive.ubuntu.com"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by loobyloo on 2009-02-15
Hi..I keep getting this error message when I go to update.  It's been going on for about a week now.  Does anyone know what the problem is?

I can see there's a couple of timeout errors there but every other site I'm on is working fine (as is my email).

Thank you
Cliff

Here's the output
---------------------------

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists](http://gb.archive.ubuntu.com/ubuntu/dists)
/intrepid-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release.gpg](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217), connection timed out

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2)  Unable to connect to ppa.launchpad.net http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
-------------------

---

### Post by loobyloo on 2009-02-15
Just tried apt-get update through the terminal and that produces the same errors.

---

### Post by ww711 on 2009-02-15
Have you tried to switch the software sources. Instead of UK, try main server from the drop down menu?

I've literally put

```
sudo apt-get udpate
```

I get positive hits using the UK sources.

---

### Post by loobyloo on 2009-02-15
Thanks ww711 - you've obviously done something magical behind the scenes there because it's working fine now :)

That was odd though - that's been timing out for a week.

---

### Post by forger on 2009-02-15
use the main server, (without "uk" or "gb"), System > Administration > Software sources > Download from: "Main server" > Close > Reload :)

---

### Post by pikpolly on 2009-02-27
What would be the command line version for that?

---

### Post by forger on 2009-02-27
```
sudo sed -i 's#http://\S*archive.\ubuntu\.com#http://archive.ubuntu.com#' /etc/apt/sources.list
sudo apt-get update
```

---

### Post by concerto on 2009-02-27
> **forger said:**
> use the main server, (without "uk" or "gb"), System > Administration > Software sources > Download from: "Main server" > Close > Reload :)

wow. this solved all my problems

I thought I couldn't do updated because Gutsy was nearing the end of it's support but this fixed everything.

Thank you all!!!!!!!!!!!

---

### Post by pikpolly on 2009-02-28
It solved mine aswell, thankyou!

---

