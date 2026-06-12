---
title: "Installing Codecs Through .Deb"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by C0rrup73dP14gu3 on 2009-09-18
just out of curiosity what .deb's would i need to install the codecs

---

### Post by sandyd on 2009-09-18
```

sudo apt-get install ubuntu-restricted-extras[FONT=monospace]
[/FONT]sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list[FONT=monospace]
[/FONT]sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
[FONT=monospace]sudo apt-get install w32codecs[/FONT] libdvdcss2[FONT=monospace]
[/FONT]

```there ya go

substitute win32codecs with win64codecs if your usin 64bit

p.s. all the stuff after the first line adds non-free components

---

### Post by Paqman on 2009-09-18
There's a good meta-package in Medibuntu called non-free-codecs that will install everything in one go, and works the same for 32-bit and 64-bit.

So to slightly modify carlee's post:


```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update && sudo apt-get install non-free-codecs

```

Paste that lot into a terminal, enter your password and you're all sorted.

---

### Post by nhasian on 2009-09-19
alternatively if you use VLC then you dont need to worry about codecs.

```
sudo apt-get install vlc
```

---

### Post by mapes12 on 2009-09-19
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by misfitpierce on 2009-09-19
Gotta love the functionality of VLC media player for music and video files. Love the codecs built in to the app. Just a great program.

---

### Post by C0rrup73dP14gu3 on 2009-09-19
basically all i wanted to know is if i could download the .debs for the codecs (long list i know) and install them that way. if so which ones would i need to download seeing as this laptop is the only one with internet

---

### Post by andrew.46 on 2009-09-20
Hi C0rrup,

> **C0rrup73dP14gu3 said:**
> basically all i wanted to know is if i could download the .debs for the codecs (long list i know) and install them that way. if so which ones would i need to download seeing as this laptop is the only one with internet

It is possible to download the MPlayer codec pack *manually* from the MPlayer site itself and also install it manually. The procedure would be:

```

$ cd $HOME
$ wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2
$ sudo mkdir -pv /usr/lib/codecs
$ tar xjvf all-20071007.tar.bz2
$ sudo cp -v $HOME/all-20071007/* /usr/lib/codecs

```

These codecs are suitable for the 32bit MPlayer. If you wish to download the Medibuntu w32codec pack (which is the same as the above, possibly less a few unimportant codecs) a direct link is:

[http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu4_i386.deb)

Details of this can be seen here:

Package: w32codecs [non-free/libs]
[http://packages.medibuntu.org/jaunty/w32codecs.html](http://packages.medibuntu.org/jaunty/w32codecs.html)

Again this is suitable for the 32bit MPlayer.

Andrew

---

### Post by 3rdalbum on 2009-09-20
> **Paqman said:**
> There's a good meta-package in Medibuntu called non-free-codecs that will install everything in one go, and works the same for 32-bit and 64-bit.

True, but it's a metapackage; so downloading the "non-free-codecs" package manually will result in your computer trying to download the w32codecs or w64codecs package. If your main Ubuntu computer doesn't have an internet connection, then you obviously can't get the real codecs package.

---

### Post by C0rrup73dP14gu3 on 2009-09-21
[QUOTE=andrew.46][http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu4_i386.deb)[/QUOTE]

k i downloaded that and tried to install it but it just gave me a error (like everything else i downloaded). really didn't say the details for it tho. my guess is that i don't have libc6 (>= 2.1.3) or libstdc++5 (>= 1:3.3.4-1).

---

