---
title: "start over or can i fix it?"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by ninavicci on 2010-09-18
my dell mini 9 with ubuntu 8.04 lts died when i accidentally ran the updates. i tinkered a little and got it to turn off and not be completely locked up and now there is no internet connection and it won't turn off... should i start over and reinstall or keep trying? obviously i know nothing about ubuntu. thanks for your help.

---

### Post by Spencer Caplan on 2010-09-18
What updates did you run? Did you do "system, administation, update-manager" or something from command line?

---

### Post by ninavicci on 2010-09-18
i just clicked the update managericon and ran them all--there was not enough space and it crashed during the updates...i have no idea which ones

---

### Post by bodhi.zazen on 2010-09-18
> **ninavicci said:**
> i just clicked the update managericon and ran them all--there was not enough space and it crashed during the updates...i have no idea which ones

First you would need to make space for the updates by making your root partition larger or deleting unnecessary files.

Fixing a partial update is a moderately complicated task and if your system will not boot you would need to first boot a live CD , make space (gparted or delete files), then probably try to finish the update via a chroot.

You would mount your ubuntu partition in say /mnt

```
sudo -i # become root

mount /dev/sdxy /mnt # change "sdxy" to your ubuntu root partition, ? sda1

chroot /mnt /bin/bash

apt-get update
apt-get dist-upgrade
```

Post any errors or reboot to hard drive after running those commands.

---

### Post by ninavicci on 2010-09-18
i started typing that code into the terminal (are you supposed to hit enter after every line?) and after i typed in the chroot line
# chroot /mnt /bin/bash
it said
cannot run command/bin/bash no such file or directory

---

### Post by bodhi.zazen on 2010-09-18
> **ninavicci said:**
> i started typing that code into the terminal (are you supposed to hit enter after every line?) and after i typed in the chroot line
# chroot /mnt /bin/bash
it said
cannot run command/bin/bash no such file or directory

Did you mount the correct partition ?

check with 

```
ls /mnt
```

---

