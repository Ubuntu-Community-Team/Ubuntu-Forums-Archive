---
title: "Grr the keyring things annoying"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2006-10-21
how do i remove the keyring and get network manager to just connect.

Ive accidently set my keyring pass to my WPA key!!! which is really long and asks me every boot.


what can i do?

---

### Post by localuser on 2006-10-22
You should be able to access the Keyring Manager from 

System | Administration | Keyring Manager

---

### Post by dgrafix on 2006-10-22
i have no keyring manager option in either admin or prefs menu
 
whats its term command?

---

### Post by localuser on 2006-10-22
Try this, dgrafix...

Go to Applications | Accessories | Alacarte Menu Editor

In the menu editor, on the left click, on System | Administration

On the right select Keyring Manager

---

### Post by dgrafix on 2006-10-22
It want there, but i found it in synaptic and installed it. Weird thing is though it it hasnt got the ubuntu symbol next to it, (which i think means it is not a 'ubuntu reccommended' install?!?).

Anyway, i installed it and now i get keyring manager on the admin menu.

Thanks

---

### Post by Watchin on 2006-10-22
Is there a way to either not have the keyring used or have keyring
not ask for a password on startup?

I accidently invoked it on initial install and now it asks every
boot before it will allow the wireless to start.

thanks,

---

### Post by AgenT on 2006-10-29
> **dgrafix said:**
> It want there, but i found it in synaptic and installed it. Weird thing is though it it hasnt got the ubuntu symbol next to it, (which i think means it is not a 'ubuntu reccommended' install?!?).

Anyway, i installed it and now i get keyring manager on the admin menu.

Thanks
gnome-keyring and gnome-keyring-manager are packages that are REQUIRED for Ubuntu. If you did not have these (which you did not, since you say you manually installed them yourself) then your installation or upgrade of Edgy was not completed. You should make sure that ubuntu-desktop is installed.

---

### Post by dgrafix on 2006-10-29
Im using ubuntu Dapper, could be why

---

