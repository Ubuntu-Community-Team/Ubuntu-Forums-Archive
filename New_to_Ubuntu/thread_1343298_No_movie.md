---
title: "No movie"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Tycoon timbo on 2009-12-01
i have installed just about every package i can find for gxine, totem and movie player but cannot get a dvd to play.  totem says it needs plugins, gxine says the files are encrypted and movie player just gives up.  anyone using theirs to play dvds?:popcorn:

---

### Post by Scott M. Sanders on 2009-12-01
You installed the Ubuntu Restricted Extras via Applications > Ubuntu Software Center?

---

### Post by Aearenda on 2009-12-01
See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by arochester on 2009-12-01
Install the Medibuntu Repository and get the package libdvdcss2

---

### Post by fooman on 2009-12-01
add the medibuntu repos and follow the instructions for playing dvds:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Tycoon timbo on 2009-12-01
thanks guys.  thats nailed that down nicely.  owe you a beer!!

---

### Post by sandyd on 2009-12-01
> **Tycoon timbo said:**
> i have installed just about every package i can find for gxine, totem and movie player but cannot get a dvd to play.  totem says it needs plugins, gxine says the files are encrypted and movie player just gives up.  anyone using theirs to play dvds?:popcorn:
run this. in the terminal
```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
sudo apt-get install libdvdcss2 libdvdread4

```

---

