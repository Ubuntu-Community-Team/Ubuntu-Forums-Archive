---
title: "Wireless not working on Intel PRO/Wireless 3945ABG on hardy"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by MONODA on 2008-04-26
I have used feisty and Gutsy on this laptop and both have installed the driver for my wireless card out-of-the-box but hardy did not. Under restricted drivers I do not see it but if I open hardware testing, it detects my wireless card but does not install the driver. How can I fix this?

---

### Post by wilson79 on 2008-04-26
I am experiencing exactly the same problem on hardy, even the wireless led on the laptop doesn't turn on. 
A workaround to this problem is to load hardy with the 2.26.22-14 kernel instead of the 2.26.24-16 kernel. To do this use GRUB at boot (by pressing Esc if it doesn't show automatically).

If anyone has a real solution please post it!!
wilson

---

### Post by abhiroopb on 2008-04-26
Experienced the same problem on an upgrade from Gutsy. Everything seemed ok, except problems with nvidia (whcih I am trying to sort out). And no wireless connection. I am using the older kernel, but a solution is in order.

Thanks!

---

