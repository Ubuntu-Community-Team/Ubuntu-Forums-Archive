---
title: "update problem"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Dave.B on 2010-07-02
I was updating Ubuntu and without thinking shut the power down.

When i rebooted and tried to restart the update it wont let me

I have had this problem in the past and know it is an easy fix but cant remember what it is

can someone please help

thanks

---

### Post by rcayea on 2010-07-02
Run this command in terminal:

ps -ef

Then look for anything with synaptic in the line. Then to end the process run: sudo kill thenumberoftheprocess

---

### Post by lkjoel on 2010-07-02
Even simpler, just type
```
killall synaptic
sudo killall synaptic
```

---

