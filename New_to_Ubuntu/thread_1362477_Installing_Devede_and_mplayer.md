---
title: "Installing Devede and mplayer"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by smileyguy on 2009-12-23
I'm trying to install Devede. I get an error about dependancy not satisfiable: mencoder.

I try to install mencoder and get the same dependance error for "mplayer-skin"

Is there an easier way to do this?

I am downloading the Karmic option (not updates one) from here
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mplayer&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mplayer&searchon=names&subword=1&version=all&release=all)

---

### Post by Grenage on 2009-12-23
How are you installing them?  Download from the sites, or package manager/apt-get?  The package manager will sert out you dependencies, and both of those apps are in the repositories.

---

### Post by smileyguy on 2009-12-23
I was trying to download a debian installer after not finding them in the Synaptics.

I just installed 9.10 and am can't remember how I installed it before.

I enter "devede" int he search space in Synaptics and nohing seems to come up:( I'd prefer to do it by Synaptics).

---

### Post by Grenage on 2009-12-23
"devede" shows up in synaptic package manager, but this should do it:

```
sudo apt-get install devede mplayer
```

---

### Post by smileyguy on 2009-12-23
Thanks. Just refreshed and it worked! Maybe i missed it the first time?

---

### Post by Grenage on 2009-12-23
Who knows! At least it's there now :)

---

