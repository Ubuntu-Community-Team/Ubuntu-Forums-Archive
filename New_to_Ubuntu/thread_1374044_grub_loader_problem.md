---
title: "grub loader problem"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by mega farkwad on 2010-01-06
I installed Ubuntu netbook remix and Grub loader shows>

Ububtu, Linux
memory test
memory test serial console
windows xp home
windows nt/2000/xp  

when i select windows xp home from the list it then asks me again to select an os

windows xp home
Ubuntu netbook remix

selecting xp home works but why is netbook remix still showing up? any way to stop this from happening?

---

### Post by stoogiebuncho on 2010-01-06
Are you sure it's grub that's asking you to chose between XP and UNR?  

What might be happening is that you have two bootloaders set up.  Grub, and Windows.  So when you select windows, it loads the windows bootloader, which in turn asks you if you want to load windows or Ubuntu.

If this is what's going on, the solution would be to modify your windows bootloader and remove the Ubuntu option.  You don't need it, since it's already in grub.

---

### Post by mega farkwad on 2010-01-06
AH your right, thanks..... (fixed) removed Ubuntu option in Boot.ini

---

