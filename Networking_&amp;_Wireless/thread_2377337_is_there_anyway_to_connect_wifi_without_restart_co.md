---
title: "is there anyway to connect wifi without restart computer?"
date: 2017-11-12
forum: Networking &amp; Wireless
---

### Post by wanggaoteng on 2017-11-12
Hi, there is a problem troubled me many times these days. My computer connect the internet through my home wifi, and i'm sure that the wifi signal is very stable. And I had set lcp-echo-failure=60.

Sometimes, after start the computer, i found that ubuntu(16.04 lts, the only one OS in my computer) cannot connect the internet. The wifi icon located in the top-right corner shows that there is no wifi connected. But my phone can connect the wifi and explore the internet.
Then i restart the computer, and it connects wifi correctly.

Also sometimes, i can explore the internet, and the wifi icon shows that the computer has connect wifi, but after a while, the web cannot be opened(the web shows that there is no network, but the wifi icon in the top-right corner shows correctly). My phone can also connect the internet.
Then i restart the computer, and it connects wifi correctly again.

Othertimes, the computer works very well.

I searched the answers in the web,and find one answer: [FONT=arial]sudo /etc/init.d/networking restart, but it doesn't work. Some answers are very complex, they are beyond my understanding and hard to operate.
[/FONT]
Is there any other ways to solve the problem without restart computer?

P.S. my computer installed with windows 7 before, and the problem never occured when the OS is win7, so i'm sure the hardwares are ok.

Best regards.

---

### Post by HermanAB on 2017-11-12
Yes, of course.

The easiest way is to click the network management widget and turn WiFi off, wait a few seconds for the dust to settle, then turn it on again.

---

### Post by wanggaoteng on 2017-11-13
> **HermanAB said:**
> Yes, of course.

The easiest way is to click the network management widget and turn WiFi off, wait a few seconds for the dust to settle, then turn it on again.

Hi, HermanAB, thank you for replying. I will try it when the wifi drops.
Best regards.

---

### Post by jeremy31 on 2017-11-13
*Thread moved to **Networking & Wireless**.*

---

### Post by wanggaoteng on 2017-11-14
> **HermanAB said:**
> Yes, of course.

The easiest way is to click the network management widget and turn WiFi off, wait a few seconds for the dust to settle, then turn it on again.

Hi, HermanAB
These days, the wifi drops sometimes after my computer restart, i use you direction, and the wifi linked again.
And I search the web, and find that

sudo /etc/init.d/network-manager restart[FONT=Calibri, serif][/FONT]
[FONT=Calibri, serif][/FONT][FONT=Calibri, serif]
[/FONT]can also works.

Thank you.

---

