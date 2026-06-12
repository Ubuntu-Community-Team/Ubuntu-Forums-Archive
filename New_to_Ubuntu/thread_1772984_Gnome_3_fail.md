---
title: "Gnome 3 fail"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Jobbo256 on 2011-06-01
I recently installed gnome 3 through the terminal and my power went out -,-

The desktop looks like an old 98, and when I try to install packages, the software center says it needs to be repaired. But when I do that, it has an error:```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 209203 files and directories currently installed.) 
Preparing to replace gnome-games-common 1:2.32.1-0ubuntu5 (using .../gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb) ... 
Unpacking replacement gnome-games-common ... 
dpkg: error processing /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb (--unpack): 
 trying to overwrite '/usr/share/gnome-games-common/cards/bonded.svg', which is also in package gnome-games-extra-data 2.30.0-1ubuntu1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Processing triggers for libglib2.0-0 ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb 
dpkg: dependency problems prevent configuration of glines: 
 glines depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing glines (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of lightsoff: 
 lightsoff depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing lightsoff (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gtali: 
 gtali depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing gtali (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnect: 
 gnect depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing gnect (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-games: 
 gnome-games depends on glines; however: 
  Package glines is not configured yet. 
 gnome-games depends on gnect; however: 
  Package gnect is not configured yet. 
 gnome-games depends on gtali; however: 
  Package gtali is not configured yet. 
 gnome-games depends on lightsoff; however: 
  Package lightsoff is not configured yet. 
dpkg: error processing gnome-games (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnotravex: 
 gnotravex depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing gnotravex (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of glchess: 
 glchess depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing glchess (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of quadrapassel: 
 quadrapassel depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing quadrapassel (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnomine: 
 gnomine depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing gnomine (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnome-mahjongg: 
 gnome-mahjongg depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing gnome-mahjongg (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of gnobots2: 
 gnobots2 depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however: 
  Version of gnome-games-common on system is 1:2.32.1-0ubuntu5. 
dpkg: error processing gnobots2 (--configure): 
 dependency problems - leaving unconfigured 

```So, uh, what do I do?

---

### Post by Jobbo256 on 2011-06-01
I was installing gnome 3 today when my computer shut off. When I turned it back on, my desktop looked like a 98 windows computer(minus the windows part) and when trying to reinstall gnome, the center said it need to be repaired. When trying to repair, it brings an error:```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 209203 files and directories currently installed.)  Preparing to replace gnome-games-common 1:2.32.1-0ubuntu5 (using .../gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb) ...  Unpacking replacement gnome-games-common ...  dpkg: error processing /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb (--unpack):   trying to overwrite '/usr/share/gnome-games-common/cards/bonded.svg', which is also in package gnome-games-extra-data 2.30.0-1ubuntu1  dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)  Processing triggers for libglib2.0-0 ...  Errors were encountered while processing:   /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb  dpkg: dependency problems prevent configuration of glines:   glines depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing glines (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of lightsoff:   lightsoff depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing lightsoff (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gtali:   gtali depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing gtali (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gnect:   gnect depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing gnect (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gnome-games:   gnome-games depends on glines; however:    Package glines is not configured yet.   gnome-games depends on gnect; however:    Package gnect is not configured yet.   gnome-games depends on gtali; however:    Package gtali is not configured yet.   gnome-games depends on lightsoff; however:    Package lightsoff is not configured yet.  dpkg: error processing gnome-games (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gnotravex:   gnotravex depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing gnotravex (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of glchess:   glchess depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing glchess (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of quadrapassel:   quadrapassel depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing quadrapassel (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gnomine:   gnomine depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing gnomine (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gnome-mahjongg:   gnome-mahjongg depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing gnome-mahjongg (--configure):   dependency problems - leaving unconfigured  dpkg: dependency problems prevent configuration of gnobots2:   gnobots2 depends on gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2); however:    Version of gnome-games-common on system is 1:2.32.1-0ubuntu5.  dpkg: error processing gnobots2 (--configure):   dependency problems - leaving unconfigured
```

So I figured out it was the games, but when I try reinstalling them individually, It gives me this:
```
E: /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb: trying to overwrite '/usr/share/gnome-games-common/cards/bonded.svg', which is also in package gnome-games-extra-data 2.30.0-1ubuntu1
```

I have no idea what I am supposed to do, and I really need help. Thanks.

---

### Post by uRock on 2011-06-01
Duplicate threads merged. Please do not create multiple threads on the same issue.

---

### Post by nerdy_kid on 2011-06-01
try

```


sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get install -f


```

---

### Post by tsteuerwald on 2011-06-02
I had exactly the same problem that you have described in the first post and the proposed way by nerdy_kid didn't worked for me.
I had to remove gnome-games-extra-data. I did this via Synaptic, however...
```

sudo apt-get remove gnome-games-extra-data

```
...should also work. Afterwards you can install gnome-games-common
```

sudo apt-get install gnome-games-common

```

May be it would be a good idea to remove most of the gnome2 packages before updating to gnome3, to prevent running into such problems as described here... 


Cheers
Timo

---

### Post by tsteuerwald on 2011-06-02
I just want to note that there didn't appeared any other problems during upgrading to gnome3, however I didn't had a shut down during the upgrade process like you. Hope this helps anyway!

---

### Post by Mariane on 2011-06-02
I had a power failure during an update and I ended up retrieving my data by plugging the hard disk as an external device on another computer... Best of luck. 

Mariane

---

### Post by M4570D0N on 2011-06-02
The windows 98 looking theme is likely the result of not having the Adwaita theme installed, which is part of then gnome-themes-standard package.

---

### Post by Jobbo256 on 2011-06-02
> **tsteuerwald said:**
>  I did this via Synaptic, however...

Thanks, I totally forgot about Synaptic! I just reinstalled the game packages, and everything else worked out fine.

---

### Post by tsuibin on 2011-09-15
me too

```
gc@dev:~$ sudo apt-get upgrade 
[sudo] password for gc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 aisleriot : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 glchess : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 glines : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gnect : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gnobots2 : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gnome-mahjongg : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gnomine : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gnotravex : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gnotski : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 gtali : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 iagno : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 lightsoff : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
 swell-foop : Depends: gnome-games-common (>= 1:3.0.2-0ubuntu1~natty2) but 1:2.32.1-0ubuntu5 is installed
E: Unmet dependencies. Try using -f.
gc@dev:~$ sudo apt-get -f upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages have been kept back:
  brasero brasero-cdrkit brasero-common cheese cheese-common empathy empathy-common eog
  evince evince-common gedit gedit-common gedit-plugins gnibbles gnome-common
  gnome-disk-utility gnome-keyring gnome-media gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-themes gnome-themes-selected gucharmap gvfs gvfs-backends
  gvfs-bin libgcr0 libgdu-gtk0 libgnome-keyring0 libgtk-vnc-1.0-0 libgucharmap7
  linux-headers-generic nautilus-sendto-empathy quadrapassel rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins seahorse sound-juicer totem totem-common
  totem-mozilla totem-plugins zenity
The following packages will be upgraded:
  gnome-games-common
1 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
24 not fully installed or removed.
Need to get 0 B/3,722 kB of archives.
After this operation, 10.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 448914 files and directories currently installed.)
Preparing to replace gnome-games-common 1:2.32.1-0ubuntu5 (using .../gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb) ...
Unpacking replacement gnome-games-common ...
dpkg: error processing /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb (--unpack):
 trying to overwrite '/usr/share/gnome-games-common/cards/bonded.svg', which is also in package gnome-games-extra-data 2.30.0-1ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games-common_1%3a3.0.2-0ubuntu1~natty2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

