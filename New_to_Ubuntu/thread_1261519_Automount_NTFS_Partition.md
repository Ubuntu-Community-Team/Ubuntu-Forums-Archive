---
title: "Automount NTFS Partition"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by RealG187 on 2009-09-08
I have an NTFS partition that's /dev/sda2 that I wish to have mounted as "/media/Files" automatically.

What lines would I add to /etc/fstab

I don't wanna screw this up...

---

### Post by chandru155 on 2009-09-08
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

Hope that will help you

---

### Post by RealG187 on 2009-09-08
Yes it did, it was easy.

In a way that's good, but in a way that's bad because if I would need to edit the /etc/fstab I would know know how.

It seems that program added the line for me.
/dev/sda2 /media/Files ntfs-3g defaults,locale=en_CA.UTF-8 0 0
So it's device_path mount_path filesystem defaults,locale=en_CA.UTF-8 0 0

I have no idea what defaults,locale=en_CA.UTF-8 0 0 means...

---

### Post by Cheezespread on 2009-09-09
_defaults_
Defaults is written in the portion where options for the mounted drive are specified. In Ubuntu the default options are :
defaults = rw, suid, dev, exec, auto, nouser, and async.

[URL="https://help.ubuntu.com/community/Fstab"]
This link [/URL] should give you a better idea.

_locale=en_CA.UTF-8 0 0_

UTF-8 is the unicode transformation Format ( 8 bit ) . More on it [here]("http://en.wikipedia.org/wiki/UTF-8"). I believe the locale section implies you are using English as your language !. Am not sure though.

The last two zeroes in that entry ( i believe ) are for the dump and fsck.

Dump is a backup utility and Fsck is the Filesystem check thing. Since you have set it to 0 for both of them , this particular entry( mounted partition) would be ignored or not added into the list of files which are to be checked or backed up.

[B][U]
Fstab[/U][/B]

/dev/sda2 /media/Files ntfs-3g defaults,locale=en_CA.UTF-8 0 0

You can edit it to this if you want to:


/dev/sda2 /media/Files ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

The auto,users part mean that the drive would be automounted and any user can mount the drive on boot.The dmask and fmask options specify the persmissions for users for the directories and files.

Please correct me if am wrong.

If you wish to read up on fstab , [this Forum entry by BodhiZazen]("http://ubuntuforums.org/showthread.php?t=283131") is the best

---

