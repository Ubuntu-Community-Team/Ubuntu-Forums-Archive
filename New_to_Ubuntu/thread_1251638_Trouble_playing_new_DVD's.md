---
title: "Trouble playing new DVD's"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by adventure man on 2009-08-27
My vlc media player and totem player both crash  (an error occured could not read from resource) when I try to play 2 new dvd's.  One is the new Indiana Jones and the kindgdom of the crystal skull and another is Network from 2006.  :confused:  rented them from netflix.

Am I missing something libcss2? :confused:

I'm confused as to why this is occuring, they play fine in winxp.
"regular" dvd's (burned media) play fine on vlc and totem.

thanks guys.

---

### Post by nandemonai on 2009-08-27
First:

```
sudo apt-get install ubuntu-restricted-extras
```

Second:

Hop over to [http://medibuntu.org/](http://medibuntu.org/) and follow the repository howto.

That should get you going ;)

The reason burnt ones play fine is because they lack copy protection.

---

### Post by powel212 on 2009-08-27
in addition to Ubuntu restricted extras you also need to enable DVD support as follows.

1.```
sudo apt-get -y install libdvdread4

```

2.```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Now it will work.

I hope that helps

Powel

---

### Post by adventure man on 2009-08-27
> **powel212 said:**
> in addition to Ubuntu restricted extras you also need to enable DVD support as follows.

1.```
sudo apt-get -y install libdvdread4

```2.```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Now it will work.

I hope that helps

Powel


got the first command to work but with number [2] I get command not found?

---

### Post by powel212 on 2009-08-28
Hmmm...

I just tested it on a fresh install. No problem.

Please try the whole thing again. If it fails please post the content of the terminal window including the error.

You are using Jaunty? Right?

I hope that helps.

Powel

---

### Post by dearingj on 2009-08-28
> **adventure man said:**
> got the first command to work but with number [2] I get command not found?

Try installing [libdvdcss2]("http://packages.medibuntu.org/jaunty/libdvdcss2.html") from Medibuntu instead of running that command.

---

### Post by adventure man on 2009-08-28
> **dearingj said:**
> Try installing [libdvdcss2]("http://packages.medibuntu.org/jaunty/libdvdcss2.html") from Medibuntu instead of running that command.


ok that did the job, had to download it to my computer and install the deb.  Mplayer worked immediately but had to do a system restart for vlc and totem to finally work.

Thank you guys for all the help.

---

