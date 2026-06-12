---
title: "Misspelled Repository index"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by nigel23 on 2011-02-17
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Fetched 2,609B in 2s (1,178B/s)
W: Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

The above is the error message i get when i update in terminal. The index was misspelled. it should hav been 'xbmc'.
Can anyone help? I tried this:   ([http://ubuntuforums.org/showthread.php?t=844043]("http://ubuntuforums.org/showthread.php?t=844043")) but I couldn't find the index in source list.

---

### Post by maqtanim on 2011-02-17
Run the following command in the terminal
```
sudo gedit /etc/apt/sources.list

```then paste the whole list here.

---

### Post by sikander3786 on 2011-02-17
Mostly, PPAs are stored in your sources.list.d directory under separate files.

Please post the output of this command first.

```
ls -l /etc/apt/sources.list.d
```

---

### Post by howefield on 2011-02-17
> **maqtanim said:**
> Run the following command in the terminal
```
sudo gedit /etc/apt/sources.list

```then paste the whole list here.

Better still to run

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by maqtanim on 2011-02-17
@[[COLOR=#D40000]**howefield**[/COLOR]]("http://ubuntuforums.org/member.php?u=186490")

errrr... I actually don't know but what is the difference between gksu and sudo?

---

### Post by howefield on 2011-02-17
gksudo should be used when invoking graphical applications, gedit in your case.

For more info, have a browse here..

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by nigel23 on 2011-02-17
this is the result of:gksudo gedit /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://tt.archive.ubuntu.com/ubuntu/](http://tt.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
```

---

### Post by maqtanim on 2011-02-17
> **howefield said:**
> gksudo should be used when invoking graphical applications, gedit in your case.

For more info, have a browse here..

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
Thanks.. :)

@[nigel23]("http://ubuntuforums.org/member.php?u=1227497")
I didnot find that ppa. Did you paste the complete list?

---

### Post by nigel23 on 2011-02-17
nigel@nigel-HP-Mini-1101:~$ ls -l /etc/apt/sources.list.d
total 56
-rw-r--r-- 1 root root 132 2011-02-10 21:42 geod-ppa-geod-maverick.list
-rw-r--r-- 1 root root 132 2011-02-10 21:42 geod-ppa-geod-maverick.list.save
-rw-r--r-- 1 root root 176 2011-02-10 21:42 google-chrome.list
-rw-r--r-- 1 root root 176 2011-02-10 21:42 google-chrome.list.save
-rw-r--r-- 1 root root 152 2011-02-10 21:42 lars-opdenkamp-xbmc-pvr-maverick.list
-rw-r--r-- 1 root root 152 2011-02-10 21:42 lars-opdenkamp-xbmc-pvr-maverick.list.save
-rw-r--r-- 1 root root 136 2011-02-10 21:42 libreoffice-ppa-maverick.list
-rw-r--r-- 1 root root 136 2011-02-10 21:42 libreoffice-ppa-maverick.list.save
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xbmc-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xbmc-ppa-maverick.list.save
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xmbc-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xmbc-ppa-maverick.list.save
-rw-r--r-- 1 root root 136 2011-02-10 21:42 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root 136 2011-02-10 21:42 ubuntu-wine-ppa-maverick.list.save
nigel@nigel-HP-Mini-1101:~$

---

### Post by sikander3786 on 2011-02-17
> **maqtanim said:**
> Run the following command in the terminal
```
sudo gedit /etc/apt/sources.list

```then paste the whole list here.
Unless you want to edit the file and specially when giving instruction to newbies, I don't recommend to open the files with gksudo or sudo. Simply this

```
gedit /etc/apt/sources.list
```

Or even better,

```
cat /etc/apt/sources.list
```

This saves the new user to do any damage to their original files ;-)

---

### Post by nigel23 on 2011-02-17
I see my misspelling inside there :o

---

### Post by sikander3786 on 2011-02-17
> **nigel23 said:**
> nigel@nigel-HP-Mini-1101:~$ ls -l /etc/apt/sources.list.d
total 56
-rw-r--r-- 1 root root 132 2011-02-10 21:42 geod-ppa-geod-maverick.list
-rw-r--r-- 1 root root 132 2011-02-10 21:42 geod-ppa-geod-maverick.list.save
-rw-r--r-- 1 root root 176 2011-02-10 21:42 google-chrome.list
-rw-r--r-- 1 root root 176 2011-02-10 21:42 google-chrome.list.save
-rw-r--r-- 1 root root 152 2011-02-10 21:42 lars-opdenkamp-xbmc-pvr-maverick.list
-rw-r--r-- 1 root root 152 2011-02-10 21:42 lars-opdenkamp-xbmc-pvr-maverick.list.save
-rw-r--r-- 1 root root 136 2011-02-10 21:42 libreoffice-ppa-maverick.list
-rw-r--r-- 1 root root 136 2011-02-10 21:42 libreoffice-ppa-maverick.list.save
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xbmc-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xbmc-ppa-maverick.list.save
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xmbc-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-02-10 21:42 team-xmbc-ppa-maverick.list.save
-rw-r--r-- 1 root root 136 2011-02-10 21:42 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root 136 2011-02-10 21:42 ubuntu-wine-ppa-maverick.list.save
nigel@nigel-HP-Mini-1101:~$
Go to Software Center > Edit > Software Sources > Other software tab and disable your XBMC PPAs (all of them). Close the window, click Reload and then from Terminal,

```
sudo add-apt-repository ppa:team-xbmc/ppa
```

```
sudo apt-get update
```

And then install the relevant pacakges.

After disabling the PPAs in Software Sources, you can delete them permanently so they don't cause confusion later.

---

### Post by nigel23 on 2011-02-17
> **sikander3786 said:**
> Go to Software Center > Edit > Software Sources > Other software tab and disable your XBMC PPAs (all of them). Close the window, click Reload and then from Terminal,

```
sudo add-apt-repository ppa:team-xbmc/ppa
```

```
sudo apt-get update
```

And then install the relevant pacakges.

After disabling the PPAs in Software Sources, you can delete them permanently so they don't cause confusion later.

Everthing seems 2b working fine. :D Thanks.
What relevant pkgs?
Shud i 'autoremove' now?

---

### Post by sikander3786 on 2011-02-17
Relevant packages, I mean the one's you want to install from xbmc ppa.

And autoremove removes any installed packages that were installed as dependency for some other package and are no longer required. You can run autoremove from time to time to keep your system clean.

```
sudo apt-get autoremove
```

Good Luck and Happy Ubuntu-ing!

---

### Post by nigel23 on 2011-02-17
> **sikander3786 said:**
> Relevant packages, I mean the one's you want to install from xbmc ppa.

And autoremove removes any installed packages that were installed as dependency for some other package and are no longer required. You can run autoremove from time to time to keep your system clean.

```
sudo apt-get autoremove
```

Good Luck and Happy Ubuntu-ing!

thanks a mil

---

