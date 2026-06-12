---
title: "Could someone please do a software sources comparison"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by kapi on 2010-10-23
Hi I had a red triangle appear in my panel to say I could only do a partial update. I remembered someone saying that debian should not be there as a software source, so I removed two sources from the list: debian etch and another. 

Can I ask please that someone check their software sources in Maverick Meerkat and tell me if they have any Debian sources.

Thanks very much

---

### Post by Verbeck on 2010-10-23
my sources.list
cleaned it up a little..
```

deb-src http://archive.ubuntu.com/ubuntu maverick main restricted 

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main multiverse universe 

deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates restricted main multiverse universe 

deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse

deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security restricted main multiverse universe 
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse

```

---

### Post by sikander3786 on 2010-10-23
It would be better to post the output of

```
sudo apt-get upgrade
```

Don't upgrade, say no where it asks "Do you want to continue [Y/n]?"

And,

```
cat /etc/apt/sources.list
```

---

### Post by kapi on 2010-10-23
Thanks, I don't know where the debian sources came from, I just wanted to ensure that they weren't needed before I deleted them. Everything seems ok

Thanks again

---

### Post by Hippytaff on 2010-10-23
> **Verbeck said:**
> my sources.list
cleaned it up a little..
```

deb-src http://archive.ubuntu.com/ubuntu maverick main restricted 

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main multiverse universe 

deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates restricted main multiverse universe 

deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse

deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security restricted main multiverse universe 
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse

```

I know I should know this, but how do I get that output (sources?)

---

### Post by AngusH on 2010-10-23
```
cat /etc/apt/sources.list
``` will output the list of sources that APT uses to get the repo listings.
Angus

---

### Post by Verbeck on 2010-10-23
[FONT=monospace]edit: nvm
[/FONT]

---

### Post by Hippytaff on 2010-10-23
Thanks all :-)

---

