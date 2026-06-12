---
title: "Grub not installing"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-06-18
Hi,
 I m using ubuntu 8.10 for a while.I have XP too.Recently i formatted XP and reinstalled it.To recover my ubuntu i tried to install grub using ubuntu 9.04 live CD.
But my output is like this

> grub> find /boot/grub/stage1
 (hd0,6)
grub> setup (hd0,6)
Error 12: Invalid device requested

I don't know why grub is not installing.I configured and using ubuntu 8.10 for a long time  and am really need it.
           Pls help me to get rid of it.
                     Thank you.
                        cheers,
                                             Balachandar.K.M

---

### Post by louieb on 2009-06-18
should work at the grub> prompt
```
[COLOR=Red]root (hd0,6)[/COLOR]
setup (hd0)
```
[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by balachandarlinks on 2009-06-25
thank you..it works...I missed to set the root.

---

