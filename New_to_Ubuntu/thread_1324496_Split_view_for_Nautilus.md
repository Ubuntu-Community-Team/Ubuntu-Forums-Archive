---
title: "Split view for Nautilus"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-11-12
okay, Über noob question:
How do I install the split view in Nautilus from this ppa?
[https://launchpad.net/~berndth/+archive/ppa]("https://launchpad.net/~berndth/+archive/ppa")

I installed it in Jaunty, but now I don't remember how and I can't find a command anywhere in the PPA.
I already added the PPA.

---

### Post by coldReactive on 2009-11-12
Copy this into a blank file:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESlxAJwEEAMaah1A8dYy/OuwBqmtTqf2N4Otnd7X516gQk9kpPrKr7l8f0+0o8CVndZyJ
PwdEpLnJiYkhypDaFf29+wDT/ycjGslrODvUqq8zxlG/6zfdiy2UUk8okDxv8BCrvs54ayrb
SF3Ky/Kkdljwed1iHWZdF5nzRUQJyVFEbE3TZF8TABEBAAG0EkxhdW5jaHBhZCBoYl9nbm9t
ZYi2BBMBAgAgBQJKXEAnAhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQHgQbTyRr85Ei
ZwP9ElashANuXnUkSvS4ZIpQymUdyfrGt0MjcYeKPxx+BFBoaY2Mde+gEyxk5fNu3gtcsNlz
sAegCYQIWD0SrPl+e54ofwNO7jZZtXFKZ3FfJph9Xu2Wson/grWVLMAQhhTDvIo5nx56hsK1
MMVsPfF0BiY07iuBioKCVOMJx406Xs8=
=/So7
-----END PGP PUBLIC KEY BLOCK-----
```

In System > administration > software sources, on the authentication tab, import the blank file you created with that copied text (You'll need to select All Files from the file types drop down, this will NOT work in Kubuntu, as Kubuntu only was gpg file types.)

After importing, add these two lines into the third-party software tab:

deb [http://ppa.launchpad.net/berndth/ppa/ubuntu](http://ppa.launchpad.net/berndth/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/berndth/ppa/ubuntu](http://ppa.launchpad.net/berndth/ppa/ubuntu) jaunty main

These are only for jaunty (9.04)

Edit: didn't see you already added the PPA.

sudo apt-get upgrade is what you should do after you add the PPA. if it doesn't appear in the updates, nor synaptic, then you're sunk, because the maintainer decided to use nautilus as a name for the package rather than nautilus-split-view and have it as an addon, and not a full replacement.

---

### Post by berndth on 2009-11-23
> **quinnten83 said:**
> 
How do I install the split view in Nautilus from this ppa?
[https://launchpad.net/~berndth/+archive/ppa]("https://launchpad.net/~berndth/+archive/ppa")

I installed it in Jaunty, but now I don't remember how and I can't find a command anywhere in the PPA.
I already added the PPA.

If you had problems installing from this PPA on Karmic, that's because I only updated the packages to Karmic a few days ago. Most likely there were not yet available when you tried it. Just try it now.

---

### Post by MiCK.ca on 2009-12-02
If I have installed this and do not wish to have it anymore...How do I unistall it. What would this be called in synaptics/terminal?

---

### Post by berndth on 2009-12-05
> **MiCK.ca said:**
> How do I unistall it.

Same as with any other PPA software. Remove the PPA from your repositories, and force a downgrade of the packages that you installed from the PPA (e.g. in Synaptic Package -> Force version). Do this for the packages nautilus, libnautilus-extension1 and nautilus-data. If you installed debug or development packages of nautilus, the same applies to them as well.

---

### Post by MiCK.ca on 2009-12-10
[http://ubuntuforums.org/showthread.php?t=1351459](http://ubuntuforums.org/showthread.php?t=1351459)

in this thread i have experienced ongoing problems. So i have removed the split view. still testing to see if solved

i thought i'd share this. I'll continue testing to see if removal stops this behavior.

---

### Post by quinnten83 on 2009-12-16
euhm, hey all.
turns out you need to run an upgrade and then restart Nautilus and it works.
I forgot to add that to this thread.
I am not experiencing any problems with this, in fact, I think it's working better in Karmic than it did in Jaunty.
So, thread solved I guess....

---

