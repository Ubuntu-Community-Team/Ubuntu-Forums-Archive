---
title: "no driver for wifi"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by isaiah40_31ph on 2011-06-16
good day to all

I have bought an emachine em350 netbook last december, it came with a pre-installed limpus os. 

but i had installed ubuntu 10.10 

so far everything works very well except for one thing. i couldnt get the wifi running. i was able to surf the web wirelessly when linpus OS was still installed.

i tried downloading a broadcom wifi adaptor installer but that too didnt work.

I'm still very new to the linux / ubuntu world so go easy on me :)

thanks very much.

mike

---

### Post by wildmanne39 on 2011-06-17
> **isaiah40_31ph said:**
> good day to all

I have bought an emachine em350 netbook last december, it came with a pre-installed limpus os. 

but i had installed ubuntu 10.10 

so far everything works very well except for one thing. i couldnt get the wifi running. i was able to surf the web wirelessly when linpus OS was still installed.

i tried downloading a broadcom wifi adaptor installer but that too didnt work.

I'm still very new to the linux / ubuntu world so go easy on me :)

thanks very much.

mikeHi, post the information from these commands, you need to enter it into the terminal
```
sudo lshw -C network
```
```
lspci
```
```
lsmod
```then post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Paqman on 2011-06-17
Have you checked in the Additional Drivers tool? You might need to plug straight into your router to get a connection, but once you do Additional Drivers might be able to install the wifi driver you need.

---

