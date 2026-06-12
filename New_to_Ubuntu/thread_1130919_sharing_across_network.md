---
title: "sharing across network"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by ELD on 2009-04-20
I have installed samba but when i try to share a folder it says i need the right permissions, i tried changing the folders permissions but it is set to root :(

This is a folder on an ntfs mounted partition btw.

Also how can i get ubuntu to auto mount ntfs on startup, i always forget when i do a fresh install :(

---

### Post by aeiah on 2009-04-20
which howto did you follow for samba? a lot of the tutorials will guide you through how to set it up properly. the same goes for mounting your ntfs partition. try searching for 'fstab ntfs' or something. fstab is the file you edit to permanently mount partitions.

---

### Post by philinux on 2009-04-20
If the ntfs folder is on a windows box you need to use windows to share it.

Can you explain your network?

---

### Post by juancarlospaco on 2009-04-20
python -m SimpleHTTPServer

*share something inside your $HOME*
;P

---

### Post by john stiles on 2009-04-20
Do not forget if you have a firewall (on the router and maybe on each desktop)to allow traffic from others on the network.

---

### Post by ELD on 2009-04-20
> **philinux said:**
> If the ntfs folder is on a windows box you need to use windows to share it.

Can you explain your network?

As i said before it is an ntfs partition that i mount under ubuntu, like many others do. It is just i don't have the right permissions on it.
And no i don't want to move everything into my home to share it, it's over 200GB would take too long to move, and i have seperate partitions for seperate media which i would like to share.

I also used a program before to auto-mount it i didnt have to edit an fstab entry, anyone know that program?

---

