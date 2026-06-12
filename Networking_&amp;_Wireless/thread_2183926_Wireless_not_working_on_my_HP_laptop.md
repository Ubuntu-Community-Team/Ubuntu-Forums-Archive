---
title: "Wireless not working on my HP laptop"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by cshillong on 2013-10-26
I just installed Ubuntu on my HP Notebook 15-e020nr which had windows 8 installed. Now I cannot connect to the internet wirelessly. I can if I use an Ethernet cable so I tired to download the drivers from HP but they only support Windows platforms. Is there a fix for this issue? Is Ubuntu doing anything so other users don't have the same problem?

---

### Post by varunendra on 2013-10-27
Welcome to the forums cshillong ! :)

> **cshillong said:**
> Is there a fix for this issue? Is Ubuntu doing anything so other users don't have the same problem?

No Ubuntu is not, and it can not do anything about it. Including support for hardware is the job of the Linux kernel development team, and with the extremely limited support they get from hardware manufacturers, they are doing their best to keep up with the ever growing variety of hardware in the market.

Now, except for some bleeding edge, "just arrived" models, there is good support for wireless. Usually, they work out-of-box. When it doesn't, you need to install the correct driver for it just like you would do in any other OS.

Please show us your card's model no. so we can see if it needs an external driver. Our preferred way to get that info is - open a terminal (Ctrl-Alt-T) and type or copy-paste the following command in it -
```
lspci -nnk | grep -iA2 net
```
Post back the output it produces in the terminal.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

