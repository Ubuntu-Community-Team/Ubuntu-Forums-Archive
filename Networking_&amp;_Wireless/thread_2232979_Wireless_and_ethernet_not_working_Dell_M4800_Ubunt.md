---
title: "Wireless and ethernet not working Dell M4800 Ubuntu 14.04"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by Pha4drus on 2014-07-05
I just installed 14.04 on my new Dell M4800. During the install as well as after, I get no networking whatsoever. Under windows I get the following hardware info:

- Dell Wireless 1550 802.11ac
- Intel Ethernet I217-LM

During install, if I connect an ethernet cable to the router, for a few seconds the installer will say there is a connection to the internet. Then it disconnects and won't connect anymore. 

Kali Linux is able to connect through ethernet, but wifi also not working.

So far I've only used Ubuntu server on commandline and with older, well supported hardware and ethernet. Any pointers where to start would be greatly appreciated. I'm also considering buying a wifi usb-dongle with out-of-the-box support on Ubuntu and would love to hear suggestions for the best dongle.

Thanks for your time!

---

### Post by varunendra on 2014-07-06
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Pha4drus on 2014-07-06
Hi thanks for helping out!

I allready fixed wireless before reading your reply: kind of cheated... I reinstalled Ubuntu with a TP link wireless USB dongle inserted. The TP-link worked out of the box and allowed ubuntu to download drivers for the Dell wireless card. So I'm all set now.

---

### Post by varunendra on 2014-07-06
Nice 'cheating', keep it up! :p

---

