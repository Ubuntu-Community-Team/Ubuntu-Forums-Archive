---
title: "installing games via iso file???"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-25
i want to install rollercoaster tycoon on my samsung nc10 netbook as i have nothing better to do with my time and i get bored quickly. now the problem is the netbook doesnt have a  CD drive and i dont have an external...my question is, is there a way to copy the CD content to a usb and make the game install from it?? also, how would i make the game (when installed) load without the CD (or USB in this instance)?


any help will be appreciated.:guitar:

---

### Post by sisco311 on 2009-10-25
Make an iso image from the CD and mount the iso in Ubuntu.
[uhelp]community/MountIso[/uhelp]

---

### Post by Jekshadow on 2009-10-25
First mount it and make it so that you can read and write to it. It will appear as a directory.

```

sudo mkdir /mnt/iso
sudo mount -o loop /path/to/my.iso /mnt/iso
sudo chmod a+rxw /mnt/iso

```

and when you are done, just unmount it and delete the directory

```

sudo umount /mnt/iso
sudo rm -r /mnt/iso

```

---

