---
title: "Synaptic Package Manager error"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by Jart44 on 2010-05-08
I was running my first Synaptic Package Manager update on a newly installed Ubuntu 10.04. Power to my building was cut and poof> GONE. 
When I went to download a theme and Synaptic Manager says error occurred.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure-a'
E:_cache->open() failed, please report

I open a terminal box to input the above sudo command and ENTER

Nothing happens.

If you could help I'd be grateful
Thanks,

---

### Post by Naitsirhc Hsem on 2010-05-08
you should be able to use the [broken] filter in synaptec to see the broken packages
from there you should be able to remove the broken packages

---

### Post by paydaydaddy on 2010-05-08
try 
```
apt-get -f install
```
then
```
sudo dpkg --configure-a
```

---

### Post by Jart44 on 2010-05-08
Thanks for the quick reply,

I entered: apt-get -f install and  sudo configure-a
Apparently root was not installed: a command prompt said TYPE
sudo apt-get istall root-system-bin 

Then [sudo] password Jart44

I have not entered a password anywhere on this system
Ya, head smacking on keyboard is imminent.:-({|=

---

