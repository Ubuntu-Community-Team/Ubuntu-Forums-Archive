---
title: "What Is In The ISO?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by opticyclic on 2010-07-26
Is there a list of what makes up the distro and how much space it takes up in the ISO?

I did the following to mount the iso:
```
sudo apt-get install squashfs-tools
sudo mkdir /media/iso
sudo mount -o loop /home/me/Downloads/Ubuntu.iso /media/iso
sudo mkdir /media/squashfs
sudo mount -o loop -t squashfs /media/iso/casper/filesystem.squashfs /media/squashfs/

```
However, when I browse the squashfs with Nautilus, the filesizes are the uncompressed sizes.

How do people work out how much space applications take up and how can I see that?

---

