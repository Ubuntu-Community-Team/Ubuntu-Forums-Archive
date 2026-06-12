---
title: "USB stopped working in Virtualbox"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Charlie Chick on 2010-01-16
Hello Everybody,

My USB has stopped working in Virtualbox 3.1.2. I had this problem when I first installed Virtualbox and followed the advice given on this very forum again, but without success. When I add usbuser to the groups, it doesn't remember. If I close and re-open the groups it has gone. I'm running a fresh install of 9.10. 

Can anybody help, please?

Many thanks,

Charlie

---

### Post by Darce on 2010-01-16
You want to add yourself (tick) to the Vboxusers group.

---

### Post by Charlie Chick on 2010-01-16
> **Darce said:**
> You want to add yourself (tick) to the Vboxusers group.

Done that - unfortunately it made no difference!

---

### Post by Concrete on 2010-01-16
Did you add your USB device to VirtualBox in Options for that system you try to use via VB?

---

### Post by Charlie Chick on 2010-01-16
> **Concrete said:**
> Did you add your USB device to VirtualBox in Options for that system you try to use via VB?

Yes, I have both enabled the USB controllers and added each USB device.

---

### Post by byStanderone on 2010-01-16
...take a look at this: [http://ubuntuforums.org/showthread.php?t=504328](http://ubuntuforums.org/showthread.php?t=504328)

---

### Post by Darce on 2010-01-16
I had to reboot my system ( real, not virtual ) before it took effect !

---

### Post by Charlie Chick on 2010-01-16
Thank you all, it appears that the problem was that I had not added myself to the vboxusers group and done a full re-boot of the entire computer afterwards.

Thank you all very much for your help.

Charlie.

---

