---
title: "Keep losing wireless"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by GrampaDan on 2009-12-06
I'm running Ubuntu 9.10, Netbook Remix. The wireless that comes with the distro won't work in my HP Mini 2140. I did some searches and found a solution by downloading hybrid-portsrc-x86_32-v5.10.91.9.3.tar, which when install instantly activates the wireless. Then following the directions, I blacklisted updates to the wireless (I think), using
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
 
Anyway, every so often I lost the wirelss and have to reinstall the driver again. I think it's when an update is downloaded and installed.
 
I'm just wondering how to keep my wireless from getting disabled or what ever causes it to fail during updates.

---

### Post by CylnZ on 2009-12-06
In synaptic, did you try _**menu>packages>lock**_ when you have the working version installed? that keeps update manager from updating to the broken version. It's what I do with power managment so my fans work. Make sure you have the working one highlighted so you lock the right thing ;)

---

### Post by GrampaDan on 2009-12-06
> **CylnZ said:**
> In synaptic, did you try _**menu>packages>lock**_ when you have the working version installed? that keeps update manager from updating to the broken version. It's what I do with power managment so my fans work. Make sure you have the working one highlighted so you lock the right thing ;)
I'm not sure what synaptic is, but I'll do some research. And I reposted the question not knowing how to find this ... sorry folks.

---

### Post by GrampaDan on 2009-12-06
Darn. I can't even find this wireless package in synaptic.

---

### Post by CylnZ on 2009-12-24
Um. Toolbar>System>Administration>Synaptic Package Manager
;)

---

### Post by Geoff918 on 2009-12-24
Yes, you have the same setup as my ex-g/f, I believe.

The problem is that the BCM43XX is not fully supported yet. SO, you're left to update the wireless setup all over again with every kernel update.

It's a pain in the butt. I don't have a good answer for you aside from not permitting kernel upgrades.

---

### Post by Geoff918 on 2009-12-24
Wait, I forgot...

Once you have it working: Go to System -> Administration -> Hardware Drivers

Select the "proprietary driver" and you're set. You won't have to deal with patching the kernel any longer. And, you won't lose your wireless, either.

I forgot that I *did* fix that whole issue on my ex's computer.

---

### Post by GrampaDan on 2009-12-27
> **Geoff918 said:**
> Wait, I forgot...
 
Once you have it working: Go to System -> Administration -> Hardware Drivers
 
Select the "proprietary driver" and you're set. You won't have to deal with patching the kernel any longer. And, you won't lose your wireless, either.
 
I forgot that I *did* fix that whole issue on my ex's computer.
 
Wow ... that seems to have done the trick!  Thanks so much!  :)

---

