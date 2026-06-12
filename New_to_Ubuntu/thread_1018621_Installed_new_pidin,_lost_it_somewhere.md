---
title: "Installed new pidin, lost it somewhere"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by cartisdm on 2008-12-22
I removed my old version of pidgin and libpurple0 in Synaptic by selecting "Pidgin" and "libpurple0" then "Mark for complete removal" (I don't know what libpurple0 is but the .deb package installer said I had to remove the old version)

I installed the new version of Pidgin (2.5.2) for Hardy using the installer, but now I can't find it anywhere.  I tried hitting Alt+F2 and typing "pidgin" but the autocomplete only gives me "pidgin_2.4.1"

Where did it go?

---

### Post by Her Ghost on 2008-12-22
you could try

```

whereis pidgin
which pidgin

```

and see if they show any results

---

### Post by cartisdm on 2008-12-22
```
dan@dan-laptop:~$ whereis pidgin
pidgin: /usr/lib/pidgin
dan@dan-laptop:~$ which pidgin
dan@dan-laptop:~$ 

```

but in the /usr/lib/pidgin directory there is only a nautilus.so document

---

### Post by Her Ghost on 2008-12-22
sorry, misread.
looks like you don't actually have it installed.

try running

```
sudo apt-get update
``` 

see if this sorts it.  if not, can you try re-installing it through package manager?

---

### Post by cartisdm on 2008-12-22
I reinstalled all the packages and this time it worked.  I don't know what happened the first time, nothing seemed to occur differently this time, weird.

Anywho, thanks for the help!

---

