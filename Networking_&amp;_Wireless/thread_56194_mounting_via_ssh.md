---
title: "mounting via ssh"
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by pataphysician on 2005-08-11
i have two linux machines, a gentoo desktop and an ubuntu laptop, on a little network here. i'm trying to mount a directory from the gentoo box to the laptop. operating from a root terminal in ubuntu, i can do this to log into the gentoo machine:

ssh 192.168.0.101

i'm prompted for the root password, which i provide. then i login.

however, if i do

mount ssh://root:password@192.168.0.101/dir_to_mount /mnt/gentoo
"mount failed, reason given by server: permission denied."

this happens even if i just do
mount ssh://root@192.168.0.101/dir_to_mount /mnt/gentoo
mount ssh://192.168.0.101/dir_to_mount /mnt/gentoo

i get the same thing. i'm never prompted for a password.

is there something else i need to do here? how can i mount a directory using ssh?

---

### Post by Dogmeat on 2005-08-11
You need to have the SHFS module installed. Get these packages in synaptic: 

```
shfs-source - (secure) SHell File System module source
shfs-utils - (secure) SHell File System mount programs

```

It will then install module-assistant too, to help you build the SHFS module for your kernel version. Follow the steps in module-assistant, and if everything goes ok you should now be able to use the shfsmount and shfsumount commands.
I did this for ubuntu, for gentoo you should have some similar packages.

---

### Post by pataphysician on 2005-08-11
thanks! i'll check it out.

---

