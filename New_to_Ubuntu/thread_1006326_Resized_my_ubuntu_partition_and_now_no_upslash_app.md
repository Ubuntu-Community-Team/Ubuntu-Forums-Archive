---
title: "Resized my ubuntu partition and now no upslash appearing"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-12-09
After i increase my ubuntu partition, now my upslash is black, how do i fix it?

---

### Post by drs305 on 2008-12-09
These instructions are just to restore the usplash. If you are having video problems which prevent normal viewing, this won't fix it.

The UUID may have changed, requiring you to update a reference.
Run this command to compare UUIDs:
```
sudo blkid  | grep swap | sed 's/\([^ ]*\)*/\l/' && cat /etc/initramfs-tools/conf.d/resume

```

If the two don't match, change the UUID in the following file to match the value from the blkid command:
```

gksu gedit /etc/initramfs-tools/conf.d/resume  # Replace UUID
sudo update-initramfs -u
sudo reboot now  # SHutdown and restart - make sure you have saved any open work files.

```

---

### Post by caljohnsmith on 2008-12-09
If the UUID of your swap partition does not match what is in /etc/initramfs-tools/conf.d/resume, another option is to just change the UUID back to what it is in that "resume" file:
```
cat /etc/initramfs-tools/conf.d/resume
```
First make sure the swap partition isn't mounted, and then change the UUID to what is in the resume file above (copy/paste it):
```
sudo swapoff -a
sudo mkswap -U "[COLOR="Blue"]<UUID>[/COLOR]" /dev/sdXY
sudo swapon /dev/sdXY
```
And replace sdXY with the swap partition. Or if you want to do it as drs305 gives, you might also have to update your /etc/fstab with the new swap partition UUID. Either way should work though.

---

### Post by ibizatunes on 2008-12-09
Thanks for the help, just got home and that fixed my issue!!

---

