---
title: "network problem with on board lan card on 780g"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by san2sh on 2008-06-15
i installed yesterday the latest version of UBUNTU 8.04 . When i tried to configure the internet connection i discovered that there's  etho:avahi in the device list in network.

now i can't connect to the internet, i have in the device list l0, eth0, & eth0:avahi,eth1 ....i have two lan cards.......my internet connection is relianc e wimax....since the network is bind to my on board lan card i couldnt connect to other lan card........when i am connecting to other lan card there is no avahi and it takes the ip address in eth1 ...but net doest work since the network card hardware address that is mapped is my onboard lan card.....how to solve the problem

the thing that needs to be solved as far as i guess is the ip should be there is eth0 instead of eth0.avahi

i searched the net and i found that i have to bring the two IP versions in eth0. but how?

here's some command results...

---

### Post by foska on 2008-08-19
I have a similar problem! Was this resolved and if so how was it done.

---

### Post by foska on 2008-08-20
Interestingly enough after I posted the above message. I "googled" my card and found that someone had already proposed a solution which was to simply shutdown the computer and remove the plug from the power supply for approximately 10 secs and replace it. After I turned the computer back on the network was then accessible and I could get on to the internet. Imagine that!

---

