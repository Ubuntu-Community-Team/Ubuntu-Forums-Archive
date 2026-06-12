---
title: "Cracking WEP"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by alokme on 2008-10-11
Hi 2 All
well i'm preety new to this environment so i need help
i've recently installed ubuntu 7.04
i've intel pro wireless 3945 abg wireless card
recently someone told me that cracking wep is possible
so i want to try it out on my network
i've downloaded "aircrack-ng-1.0-rc1.tar.gz" and "ipwraw-ng-2.3.4-04022008.tar.bz2" for the same but my lack of knowledge commands of ubuntu hinders me to install both of them

can someone please tell me step by step approach with commands to do the same???

---

### Post by bobyy on 2008-10-11
Maybe you are mising the point..
You tell us you are new in linux ...instead to try learn linux,and do useful thinks you jump directly to crack networks...
Just search the web ...and you wil have all the answers is not necesary to waste time of people who are willing to learn linux

ciao

---

### Post by AlexBellisBrown on 2008-10-11
> **bobyy said:**
> You tell us you are new in linux ...instead to try learn linux,and do useful things you jump directly to crack networks...


Each to thier own, he can use Linux for anything he wants, besides, its not illegal to crack your own network if your playing around.:popcorn:

Start easy grasshopper, for example, if you know nothing about how wireless works, cracking WEP will be very hard for you. Look, i recommend you read abit about it first, also, download yourself a program from the Add/Remove programs, its called Wireshark, its basically a packet sniffer, learn what all these things are, and then get complicated.

In order to capture a WEP password, you need to analize the "packets" that go between router and wireless device, once enough data is captured, the program can crack the encryption, giving you the password.

Its complicated, and not quite why Ubuntu was invented, its possible some people might not be too happy about me replying in this much detail, but meh, you need help, thats what were here for.

:popcorn:

---

### Post by alokme on 2008-10-12
well i got ur point
but when i try to install aircrack...some error occurs
i type "sudo apt-get install aircrack-ng"
ideally it should install the application...but it says application not found

i installed aircrack-ng-1.0-rc1.tar.gz.....but still the same problem
what to do?

---

### Post by VladNistor on 2008-10-12
Have you tried going to the aircrack-ng website for a giude on installing? Their guide is actually based on ubuntu/debian so just follow it step by step and you should be alright, you're probably missing a one. 

They have some pretty good guides on cracking WEP/WPA, give them a read.

You need to read at least the guides to understand what you're actually doing, and then read some more. It's the only way you can know what to do when the guide doesn't work for you.

---

