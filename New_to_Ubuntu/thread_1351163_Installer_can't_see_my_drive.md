---
title: "Installer can't see my drive"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by poisonborz on 2009-12-10
Hola,

I'm trying to install Kubuntu 9.10 from a pendrive to a 200GB hdd on a A7N8X-E motherboard. The bios sees the drive, as does the Live OS, but when I try to install, nothing is shown on the Drives panel (only a cropped yellow alert sign and no text). I've tried a low-level format, and converting the partition to ext4 with gparted, flagged as boot, everything seems to be fine, but the installer just doesn't see it. What could be the problem?

---

### Post by poisonborz on 2009-12-11
Hola,

I'm trying to install Ubuntu 9.10 from a pendrive to a 200GB hdd on a A7N8X-E motherboard. The bios sees the drive, as does Nautilus in the Live OS, but when I try to install, nothing is shown on the Drives panel. I've tried a low-level format, and converting the partition to ext4 with gparted, flagged as boot, everything seems to be fine, but the installer just doesn't see it. What could be the problem?

---

### Post by cariboo on 2009-12-11
I ran into a similar problem. What worked for me was to mount the drive, and when it came to the partitioning section, it asked  me if I wanted to unmount the drive before proceeding. I clicked yes and the drive showed up in the partitioning window. To mount a drive go to Applications-->Accessories-->Terminal, then in the terminal type:

```
sudo mount /dev/sdX /mnt
```

Substitute your device label for the one in the example above. If you aren't sure what the device label is, in the same terminal type:

```
sudo fdisk -l
```

This command will list all the drives in your computer.

---

### Post by poisonborz on 2009-12-17
I finally found the solution: anyone with an older mobo that uses a separate RAID controller (~fakeraid) should try this:

# Boot Ubuntu Karmic LiveCD as usual
# Once booted, open a terminal and type:
sudo apt-get remove dmraid
# check everything went fine with the following command, value must be zero 0
echo $?
# Double click on Install Ubuntu 9.10
# Proceed as usual Forward-> Forward->
# Hopefully your disk must be recognized now.

---

