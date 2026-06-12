---
title: "Synaptic package manager error"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Hutom on 2009-05-12
Dear friends, every time I install anything through Synaptic Package Manager the following error occurs. Be it firefox, Latex, Kile, Audacity, Vlc or anything else, they all got installed and are working properly; but every time the same error will occur. I don't understand it. Can anybody help me?


```
E: libwmf0.2-7: subprocess post-installation script returned error exit status 1
E: ttf-dejavu-extra: subprocess post-installation script returned error exit status 1
E: ttf-dejavu: dependency problems - leaving unconfigured
E: vlc: dependency problems - leaving unconfigured
E: xfonts-scalable: subprocess post-installation script returned error exit status 1
E: xorg: dependency problems - leaving unconfigured
```

---

### Post by Dill on 2009-05-12
Try 

```
sudo apt-get update
```

which will make sure you're software is up-to-date, or

```
sudo apt-get -f install
```

... which will force installation of programs if there's something left uncompleted.

Cheers,
Dill

---

### Post by swoody on 2009-05-12
It seems like you may have an issue with your 'ttf-mscorefonts-installer' package. Try
```
sudo apt-get purge ttf-mscorefonts-installer
```
```
sudo apt-get autoclean
```
and then
```
sudo apt-get install ttf-mscorefonts-installer
```

Post back here, and let us know if that works for you or if the problem persists :)

---

### Post by Hutom on 2009-05-12
@ **Dill**,

Update was done properly. But while running [COLOR="Red"]sudo apt-get -f install[/COLOR] this is what happened,

```
 sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libwmf0.2-7 (0.2.8.4-6ubuntu0.8.04.1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing libwmf0.2-7 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ttf-dejavu-extra (2.23-1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ttf-dejavu:
 ttf-dejavu depends on ttf-dejavu-extra; however:
  Package ttf-dejavu-extra is not configured yet.
dpkg: error processing ttf-dejavu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on ttf-dejavu; however:
  Package ttf-dejavu is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
Setting up xfonts-scalable (1:1.0.0-6ubuntu0.8.04.1) ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing xfonts-scalable (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xfonts-scalable (>= 1:1.0.0-1); however:
  Package xfonts-scalable is not configured yet.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwmf0.2-7
 ttf-dejavu-extra
 ttf-dejavu
 vlc
 xfonts-scalable
 xorg
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


@ **swoody**,

This is the reply to [COLOR="Red"]purge[/COLOR]-
```
sudo apt-get purge ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ttf-mscorefonts-installer

```


Reply to autoclean -
```
 sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

reply to install -
```
$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ttf-mscorefonts-installer
```

---

### Post by swoody on 2009-05-12
Try
```
sudo defoma-reconfigure -f
```

---

### Post by Hutom on 2009-05-12
[COLOR="Red"]sudo defoma-reconfigure -f[/COLOR] solved the problem. Thanks to both of you, Dill and Swoody.

---

### Post by swoody on 2009-05-12
Awesome! Glad to hear it's working for you now :D

---

