---
title: "Synaptic fails to open"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by nnjond on 2010-05-18
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


 This leads to nowhere and just hangs...

I'm hopping that someone just needs to spell out an obvious command to me that will enable me to open synaptic.

---

### Post by Peter09 on 2010-05-18
Yes that was the right command - it can take quite a while for some things to be processed, how long did you leave it before you cancelled it.

---

### Post by nnjond on 2010-05-18
Thanks for your interest.

I've tried it several times leaving it mor or less indefinetly.

---

### Post by Peter09 on 2010-05-18
Try
> Open File Manager Superuser Mode and navigate to /var/cache/apt/ and delete the 2 cache files. 
 
That should clean up any intermediate or corrupt files, then upgrade again.

---

### Post by nnjond on 2010-05-18
Thanks.

I've rm files. Synaptic still wont open.

~$ sudo dpkg --configure -a
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono


Still hangs here...

What should i upgrade ?

---

