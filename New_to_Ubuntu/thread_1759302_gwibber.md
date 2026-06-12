---
title: "gwibber"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by wog on 2011-05-15
I find gwibber annoying, so I uninstalled it, but I still find gwibber-service in System Monitor.

Should gwibber-service still be running if gwibber is uninstalled?
What does gwibber-service do?

---

### Post by mikewhatever on 2011-05-17
Obviously, it should not be running. Try to re-login, and if it's still there, check for gwibber leftovers with the following command:
```
dpkg -l | grep gwibber
```

If there is output, then some gwibber packages are still there.

---

### Post by wildmanne39 on 2011-05-17
> **wog said:**
> I find gwibber annoying, so I uninstalled it, but I still find gwibber-service in System Monitor.

Should gwibber-service still be running if gwibber is uninstalled?
What does gwibber-service do?

Hi, if they are still there remove them by typing this command in a terminal.
sudo apt-get --purge remove --force {the name of the package you want to remove} without the brackets.

---

### Post by wog on 2011-05-27
Okay, this is a problem.

when I typed in:
```
dpkg -l | grep gwibber
```
I got:
rc  gwibber                               2.32.2-0ubuntu2                            Open source social networking client for GNOME
ii  gwibber-service                       3.0.0.1-0ubuntu3                           Open source social networking client for GNOME
ii  gwibber-service-facebook              3.0.0.1-0ubuntu3                           Facebook plugin for Gwibber
ii  gwibber-service-identica              3.0.0.1-0ubuntu3                           Identi.ca plugin for Gwibber
ii  gwibber-service-twitter               3.0.0.1-0ubuntu3                           Twitter plugin for Gwibber
rc  libgwibber0                           0.0.6-0ubuntu1                             Gwibber - shared library
ii  libgwibber1                           0.1.1-0ubuntu1                             Gwibber - shared library

When I typed in:
```
sudo apt-get --purge remove --force gwibber
```
I got:
E: Command line option --force is not understood

I removed the --force switch and then got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a kdelibs-data liblualib50 libavahi-qt3-1 apport-hooks-medibuntu
  liblua50
Use 'apt-get autoremove' to remove them.

Okay...
but typing in 
```
apt-get remove
```
gets me this:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Finally, 
```
sudo apt-get remove
``` 
removes all those files it said it would remove, and yet 
```
dpkg -l | grep gwibber
```
produces the same list as above without variation.

Further, a repetition of
```
sudo apt-get --purge remove gwibber
```
produces:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gwibber*
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Am I going to have to remove those files one at a time? If so, how?

---

### Post by wog on 2011-05-28
I finally gave in and went looking for gwibber in Synaptic.

I've gone from having 7 listings to 3. I'm not sure how to (find and) get rid of the other three.

At least gwibber-service no longer shows up in processes! :)

---

