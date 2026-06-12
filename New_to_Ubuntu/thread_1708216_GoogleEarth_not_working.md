---
title: "GoogleEarth not working"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by raymondvillain on 2011-03-16
Ubuntu 10.10, 64 bit AMD, installed GoogleEarth twice but it won't start.

Here is the error message I get when I type googleearth on the command line in a terminal window:

> username@computername~$ googleearth
/usr/lib/googleearth/googleearth-bin: symbol lookup error: /usr/lib/googleearth/libQtWebKit.so.4: undefined symbol: _Z34QBasicAtomicInt_fetchAndAddOrderedPVii
username@computername:~$ 

Don't know what this means.  What does one do to resolve something like this?

Thanks in advance

---

### Post by gandaran on 2011-03-16
what package type did you install google-earth from? .deb or .bin?
did you also install the **lsb-core** package from package manager?

---

### Post by raymondvillain on 2011-03-16
I used the command line:

> username@computername:~$ sudo apt-get googleearth-package
username@computername:~$ sudo apt-get install lsb-core
username@computername:~$ sudo make-googleearth-package --force


and then I went to my home directory, and right-clicked on
/home/username/googleearth_6.0.1.2032+0.5.7-1_amd64.deb

and selected "Open with GDebi package installer"

The GoogleEarth icon is indeed in my Internet tab ("Applications>Internet") but when I click on it nothing happens.

Hope this helps.

---

### Post by raymondvillain on 2011-03-16
I just tried something else.

Went to the GoogleEarth web site and downloaded version 6.  Then right clicked on the .deb file and installed it.

Now when I start GoogleEarth I get a window that says

> NOTICE
Google Earth could not write to the current cache or My Places file location.  The values will be set as follows:

MyPlaces Path: "/home/username/googleearth"
Cache Path: "/home/username/googleearth/Cache"


Then the Google Earth splash screen appears briefly and everything goes away.

---

### Post by gandaran on 2011-03-16
> **raymondvillain said:**
> I used the command line:



and then I went to my home directory, and right-clicked on
/home/username/googleearth_6.0.1.2032+0.5.7-1_amd64.deb

and selected "Open with GDebi package installer"

The GoogleEarth icon is indeed in my Internet tab ("Applications>Internet") but when I click on it nothing happens.

Hope this helps.
I'm not sure about this but don't you have to install 32-bits libs to run google-earth in 64-bits systems?
have you done it?

---

### Post by raymondvillain on 2011-03-16
What is the best way to remove all traces of Google Earth from my system?

Something like

```
sudo apt-get remove --purge GoogleEarth
```

All suggestions most welcome.

---

### Post by raymondvillain on 2011-03-16
Gandaran suggested 32 bit libs but that doesn't sound right to me.  I did have Google Earth working just fine on 64 bit Ubuntu 9.04.

Wish I hadn't upgraded.

To answer your question, gandaran, no I did not install 32 bit libs.  But thanks for the suggestion.

---

### Post by gandaran on 2011-03-16
> **raymondvillain said:**
> What is the best way to remove all traces of Google Earth from my system?

Something like

```
sudo apt-get remove --purge GoogleEarth
```

All suggestions most welcome.
the best is to use synaptic package manager, mark the google-earth for complete removal and apply.

---

