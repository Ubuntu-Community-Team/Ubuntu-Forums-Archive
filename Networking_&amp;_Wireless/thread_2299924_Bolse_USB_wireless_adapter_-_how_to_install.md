---
title: "Bolse USB wireless adapter - how to install"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by RobertSt on 2015-10-22
Hello,

I have been using someone else computer with Ubuntu on it, and always loved it. Now I don't have access anymore and want go get it on my own computer which I just bought used.

I was able to install everything (dual boot for right now) and saw the comments about changing the boot order, thank you all. the only issue was that I selected to install version 15.10 but it downloaded and installed 14.04. No big deal.

My question is: How do I install the driver for a wireless USB adapter? ([http://mybolse.com/product/detail_B00EZV8ZJI.html](http://mybolse.com/product/detail_B00EZV8ZJI.html))

Right after installation the wireless worked, but intermittent. My regular wifi network (home) is declared as 'being out of range' and I am connected to a local hotspot.

The manufacturer has a linux driver, but I have no idea how to install it. Anybody out there who would give me a detailed guide on how to do it?

Thank you.

---

### Post by Bucky Ball on 2015-10-22
Welcome. First up, open a terminal and, with the wireless dongle plugged in, paste in this command and hit return:

```
sudo lshw -C network
```

Post the output of that back here between code tags, please (see the last link in my signature).

---

