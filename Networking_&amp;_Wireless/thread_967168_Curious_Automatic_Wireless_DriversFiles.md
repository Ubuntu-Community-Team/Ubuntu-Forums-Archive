---
title: "Curious: Automatic Wireless Drivers/Files"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by kestal on 2008-11-01
Though I know this may be utterly 'newbie' of me to ask, I will do so anyway, because I am curious.

What is stopping Canonical/Ubuntu Developers from including wireless drivers (like B43/B44) or certain atheros files into default Ubuntu Packages available from first install?

is it to do with copyright issues? or not open source?

I know for the b43 drivers (even without the use of Ndiswrapper or anything), all you have to do is place a file into lib/firmware/*** generic/, and it works (tried it on multiple laptops with the same issue and worked every time)...  I mean, if all it takes is dropping  a file into the folder, or even including the install to detect the hardware (and if present then to drop it in the folder by default), then whats the hold up?

Its not TOO bad for me as I have the files needed on a jumpdrive, for every time I install Ubuntu/Xubuntu, but I only have wireless at home so its just inconvenient. If its a copyright issue, I understand that not much can be done though until the developers of the hardware give it thumbs up.. I am just not too sure on what the issues are with this.

I guess I may be just a bit confused. On that note though, other than that, Ibex is great.

---

### Post by kestal on 2008-11-02
anyone wish to fill me in? I am still not used to this whole open source/closed source bit.

---

### Post by Ayuthia on 2008-11-02
> **kestal said:**
> Though I know this may be utterly 'newbie' of me to ask, I will do so anyway, because I am curious.

What is stopping Canonical/Ubuntu Developers from including wireless drivers (like B43/B44) or certain atheros files into default Ubuntu Packages available from first install?

is it to do with copyright issues? or not open source?

I know for the b43 drivers (even without the use of Ndiswrapper or anything), all you have to do is place a file into lib/firmware/*** generic/, and it works (tried it on multiple laptops with the same issue and worked every time)...  I mean, if all it takes is dropping  a file into the folder, or even including the install to detect the hardware (and if present then to drop it in the folder by default), then whats the hold up?

Its not TOO bad for me as I have the files needed on a jumpdrive, for every time I install Ubuntu/Xubuntu, but I only have wireless at home so its just inconvenient. If its a copyright issue, I understand that not much can be done though until the developers of the hardware give it thumbs up.. I am just not too sure on what the issues are with this.

I guess I may be just a bit confused. On that note though, other than that, Ibex is great.

I am not sure about Atheros, but for the b43 driver, it requires portions of a proprietary firmware file.  This proprietary file has licensing on it that does not allow Ubuntu to include the file on the CD or the initial install.

Broadcom does provide a proprietary version of their wireless driver (for the 4311, 4312, 4321, 4322, and 4328) cards.  It does not require any firmware and is included in Intrepid and Hardy (if you have 2.6.24-21 or higher installed).  However, it is proprietary so if you want to use it, you have to go into System->Administration->Hardware Drivers to activate it.  If I understand correctly, Ubuntu does not install proprietary software on the initial install, but does allow you to install them later if you want it.

Hope that helps.

---

### Post by kestal on 2008-11-02
See, thats weird.. cuz I have tried to go to System -> Administration -> Hardware Drivers from an out of the box install, but it did NOT detect anything related to broadcom at all. Even after restarts and other things.

It DID, however, detect it AFTER I placed files in the firmware / folder (from my jumpdrive). Thats why I am confused.

Thanks for the reply though, I figured this thread would get lost.

---

### Post by Ayuthia on 2008-11-02
> **kestal said:**
> See, thats weird.. cuz I have tried to go to System -> Administration -> Hardware Drivers from an out of the box install, but it did NOT detect anything related to broadcom at all. Even after restarts and other things.

It DID, however, detect it AFTER I placed files in the firmware / folder (from my jumpdrive). Thats why I am confused.

Thanks for the reply though, I figured this thread would get lost.

Is this in Hardy?  If so, I think that it is a bug in there.  It looks like it is fixed in Intrepid though.  I had the same problem, but I usually install it manually.

---

