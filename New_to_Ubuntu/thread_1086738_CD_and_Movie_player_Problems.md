---
title: "CD and Movie player Problems"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by ian19jam on 2009-03-04
1) When I want to use a CD on the computer it won't recognize any of them and Movie Player keeps saying that there is an error and does not recognize anything and that you might not have permission to open.
When I go to Windows XP it works perfectly.
 What am I doing wrong with Ubuntu and Movie player? I am no computer expert and so simple answers please.
Many thanks Ian

---

### Post by LowSky on 2009-03-04
```
sudo apt-get install ubuntu-restricted-extras
```

you may also need the medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ian19jam on 2009-03-04
I typed in the code that you kindly sent me in the terminal and it processed itself through then it came to a stop and froze up. Now it is asking me to process this manually and U I simply do not understand. Please can you advise as to what I should do Thank you Ian

---

### Post by avtolle on 2009-03-04
What is the error message you are receiving? If it references "dpkg --configure -a", open a terminal and do```
sudo dpkg --configure -a
```You will be asked for your password, type it in (you will receive no visual confirmation at all), press Enter, and see if this fixes the problem. If you have another error message than what I presumed, or if you get other messages, please post them here.

---

### Post by ian19jam on 2009-03-04
This did not appear to work and terminal immediately returned to the phrase desktop: $

I tried playing a disc but the tracks all carry a lock sign at the the top of the music sign on each file. I am somewhat puzzled Is there a solution please? Many thanks

---

