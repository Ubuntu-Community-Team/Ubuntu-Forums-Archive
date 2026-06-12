---
title: "Update Error Message"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Wyatt208 on 2009-03-17
I have Ubuntu 8.10 (Intrepid Ibex) and I have installed many various applications. Anyways, I run the update manager and I get this message :
Not all updates can be installed 
Run a partial upgrade, to install as many updates as possible.

and so on. This message doesn't affect my ability to update, It just worries me that I might not be able to upgrade sometime in the future.

---

### Post by Volt9000 on 2009-03-17
Does it give any more information than that? Like what updates weren't applied?

---

### Post by BDNiner on 2009-03-17
They are normally greyed out when you cannot update them. If u can list the updates that are broken then we will see what is going wrong. Running 
```

sudo apt-get update
sudo apt-get upgrade

```
will give a better idea of what is not being updated.

---

### Post by avtolle on 2009-03-17
My perspective: sometimes, there are apps ready for upgrade, but the dependencies aren't ready yet, or, the upgraded/updated apps have hit the server before the upgraded/updated dependencies. Update manager recognizes this, and generally, the user will be offered a partial upgrade/update for those things which are now safe to install (which won't break the user's system). When I've encountered this in the past, I've allowed the partial upgrade/update on my test system; then, when the rest of the packages are ready and downloaded there, I go ahead and do the full thing on my production machine. 

That said, I've not had any problems with partials. There are threads on the Forum posted by folks who have. To be safest, I'd suggest when confronted with the "partial upgrade" message to cancel, and check the status later (perhaps the next day) to see if a full upgrade can be accomplished at that point.

Another thought; changing servers to the main server in Software Sources, if one is using another server. That has seemed to be a solution in the past for me and, from what I've read, others. 

HTH.

---

### Post by rafac24 on 2009-03-17
Pretty sure I had this problem once and it was because I had CD-ROM enabled in Software Sources. 

System -> Administration -> Software Sources
Uncheck the box that says 'Cdrom with Ubuntu 8.10'

Don't know if that will resolve the issue but it's worth a look.

---

### Post by Wyatt208 on 2009-03-17
I ran the code: and this is what came up:

```
W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://fr.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://voxel.dl.sourceforge.net/sourceforge/actiongame/AssaultCube_v1.0.2.tar.bz2/dists/intrepid/main/binary-i386/Packages.gz  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
wyatt@wyatt-laptop:~$ 
```

The assault-cube binary is understandable, but.. aha! It's trying to fetch updates for feisty. If I delete those off of my source list, will that adversely affect my upgrading ability?
Also, the update from CD-ROM box was not checked.

---

### Post by Botbob89 on 2009-03-17
What's your internet connection? As I'm at university, when I'm on campus I'm behind a proxy that requires some configuration on Ubuntu....

---

### Post by Wyatt208 on 2009-03-18
I just have Wi-Fi , I don't know much about proxy and that stuff. The message does not affect my ability to download though. It's just wierd.

---

### Post by Therion on 2009-03-18
Have you tried using a different download server?

---

### Post by Wyatt208 on 2009-03-18
I'm pretty sure it's the feisty server that's messing me up, but it I uncheck that in software sources, will that adversely affect my upgrading ability?[ATTACH]106824[/ATTACH] That's what I get when I update. Also, In the update manager itself, it says : The package information was last updated 62 days ago. But still, I can fully update. Why is that?

---

### Post by drs305 on 2009-03-18
Untick the feisty references via synaptic or manually edit sources.list and remove them. It will not hurt your current install and will prevent the associated error messages.

---

### Post by Wyatt208 on 2009-03-19
Thanks.Now it works.

---

