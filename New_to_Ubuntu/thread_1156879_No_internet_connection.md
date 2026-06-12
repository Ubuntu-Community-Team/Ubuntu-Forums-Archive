---
title: "No internet connection"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by nyuwa on 2009-05-12
I have been trying for a very long time now, but still cannot establish an internet connection. Just yesterday installed Ubuntu 9.04.
Equipment is old: Dell Optiplex GX1, PIII, 450 MHz, 256 MB Ram
Yet, I used it for year (!) for work with internet connection.
Currently, my work computer and 3 of childrens computers are connected via a hub (I know, I should not do that) and to a DSL. So far, internet connection IS possible with all four computers, the only computer that is refusing to respond, is the one running Linux.
I have tried to follow the instructions in a simple guidebook, the official documentation and some of the hints received elsewhere. So far no success.

Since Linux seems to work only properly, if you have access to the internet, this is a very import issue.
Thank you in advance.

---

### Post by Gidskid on 2009-05-12
Wired or Wireless and have you got the appropriate drivers for your Card installed?

---

### Post by nyuwa on 2009-05-13
Wired connection.
The computer has always been working fine (internet/mail etc.) as it was (under Windows). If I need Linux specific drivers, where/how do I get them, without internet connection.

---

### Post by Bartender on 2009-05-13
What happens if you unplug (not turn off, unplug) the DSL modem for a few minutes, then bypass the switch?  
Unplug the DSL modem for a few minutes so it powers down and sumps settings, then power it back up, then connect directly to the Linux PC, then turn on Linux PC.
If you go into Network Manager does it see the NIC?  You should see eth0.

Have you checked out Docs?
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

---

### Post by superprash2003 on 2009-05-13
post output of **ifconfig** from the terminal

---

### Post by tarps87 on 2009-05-13
> **nyuwa said:**
> Wired connection.
The computer has always been working fine (internet/mail etc.) as it was (under Windows). If I need Linux specific drivers, where/how do I get them, without internet connection.

You will need different drivers to the windows ones, but it most cases the drivers for internal wired cards are already built into the kernel. Which is a point, is the card internal or external.

can you please post the output of
```
sudo lshw | grep "network"
```

> **superprash2003 said:**
> post output of **ifconfig** from the terminal
+1

---

### Post by nyuwa on 2009-05-17
Good evening
I bought myself a new rooter and somehow managed to establish an internet connection.
Thank you all.
   .... there are still MANY (!!!) things I do not understand (are unable to handle) .......

---

