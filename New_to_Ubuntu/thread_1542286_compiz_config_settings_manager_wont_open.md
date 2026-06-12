---
title: "compiz config settings manager wont open"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by libihero on 2010-07-30
I tried installing compiz .9 using this guide:
[http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/](http://santiance.com/2010/07/compile-compiz-0-9-0-in-ubuntu/)
it didn't work that well on my computer, so I didn't want to use it any more.
however when i try to open my normal ccsm, this is what i get in the terminal:
```
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 125, in <module>
    context = compizconfig.Context(ccm.getDefaultScreen())
AttributeError: 'module' object has no attribute 'getDefaultScreen'

```

---

### Post by Raymond2201 on 2010-07-30
you should really just install this from synaptic package manager. To be on the safe side i would completely remove compiz and install all of it from either apt or synaptic.

to remove all compiz:
```
 sudo apt-get purge compiz-core
```

reinstall:
```
sudo apt-get install compiz 
```

Install settings manager:
```
sudo apt-get install compizconfig-settings-manager
```


hope this helps with your issue.

PS.This will remove all your settings.

---

### Post by libihero on 2010-08-01
still dont work :(

---

### Post by Raymond2201 on 2010-08-01
Ah you installed from source?

try this, open terminal and navigate into the directory you unzipped and built the installation from (the one where you presumably ran ./configure make make install etc...)

from the link you posted this might be on your Desktop.

once you find the directory type this in the terminal

```
sudo make uninstall
```

if this does not work then you might have to remove all the install files manually and as this was really a user made install you are probably best taking this up with the author of the install script :)

---

