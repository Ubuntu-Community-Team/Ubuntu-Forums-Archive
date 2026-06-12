---
title: "Can I temporarily install a different distro along ubuntu?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-26
Hello:

I blew out windows completely and have a 100% ubuntu laptop.

My questions:

1) Can I install a different linux distribution along side ubuntu and have a dual-boot?

2) If #1 is possile, can I later remove that distribution and end up with my original ubuntu completely intact with my pc booting into ubuntu?

Thank you.

Rob.

---

### Post by Vaphell on 2010-08-26
you want to check out the look and feel? virtualbox

---

### Post by afroman10496 on 2010-08-26
> **Robert.Thompson said:**
> Hello:

I blew out windows completely and have a 100% ubuntu laptop.

My questions:

1) Can I install a different linux distribution along side ubuntu and have a dual-boot?

2) If #1 is possile, can I later remove that distribution and end up with my original ubuntu completely intact with my pc booting into ubuntu?

Thank you.

Rob.

Actually, i would reccomend a live USB:

```
sudo apt-get update && sudo add-apt-repository ppa:gezakovacs/ppa && sudo apt-get install unetbootin -y
```

**PS: If you want to try out openSUSE, you have to go [here]("http://en.opensuse.org/SDB:Live_USB_stick") **

---

### Post by oldfred on 2010-08-27
This is older using grub legacy but shows some of the planning required. I think he used two drives.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

You do have to plan what boot loader you want in the MBR. If not Ubuntu's grub2 you will have to reinstall it if you uninstall the second distribution.

Do you want to share data, so you could have same firefox profile in both? Then you may want another /data partition also.

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Paqman on 2010-08-27
Sure, you can have as many different OSes on one machine as you've got room for.

To remove an installed OS, just delete it's partitions then prod the bootloader into automatically reconfiguring itself with the command:
```
sudo update-grub
```

---

### Post by Peter09 on 2010-08-27
As said before the best way to check out another distro is to use virtualbox, no partitioning or changes to grub.

---

### Post by Robert.Thompson on 2010-08-27
I opted to try virtualbox.

I installed it and then installed PCLinuxOS on it - it worked perfectly!

Each post provided me with much needed input as I 'climb the curve'!

Thanks,

Rob.

---

