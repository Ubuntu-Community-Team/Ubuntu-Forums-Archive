---
title: "Broadcom wireless card not found"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by N4WVE on 2009-03-03
[FONT="Comic Sans MS"][COLOR="DarkRed"]I downloaded Ubuntu but can't use it as it does not see my network card.  I use a Broadcom wireless card.  How do I get this thing to work?  I set it up as a dual boot system on my vista pc and that all works fine, but I HAVE to have internet access. PLEASE HELP![/COLOR][/FONT]

---

### Post by jgoguen on 2009-03-04
Could you please open the Restricted Drivers Manager (System -> Administration -> Hardware Drivers) and see if it lists anything in there about your card?  If it does, select the driver and press the **Activate** button.  Enter your password when prompted, and Ubuntu will download the driver.

If there's nothing about your Broadcom card, could you post the output of this command so we can help you better?
```
lspci | grep Broadcom
```

Thanks in advance!

---

