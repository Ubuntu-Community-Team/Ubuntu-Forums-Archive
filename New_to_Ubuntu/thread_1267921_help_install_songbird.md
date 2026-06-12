---
title: "help install songbird"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by MelDJ on 2009-09-16
hi there. i downloaded the songbird deb from getdeb. now i cant install it as this comes up: installArchives() failed

the screenshot shows the terminal output (as i cant copy it). Please help.:(

---

### Post by Cypher on 2009-09-16
That's not Songbird complaining, but rather Firefox-branding that's failing. You have pending installs that weren't finished.

Drop to the terminal and type "sudo apt-get install -f" and see what happens. If that still fails, then install songbird directly with "sudo dpkg -i <songbird>.deb"

Regards

---

### Post by MelDJ on 2009-09-16
did it and this came:
Unpacking songbird (from songbird_1.2.0-1~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of songbird:
 songbird depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing songbird (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 songbird

---

### Post by Cypher on 2009-09-16
Ahh..that's where firefox-branding is coming into the picture. Are you on Hardy Ubuntu? And did you download the right version for your version of Ubuntu?

Regards

---

### Post by MelDJ on 2009-09-16
yes. got the right version. now synaptic says i have 2 broken dependencies: firefox and firefox-3.5.
:(

---

### Post by Cypher on 2009-09-16
so "sudo apt-get -f install" gives that message or the DPKG command?

Regards

---

### Post by MelDJ on 2009-09-16
the dpkg command gives that.
sudo apt-get -f install gives this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox-3.5-branding
The following NEW packages will be installed:
  firefox-3.5-branding
0 upgraded, 1 newly installed, 0 to remove and 38 not upgraded.
3 not fully installed or removed.
Need to get 0B/158kB of archives.
After this operation, 295kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 144165 files and directories currently installed.)
Unpacking firefox-3.5-branding (from .../firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Cypher on 2009-09-16
OK..try this..
```

cd /usr/share/applications
sudo mv firefox.desktop firefox.desktop.bak
sudo apt-get -f install

```
This should move the contentious file out of the way and firefox-branding should install and hopefully songbird after that..

Regards

---

### Post by MelDJ on 2009-09-16
it didn't work. installing firefox branding gave the same message :confused:

---

### Post by Cypher on 2009-09-16
OK, so it isn't looking at the file in that directory but rather using the package list to say that there 2 packages which have the same file. 

Now I'm a little confused, since you are on Hardy, there is no firefox-3.5-branding package available for that release? I can't actually find any -branding package for Hardy. firefox-3.0-branding is available from Intrepid onward, and firefox-3.1(3.5)-branding from Jaunty onward..

..and I just saw the line:
```

dpkg: error processing /var/cache/apt/archives/firefox-3.5-branding_3.5.4~hg20090914r26358+nobinonly-0ubuntu1~umd1~hardy_i386.deb (--unpack):
trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package **firefox-3.0**

```
So there's a conflict here that isn't easily resolved.

Did you grab just the Songbird DEB file from getdeb.net or others as well?

Regards

---

### Post by MelDJ on 2009-09-16
i am really confused!:KS
yes i only got the deb package from getdeb. for hardy 32 bits

---

### Post by MelDJ on 2009-09-16
songbird works. but the broken packages persist. thanks anyway:KS

---

