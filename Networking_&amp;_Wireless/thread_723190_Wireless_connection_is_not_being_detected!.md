---
title: "Wireless connection is not being detected!"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by yehudah2002 on 2008-03-13
Hi everybody,
I have a problem with Xubuntu (7.10) regarding wireless networking:
The wireless card / antana is in the computer, but there is no detection of it. Not in the "lspci" command, nor in the network manager.
Also, there is no "restricted drivers" displying on the "restricted drivers managers".

I have no idea what I should do, because it worked just fine on the Win98.
Please help me! :(

Sincerely,
yehudah2002

"cuz u can't beat da best..."
:popcorn:

---

### Post by rklauco on 2008-03-13
Well, if the **lspci** output will be attached, it should help...
Try to execute 
```
lspci -v > /tmp/lspci.output.txt
dmesg > /tmp/dmesg.output.txt
```
and upload the files from /tmp direcotry.
What type of card is it? (maker/model...).

---

### Post by yehudah2002 on 2008-03-13
What do you mean "what type of card is this"? how should I know? or yet again: how CAN I know?

---

### Post by rklauco on 2008-03-13
Well, I assume you bought the card :-)
If not, the dmesg and lspci I recommended above should help to point us to the right direction...

---

