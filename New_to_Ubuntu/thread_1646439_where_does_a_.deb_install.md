---
title: "where does a .deb install?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Azatos on 2010-12-15
Alright Im back on ubuntu on my main PC,  Ive installed a .deb from this website [http://sourceforge.net/projects/vbam/](http://sourceforge.net/projects/vbam/)  just want to play some games on my pc.

It installs fine however I literally do not know where any runnable files are.

---

### Post by 73ckn797 on 2010-12-15
See if it is here: ```
/usr/share
```

---

### Post by sgosnell on 2010-12-15
They could be anywhere.  The location is determined by the creator of the .deb.  Executables are usually placed in /usr/bin, /usr/local/bin, /usr/sbin, or somewhere in the /home hierarchy.  But sometimes they go in /opt or elsewhere.  You can find the executable, if you know part of the name, by typing "locate file" in a terminal, replacing file with part of the name of the executable.  If the name of the game is fungame, you might use "locate fungame" to find it.  You can also search for files from Nautilus.

---

### Post by dabomb1022 on 2010-12-15
a deb is kind of like a zip file. You make a folder like /usr/share/whatever inside of the .deb and as it is executed it copies the files there

---

### Post by oldos2er on 2010-12-16
```
dpkg -L <name of deb>
```

Or, you can see the same info in Synaptic; right-click on an installed package, Properties, Installed Files.

---

