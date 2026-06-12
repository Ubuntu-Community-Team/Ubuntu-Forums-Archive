---
title: "Wifi disabled in ACER Aspire 4745g laptop"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by bobby6 on 2013-09-09
Hello guys, im new in Ubuntu.. liked the OS. Its pretty cool just starting my surfing in my New OS. Cant connect to wifi. It said wifi disabled. Kinda new in this one so pls can u help.. If theres a need for drivers or anything.. can u please advice and if possible attached some links were to downloads such..


Thanks in advance..

Bobby

---

### Post by varunendra on 2013-09-10
Welcome to the Ubuntu Forums Bobby ! :)

Please open a terminal (Ctrl+Alt+T) and post the outputs of following commands so we can see some basic information :
```
lspci -nnk | grep -iA2 net
rfkill list all
```
You can copy-paste the above in terminal to avoid typos.

While posting the outputs, please wrap them in 'Code' tags to preserve the formatting. Follow the "Using Code tags" link in my signature below to see how. :)

---

