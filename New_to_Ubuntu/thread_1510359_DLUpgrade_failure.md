---
title: "DL/Upgrade failure"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by nnjond on 2010-06-15
Hi,

Have not been able to complete an update since i clean installed Lynx:

"Not all updates can be installed

Attempt a partial ingrade?"

When i attempted a partial upgrade, It will hang all day at:

Setting up libgdatal.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdatal. 4-cil into Mono

Another mssge i get is...

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

But i cant open Synaptic


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

nnjond@nnjond-desktop:~$ sudo dpkg --configure -a'
> 
>

:~$ sudo apt-get install -f
[sudo] password for nnjond: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nnjond@nnjond-desktop:~$ sudo dpkg --configure -a
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono

---

### Post by Chesamo on 2010-06-15
Some packages just take a really long time to configure.

---

### Post by nnjond on 2010-06-15
Not all day

---

### Post by Chesamo on 2010-06-15
Fair enough. It sounds very odd...

OH! You accidentally copied the last apostrophe when pasting the code. ```
sudo dpkg --configure -a[COLOR="Red"]**'**[/COLOR]
``` ```
sudo dpkg --configure -a
```

---

### Post by nnjond on 2010-06-15
nnjond@nnjond-desktop:~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
dpkg: status database area is locked by another process
nnjond@nnjond-desktop:~$

---

### Post by Chesamo on 2010-06-15
Are you running Synaptic or something? Reboot then do that command first-thing.

---

