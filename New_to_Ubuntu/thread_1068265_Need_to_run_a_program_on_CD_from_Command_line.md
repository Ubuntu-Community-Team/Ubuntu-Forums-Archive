---
title: "Need to run a program on CD from Command line"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-12
How would you run a .deb package ......on a CD....from the command line only (server ubuntu)?


thx

---

### Post by boof1988 on 2009-02-12
> **mistypotato said:**
> How would you run a .deb package ......on a CD....from the command line only (server ubuntu)?


thx

EDIT: Note to self... gdebi is a a GUI based package installer.

Note to others... the following part (in red font) is incorrect.  I just didn't want to remove it, since that would make some other posts make less sense (maybe?).

[COLOR="Red"]I don't know if the file needs to be copied to the HDD first or not but to install a .deb package (I believe):

```

sudo gdebi <path to file>
```

Maybe try...

```
man gdebi
```

...first to make sure it is correct.  And there might even be an option to simulate the install to make sure all dependencies are met.[/COLOR]

For installing applications on server edition, you might want to try using (check out) the following to install stuff and see what is installed:

```

sudo aptitude
```

-or/and-

```
man aptitude
```

---

### Post by mistypotato on 2009-02-12
Now if I could only figure out how to get to the CD  :(

---

### Post by boof1988 on 2009-02-12
> **mistypotato said:**
> Now if I could only figure out how to get to the CD  :(

If you can post:

```
cat /etc/fstab
```

```
ls -al /media/
```

and

```
mount
```

We can see if the drive is mounted or not and then go from there.

---

### Post by anewguy on 2009-02-12
If you let the CD spin up, it will probably mount as /media/cdrom.  So, to access a file on the cd rom, you could do a couple of things:

in command line, cd /media/cdrom, then ls to see if your program is there - if in a subfolder just cd to it.  Once you are at the proper folder follow the instructions for a deb file.

you can probably also point aptitude or apt-get at it via something similar to the following:

sudo apt-get install /media/cdrom/.......



dave :)

---

### Post by snova on 2009-02-12
The other posts should be enough to get you going, however:

1) Gdebi probably isn't on a server. :)
2) apt-get doesn't work with package files.

The correct command to install a package would be:

```
dpkg --install /path/to/package.deb
```

(--install can be shorted to -i)

---

### Post by boof1988 on 2009-02-12
> **snova said:**
> 1) Gdebi probably isn't on a server. :)

I believe you are correct.

My apologies for the misinformation.

---

