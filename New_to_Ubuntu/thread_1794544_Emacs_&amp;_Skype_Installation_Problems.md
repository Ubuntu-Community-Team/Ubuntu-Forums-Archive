---
title: "Emacs &amp; Skype Installation Problems"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by xptional on 2011-07-01
Hi :)

Please help me regarding installation of subjected problems, I can't troubleshoot as I am new, as I search some threads but they couldn't help me out. :(

```
sudo apt-get install emacs21
```
Output
[HTML]khan@khan:~$sudo apt-get install emacs21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacs21 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emacs21 has no installation candidate
[/HTML]

Then for skype
```
sudo apt-get install skype
```

Output
[HTML]khan@khan:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-dbus (>= 4:4.5.3) but it is not installable
         Depends: libqt4-network (>= 4:4.5.3) but it is not installable
         Depends: libqtcore4 (>= 4:4.5.3) but it is not installable
         Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
E: Broken packages
[/HTML]

I thank you in advance !

---

### Post by kamaji792 on 2011-07-01
Hi *xptional*,

I'm not a wiz at this but it might be worth doing the following first:
```
sudo apt-get update
sudo apt-get upgrade
```

Then try installing the packages you want.

atb k

<edit r2>
By the way, why are you installing **emacs21** and not **emacs** ?
</edit>

---

### Post by diesch on 2011-07-01
Use either emacs22 or emacs23 with Ubuntu 10.10


It looks like your skype package isn't for Ubuntu 10.10 but for an older version.  What does
```
apt-cache policy skype
``` print?

---

### Post by xptional on 2011-07-01
Thanks for your responses. 

@kamaji792 :  Its not issue of update or upgrade..

```
 sudo apt-cache policy skype
```

Output

[HTML]khan@khan:~$ sudo apt-cache policy skype
[sudo] password for khan: 
skype:
  Installed: (none)
  Candidate: 2.2.0.35-0lucid1
  Version table:
     2.2.0.35-0lucid1 0
        500 http://archive.canonical.com/ubuntu/ lucid/partner Packages
[/HTML]

Linux Version
[HTML]khan@khan:~$ uname -a
Linux khan 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
[/HTML]

Your help will oblige me to rethank ! :)

Anyhow
```
sudo apt-get update
```
[HTML]khan@khan:~$ sudo apt-get update
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Reading package lists... Done
[/HTML]

---

### Post by xptional on 2011-07-01
May it helps, further ....
```
sudo apt-get -f install
```
[HTML]khan@khan:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  texlive-extra-utils libboost-regex1.40.0 texlive-base texlive-pictures-doc
  texlive-fonts-recommended texlive-pstricks-doc dvipng lmodern texlive-common
  texlive-latex-extra-doc libaiksaurus-1.2-0c2a libfftw3-3 texlive-pstricks
  luatex preview-latex-style ttf-lyx prosper tipa
  texlive-latex-recommended-doc texlive-latex-base-doc libboost-signals1.40.0
  libt1-5 asymptote libaiksaurus-1.2-data texlive-latex-extra texlive-binaries
  lyx-common pgf netpbm texlive-latex-recommended asymptote-doc
  texlive-generic-recommended texmaker-data texlive-latex-base
  texlive-fonts-recommended-doc psutils libsigsegv0 ps2eps libnetpbm10
  latex-beamer texlive-luatex texlive-font-utils latex-xcolor libaudio2
  texlive-doc-base tex-common lacheck freeglut3 texlive-pictures libmng1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
[/HTML]

---

### Post by diesch on 2011-07-01
So you're trying to install Skype from the Ubuntu partner repository for lucid, but according to your footer you are using maverick - that can't work.

Fix your package sources in */etc/apt/sources.list* and */etc/apt/sources.list.d/** to only use repositories for maverick (most likely you just need to replace "lucid" by "maverick" everywhere).

---

### Post by xptional on 2011-07-04
I am sorry about the old signature,... thanks for indication.

anyhow , problem persists .. 

I am grateful to you for solving it !

Waiting for fruitful response  . Thnx

---

### Post by xptional on 2011-07-06
SOLVED

There were some options that have been unmarked, in Synaptic Package Manager's Repositries. 

like

Ubuntu Software ... Downloadable from the internet... I have marked all the options,  and 

Other Software ... I have marked all the options , like, e.g. [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu).. and similar like that.

It works..

---

