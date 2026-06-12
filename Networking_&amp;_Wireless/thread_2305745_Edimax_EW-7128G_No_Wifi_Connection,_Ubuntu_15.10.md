---
title: "Edimax EW-7128G No Wifi Connection, Ubuntu 15.10"
date: 2015-12-08
forum: Networking &amp; Wireless
---

### Post by jon105 on 2015-12-08
I have a PC running Ubuntu 15.10 with a Edimax wireless card installed (EW-7128G). I am new to Linux in general and would like some help in getting the wireless connected.

I found this page but don't really know where to start ---> [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

I ran just basic commands I found online for a little more info, as seen in the attachment. 

Thank you ahead of time for your help

---

### Post by chili555 on 2015-12-08
It appears that you have a driver and that it has created a wireless interface; namely wlp3s1.

Does it scan and see networks?```
sudo iwlist wlp3s1 scan
```Can you click the Network Manager icon, see your network, click it and connect?

Any clues in the log?```
dmesg | grep rt2
```

---

### Post by jon105 on 2015-12-08
Thank you chili for your interest and help.

Now it works? So I've been at this for a couple of days now running commands and searching the web for help. After I posted this thread I turned off the PC until you responded, in which I turned it back on again to run those commands and the network showed up. I honestly don't know what I did, but it now works after about 3 days of trying. I've restarted it before so I do not know why all of a sudden it decided to work and show up.

I don't know if it will help anyone but I ran numerous commands those three days such as:

sudo apt-get update
sudo apt-get dist-upgrade

Among others that I do not remember.

By the way, can you explain in some detail what those commands do exactly. I put them in but don't necessarily understand them.

Thanks again for your for you help, I will post back if I have any problems with connections dropping and such.

---

### Post by chili555 on 2015-12-08
Did you know that apt-get has a handy manual page?```
man apt-get
```It says:>  **update**
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.
Therefor, if your existing package index file says you have some_package-1.0 and the updated list you got now says the latest available is some_package-1.1, then it will be marked for upgrade. The upgrade will not actually take place; that is, the later package downloaded and installed until you sudo apt-get upgrade or dist-upgrade.> **dist-upgrade**
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
Frankly, for many, including me, it is just a lot easier to let Update Manager handle all this, download all the upgrades in the background and pop-up a notifier when they are ready for me to approve the installation.

I hope the wireless has been scared to life permanently but feel free to post back if we may help.

---

### Post by jon105 on 2015-12-09
Thank you so much chili.

---

