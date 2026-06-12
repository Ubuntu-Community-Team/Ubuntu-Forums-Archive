---
title: "Removing boot options and their disk space contents"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Jaraqui on 2010-07-16
Hi guys,

   The following options are available in my bootime:
   1) Ubuntu, with Linux 2.6.32-23-generic <-- DEFAULT OPTION
   2) Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
   3) Ubuntu, with Linux 2.6.32-22-generic
   4) Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
   5) Ubuntu, with Linux 2.6.32-21-generic
   6) Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
   7) Memory test (memtest 86+)
   8) Memory test (memtest 86+, serial console 115200)
   9) Linux (on /dev/sda2)
  10) HD recovery (on /dev/sda2)
  11) Linux (on /dev/sda3)
  12) HD recovery (on /dev/sda3)

   I need to:
   a) remove options (3) to (6) and the disk space
      content associated with them;
   b) remove options (9) to (12) and the disk space
      content associated with them.

   How can I do?

Regards
Jaraqui

---

### Post by linux18 on 2010-07-16
for options 3 - 6 those are the old kernels that came with ubuntu or an update and another update superseded them. in other words, the newer options are from updates to newer better ( usually ) kernels. they aren't removed automatically because if something stops working in a new kernel you can just go back to the old one. if everything is working fine right now you can remove the kernel images through synaptic, just search for "kernel image" and ONLY delete the ones you don't want  ( always keep the kernel with the biggest number thats the new one ) then sudo grub-update to remove the options from the list.

as for the other options just erase the partition in gparted and sudo grub-update to remove the items from the list. 

to claim all of the disk space from the other partitions you need to use a live cd and resize the ubuntu partition to fill all of the empty space.

good luck!

---

### Post by noidian on 2010-07-16
If your using the new grub2 (i.e. you installed ubunutu Lucid Lynx 10.04) then you can edit /boot/grub/grub.cfg 
otherwise older versions:

edit /boot/grub/menu.lst

Use this site:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

To resize the and remove you can resize as mentioned above and gparted. It is preferable to keep atleast one extra version unless your running a bare minimum version.

---

### Post by linux18 on 2010-07-16
> **noidian said:**
> If your using the new grub2 (i.e. you installed ubunutu Lucid Lynx 10.04) then you can edit /boot/grub/grub.cfg 
otherwise older versions:

edit /boot/grub/menu.lst

Use this site:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
editing grub.cfg doesn't free up the disk space

---

### Post by egalvan on 2010-07-16
> **linux18 said:**
> editing grub.cfg doesn't free up the disk space

And editing grub.dfg is not recommended.

Either edit the proper grub file and update grub,
or see if StartUpManager has matured to the point that it will perform this function under GRUB2 (it worked for GRUB Legacy)

---

### Post by Jaraqui on 2010-07-16
Thanks a lot, guys.

I will mark the topic as [SOLVED], learn and try the 
top recommendations.

Best regards
Jaraqui

---

### Post by drs305 on 2010-07-16
A really easy way to remove older kernels (and eliminate them from the menu as well) is via the GUI app Ubuntu Tweak. Scroll to the "Removing Older Kernels" section of this post for more details on removing these kernels:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by cariboo on 2010-07-16
You can use synaptic to remove old kernels, do a search for linux-image, and select Mark for complete removal.

---

### Post by egalvan on 2010-07-17
> **drs305 said:**
> A really easy way to remove older kernels (and eliminate them from the menu as well) is via the GUI app **Ubuntu Twea**k. 

Man, I had TOTALLY forgotten about Tweak!

Yes, it works wonders.

Absolutely +1

---

