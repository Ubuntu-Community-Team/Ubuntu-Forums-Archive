---
title: "Grub extra copies of OS listed"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by miradus on 2011-04-10
So,

Was wondering how to clean up the grub boot file to remove the multiple instances of ubuntu listed at boot login. There are also several windows 7 loaders listed with these. 

I have a dual boot, and only one copy of ubuntu and one copy of windows 7 but for some reason 2 of each showed up after updates after the install. Any thoughts?

---

### Post by ksprasad on 2011-04-10
Hi,
 
 run the command,
 
 sudo update-grub
 
Regards,
ksprasad

---

### Post by ksprasad on 2011-04-10
for more reference, follow the below link :-)
 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 
Regards,
ksprasad

---

### Post by ~Plue on 2011-04-10
the multiple ubuntu entries are probably the older kernels. you could search for *linux-image* in synaptic and remove them or use [ubuntu-tweak]("http://ubuntu-tweak.com/")
both methods are explained in detail here >> [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

not so sure about the multiplying windows entries though.. what doest the titles say?

---

### Post by miradus on 2011-04-10
> **~Plue said:**
> the multiple ubuntu entries are probably the older kernels. you could search for *linux-image* in synaptic and remove them or use [ubuntu-tweak]("http://ubuntu-tweak.com/")
both methods are explained in detail here >> [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

not so sure about the multiplying windows entries though.. what doest the titles say?

Two say Windows 7 Loader, and one says Windows Vista Loader, odd eh?

---

### Post by ~Plue on 2011-04-10
> **miradus said:**
> Two say Windows 7 Loader, and one says Windows Vista Loader, odd eh?
did you check and see which of them works? see if *sudo update-grub* picks it up correctly

---

### Post by miradus on 2011-04-11
> **~Plue said:**
> did you check and see which of them works? see if *sudo update-grub* picks it up correctly

I ran the update and all three work, the first 2 load the same windows version of 7 on my primary partition, and the 3rd is my recovery partition.

---

### Post by Rex Bouwense on 2011-04-11
If the extra listing of Ubuntu is not a previous kernal, it probably is the recovery start up.  You probably need to keep at least one previous kernal on the list in case something happens to the one that you are using so be careful what you are deleting.

---

