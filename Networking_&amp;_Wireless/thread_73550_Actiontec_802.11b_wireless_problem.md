---
title: "Actiontec 802.11b wireless problem"
date: 2005-10-09
forum: Networking &amp; Wireless
---

### Post by Matt73 on 2005-10-09
Hi all,

I've just installed Ubuntu on my machine and i'm having problems getting Ubuntu to use my network hardware.  If I go into network tools I cannot see my actiontec hardware listed to configure however if I go into devices the USB entry says that I have a prism 2.5 802.11b lan card installed.  

I've done iwconfig and under the entry wlan0 it says "no wireless extensions".  I know the card is almost installed correctly and I get the feeling I just need to do something simple and it'll be working in no time.  

I've done a ping on my machine from network tools and I can ping myself (but nothing else of course).

Do I need to update my driver with ndiswrapper, update my firmware or simply put something in the network interfaces file?  I'm soooo close I can almost taste it.  Can anybody suggest anything because i've been going round in circles for the last 2 days.

Thanks.

---

### Post by XDevHald on 2005-10-09
[QUOTE=Matt73]Hi all,

I've just installed Ubuntu on my machine and i'm having problems getting Ubuntu to use my network hardware.  If I go into network tools I cannot see my actiontec hardware listed to configure however if I go into devices the USB entry says that I have a prism 2.5 802.11b lan card installed.  

I've done iwconfig and under the entry wlan0 it says "no wireless extensions".  I know the card is almost installed correctly and I get the feeling I just need to do something simple and it'll be working in no time.  

I've done a ping on my machine from network tools and I can ping myself (but nothing else of course).

Do I need to update my driver with ndiswrapper, update my firmware or simply put something in the network interfaces file?  I'm soooo close I can almost taste it.  Can anybody suggest anything because i've been going round in circles for the last 2 days.

Thanks.[/QUOTE]
How-To get your network card device detected and up and running "The Right Way":
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by Matt73 on 2005-10-09
wlan0 says "no wireless extensions".  Does this mean the driver isn't installed correctly? 

I'm a total newbie when it comes to Linux and i had problems installing ndiswrapper.  If I manage to install it what driver would I use afterwards?

---

