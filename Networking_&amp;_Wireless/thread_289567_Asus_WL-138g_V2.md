---
title: "Asus WL-138g V2"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by aks_! on 2006-10-31
Hello,

I have a problem that I can't solve. I have installed Asus wl-138g v2 wireless card to my computer running Edgy Eft. The card gets properly recognized by the system (it is listed in the Networking and also in the Device Manager), but Network Manager (Gnome) doesn't show any wireless connection available, when there should be one (wifi router is about 10 meters away). I also tried to installed the Linux drivers found on Asus site but there has been no success so far even with these drivers installed.

Does anyone know what to do?

Thanks.

---

### Post by aks_! on 2006-10-31
If the wireless card is recognized by the system, it should work or am I mistaken? I would just like to locate the source of the problem so I could eliminate it.:)

---

### Post by aks_! on 2006-10-31
OK, I have managed to install the drivers using ndiswrapper (see [http://www.ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://www.ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318) ).

---

### Post by lfys on 2006-11-14
and did they work?

---

### Post by 4martin1 on 2006-12-01
I followed the intructions of nbound in the post [http://www.ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://www.ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318) to install my asus 138g V2 wireless card. And yes, it works!!!

---

### Post by haytona on 2008-02-26
For gutsy (0710) see: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)
(adding this here as google landed me here)

---

