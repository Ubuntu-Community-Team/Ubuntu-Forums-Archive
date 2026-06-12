---
title: "Mapping drive located on novell oes server"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by FUBAR-BDHR on 2014-06-15
I have a couple of Novell servers one is Netware 6.5 the other is a OSE server.  I need to be able to map to the drive son these server (can do without the 6.5 one but definitely need the OES shares) but everything I found on how to do it does not work.  Most of the things require ncpfs to be installed which seems to no longer be available.  I've also seen examples of just using mount but these also fail with messages about wrong fs type, bad superblock, bad option.  

So how do you actually map a Novell network drive in Ubuntu 14.04?

---

### Post by bab1 on 2014-06-15
> **FUBAR-BDHR said:**
> I have a couple of Novell servers one is Netware 6.5 the other is a OSE server.  I need to be able to map to the drive son these server (can do without the 6.5 one but definitely need the OES shares) but everything I found on how to do it does not work.  Most of the things require ncpfs to be installed which seems to no longer be available.  I've also seen examples of just using mount but these also fail with messages about wrong fs type, bad superblock, bad option.  

So how do you actually map a Novell network drive in Ubuntu 14.04?

The ncpfs package is available in Ubuntu 12.04 LTS.  Ubuntu 12.04 is supported until 2017.

---

### Post by FUBAR-BDHR on 2014-06-15
Not really sure how that helps with 14.04 unless I can use the older ncpfs package?

---

### Post by bab1 on 2014-06-15
> **FUBAR-BDHR said:**
> Not really sure how that helps with 14.04 unless I can use the older ncpfs package?

The party line to your question *"So how do you actually map a Novell network drive in Ubuntu 14.04?" * is,  you can't.

Who knows whether you can use the older package.  You can always try it.  You would have to load the 12.04 repos however.  For sure you will have libc6 version conflicts.
 
Why do you have to use 14.04?  If the data is sooooo important  I'd install 12.04, the ncpfs package and retrieve the data.

---

### Post by FUBAR-BDHR on 2014-06-16
Well the workstation is already configured and running 14.04.  Seems like a step backwards to wipe everything, reload with an older version, and configure everything on the machine again to access the server.

---

### Post by bab1 on 2014-06-16
> **FUBAR-BDHR said:**
> Well the workstation is already configured and running 14.04.  Seems like a step backwards to wipe everything, reload with an older version, and configure everything on the machine again to access the server.
Sometimes you do what you have to do.  I'd put the retrieved data on a separate disk for safe keeping.  Later you can reinstall 14.04 if you wish.

---

