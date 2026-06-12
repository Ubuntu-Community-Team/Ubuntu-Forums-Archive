---
title: "I can Ping &amp; SSH into my Raspberry Pi from windows but not from Ubuntu"
date: 2019-08-16
forum: Networking &amp; Wireless
---

### Post by hexdro on 2019-08-16
Hi everybody 

I am currently dual booted, running windows 10 and Ubuntu 18.04 and am  currently trying to use the Raspberry pi for varsity work.

Initially I set up the pi by setting a static IP, turning on SSH, and  setting a static IP in Ubuntu.  This worked for a while after which one  day it magically stopped working. I am able to Ping and SSH into the pi  from my windows boot, and from other computers, just not Ubuntu on my  own machine.

I re-installed Ubuntu and again this worked for a while, but then  stopped working soon thereafter. I have reinstalled Ubuntu a 3rd time  with no success.

To my knowledge I am doing the correct network configurations, as proven  by the fact I can get it to SSH with other machines running Linux based  operating systems. Furthermore I have disabled fast boot in windows and  that has not helped much...

I have searched the internet for days and seriously want to get this working with Ubuntu ASAP. 

Any help would be appreciated !!

---

### Post by The Cog on 2019-08-16
Doesn't work covers a lot of possibilities. Try 
```
ping <address of the pi>
nc -v <address of the pi>
```
and post the results.

---

### Post by TheFu on 2019-08-16
My ssh troubleshooting steps: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
Concrete facts would be helpful.

A good start is:
```
ssh -vvvv user@host
```

---

