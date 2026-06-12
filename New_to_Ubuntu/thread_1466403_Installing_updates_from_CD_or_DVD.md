---
title: "Installing updates from CD or DVD"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Lewis Wilson on 2010-04-30
After Ubuntu OS. was installed I tried to install the update CD which I bought together with Ubuntu. Well the DVD drive keeps on un-mounting its self so after about 8 shots at this and several phone calls I am still failing to complete this task. Could you please tell me what error I'm making. The rest of Ubuntu appears to run very well in fact I should have dumped Microsoft sooner.

---

### Post by Jon Monreal on 2010-04-30
Do you still have Windows installed? If so, the first thing I would try would be to get the latest firmware for the CD/DVD drive and install it (which usually has to be done in Windows unfortunately). You can usually find this at the OEM's (such as Dell) website.

If they don't have newer firmware there, feel free to go to Applications>Accessories>Terminal, type
```
sudo lshw | grep DVD
```
press enter, enter your password, and post the output here.

If you don't have Windows installed, please say so and we can try something else.

---

