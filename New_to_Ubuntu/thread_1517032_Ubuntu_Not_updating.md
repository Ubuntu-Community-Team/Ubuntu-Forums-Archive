---
title: "Ubuntu Not updating"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by mmgraves on 2010-06-24
This is on a HP Mini 1000. Ubuntu 10.04 for Netbook. When trying to update it just says "A problem occurred when checking for the updates." I can't get into and run the following programs: Update manager, Synaptics Package manager, Software Sources, Ubuntu  Software Center...basically nothing in the system folder works. Any ideas?

---

### Post by philinux on 2010-06-24
> **mmgraves said:**
> This is on a HP Mini 1000. Ubuntu 10.04 for Netbook. When trying to update it just says "A problem occurred when checking for the updates." I can't get into and run the following programs: Update manager, Synaptics Package manager, Software Sources, Ubuntu  Software Center...basically nothing in the system folder works. Any ideas?

Yes, open a terminal, apps>accesories and use these two commands one at a time. Post back all error messages.

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

---

### Post by mmgraves on 2010-06-24
It gets to reading package list and sits at 0% and then it goes back to the terminal and says this:

Bus errorackage Lists

For both update and upgrade

---

### Post by philinux on 2010-06-24
> **mmgraves said:**
> It gets to reading package list and sits at 0% and then it goes back to the terminal and says this:

Bus errorackage Lists

For both update and upgrade

Not seen that error before. However. [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/63850](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/63850)

See comment #2. There are two .bin files it recommends removing.

---

### Post by mmgraves on 2010-06-24
I got to the two bin files, but I can't delete them.  How to I get privileges to move them to trash?

---

### Post by mikewhatever on 2010-06-24
To move the files to trash:
sudo mv /var/cache/apt/*.bin ~/$USER/.local/share/Trash

to delete them
sudo rm /var/cache/apt/*.bin

---

### Post by mmgraves on 2010-06-24
This is what it says now:

E:Unable to write mmap - msync (5: Input/output error), E:The package lists or  status file could not be parsed or opened.

[INDENT]This is a serious problem. Try again later. If this  problem appears again, please report an error to the developers.[/INDENT]

---

### Post by sandyd on 2010-06-24
> **mmgraves said:**
> This is what it says now:

E:Unable to write mmap - msync (5: Input/output error), E:The package lists or  status file could not be parsed or opened.[INDENT]This is a serious problem. Try again later. If this  problem appears again, please report an error to the developers.[/INDENT]
This is a problem due to msync not synchronizing the apt caches and packagelists properly. This is a sign of disk problems.
to run a disk check, first boot up with a livecd.
then run```

sudo fdisk -l
```Identify your linux partition from them. (should be something similar to /dev/sda1)
then run
```

sudo fsck -y -f -v /dev/sda1

```while replacing /dev/sda1 with your linux partition

---

