---
title: "Where are network profiles stored?"
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by emendelson on 2005-04-22
Hello,

I once found this information, but now can't find it again, and I hope a guru can help me out:

Where does the Network Settings application (System/Administration/Networking store its profiles? I would like to edit them by hand, but can't find them.

Thanks for any help.

---

### Post by ejohney on 2005-04-22
kind of all over the place, which section do you need? 

the connections tab is /etc/network/interfaces
general is /etc/hostname
dns is /etc/resolv.conf
and hosts ist /etc/hosts

hope that's what you needed  :)

---

### Post by emendelson on 2005-04-23
Thanks for that - and the file with the configuration for the networking profiles found in the Gnome network settings application are here:

/etc/gnome-system-tools/network

Those were the ones that I couldn't put my hands on...

---

### Post by benbacardi on 2007-10-26
Where are they stored in 7.10? I need to remove some settings and I can't find where the network manager stores the settings to alter them...

Any help much appreciated!

---

