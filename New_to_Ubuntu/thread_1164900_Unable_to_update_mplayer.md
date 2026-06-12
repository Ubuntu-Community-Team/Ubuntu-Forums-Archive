---
title: "Unable to update mplayer"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by lolwhites on 2009-05-20
When I run ```
sudo apt-get update
sudo apt-get upgrade
```

I get the following error message, and mplayer gets held back.

```
 Depends: libasound2 (> 1.0.18) but 1.0.17a-0ubuntu4 is installed.
                 Depends: libcaca0 (>= 0.99.beta15-1) but 0.99.beta13b-5 is installed.
                 Depends: libcdparanoia0 (>= 3.10.2+debian) but 3.10.0+debian-1 is installed.
                 Depends: libdbus-glib-1-2 (>= 0.78) but 0.76-1 is installed.
                 Depends: libjack0 (>= 0.116.1) but 0.109.2-3ubuntu1 is installed.
                 Depends: libpulse0 (>= 0.9.14) but 0.9.10-2ubuntu9.3 is installed.
                 Depends: libx264-65 (>= 1:0.svn20081230) which is a virtual package.

```

I don't seem to be able to install the missing dependecies with synaptic or apt-get.

---

### Post by Bachstelze on 2009-05-20
Which version of Ubuntu are you using?

---

### Post by lolwhites on 2009-05-20
Intrepid

---

### Post by Bachstelze on 2009-05-20
Your repos are somewhat messed up, then, because the mplayer version you're trying to install is *not* the Intrepid version.

Please paste the contents of your [font="monospace"]/etc/apt/sources.list[/font].

---

### Post by lolwhites on 2009-05-20
I checked my sources and, indeed, I'd added the Medibuntu repository for Jaunty. Changed it to Intrepid and the problem has gone.

---

