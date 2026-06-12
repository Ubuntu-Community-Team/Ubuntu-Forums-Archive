---
title: "Hardware drivers facility - endless 'searching'?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by candtalan on 2009-01-21
Ubuntu 8.10
I have installed and updated, and on a previous occasion I have then enabled Visual effects; hardware drivers were searched for automatically and were installed ok, and compiz worked great!

I now want to enable the nvidia driver again, but it is not successful. I must have disabled the Visual effects or something in the recent past, anyway the hardware drivers don't seem to be getting found locally and there is just searching. This continues for a time, then stops, I guess it times out somewhere.

Could it be that these are downloaded from nvidia machines and may be occasionally out of action? Or should I be seeking a possible problem on my machine?

tia

---

### Post by gettinoriginal on 2009-01-21
First, try going to system, administration, software sources and make sure the box for "software restricted by copyright" is checked, then run:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
That should install the Nvidia drivers. then do the hardware search again.  :p

---

### Post by candtalan on 2009-01-21
thanks however, the same problem remains. 
To try something else, I used synaptic to remove compiz settings manager, and then restarted the machine for good measure. I then used 
System>Preferences>Appearence>visual effects (choose extra)
this acts to show the search for available drivers or the downloading window. Neither leads to success. The driver for this machine seems to be 173. 
i have just also tried this on a different machine which wanted driver 177, and it installed ok, quite quickly.

Any clues?
tia


Desktop effects cound not be enabled

---

### Post by gettinoriginal on 2009-01-21
System, Administration, Hardware Drivers will also search.

---

### Post by candtalan on 2009-01-21
The drivers 'installed' when using a live cd 8.10

I regret to say I decided to stop troubleshooting and try a reinstall.

Reinstall 8.10, all updates,  restart as required etc, then hardware drivers, restart

(success!!)

compiz works well.
:-)


So I conclude that something was damaged before to cause trouble, but I dont know quite what.

Anyway ok now.

Thanks for the responses guys!

---

