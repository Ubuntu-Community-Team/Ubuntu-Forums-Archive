---
title: "Updating"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by IamWayne on 2009-05-08
I am having trouble updating. I have jaunty installed. Whenever I try to update I get this message:

 The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


  Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Some index files failed to download, they have been ignored, or old ones used instead. Sorry, I'm a noob.

---

### Post by taurus on 2009-05-08
Go into System -> Administration -> Software Sources and remove the check mark(s) for your Cdrom.  Then, update your machine again.

---

### Post by Didius Falco on 2009-05-08
Go to **System/Administration/Software Sources** an uncheck the I**nstallable from CD-ROM/DVD**box on the **Ubuntu Software** tab.

Make sure you've closed Synaptic and/or Update Manager before doing this. It'll prompt you to reload the sources, do so and then you will be able to Update.


Regards,

Didius

On Edit: I type too slow...<G>

---

### Post by IamWayne on 2009-05-08
> **taurus said:**
> Go into System -> Administration -> Software Sources and remove the check mark(s) for your Cdrom.  Then, update your machine again.



O.K. I'll try that Thanks! Yeah who needs 'em.

---

### Post by IamWayne on 2009-05-09
This worked, problem solved. Thanks everybody!:):)

---

