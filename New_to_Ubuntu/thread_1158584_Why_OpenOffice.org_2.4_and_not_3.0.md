---
title: "Why OpenOffice.org 2.4 and not 3.0"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by geebob on 2009-05-13
Why does ubuntu ship with an older version of openoffice.org?  Are there advantages or disadvantages to upgrading?

---

### Post by Jazzy_Jeff on 2009-05-13
It just depends on which version you are using. Ubuntu 9.04 comes with version 3.0.

---

### Post by zeroseven0183 on 2009-05-13
I saw this in Google search results: [http://www.tectonic.co.za/?p=3447]("http://www.tectonic.co.za/?p=3447")

> We&#8217;d originally been hoping to include OpenOffice.org 3.0 in Ubuntu 8.10. Our original plan had been to provide packages that could be installed alongside 2.4.1 (rather than replacing it) once 3.0 reached the late beta or release candidate stage. However, a couple of factors made this much harder than we originally expected.

Read along...

Meanwhile you can enjoy the version 3.0 on the new Ubuntu 9.04. Or upgrade it to version 3.1.

---

### Post by Frak on 2009-05-13
You seem to be using an older version of Ubuntu. Jaunty Jackalope, the newest version, ships with the up-to-date version of OpenOffice.org.

---

### Post by fballem on 2009-05-13
> **Frak said:**
> You seem to be using an older version of Ubuntu. Jaunty Jackalope, the newest version, ships with the up-to-date version of OpenOffice.org.

If you're using an older version of ubuntu, and don't want to change to Jaunty, then there are ways to install newer versions of OpenOffice. I use Jaunty myself, so someone else will have to confirm if 3.0 is in the backports. If it is, then upgrading to OpenOffice is relatively simple. If it is not, then let us know what version you are running and we'll see if we can find the instructions to use OpenOffice 3.0

---

### Post by jowilkin on 2009-05-13
If you don't want to upgrade to Jaunty, just add this ppa to your aptitude sources, it will give you OpenOffice 3.1: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Just add the following lines to the bottom of /etc/apt/sources.list
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
```

Then add the key for the repo, on the command line run:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xd2bb86e0ebd0f0a43d4db3a760d11217247d1cff
```

Then update aptitude and install openoffice:
```
sudo aptitude update
sudo aptitude install openoffice.org
```

---

