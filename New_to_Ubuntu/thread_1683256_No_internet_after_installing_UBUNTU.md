---
title: "No internet after installing UBUNTU"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by billy073 on 2011-02-07
Hi, I'm new to UBUNTU. I installed the disc on a separate partition and run Win XP on the other one. After I installed UBUNTU and opened it I could not get on line. I have a Compaq V2403nr laptop with built in wireless card. I have tried a number of things from the internet but nothing works. I also can't play movies or use RythumBox but those can wait. Is there anyone out there that can explain what to do to get internet access ? I am not an expert and don't understand expert advice. I'm lookin for a simple easy solution as I'm sure many others are.
Thanks,

---

### Post by Rubi1200 on 2011-02-07
Hi and welcome to the forums :-)

We need to know what wireless card you have.

Go to Applications > Accessories > Terminal:

```
sudo lshw -C network
```

Copy/paste the results and post them here.

Also, of the following command:

```
ifconfig -a
```

---

