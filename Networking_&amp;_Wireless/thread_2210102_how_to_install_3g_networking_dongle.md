---
title: "how to install 3g networking dongle ?"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by charlie11 on 2014-03-09
i am using a ZTE 3g networking dongle model:K3770-Z HSPA the connection is successfully established but when i try to open a page 
there is no response 
can anyone help me with this ?

---

### Post by varunendra on 2014-03-11
Hello charlie11!

Please show us some command outputs when your modem is plugged-in.

Unplug your modem (if already plugged) > wait about 10 seconds > plug it > wait about 30 seconds > Open a terminal (Ctrl-Alt-T) and run the following commands -
```
uname -mr
lsb_release -d
lsusb
dmesg | tail -40
```
Copy the whole output using your mouse cursor, and paste here in your next post.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

