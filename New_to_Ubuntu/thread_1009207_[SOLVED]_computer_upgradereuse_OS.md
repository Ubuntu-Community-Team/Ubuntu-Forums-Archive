---
title: "[SOLVED] computer upgrade/reuse OS"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-12-12
I just recently rebuilt my computer(cpu,mobo,ram,video card).  I was hoping to "reuse" the OS compared to loading from scratch.  I attempted to boot it, and i get a hung load screen, and it takes me to a CLI that i am not familiar with.

Thanks in advance

---

### Post by tomtom1982 on 2008-12-12
Well, during the install your system is being installed with the drivers for YOUR system with YOUR hardware.

If you want to use your installation with other hardware, you have to use a generic kernel with all drivers like on Debian Lenny(Beta).

So you have to reinstall your system. If you´ve got a separately /home-partition, you can use it without formatting and (the most) system-settings will hold up.

---

