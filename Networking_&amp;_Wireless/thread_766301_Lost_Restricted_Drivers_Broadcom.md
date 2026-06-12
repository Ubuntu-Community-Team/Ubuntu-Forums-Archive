---
title: "Lost Restricted Drivers Broadcom"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by chembro84 on 2008-04-25
Hello all.  I recently installed Hardy, my laptop is an HP dv6000.  Everything installed great and then I enabled the restricted drivers so that I could use my broadcom wireless card.  Well the card worked after that but there were no SSIDs listed in the wireless manager.  So I tried looking around and doing some stuff with NDISwrapper manually.  Well now the card does not show up at all in the network manager nor is it listed in the restricted drivers manager any longer.  Does anyone have any idea how to get the card to show up in the network manager/restricted drivers area?  Thanks!

---

### Post by chefhossein@verizon.net on 2008-04-27
I have the same machine HPdv6000 i have the same problem. there are so many different solution, but i can not get them to work. let me know if you have any ideas. 
thanks alot.

Hoss:mad:

---

### Post by kevdog on 2008-04-27
Please do the following:

lshw -C network
lspci -nn
lsmod

Thanks, then we can recover and start afresh

---

