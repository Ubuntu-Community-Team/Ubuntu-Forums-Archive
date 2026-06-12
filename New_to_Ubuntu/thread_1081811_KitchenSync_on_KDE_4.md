---
title: "KitchenSync on KDE 4?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-26
I'm trying to get KitchenSync running on Kubuntu Intrepid but there doesn't seem to be an available version. MultiSync isnt working for some reason but synce-kpm recognises my device and syncs fine. The only problem is synce-kpm doesn't actually sync with any programs in any way that I can get to work.

I absolutely love synce-kpm and cant believe it recognises my device and displays so much info when It's been such a pain to get anything else to work!

I found [this]("http://www.nabble.com/kde4-kitchensync-for-current-opensync-packaged-td19278317.html") but it's for OpenSUSE and in RPM. Alien just returns a string of errors when I try to convert it to .deb

```
chris@Linux-desktop:~/Desktop$ sudo alien --to-deb kitchensync.rpm
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
warning: kitchensync.rpm: Header V3 DSA signature: NOKEY, key ID 127951f7
Unpacking of 'kitchensync.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.
```

Does anyone know of a way to get KitchenSync installed in KDE 4+? I had the understanding that packages were backwards compatible with their desktop environments.

I've got a .deb file for KitchenSync but it says there is unsatisfiable dependencies **libkcal2b**

When I download **libkcal2b** the deb installer tells me I need **libkdepim1a**. When I downloaded that deb it tells me I need **libkcal2b** just like the KitchenSync deb does... How can packages be dependencies of eachother? There's no way to install them?

---

### Post by Xiong Chiamiov on 2009-02-27
Did you have this program working before?  If so, what did you do that caused it to stop working?

---

### Post by HittingSmoke on 2009-02-27
> **Xiong Chiamiov said:**
> Did you have this program working before?  If so, what did you do that caused it to stop working?

No no. This package doesn't have a KDE 4 version. It's not in the intrepid repos, the last was Hardy. I got a hold of a .deb for it and it's dependencies but I'm getting the errors above. The dependencies for KitchenSync claim to also be dependencies of each other, so each time I try to install one it says I need the other first.

I just want to know if there's a way to get it working on Kubuntu Intrepid

---

### Post by pwabrahams on 2010-12-17
I too am pining for a working Kubuntu version of KitchenSync -- in this case, for Meerkat.  I'm also running OpenSUSE -- and the lack of KitchenSync gives me a good reason to continue running it.  I wonder why OpenSuSE supports it and Kubuntu doesn't.  Of course the two systems use different package formats (**.deb** versus **.rpm**), but that in itself doesn't explain it.

In my case I'm trying to sync a Palm Pilot, and the disappearance of kpilot in KDE4 left me high and dry.  I've been trying an exotic solution: running the Palm desktop in Windows under VirtualBox.  Trouble with that is that VirtualBox's handling of USB devices is flaky when the device is connected only intermittently; the Palm shows up with **lsusb** only when it's actually syncing. Sometimes it works and sometimes it doesn't.

---

