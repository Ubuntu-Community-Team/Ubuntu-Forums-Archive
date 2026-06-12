---
title: "installing new tomboy?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by woodnymph on 2009-12-31
over me head so far, kick me if i'm in the wrong forum .. 

i need some help/advice/ location of a howto to build packages

i want to get the current karmic version of tomboy installed on an 8.04 release.  not sure how to do this.  any help?  thx

---

### Post by ace214 on 2009-12-31
I'm no expert, but I feel like this is going to be complicated because of the Mono upgrade that changed a bunch of packages...

You could always get the deb from packages.ubuntu.com and see what kind of dependencies it tries to install.

---

### Post by woodnymph on 2009-12-31
true.  thats what i'm finding .. i seem to be trapped in a loop with mono, libc6, and lib-bin .. 

maybe an earlier version of tomboy other than karmic would get me around the mono upgrade??

what i am really trying to do is get a new-enough version of tomboy to allow syncing via ubuntuOne ..

---

### Post by ace214 on 2009-12-31
I think Karmic was the earliest to have that set up.

I assume there's some reason you're not simply upgrading to Karmic?

---

### Post by woodnymph on 2009-12-31
i am running hardy and waiting for lucid to direct upgrade, which i can't from here - would have to upgrade sequentially through intrepid, etc.  just trying to get notes etc synced via cloud

---

### Post by spcwingo on 2009-12-31
You could also just use gnote (a C++ port of tomboy) and sidestep the mono mess.  All you would have to do is add their ppa.  To add the ppa just copy/paste this in your text editor:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESf+LcQEEANEcA8OSONXj2LN+NcoxPXKXnUjdQeWuIDt0WEn97pqlTuZEkwLEZBt7SOAO
rjExaWkYya2FaYfZdTs1KDEsLRuGhaDkzMYBVYnBrtuhS6yYbbGjgD4XgxDU5y5+H0rfF6td
vPwB1+iIpxUPDwFXKfUVnYaMl1bbNMlrlax6bS1jABEBAAG0FkxhdW5jaHBhZCBnbm90ZSBz
dGFibGWItgQTAQIAIAUCSf+LcQIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEEdDyT5a
q1VTTOsD/0mgL2nflJoIMrc/IHwi5nqMBeA/PLVjE9LvuTZDfjOPIugxdth3sL3a4UHGrfpl
/0/X4dRTKV/+T02rbALXL9O0iYVJIRHOWCOf2iccZhHpxIsbCq6x3QpK6PTcACk0A4w2iTHf
g+vHHSheMFF27Eer5A4L7+cRn0kCm8tyHabu
=ebOF
-----END PGP PUBLIC KEY BLOCK-----

```

save it as gnote.gpg in your home folder.  Next press ALT+F2 and in the run dialog box that comes up enter:

```
gksu gedit /etc/apt/sources.list
```

at the bottom of that file copy/paste this:

```
#gnote
deb http://ppa.launchpad.net/gnote/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/gnote/ppa/ubuntu hardy main 
```

Save and close.  Finally open a terminal and copy/paste this command:

```
sudo apt-key add ~/gnote.gpg && sudo apt-get update && sudo apt-get install -y gnote
```

---

