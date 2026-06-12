---
title: "Asus Netbook : Enabling wireless reboots laptop"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by marky2 on 2014-05-24
my wireless connection on my asus netbook i think its broken...coz if i enable wireless connection it will restart my lappy and i cant use it...how can i fix it???please help

---

### Post by bapoumba on 2014-05-24
Post moved to its own thread.

---

### Post by varunendra on 2014-05-25
Hello marky2, Welcome to the forums!

Please open a terminal (Ctrl-Alt-T), run the following commands in it, and post back their results here -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

