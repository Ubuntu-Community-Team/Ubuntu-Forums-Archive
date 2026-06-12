---
title: "No Internet after install?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by chris062689 on 2009-07-26
I recently decided to try out Ubuntu 9.04 / Kubuntu 9.04 again.
I've used them in the past, and never remembering this kind of problem on the same computer...

I'm using a GA-EP35-DS3L motherboard, the ethernet works and I can get online just fine when using the LiveCD, but after I install and reboot, it says eth0: Unavailable.

Can anyone help me?  Thanks.

[EDIT: About to try on Ubuntu 9.04 (instead of Kubuntu) just making sure it's not Kubuntu specific.]

---

### Post by ktechkio on 2009-07-26
Please produce output for netstat and ifconfig and dmesg in terminal

---

### Post by chris062689 on 2009-07-26
This problem is not specific to Kubuntu.
I assume it's something with the kernel.

[http://pastebin.com/m1b5fbb9b](http://pastebin.com/m1b5fbb9b)

---

### Post by ktechkio on 2009-07-26
Why don't you try Kubuntu karmic alpha 3 like me. Lightning fast!:KS

---

### Post by Liolikas on 2009-07-26
In ifconfig I see eth0, but it has no IP.
Maybe try something like:
dhclient eth0
And post here what happens.

---

### Post by Liolikas on 2009-07-26
Also show your card model:
sudo lspci|grep Ethernet

---

### Post by Michael.Godawski on 2009-07-26
I would not play with an early Alpha version yet, if your main objective is to install a working system. 

Alphas are still development versions and can have bugs and produce crashes. If you like to tinker and test, then an Alpha version is for you, otherwise it is not. 

Can you please post also the outputs of
```

sudo lshw -C network
iwconfig
ifconfig
cat /etc/network/interfaces 
```

---

### Post by chris062689 on 2009-07-26
I've already reinstalled Windows.
Don't take it the wrong way though, I'm not giving Linux the middle finger, I was just testing out something (I normally run Ubuntu in Virtualbox.)

I'll try again when Karmic reaches a further Beta, and if it hasn't been resolved by then I'll file a bug report.

---

### Post by Liolikas on 2009-07-26
Go into windows system information and post card model at least.
It is hopeless to wait until someone will even try to fix something that works for everyone.

---

### Post by ktechkio on 2009-07-26
> **Michael.Godawski said:**
>  

If you like to tinker and test, then an Alpha version is for 

Thats what I like :popcorn:

Why not do an upgrade (by getting internet via other means!) 
Oh and produce output for lspci

---

### Post by chris062689 on 2009-07-26
Realtek RTL8168B/8111B Family PCI-E Gigabit Ethernet

If someone else searches and finds this thread (and is still having this problem) go ahead and revive it I suppose.

---

### Post by Liolikas on 2009-07-26
This card generally works well on Linux r1000 module is responsible for it.
sudo modprobe r1000
Should force if on.

---

