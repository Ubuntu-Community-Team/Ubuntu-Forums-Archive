---
title: "lime wire"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by jojom271 on 2009-08-15
looking for limewire  or peer to peer program tried downloading limewirelinux.deb  but was unable to install. need help. please provide code

---

### Post by XubuRoxMySox on 2009-08-15
The Linux version is called Frostwire. It does not appear in the repositories and is available for Ubunbtu [here]("http://www.frostwire.com/download/?os=ubuntu&").

-Robin

---

### Post by sandyd on 2009-08-15
I think that hes trying to install [http://www.limewire.com/download/releases](http://www.limewire.com/download/releases)
limewire now has its on linux version.

open up a terminal and try copy and pasting this in.
```

cd ~/Desktop
wget http://download.limewire.com/download/LimeWireLinux.deb
sudo dpkg -i LimeWireLinux.deb
sudo apt-get -f install
rm LimeWireLinux.deb

```
or for frostwire
```

cd ~/Desktop
wget http://newyork1.frostwire.com/frostwire/4.18.1/frostwire-4.18.1.i586.deb
sudo dpkg -i frostwire-4.18.1.i586.deb
sudo apt-get -f install
rm frostwire-4.18.1.i586.deb

```

---

### Post by nair on 2009-08-16
I was under the impression that Limewire was sort of a sketchy application...at least it was back in the day when I used it on Windows.  I guess that may be the kicker though...using it on Windows or using it on Linux.

---

### Post by rifak on 2009-08-16
i installed it a while ago, and i cant remember exactly what dependencies i need along with it. if it throws up an error about not having the dependencies, go into synaptic and search for them, install them, then go back to limewire and try

---

### Post by Soul-Sing on 2009-08-16
> **dixiedancer said:**
> The Linux version is called Frostwire. It does not appear in the repositories and is available for Ubunbtu [here]("http://www.frostwire.com/download/?os=ubuntu&").

-Robin

Indeed, and sun java is needed.

---

