---
title: "Unable to connect to the internet in Ubuntu 11.04?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by AllenVlog on 2011-07-19
I've used other versions of Ubuntu, but never was able to connect.
On my new laptop, I downloaded 11.04. I'd like to use it as my only OS, but I can't connect to the internet.
I've tried giving it my internet pass, but it's not working, and it wont even connect when connected to the motem.
Thanks for the help.

---

### Post by androssofer on 2011-07-19
> **AllenVlog said:**
> I've used other versions of Ubuntu, but never was able to connect.
On my new laptop, I downloaded 11.04. I'd like to use it as my only OS, but I can't connect to the internet.
I've tried giving it my internet pass, but it's not working, and it wont even connect when connected to the motem.
Thanks for the help.

can u provide more info, is it wireless or ethernet your tryin to connect using?

if you have ur cables plugged in and you type:

```
ifconfig
```

what comes up?

---

### Post by LostRealist on 2011-07-19
I'm having the same problem. This is my first experience with Linux/Ubuntu. When I first installed it networking worked but web pages took about 10 minutes to load. Now it will not connect to any network at all. I'm using a wireless network. Should I try ifconfig too?

---

### Post by wep940 on 2011-07-19
Please do post back the output of the ifconfig as asked for above.  Also please post back the following as well:

lspci

If this is a built-in wireless card, you may also want to try the following and post back the results as well:

lspci | Wireless

If that doesn't return anything, then try:

lspci | wireless


If you don't know yet, these 2 commands must be done in a terminal window (applications/accessories/terminal).  Just highlight the output, right click and click copy, then come back to a new post in this thread and paste in the results.

---

