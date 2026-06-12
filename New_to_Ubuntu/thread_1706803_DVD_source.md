---
title: "DVD source"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by firefya on 2011-03-14
inserted a run of the mill DVD, movie player lacked the plug-in necessary to play the bastard. 

plug-in needed is named DVD source.

im using 10.10 notebook remix on an ASUS A52 jC x1

---

### Post by oldos2er on 2011-03-14
You need libdvdcss2. See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by firefya on 2011-03-14
should i try to do it via synaptic?

in terminal this happened:


[sudo] password for zane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdvdread84

---

### Post by firefya on 2011-03-14
okay, installed libdvdread4 via synaptic

opened the terminal and entered command line:

> sudo /usr/share/doc/libdvdread4/install-css.sh

this came up

[QUOTE]sudo: /ur/share/doc/libdvdread4/install-css.sh: command not found[QUOTE]

---

### Post by sanderd17 on 2011-03-14
Learn to read:

It's libdvdread4, not libdvdread84 like your output says and /usr/share and not /ur/share.

---

### Post by firefya on 2011-03-14
"learn to read" is prob the best advice i've ever gotten.

sry, im a little intimidate by this, i lack pretty fundamental knowledge which is why i decided to make the foray into linux os. 

copy and pasting from now on.

---

### Post by stoogiebuncho on 2011-03-14
Learn to read is pretty harsh... it's easy to make typos, even if you've been using linux your whole life.

Here's the method I always use to enable DVD playback on my machine.  You can copy and paste these commands into your terminal.

First, I add the Medibuntu Repository:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Next, I install libdvdcss2:
```
sudo apt-get install libdvdcss2
```

That should do it.  

More information on Medibuntu if you want it: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

