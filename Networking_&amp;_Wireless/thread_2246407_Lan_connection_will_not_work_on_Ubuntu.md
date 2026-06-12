---
title: "Lan connection will not work on Ubuntu"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by maxim14 on 2014-09-30
Hello everyone,
I am new to ubuntu, I'm running ubuntu 14.04, I am not dual booting and my lan card is enabled from bios, i even connected another one "TP-Link TF-3239DL" but ubuntu will still won't recognize either of them, so I am really confused, if anyone has any ideas how to test stuff I would do it as soon as possible and repost results, and if someone has the time can they walk me through this, am really desperate because of this... I don't know what to do next
thank you in advance for your time.

---

### Post by varunendra on 2014-10-01
Hello maxim14, Welcome to the forums!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
sudo lshw -C network
sudo ethtool eth0
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

