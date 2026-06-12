---
title: "Dell wireless problem"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by LiquidInferno on 2007-03-20
I have a dell laptop and the wireless card used to work just fine. However, I was looking for a program that would scan wireless networks around and let me connect since I change locations a lot, and finding out the network name is not always easy. I came across a program called swscanner - and ever since I have used that, I am unable to connect to anywhere wirelessly. 

Does anyone have any suggestions on how to fix this and also a program like swscanner? Thank you.

---

### Post by Floppyjoe on 2007-03-20
Network Manager is a good program to show you and allow you to connect to wireless and wired networks. For it to work you need to disable all your network interfaces in System/Administration/Networking and it also would help to comment out all but the lo interface in /etc/network/interfaces by putting a # in front of the lines.

---

