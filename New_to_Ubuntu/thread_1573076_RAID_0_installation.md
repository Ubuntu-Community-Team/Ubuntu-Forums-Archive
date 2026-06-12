---
title: "RAID 0 installation"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by marklah on 2010-09-12
Hi,

I have been trying to install ubuntu 10.04 on a software RAID 0 configuration using the alternate installation cd. I have created two raid 0 partitions, a / and a swap. And I have also created a non raid partition for the /boot (I read it needs to be on a non raid partition??).

The installation is successful, however on reboot ubuntu doesn't load. I just get a blank screen with a flashing _. Any tips would be greatly appreciated. 

Thanks

---

### Post by sikander3786 on 2010-09-12
It is not an installation issue. Installation seems fine and successful to me. On some graphics cards, the new Ubuntu splash screen doesn't show up. It is just a flashing cursor that leads to the desktop. Wait and see, Ubuntu might be able to boot after that black screen.

Which graphics card are you using?

---

### Post by marklah on 2010-09-12
Yeah I know what you mean- I have reverted back to a non-RAID configuration for now and while I still get the flashing _, Ubuntu does boot. 

My graphics card is a Radeon X1950- it is supported by ubuntu as it works fine in a non RAID config. 

In the RAID config it seems like the boot loader can't find the ubuntu files so it never loads.

---

### Post by marklah on 2010-09-13
I can install ubuntu in a RAID 0 configuration on a virtual machine and it works fine so I am confused why I cant get it working on the actual hardware???

---

### Post by sikander3786 on 2010-09-14
> **marklah said:**
> I can install ubuntu in a RAID 0 configuration on a virtual machine and it works fine so I am confused why I cant get it working on the actual hardware???
I think it works a bit different in a Virtual Machine. It is a Virtual HDD and Virtual MBR so GRUB easily sets itself in the only HDD's MBR.

Raid configuration problems are solved by this nice how-to.

[http://ubuntuforums.org/showpost.php?p=9237139&postcount=18](http://ubuntuforums.org/showpost.php?p=9237139&postcount=18)

---

