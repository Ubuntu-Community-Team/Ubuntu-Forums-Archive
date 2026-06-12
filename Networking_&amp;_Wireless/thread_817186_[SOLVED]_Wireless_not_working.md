---
title: "[SOLVED] Wireless not working"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by magical_graam on 2008-06-03
I'm using Ubuntu 8.04. When I open network manager, it does not give me the option to search for wireless routers. I am using a Dell Inspiron 1525 with a 1395 wireless mini-card. I tried this tutorial [http://sudan.ubuntuforums.com/showthread.php?t=297092]("http://sudan.ubuntuforums.com/showthread.php?t=297092")
but when I do the last part to check if the wireless is working
```
sudo iwlist scanning
```
it comes up with
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Also, I used the .exe file for 1395 (R174292.EXE) instead of the one for 1390 (R151517.EXE) but it didnt work. Help please!

btw I'm new at linux, only started using it on Sunday, so try and keep it simple.

---

### Post by vexingmodstwo on 2008-06-03
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If that doesn't work for you, it will at least get you set up to try something else.

---

### Post by magical_graam on 2008-06-03
Which model should I use for step 2 or how can I find out?

---

### Post by vexingmodstwo on 2008-06-03
> **magical_graam said:**
> Which model should I use for step 2 or how can I find out?

There's a chart that tells you...  Make sure you read all the instructions as there are commands in there to tell you how to find out the information needed.  In this particular instance, you would find out by issuing this command:

```
lspci -n | grep '14e4:43'
```

---

### Post by magical_graam on 2008-06-03
Thanks! Its working now

---

### Post by vexingmodstwo on 2008-06-03
> **magical_graam said:**
> Thanks! Its working now

The wireless card is working?  Awesome.

You should mark this thread solved.

---

