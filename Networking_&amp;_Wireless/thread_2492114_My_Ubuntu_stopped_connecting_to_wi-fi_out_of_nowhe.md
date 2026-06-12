---
title: "My Ubuntu stopped connecting to wi-fi out of nowhere, but wi-fi works on windows"
date: 2023-10-31
forum: Networking &amp; Wireless
---

### Post by joananoites on 2023-10-31
[COLOR=#0C0D0E][FONT=-apple-system]Hello! I've been using ubuntu for a little less than a year and everything was ok until out of nowhere I turn my pc on in the morning and ubuntu doesn´t connect to my wi-fi, I also tried to connect to my phone's hotspot and it also didn't work. This is what shows up when I run the lshw -C network command (excuse the quality):

[https://i.stack.imgur.com/pzwt2.jpg](https://i.stack.imgur.com/pzwt2.jpg)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]For context, I am using a dual boot with windows and the connection on windows is just fine and my ubuntu version is 22.04, I tried to fix this with following this tutorial ([https://www.youtube.com/watch?v=Rc7lZV_xvTU](https://www.youtube.com/watch?v=Rc7lZV_xvTU)) but it didn't work, can anyone please help me? Thank you in advance.

[/FONT][/COLOR]Edit: I solved the  problem by inserting my USB that had the ubuntu downloading software  burned into it and choose try ubuntu and it connected to wi-fi, when i  disconnected the USB and went back to my actual ubuntu on my pc it was  connecting lol

---

### Post by jeremy31 on 2023-10-31
Any results from terminal for ```
sudo dmesg|grep mt7921
```

---

### Post by joananoites on 2023-11-01
i solved it but tysm for answering :D

---

### Post by jeremy31 on 2023-11-02
Did Windows hybrid shutdown/fast startup cause it?

---

