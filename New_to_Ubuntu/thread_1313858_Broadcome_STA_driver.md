---
title: "Broadcome STA driver"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by tesko on 2009-11-04
hey total newbie here.  have lenovo s10 and downloaded latest ubuntu remix for netbooks I beleive koala based.  The live flash works great.  hardware upgrade finds broadcom sta drive and then updates it and i get wireless.  I installed now Ubuntu remix on the laptop and the hardware upgrade finds STA drive but will not activate it for some reason.  I keep pressing activate and add my password but it does not activate it.  i am not sre what else to try.  I really like it based on live usb flash experience but without wirelles it is not possible to use it.

---

### Post by dvlchd3 on 2009-11-04
Try bringing up a terminal and typing:

```

sudo apt-get update && sudo apt-get install b43-fwcutter

```

---

