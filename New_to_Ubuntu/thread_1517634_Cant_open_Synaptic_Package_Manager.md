---
title: "Cant open Synaptic Package Manager"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by nnjond on 2010-06-25
Hi,

Can someone please help me. I Have not been able to complete an update since i clean installed Lynx: Perhaps you'l understand my situation better than me by looking at these messages:

"Not all updates can be installed

Attempt a partial ingrade?"

When i attempted a partial upgrade, It will hang all day at:

Setting up libgdatal.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdatal. 4-cil into Mono

Another mssge i get is...

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

nnjond@nnjond-desktop:~$ sudo apt-get install -f
[sudo] password for nnjond: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nnjond@nnjond-desktop:~$ 

nnjond@nnjond-desktop:~$ sudo dpkg --configure -a
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono


IT hangs here all day!!! -And i cant open Synaptic,

---

### Post by cyrus_nk on 2010-06-25
I've had a problem like that, upgrade was hanging to a certain point.

You can open System > Update Manager?

Do you see the upgrade button?

---

### Post by nnjond on 2010-06-25
I get the mssge:

Not all updates can be installed

And

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by pricetech on 2010-06-25
If you just installed, which seems to be case from your original post, then you must have a corrupt install.  Did you check the disk first before installing ??  You might have a bad burn.  I'd do that first, and if the disk is okay, I'd just reinstall.

---

### Post by nnjond on 2010-06-25
Thanks for your advice, but im sure i checked the disk before i installed.

---

