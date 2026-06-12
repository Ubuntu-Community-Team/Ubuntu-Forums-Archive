---
title: "data through rs232"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by aritrakundu on 2008-04-02
I am using UBUNTU.I am having a problem of sending text files through rs232 from one terminal to another.
I am using USB-Serial adapters for transferring data as I have no serial ports. So when I plug the adapters on one terminal it appears as ls /dev/ttyUSB0 and on the other terminal it appears as ls /dev/ttyUSB1. So to sent a text file I typed the following in the first terminal:
#to set the baud rate:
stty 9600 cs8 -istrip -parenb < /dev/ttyUSB1
cat filename.txt > dev/ttyUSB1

But no data is being transferred. Please help me.

---

