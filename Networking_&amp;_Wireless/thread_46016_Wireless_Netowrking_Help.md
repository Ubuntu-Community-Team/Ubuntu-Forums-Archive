---
title: "Wireless Netowrking Help"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by Andre N. on 2005-07-02
I need help with connecting to my home network. It is a wireless network. I have already set up ndiswrapper. I can scan for nearby networks, yet I cannot connect to my own network. I am sure that I have set up everything correctly. Can someone plaese help me? Thanks.

---

### Post by remin8 on 2005-07-02
Using the GUI configuration utility should be a breeze one you get the ndsiwrapper set up properly. Go to Applications->System Tools->Network Tools then select your wireless card under the Network Device dropdown list. Click on configure and enter your key and you really should be set.

---

### Post by Andre N. on 2005-07-02
I tried doing that, but it didn't work. I put in my key correctly too. By the way, I'm using a Pre-shared WPA key at the moment. I have also tried WEP, but nothing seems to work.

---

### Post by spd106 on 2005-07-03
Hi, it would be easiest to temporarily disable all encryption until you can verify that it will work. Can you provide us with some more information, perhaps some output from "$ifconfig" or "$ifup".

Alternatively you might want to read this wiki page about wpa_supplicant
[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

Hope this helps

---

### Post by Andre N. on 2005-07-03
I am a Linux noob so I don't know what you are talking about. How would I get that information? Thanks for the howto. I will try that.

---

### Post by az on 2005-07-03
[https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA](https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA)

---

### Post by Andre N. on 2005-07-04
Thanks everyone for helping. I figured out how to solve my problem.

---

### Post by DFreeze on 2005-07-04
Congrats! Could you share it with us folks?   :smile:

---

### Post by Andre N. on 2005-07-04
It was actually a mistake on my behalf. I messed up my interfaces file in the network folder. ](*,) That's it. You shouldn't mess with anything you are not familiar with.  [-X  Lesson learned.

---

