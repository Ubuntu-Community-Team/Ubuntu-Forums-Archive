---
title: "Mobile broadband not working"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by warnainv on 2013-12-18
I'm a new to linux. I have installed ubuntu 12.10 in my laptop. my dongle worked fine for that version. Then I upgraded the os to Ubuntu 13.04 and then I can't connect to internet using my dongle. please help me solve this issue. thanks.

---

### Post by varunendra on 2013-12-20
Welcome to the forums warnainv !

Please open a terminal (Ctrl-Alt-T), remove the USB dongle, wait about 20 seconds, replug it, and in the terminal, run the following commands -
```
lsusb
dmesg | tail -20
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

