---
title: "Removing usplash"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by obscur156 on 2009-02-20
Hi,i want to know if removing usplash would give me better boot speed?

And if i will be able to see whats happening whyle its booting?

---

### Post by oldos2er on 2009-02-20
Remove the words "quiet splash" from a kernel entry in /boot/grub/menu.lst. I don't think it changes boot time very much though.

---

### Post by obscur156 on 2009-02-20
Thanks for the info oldos2er,i will try that. ;)

---

### Post by mcduck on 2009-02-20
Actually you only need to remove the "splash". Removing "quiet" just results in a more verbose output during the boot, or displaying the boot messages together with the splash if you remove "quiet" but leave "splash".

quiet + splash -> graphical boot
splash -> graphical boot with boot text
quiet -> boot text
- -> verbose boot text

Anyway, on my computer the difference is about one second. Is it worth it, that's up to you to decide. :)

---

### Post by obscur156 on 2009-02-20
Hey thanks Mcduck for your pretty detailled information.
Thanks again,regards. ;)

---

