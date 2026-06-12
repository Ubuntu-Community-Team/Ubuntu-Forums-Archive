---
title: "Ubuntu 9.10 no wireless connection"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by adrenalinche on 2010-05-14
Hi everyone,
I installed ubuntu 9.10 today and now i am trying to connect to a wireless network, but the network manager doesn't show any wireless connections. I tried searching for the same problem in ubuntu forums, people say that that might be a driver problem, others say that the interfaces file should be edited somehow. 

Well, I am a total noob and need some help. Can anyone explain to me how to fix this problem? I don't know any commands for the terminal, so talk to me like to an idiot. 

;(

Greetings,
adrenalinche

---

### Post by dhirendra1 on 2010-05-14
Wireless network will work only after you  enable the driver.  You can connect the CPU on ethernet (wired network) and through System > Administration  > Hardware Driver enable the wireless card.  The wireless network should work thereafter.

---

### Post by adrenalinche on 2010-05-15
Hi again :)
So here is what i did and how far i came to any decision. 
1. I made a bootable USB for my netbook with ubuntu 10.04
2. I installed it
3. I made the wired internet connection work(terminal - sudo pppoeconf)
4. I went to System - Administration - Hardware Drivers and tried the two options there:
- Broadcom B43(or something like that)
- Broadcom STA

I still don't even see the icon up there for the internet connection. Now i have the STA driver installed and have no idea how to make the wireless work :(((
Please give me an advise.

---

