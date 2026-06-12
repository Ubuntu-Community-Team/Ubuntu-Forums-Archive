---
title: "New User - Can't Setup Wireless"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by xaxtree on 2009-03-05
Hello I'm fairly new to Ubuntu and I've had this problem before but some reason I cannot connect to my router, I have an Acer Aspire 5100 laptop, and I used a live CD to install this time but wasn't downloaded from a book I had.  Sorry if I didn't search but I don't want to trial an error searchs.

---

### Post by pytheas22 on 2009-03-05
Please post the output of these commands:
```

sudo iwlist scan
lspci -nn
lsusb
uname -rm
```

---

### Post by crapple on 2009-03-05
Go to system>administration>hardware drivers.

If you see a driver for a wireless card make sure it is enabled.  You might have to have to have internet connection to download drivers.  Once they are enabled you should be able to click on the network manger in the top bar on the screen.  There should be a list of wireless networks select yours.

---

