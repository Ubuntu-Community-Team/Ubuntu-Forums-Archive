---
title: "How do I upgrade - I cant :("
date: 2009-11-13
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-13
If I do > System > Administration > Update Manager - there is no option to upgrade to the latest ubuntu, (i am using intrepid 8.10)

What is the code to apply to the terminal to get the machine to upgrade?

T h A a N k S

---

### Post by Fire_Chief on 2009-11-13
Yes, that's correct. You cannot do a dist-upgrade from 8.10 to 9.10. I was in the same boat and just did a clean install. It's easier to move if you've made a backup of /home or kept it on a separate partition and don't format it during install.

I didn't try using the Alternate CD to do an upgrade but I think you may be able to do that if you like.

Cheers!

EDIT* on a side note, since I did a clean install and formatted all partitions as ext4, my system is blazing fast!

---

### Post by QIII on 2009-11-13
You probably won't be able to go directly to Karmic ... I don't think.

If you want to upgrade rather than install fresh

```
apt-get install update-manager-core
``````
sudo apt-get update
``````
sudo apt-get upgrade
```(You may have to reboot here...)

```
sudo do-release-upgrade
```I don't know if the last will get you straight to Karmic or Jaunty, but I suspect the latter.

(Sorry about all the edits -- trying to do too many things at once to think straight!)

---

