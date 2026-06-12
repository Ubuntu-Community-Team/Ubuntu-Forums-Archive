---
title: "Upgrade error"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by will547_us on 2011-04-27
I don't understand this:

"An error occurred. The following details are provided.
E: prelude-lml: subprocess installed post - installation script returned error exit status 1"

I got the error in Terminal and Synaptic.

Maverick Meerkat 
Dell XPS M1330

TIA, Will

---

### Post by Rubi1200 on 2011-04-27
Hi,

run the following commands please and post the output here if errors are generated:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

---

### Post by will547_us on 2011-04-27
Rubi1200

sudo dpkg --configure -a
Setting up prelude-lml (1.0.0-1)...
Starting Prelude LML: prelude -lmlinvoke-rc.d: initscript prelude -lml, action "start" failed
dpkg: error processing prelude-lml (--configure): subprocess installed post -installation script returned error exit status q
Errors were encountered while processing:prelude-lml

sudo apt-get install -f
Starts: "check - verify that there are no broken dependencies
markauto- mark the given packages as automatically installed"
etc etc with a list of -letter commands 
ends with this has super cow powers

Sorry I'm doing this long hand on crutches with a broken leg and a crushed foot. My Ubuntu computer is one end of the house and I'm writing on Windows PC in other end of house.
Will

---

### Post by will547_us on 2011-04-27
I tried:

sudo apt-get update  OK

then I tried:

sudo apt-get dist-upgrade

"Reading package list... done
Building dependency tree
Reading state information...Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
1 not fully installed or removed
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y/n]? y"

Then same result as above in sudo dpkg --configure -a
Plus the following:
E: Sub process /usr/bin/dpkg returned an error code (1)


What should I try now?
-Will-

---

### Post by Rubi1200 on 2011-04-27
Let's try removing the package:

```
sudo apt-get remove  prelude-lml
```

Followed by ```
sudo apt-get update
```

Let me know if that works.

---

