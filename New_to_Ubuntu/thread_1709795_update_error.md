---
title: "update error"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by unknow04 on 2011-03-18
ey guys I need help, i can't update, it just show me this error

W:Failed to fetch [http://ppa.launchpad.net/webupd8team/light-themes/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/webupd8team/light-themes/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/webupd8team/light-themes/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/webupd8team/light-themes/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.



Any idea ??

---

### Post by aktiwers on 2011-03-18
It looks like you got some sources that are offline.

```
gksudo gedit /etc/apt/source.list
```And remove the lines that has 
".. [http://ppa.launchpad.net/webupd8team]("http://ppa.launchpad.net/webupd8team/light-themes/ubuntu/dists/maverick/main/source/Sources.gz")..."

In them.

Then save and run:
```
sudo apt-get update
```

---

### Post by unknow04 on 2011-03-19
doesn't seems to be any line like that, just this

deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) maverick main #Telepathy

i use it because my photo desn't save on telepathy, but its works fine last time i updete, i delete it anyway 
but the error still there

---

### Post by unknow04 on 2011-03-19
I fix it, the repositories was on the option menu, on other software xD... thanks anyway

---

### Post by grizzler on 2011-03-19
Check the .list files in the **/etc/apt/sources.list.d** directory. There's bound to be one with webupd8team and/or light-themes in the name.

Edit: never mind. Beat me to it.

---

