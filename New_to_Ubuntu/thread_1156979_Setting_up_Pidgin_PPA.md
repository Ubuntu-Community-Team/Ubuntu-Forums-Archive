---
title: "Setting up Pidgin PPA"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by coldReactive on 2009-05-12
I tried setting up the Pidgin PPA from [here]("http://pidgin.im/download/ubuntu/"). But I get the following error after I do sudo apt-get update:

```
E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)
```

All that's in there is this:
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu main
```

---

### Post by binbash on 2009-05-12
I can confirm this.Fix : 

sudo gedit /etc/apt/sources.list.d/pidgin-ppa.list

Delete everything there and replace with : 

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main

---

### Post by coldReactive on 2009-05-12
Thank you.

---

