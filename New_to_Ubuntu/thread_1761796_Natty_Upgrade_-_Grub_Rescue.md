---
title: "Natty Upgrade - Grub Rescue"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-18
Hi all,

Just upgraded to Natty on my main Desktop PC. During the upgrade, it asked where grub should be installed. I had no idea so I randomly clicked hda1. It's just finished the install and now I have a grub rescue prompt.

Here's the kicker, I have no working USB ports on this computer or CD drive, it was installed over a netboot with a friends laptop. Needless to say, my friend isn't here so I'm stuck with the normal help on the internet.

Is there any way to boot the machine? I've followed this [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode) and I get stuck at insmod /boot/grub/linux.mod as I get
```
error: symbol not found: 'grub_mm_base'.
```

Can anyone help?

---

### Post by Blasphemist on 2011-05-18
> **Chrissd said:**
> Hi all,

Just upgraded to Natty on my main Desktop PC. During the upgrade, it asked where grub should be installed. I had no idea so I randomly clicked hda1. It's just finished the install and now I have a grub rescue prompt.

Here's the kicker, I have no working USB ports on this computer or CD drive, it was installed over a netboot with a friends laptop. Needless to say, my friend isn't here so I'm stuck with the normal help on the internet.

Is there any way to boot the machine? I've followed this [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode) and I get stuck at insmod /boot/grub/linux.mod as I get
```
error: symbol not found: 'grub_mm_base'.
```

Can anyone help?
Does this command return an error?
```
insmod linux
```
What were the results of the prior steps you performed? Are you sure the prefix path and root= settings correct for sure? What are those settings?

---

### Post by Chrissd on 2011-05-18
As it happens, I have just managed to get net boot working from my netbook and virtualbox, so I've managed to reinstall. 


Appreciate the assistance!

---

