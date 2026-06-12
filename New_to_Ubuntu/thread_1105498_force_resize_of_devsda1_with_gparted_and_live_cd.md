---
title: "force resize of /dev/sda1 with gparted and live cd"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by LTFC2020 on 2009-03-24
Hi
I have been dual booting with ubuntu 8.04 and mint and I would like to reduce the size of the mint partition and increase the size of the ubuntu partition
I sucessfully reduced the size of the mint partition using gparted and the live cd, however when I then right click on the ubuntu partition (in an attempt to use the unallocated space left by reducing the mint partition) the resize/ move option on the menu is greyed out.
How do I force this to appear so I can use the unallocated space for ubuntu?
Thanks in advance

---

### Post by bodhi.zazen on 2009-03-24
The free space must be adjacent to your ubuntu partition.

You must also do this in two steps downsize -> apply changes - upsize -> apply changes.

The other problem may be that you are using an extended partition. In that case increase the size of the extended partition then add to Ubuntu.

The last potential problem may be that the live  Cd mounted your swap partition. Hard to know really ;)

Screenshot of gparted might help.

---

### Post by LTFC2020 on 2009-03-24
I have included a screenshot of gparted showing the unallocated section that I wish ti incorporate in the /dev/sda1 ubuntu partition

---

### Post by bodhi.zazen on 2009-03-24
First you will need to unmount the swap

You can do this from gparted or the command line

```
sudo swapoff /dev/sda5
```You then need to resize (downsize) the extended partition (/dev/sda2).

You then apply changes

You will then be able to upsize.

---

### Post by LTFC2020 on 2009-03-24
it says command not found in the terminal when I paste that command in
how can I do it through gparted?

---

### Post by bodhi.zazen on 2009-03-25
me bad, you need a space in there , I fixed it.

---

### Post by LTFC2020 on 2009-03-25
sorry, I`m a bit confused.  A space in where?

---

### Post by bodhi.zazen on 2009-03-25
between the word swapoff and /dev/sda5

sudo swapoff /dev/sda5

---

### Post by LTFC2020 on 2009-03-26
ok thanks I`ll try that later (computer is at work now)

---

### Post by LTFC2020 on 2009-03-26
invalid arguement now apparently

richard@richard-laptop:~$ sudo swapoff /dev/sda5
swapoff: /dev/sda5: Invalid argument
richard@richard-laptop:~$

---

