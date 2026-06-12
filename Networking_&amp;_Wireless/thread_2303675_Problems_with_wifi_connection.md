---
title: "Problems with wifi connection"
date: 2015-11-20
forum: Networking &amp; Wireless
---

### Post by amel4 on 2015-11-20
Hi all, I am new to Ubuntu and this forum and I hope I am posting this on the right place. I Installed Ubuntu 14.04 and when I start Ubuntu i can go online through wifi connection for about 5 minutes and then it crashes but the icon for connection at the upper right corner is showing that it is still connected. If I disconnect it goes in to the loop, trying to connect over and over. I can connect on this wifi network on windows and my phone so I am guessing the connection is not the problem, what can I do to solve this? Thanks in advance!

---

### Post by QIII on 2015-11-20
*Moved to** Networking & Wireless***

---

### Post by tgalati4 on 2015-11-20
Welcome to the forums.  There are some wireless cards with known, disconnection issues.  What card do you have?

Open a terminal:

```
lspci | grep Network
```

---

### Post by amel4 on 2015-11-20
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter - that is the output of [COLOR=#000000][FONT=Ubuntu Mono]lspci | grep Network[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-11-20
Some reading:

[http://www.dedoimedo.com/computers/ubuntu-trusty-realtek.html](http://www.dedoimedo.com/computers/ubuntu-trusty-realtek.html)

[http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04)

[http://unix.stackexchange.com/questions/170012/rtl8723be-realtek-wifi-card-driver-not-working-on-ubuntu-14-04](http://unix.stackexchange.com/questions/170012/rtl8723be-realtek-wifi-card-driver-not-working-on-ubuntu-14-04)

Pick a solution and then work through the steps and report back.  Take notes and document what changes you made.

---

### Post by amel4 on 2015-11-20
it seems that the solution from the second link you provided solved the problem, thank you very much!

---

### Post by tgalati4 on 2015-11-20
You are quite welcome.  I didn't know exactly what to recommend, since there were quite a few solutions suggested when I did a web search. And I didn't have that wireless card to test, so you were on your own.  That is the beauty of Linux.  It's your problem.  Own it.  Fix it.

Make a list of annoyances and over time, you will find ways to fix or ignore each one of them.  Enjoy your journey.

You can mark this thread as SOLVED, using the thead tools just above the first post.

---

