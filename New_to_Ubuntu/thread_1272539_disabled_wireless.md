---
title: "disabled wireless"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by ganches on 2009-09-22
ive been running juanty for a while on my gateway laptop with no problems until i logged in on campus, and now i cannot log in at home. i followed the help center instructions and got stuck after finding my ethernet disabled, but NetworkManager shows networking and wireless enabled. 
82573L Gigabit Ethernet Controller
PRO/Wireless 3945ABG [Golan] Network connection 
anything helps 
thanks

---

### Post by mikeyphi on 2009-09-22
I lost my wireless card following a recent Hardy update. I rebooted into a previous kernel and all's well!

Try it - on the Grub screen - select an older kernel for boot.

---

### Post by ganches on 2009-09-22
i tried booting in two previous kernels, but sudo lshw -c network still shows network disabled at ethernet interface

---

