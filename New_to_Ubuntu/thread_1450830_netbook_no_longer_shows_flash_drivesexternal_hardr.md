---
title: "netbook no longer shows flash drives/external hardrive in volumes"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Iknownothing on 2010-04-09
Deleted games and software that came with the net book remix to make space on hardrive now no longer shows flash drives/external hardrive in volumes, net book is a mini 9

---

### Post by -humanaut- on 2010-04-09
What did you delete?? 

try this "sudo apt-get install hal"

---

### Post by Iknownothing on 2010-04-09
hal is already the newest version.
The following packages were automatically installed and are no longer required:
  python-crypto empathy-doc telepathy-salut libqt4-assistant gnome-mahjongg lsb-graphics lsb-desktop libindicate-gtk1 m4
  ncurses-term libempathy-gtk28 python-telepathy libloudmouth1-0 gnome-games-common telepathy-haze libqt4-gui gnotski lsb
  pax iagno telepathy-gabble libempathy-gtk-common telepathy-butterfly python-papyon lsb-core lsb-cxx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carl@carl-netbook:~$ 
 
Nothing has happened as of yet, what did I delete, I really can't remember, lots

---

### Post by -humanaut- on 2010-04-09
Try downloading pmount "sudo apt-get install pmount" if you can't mount from that my guess is well have to reconfigure the fstab file one more thing when you plug a device in can you open a terminal type "dmesg | tail" and post it here

---

### Post by Iknownothing on 2010-04-10
> **-humanaut- said:**
> Try downloading pmount "sudo apt-get install pmount" if you can't mount from that my guess is well have to reconfigure the fstab file one more thing when you plug a device in can you open a terminal type "dmesg | tail" and post it here Thank you so much, worked a treat, cheers!!!

---

### Post by -humanaut- on 2010-04-10
No problem, Glad I could help you out.

---

