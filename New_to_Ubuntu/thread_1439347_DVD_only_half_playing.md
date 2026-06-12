---
title: "DVD only half playing"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by scorpious on 2010-03-26
Sorry if this is a repost.

I'm running Kubuntu 9.10 \n \l. (I think)

When I insert this dvd (bro-town series 2) Dragon player only plays the warning page and the short advertising blurb you get at the start of every movie, then goes back to the start.
I can't get it to play the "movie" itself.

Any idea's here?

cheers.

---

### Post by coffeecat on 2010-03-26
Have you got libdvdcss2 installed? You need that for playing commercial encrypted DVDs. If not, go to [http://www.medibuntu.org/](http://www.medibuntu.org/) . Follow the repository howto and then install libdvdcss2. Also, check to see whether you have libdvdread4 installed. It looks as though you have, but check anyway.

---

### Post by scorpious on 2010-03-26
I have libdvdread4.
When I try to install libdvdcss2 I get

```
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
```

Does "libdvdcss2" have a new name or aa upgrade?

cheers

---

### Post by coffeecat on 2010-03-26
> **scorpious said:**
> When I try to install libdvdcss2 I get

```
Package libdvdcss2 is not available,
```

Which must mean you haven't enabled the Medibuntu repository, or you haven't done a 'sudo apt-get update' after enabling the Medibuntu repository. It's still there, downloadable from Medibuntu:

[http://packages.medibuntu.org/karmic/libdvdcss2.html](http://packages.medibuntu.org/karmic/libdvdcss2.html)

You can download the version appropriate to your architecture and install it manually if you want, but it's better to enable the repository and install it through the package manager because there are other useful packages available from Medibuntu. Not least w32codecs (or w64codecs) which you'll probably be needing sooner or later.

---

### Post by dnairb on 2010-03-26
IIRC once you have libdvdread4 installed, all that is necessary is to run the following in terminal to install libdvdcss2:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If this doesn't work, you can run the following as a single command in terminal to add the Medibuntu repository, update the packages list and install libdvdcss2:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update && sudo apt-get install libdvdcss2
```

---

### Post by scorpious on 2010-03-26
Yep installing libdvdcss2 did the trick.

Thanks for the help.

---

