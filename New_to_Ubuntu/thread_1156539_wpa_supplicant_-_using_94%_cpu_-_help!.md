---
title: "wpa_supplicant - using 94% cpu - help!"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by crazyjaco on 2009-05-11
Hi. I'm extremely knew to linux. I just installed Jaunty Jackalope on my other computer two days ago.
 
I originally thought I was having a problem with my mouse. I read through the forums and did as suggested in some threads to create an 'fdi' file for the driver/hal/whatever. That seemed to fix it upon restart.
 
The next restart, it was back, but worse. Not only was my mouse misbehaving, but so too was my keyboard and more. This was suspiscious to me. I opened up System Monitor and found my cpu spiking and pegged at 100% for long periods, but no processes seemed to be eating up more than 10% of cpu and even then only one.
 
I read some more on the forums and found the 'top' command for the terminal.
 
wpa-supplicant is taking up 94% of my cpu.
 
What is this? It sounds like something to do with a wifi card.
 
How can I make this PC usable again?

---

### Post by lavinog on 2009-05-13
Can you post your system specs/model?

You can kill wpa-supplicant with the following:
```
sudo pkill wpa-supplicant
```
Doing so might disable your wireless access, but it might help to pin point the problem.

---

