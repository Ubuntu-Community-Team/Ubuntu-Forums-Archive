---
title: "Wireless internet not working"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by brianomarr on 2011-05-28
I have an HP Pavilion dv5 and I installed Ubuntu today. Everything is great except the wifi internet is not working. My modem in my pc is Agere Systems HDA modem.

Please help me

---

### Post by terrykiwi83 on 2011-05-28
can you see the wireless networks available? or is your device not even installed?

---

### Post by gandaran on 2011-05-29
> **brianomarr said:**
> I have an HP Pavilion dv5 and I installed Ubuntu today. Everything is great except the wifi internet is not working. My modem in my pc is Agere Systems HDA modem.

Please help me
isn't that Agere Systems HDA a dial-up modem? 
post the output typing in terminal
```
lspci
```
and
```
lsusb
```
so we can check which wireless chip the computer has.

---

