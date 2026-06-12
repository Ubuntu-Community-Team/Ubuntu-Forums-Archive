---
title: "NetworkManager wireless ap preference"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by kiddyfurby on 2007-07-03
Is there any preference list that NetworkManager maintains?
I've previously connected to a wireless network that I no longer want to access
Is there anyway to stop NetworkManager from connecting to it again?

---

### Post by spd106 on 2007-07-03
Try the Network Manager wiki page, specifically the part about gconf.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-d2b310228dc887b6cddf4465b6a53cdc4dc9be28)

---

### Post by kiddyfurby on 2007-07-05
thanks, will take a look

i've actually searched for such key in gconf
found the ap name, but i can't delete the "folder", only keys in it can be deleted.

---

### Post by spd106 on 2007-07-05
If it contains no keys the folder will be automatically deleted when gconf is restarted. 

You can also use the command line based gconftool-2 utility to achieve the same goal or even edit the xml directly, it just takes more skill/experience as mistakes are easier.

---

### Post by kiddyfurby on 2007-07-09
yay, its working

searched for the ap name and removed the corresponding keys in gconf
btw i think networkmanager should provide ui for this, as gconf-editor is not supposed to be installed

---

