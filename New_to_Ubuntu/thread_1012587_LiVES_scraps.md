---
title: "LiVES scraps"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by icyest on 2008-12-16
Hi, I recently tried to install LiVES, which is suppose to be my Linux equivalent to Windows Movie Maker here:
[http://www.getdeb.net/release/3545](http://www.getdeb.net/release/3545)

The installation was incomplete and I didn't quite understand what was going on seeing as how I'm used to window's method of "download and Install"

I believe I have installed a few "packages" whatever those are, and they are on my computer. I'd like to delete these remnant fragments because I don't like incomplete scrap on my computer. Where can I locate them precisely? Synaptic Package Manager is insufficient in filtering out recently downloaded packages.

---

### Post by adobrakic on 2008-12-16
Try

```

sudo apt-get autoremove 

```

```

sudo apt-get clean

```

---

### Post by icyest on 2008-12-16
An explanation on what this does might help.

Is there a visual user interphase for doing this? I don't feel like doing anything permanent to my computer unless I know exactly what it is.

---

### Post by adobrakic on 2008-12-16
> 
autoremove
autoremove is used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed. 


> 
clean
clean clears out the local repository of retrieved package files.
It removes everything but the lock file from
/var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
APT is used as a dselect ( method, clean is run automatically.
Those who do not use dselect will likely want to run apt-get clean
from time to time to free up disk space.


hope this helps
:D

---

