---
title: "Synaptic fails to open"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by nnjond on 2010-05-29
Left confused by aborted Install

Hi, 
Can someone help me please? My prob it seems is that, Banshee didn't install properly and won't open. Synaptic Package Manager wont open and returns:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have failed to understand this advice But I ...

~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono


This leads to nowhere and just hangs all day.

Since then update has failed and returns:

Software index is broken
run sudo apt-get install -f 

~$ sudo apt-get install -f 
[sudo] password for nnjond: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
nnjond@nnjond-desktop:~$ 

I've rebooted and now I get:

nnjond@nnjond-desktop:~$  sudo apt-get install -f 
[sudo] password for nnjond: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nnjond@nnjond-desktop:~$ 


I'm hopping that someone just needs to spell out an obvious command to me that will enable me to open synaptic.

---

### Post by wojox on 2010-05-29
Try running these back and forth a few times:

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f 
```

---

