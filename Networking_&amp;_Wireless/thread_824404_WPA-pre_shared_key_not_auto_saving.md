---
title: "WPA-pre shared key not auto saving"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by cutcrank on 2008-06-10
Hi,

I have a vaio laptop, vgn b77gp, on which Gutsy is running. Whenever i connect to my office wireless network it is asking me to enter the wpa-preshared key. Earlier it was not like this and the preshared key was saved in the laptop and i was able to connect without entering it everytime. Now it is not getting saved. What could be the problem?

Thanks.

---

### Post by almax00 on 2008-06-10
is there a kwallet icon in your "system tray"? right click it and you can configure kwallet. if there isn't go to konsole and enter kwalletmanager and kwallet will launch and you can configure it. check to see if "enable the KDE wallet subsystem" is checked.

i stopped using kwallet for my WPA phrase because it seemed like my connection kept dropping so i just manually enter it the few times i have to re-boot,etc. YMMV

---

### Post by cutcrank on 2008-06-11
> **almax00 said:**
> is there a kwallet icon in your "system tray"? right click it and you can configure kwallet. if there isn't go to konsole and enter kwalletmanager and kwallet will launch and you can configure it. check to see if "enable the KDE wallet subsystem" is checked.

i stopped using kwallet for my WPA phrase because it seemed like my connection kept dropping so i just manually enter it the few times i have to re-boot,etc. YMMV

It's gutsy with gnome which is installed in the laptop.

Will it work the same if i use wifi radar?

---

