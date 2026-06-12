---
title: "node that is chosen in a mesh system?"
date: 2021-06-05
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2021-06-05
I have a new router mesh system that I have a question about.
I have 2 nodes.
I have an intel card that connected to a node that was:
Link Quality=56/70  Signal level=-54 dBm

I disconnected and reconnected to a different node (different MAC):
Link Quality=70/70  Signal level=-38 dBm 

The 1st node is on a different floor of the house.
The 2nd node is about 20ft away.

My question is why wasn't the 2nd node chosen in the 1st place?

---

### Post by chili555 on 2021-06-05
Network Manager doesn't yet automatically default to the strongest SSID. Frankly, in your case, I strongly doubt that you'd notice any performance difference between 56/70 and 70/70 signal strength.

If you feel that there is a posssible diffrence, bind Network Manager to the stronger by its MAC address like this: 

[https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112](https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112)

---

### Post by bjlockie on 2021-06-05
thanks.
I do get a performance increase.
It is an ax card and I get 1.2Gbps that close. :-)
I remote desktop into that machine so I need the speed.

---

