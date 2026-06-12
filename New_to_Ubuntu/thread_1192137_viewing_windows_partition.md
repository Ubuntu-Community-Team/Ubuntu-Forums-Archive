---
title: "viewing windows partition"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by brianhillman on 2009-06-19
ok im not very good w/computer ( not enough to get beryl to work) and i need help viewing the files on my windows 7 partition since win 7 is going to expire very soon. also is it possible to run .exe files i have on the win side? ( mostly games)

---

### Post by starcraft.man on 2009-06-19
Win 7 isn't expiring soon. I thought MS was giving free 1 year keys to anyone who signed up?

Also, you don't need anything extra to look at ntfs partitions. Install the restricted packages and that includes ntfs-3g, a driver to read windows partitions. To do so, open a terminal, Applications > Accessories > Terminal and type in "sudo aptitude install ubuntu-restricted-extras" and then push enter. Once done, go to Places in the top panel and you should see under the entry "Computer" several partitions, select the one you want to mount and read and you'll be prompted for your login password and that's it.

You can copy over any files after that to Linux without trouble.

As to .exes, google a program called WINE. You might also want to search for a program called playsonlinux. It's a bit involved to get such windows programs working on linux, don't expect it to work perfect or be a perfect windows replacement.

---

### Post by valikor on 2009-06-19
Starcraft.man--let's play some Starcraft :)

---

### Post by starcraft.man on 2009-06-19
> **valikor said:**
> Starcraft.man--let's play some Starcraft :)

Hehehe, not right now, haven't played in a bit. Reminds me, I need a new icon, seen new Starcraft 2 wallpapers.

---

### Post by brianhillman on 2009-06-19
Thanks man that helped a lot. with the whole win 7 thing i think there are 2 versions at this point the beta and release candidate i am running the beta and i believe it expires ( yesterday i got a warning saying 13 more days)

---

### Post by starcraft.man on 2009-06-19
> **brianhillman said:**
> Thanks man that helped a lot. with the whole win 7 thing i think there are 2 versions at this point the beta and release candidate i am running the beta and i believe it expires ( yesterday i got a warning saying 13 more days)

Yup. If you wanna keep it, you have to get the RC version and register for a key. Or just stay with Ubuntu, that's good too. I mean it's not like I'm trying to get you not to use linux, it's a good OS.:lolflag:

Anyway, just dump all your important files onto your home directory (assuming it's big enough) and then you can safely reformat the windows section into an NTFS storage drive (or EXT3/4) or get an RC key and put in Windows. Lots of options.

---

