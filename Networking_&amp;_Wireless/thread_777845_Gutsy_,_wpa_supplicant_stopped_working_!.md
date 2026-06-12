---
title: "Gutsy , wpa_supplicant stopped working !"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by guix on 2008-05-01
Hi,

I'm still on Gutsy and suddenly (after the last update which updated only update-manager and update-manager-core) my atheros ar5212 chipset can't connect to my access point. Instead it keeps trying to connect to other access points.

I didn't change any setting, I'm not using network manager, it's all in /etc/network/interfaces and was working very well.

In htop I see that wpa_supplicant often launches, normal because it can't connect.

I checked the wireless connection on Windows with my usual settings and it's fine...

Anyone else having this kind of problem ?

---

### Post by guix on 2008-05-09
Nobody has a clue ?

---

### Post by kevdog on 2008-05-09
Update broke your patched madwifi driver.  That is what happened.  Need to recompile or just reinstall the driver.

---

### Post by guix on 2008-05-09
Thanks a lot for replying !
Something got updated lately in Gutsy regarding the wireless stack ? I didn't notice.
I didn't recompile yet because "iwlist scanning" for instance works so thought it wasn't a madwifi problem.

---

### Post by guix on 2008-05-10
Upgraded to Hardy and still the same problem, I've written a more detailed post here : [http://ubuntuforums.org/showthread.php?t=789269](http://ubuntuforums.org/showthread.php?t=789269)

---

