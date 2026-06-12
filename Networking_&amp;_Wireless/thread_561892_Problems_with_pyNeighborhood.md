---
title: "Problems with pyNeighborhood"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by iangregson on 2007-09-28
Hi there,

I wonder if anyone can help me, i am having problems with pyNeightborhood.. In the network tab ... i can now see my workgroup but double clicking it gives "Failed to scan workgroup Development"  

anyway I managed to add the machine (vista) directly using add, add machine... and entering the ip address etc...

So i can see my vista machine with all its shares, excellet but after clicing on any of the shares it says "Failed to mount" but i have no other information..

In Edit, preferences i have deselected Always use anon logins and entered a username and password that exists on my vista machine..

Is there any other way to see a detailed error output as the Failed to scan workgroup and failed to mount don't really give that much helpful information.

If anybody has any information i would be really grateful if you can share it... i follwed this guide to install the pyNeighborhood  

[http://ubuntuforums.org/showthread.php?t=280473&highlight=smbfs+gui](http://ubuntuforums.org/showthread.php?t=280473&highlight=smbfs+gui)

Also another thing is where is the standard place to mount shares in ubuntu... i am guessing but i presume MNT ??? i know you can mount anywhere you please but i wanted to try and keep things king of standard if possible... anybody know?

Thanks in advance

---

### Post by iangregson on 2007-09-28
I also saw this post that recommends to install midnight commander... i did this and rebooted but everything is still the same

[http://ubuntuforums.org/showthread.php?t=424489](http://ubuntuforums.org/showthread.php?t=424489)

---

### Post by bremen on 2007-10-29
The problem is that regular users do not have permission to mount shares.  From the command line run py

```
gksudo pyNeighborhood
```

Be careful though as any file manager you lunch from it will inherit root permissions (which is far from ideal but at least works)

---

