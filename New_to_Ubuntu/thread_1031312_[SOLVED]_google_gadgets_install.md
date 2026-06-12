---
title: "[SOLVED] google gadgets install"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by yakinikku on 2009-01-05
Hello all,

    I have a dell mini 9 and I am trying to install google gadgets on the dell built distro of hardy.  Naturally since google has not designed an lpia build of the software, I initially tried the force architecture command.  This got the program installed and had an icon listed in one of the applications menus (I believe it was "internet"), but it would give me errors so I removed it.  The next step I did was to follow the steps listed here:

[http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)

these steps worked for skype and a couple of other packages that I wanted to install.  Alas, google gadgets installs however, there is no icon or any indication that the software is installed other than what is shown in synaptic.  So again, I uninstalled.  Next, I went here:

[https://launchpad.net/~googlegadgets/+archive](https://launchpad.net/~googlegadgets/+archive)

and found a ready-built lpia package for google gadgets.  Again I installed and Again, no icon showing that the program was installed.  

Any suggestions?

---

### Post by northern lights on 2009-01-05
Just install *screenlets* from the repos. It runs Python Screenlets as well as Google Gadgets.

```
sudo apt-get update && sudo apt-get install screenlets
```

---

### Post by supererki on 2009-01-05
well... i did it like. : 
first
add 

deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main

to /etc/sources.list

then sudo apt-get update
then sudo apt-get install google-gadgets
then Alt+F2 -> ggl-gtk

or just download the tarball from somewhere
extract
./configure
make
make install

---

### Post by supererki on 2009-01-05
/etc/apt/sources.list
sorry

---

### Post by binbash on 2009-01-05
[http://www.getdeb.net/app/Google+Gadgets](http://www.getdeb.net/app/Google+Gadgets)

---

### Post by yakinikku on 2009-01-05
> **northern lights said:**
> Just install *screenlets* from the repos. It runs Python Screenlets as well as Google Gadgets.

```
sudo apt-get update && sudo apt-get install screenlets
```

just did this install....but i did it thru synaptic instead.  anyway, same thing, there is no indication that the program is installed other than synaptic telling me so.  am i doing something wrong?

---

### Post by yakinikku on 2009-01-05
> **binbash said:**
> [http://www.getdeb.net/app/Google+Gadgets](http://www.getdeb.net/app/Google+Gadgets)

i already tried this.  this package is set as i386 architecture...the mini 9 runs lpia architecture.  i did a few different steps and this would not install properly

---

### Post by yakinikku on 2009-01-05
> **yakinikku said:**
> just did this install....but i did it thru synaptic instead.  anyway, same thing, there is no indication that the program is installed other than synaptic telling me so.  am i doing something wrong?

ok, i got this program working.  i downloaded the deb file from getdeb.  unfortunately i cannot install any screenlets made for google gadgets.

---

### Post by northern lights on 2009-01-05
> **yakinikku said:**
> just did this install....but i did it thru synaptic instead.  anyway, same thing, there is no indication that the program is installed other than synaptic telling me so.  am i doing something wrong?
If the package *screenlets* is installed a launcher with the same name should appear under "Applications > Accessories", if it doesn't, run it from either the terminal or the Alt+F2 dialog using```
screenlets-manager
```
or```
screenlets-manager > /dev/null
```

---

### Post by WinterWeaver on 2009-01-05
OH wow I didn't even know of this google gadgets linux package. Just installed the deb now. It's exactly what I was looking for :)

---

### Post by yakinikku on 2009-01-05
thanks for all the replies northern lights. 

I got this working, but it ended up not working how I had hoped due to it conflicting with maximus, so I removed it.

What I did for google gadgets was this;  I used the force architecture command again.  It told me that the program had some file dependencies that were not met (it listed these files) so it installed with errors.  I then installed these files thru synaptic and it worked.  

so from this point, I removed the software again, as I wanted the install to at least show in synaptic.  I tried the lpia change again, and again no icon shows in in applications -> accessories.  It appears that the only way to get google gadgets working properly on the dell build of hardy is to force architecture and install the package dependencies manually.

---

