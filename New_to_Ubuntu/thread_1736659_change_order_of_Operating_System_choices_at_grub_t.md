---
title: "change order of Operating System choices at grub terminal"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by audit on 2011-04-22
I want to change the order that the OS are listed at my grub terminal how do I do this?

---

### Post by ohadcn on 2011-04-22
enter /etc/grub.d and rename the files as you want to order the os'es on your machine.
each file represent one kind of OS, and they are ordered by the numbers before the file name, (windows is in os_prober file).
for those changes to take affect you need to run grub-mkconfig command as root.

for example, if I want the order memtest / Linux / windows, i will change the names to 10_memtest, 20_linux_proxy, 30_os_prober.

---

