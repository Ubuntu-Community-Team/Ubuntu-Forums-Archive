---
title: "Intel Centrino 2230 on Ubuntu 14.04, password not working?"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by robert157 on 2015-02-05
So, I decided to try out Ubuntu for the first time as a dual-boot on my laptop, and I can't get my wifi to work.  When it goes to connect, it tries for a minute, then asks me for my password again.  I know for sure the password is correct, I have checked it many many times, checked for an extra space at the beginning/end, etc.  I can connect fine when on Windows on the same laptop, so it has to be an issue with the driver of some sort.  However, the driver seems to be correct, and I've tried all the troubleshooting tips I can find.  Any tips?

---

### Post by ajgreeny on 2015-02-05
Show us the output in terminal of command ```
lspci -nnk | grep -iA2 net
```

---

### Post by danbebber on 2015-03-29
The Intel Centrino 2230 is a card with a lot of problems, see this thread [https://communities.intel.com/thread/38676](https://communities.intel.com/thread/38676)

I had terrible problems with wifi using this card in my Dell Inspiron 17SE, until I read that if Bluetooth is disabled the card will work. I tried that and now wifi is stable and fast.

---

