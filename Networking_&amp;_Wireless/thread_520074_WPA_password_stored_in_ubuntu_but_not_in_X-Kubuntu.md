---
title: "WPA password stored in ubuntu but not in X-/Kubuntu"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Tmi on 2007-08-07
As the topic states ....
I'm using a wireless connection with WPA password. In "normal" Ubuntu my WPA password is stored in the keyring thingie and thus I only have to type my own use password to get connected rather than the whole WPA password.

After installing Xubuntu-desktop to try it out I noticed that it didn't connect me to my wireless while booting. I launch Knetworkmanager and manually enter my WPA password, and it works fine. The password is, however, not stored, so I have to type it in after every reboot, which is fairly annoying as it is 50 characters long.
I instead try the other network manager, which I think is the one called NetworkManager just as in normal Gnome. When I start that I can't even chose WPA, it only has WEP-options.

So in short, in Xubuntu I can't use the KDE network manager since it doesn't store the password, and I can't use the Gnome network manager since it won't allow WPA.
The latter does however work in normal Ubuntu (gnome).

So, is there any easy way to fix this or should I just stick with normal ubuntu where it all works?

---

### Post by jimrz on 2007-08-07
> **Tmi said:**
> As the topic states ....
I'm using a wireless connection with WPA password. In "normal" Ubuntu my WPA password is stored in the keyring thingie and thus I only have to type my own use password to get connected rather than the whole WPA password.

After installing Xubuntu-desktop to try it out I noticed that it didn't connect me to my wireless while booting. I launch Knetworkmanager and manually enter my WPA password, and it works fine. The password is, however, not stored, so I have to type it in after every reboot, which is fairly annoying as it is 50 characters long.
I instead try the other network manager, which I think is the one called NetworkManager just as in normal Gnome. When I start that I can't even chose WPA, it only has WEP-options.

So in short, in Xubuntu I can't use the KDE network manager since it doesn't store the password, and I can't use the Gnome network manager since it won't allow WPA.
The latter does however work in normal Ubuntu (gnome).

So, is there any easy way to fix this or should I just stick with normal ubuntu where it all works?

never have used network-manger/network-manager-gnome with KDE, but have used it successfully in xfce. if I remember correctly you need to manually add it to your startup progs in xfce.

---

### Post by Tmi on 2007-08-08
I think I tested that with no help. It's not the program startup that is not functioning, it's just that it doesn't store the WPA password. In Gnome keyring handles this, so maybe there is something similair in Xfce?

---

