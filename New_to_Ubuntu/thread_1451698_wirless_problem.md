---
title: "wirless problem"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by pgrady on 2010-04-10
im trying to setup a wireless connection, i just installed ubuntu and its not detecting any wireless connections. the wireless network i am trying to connect to is a password procted network that uses cybergatekeeper idk what im doin any advice would help

---

### Post by fremantle on 2010-04-10
this page might help you
[http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")

---

### Post by fremantle on 2010-04-10
Wait, do u hav a broadcom wir. card?

---

### Post by 2hot6ft2 on 2010-04-10
> **fremantle said:**
> this page might help you
[http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")
Did I miss where the OP said what their wireless adapter is? Pulls out last few hairs!!!

It would be more help to know what wifi adapter you have.
Open a terminal
Applications > Accessories > Terminal
and run

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

By the way welcome to the forum.

---

### Post by pgrady on 2010-04-11
its a pain in the *** to do everything ppl are suggesting and stuff since i have one computer at the moment and have to switch between vista and ubuntu everytime i wanna try something to fixit, im gonna get an ethernet cable today and then ill try to fix the wirless problem. i have a feeling its the wireless driver since im not getting any wireless connections at all, when theres about 15 or so wireless connections that i can receive on vista

---

