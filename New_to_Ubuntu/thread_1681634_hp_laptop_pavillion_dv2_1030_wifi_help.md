---
title: "hp laptop pavillion dv2 1030 wifi help"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by slixz85 on 2011-02-04
hi i have run into this issue before with a dell and was able to find the wifi driver easily without having to hook up a ethernet cord. now i dont have an ethernet cord but can get on wifi with second laptop had same problem with it having to get wifi drivers. it is a dell inspiron mini 10 and i used the bcmwl-kernel-source and dependencies

now needing to get the dv2 online without a wired connection. has anyone known of the wifi fix for these machines. i cannot find it

here is the full specs on the dv2 [http://www9.dealtime.com/Hewlett-Packard-HP-Pavilion-Dv2-1030-Us-Entertainment-Notebook-PC-Espresso/prices](http://www9.dealtime.com/Hewlett-Packard-HP-Pavilion-Dv2-1030-Us-Entertainment-Notebook-PC-Espresso/prices)

---

### Post by TechWiz2100 on 2011-02-04
link is useless

use this and post results
```

lspci

```

---

### Post by slixz85 on 2011-02-04
cant copy and paste all of it from other laptop but im sure all the info u need that came from that is.

02:00.0 network controller: broadcom corporation bcm4322 802.11a/b/g/n/ wireless lan controller (rev 01)
08:00.0 ethernet controller: realtek semiconductor co. rtl8101e/rtl8102e pci express fast ethernet controller (rev 02)

dont know why posted ethernet lol

but there it is thanks

---

### Post by TechWiz2100 on 2011-02-05
Try this first: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

and if that dun work use this: [http://ubuntuforums.org/showthread.php?p=5636495]("http://ubuntuforums.org/showthread.php?p=5636495")

---

