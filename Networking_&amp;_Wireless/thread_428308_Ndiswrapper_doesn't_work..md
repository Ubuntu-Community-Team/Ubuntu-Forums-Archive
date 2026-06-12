---
title: "Ndiswrapper doesn't work."
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Koichi on 2007-04-30
Hello! 
I installed newest ndiswrapper on my computer and installed .inf file to make my wireless active. But it did not work.
I did like this,

1, install linux-headers

2, Get ndiswrapper from ndiswrapper web site & install

3, Install .inf file

4, Modprobe 

Problem is when I did modprobe command, it loads but it does not say anything on the dmesg command. And my wireless LED should turn on. 
Please help me.

THX

---

### Post by madmetal on 2007-04-30
> **Koichi said:**
> Hello! 
I installed newest ndiswrapper on my computer and installed .inf file to make my wireless active. But it did not work.
I did like this,

1, install linux-headers

2, Get ndiswrapper from ndiswrapper web site & install

3, Install .inf file

4, Modprobe 

Problem is when I did modprobe command, it loads but it does not say anything on the dmesg command. And my wireless LED should turn on. 
Please help me.

THX


which ubuntu version do you have?
have you tried to make your wireless work with restricted drivers manager and ndiswrapper utilites comming with synaptic? which wireless card do you have?

---

### Post by Koichi on 2007-04-30
Thank you.
I use newest version of ubuntu called Fiesty Fawn.
I have broadcom wireless card inside. And I use compaq presario C302NR. When I was using suse linux, I could use my wireless so easy like I could do that in the way that I've posted above.

---

### Post by AJL on 2007-04-30
what does 

**ndiswrapper -l**  tell you

---

### Post by Koichi on 2007-04-30
It told like this:

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

---

### Post by Floppyjoe on 2007-04-30
Did you blacklist the native bcm43xx driver?
```
sudo gedit /etc/modprobe.d/blacklist
```
add:
```
blacklist bcm43xx
```
then save this file.

---

### Post by Koichi on 2007-04-30
I did. But it is still same condition. I think newest release has some problem on it. Because so many people tried but they could not make it.

---

### Post by Floppyjoe on 2007-04-30
Do you have a button on your computer that activates the wireless?
Have you enabled roaming on the wireless card in System/Administration/Network?

---

### Post by Koichi on 2007-04-30
Yes, I have tried to do that. But it did not work. I acrivated roaming as well. But it never turns on. (LED)

---

### Post by m_bridge on 2007-05-01
same problem here, 
```
bridge@blue:~$ ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

```

r818x is **not** loaded, it does not show up in *lsmod*
and this is the default content of */etc/modprobe.d/blacklist * on afresh install
```
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

```

---

### Post by AJL on 2007-05-01
koichi

run **sudo modprobe ndiswrapper**

---

### Post by antibios on 2007-05-05
I've managed to get the following working on my Dell Latitude D620
The card shows up as:
```
lspci -nn 

0c:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
```

I could only get it working with ndiswrapper version 1.30  (I didn't test any of the later versions, but the latest doesn't work).

Which doesn't compile with the feisty default kernel, so I downgraded the kernel to 2.6.17 (from edgy)

And to stop it from crashing all the time I had to add noapic, nolapic, irqpoll to my kernel options.

Booting with the following options:
```

 noapic nolapic irqpoll ro quiet splash resume=/dev/sda5

```

---

### Post by Whiffle on 2007-05-05
Which versions of the windows inf are you using?  On the trendnet 424 on my desktop I used the Windows ME version, but the other versions didn't work as well.  You might try them all.

---

### Post by Candace on 2007-05-05
Hi,
I was able to get ndiswrapper, version 1.4.1 working great. It sounds like you might be ready for step 3 in this How To: 

[http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505)

Have you compiled the ndiswrapper program? Have you installed the R151517.EXE driver? The above HowTo is very good, and worked for me on an HP dv2000 with wireless card Broadcom 1390 WLAN MiniPCI. It seems like a different solution is needed for Feisty on each different laptop model/wireless card, so no guarantees. But I hope that helps.

---

