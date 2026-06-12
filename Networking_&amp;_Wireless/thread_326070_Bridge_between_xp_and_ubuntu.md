---
title: "Bridge between xp and ubuntu"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by retardedhobo on 2006-12-27
Hello, i have about 2 days experience with Ubuntu (edgy eft) so configuring it is challenge. But, here is my problem:

I want to have my Ubuntu box connect to the internet via my XP box. I dont have a crossover cable, so the U box is going(via Ethernet) to a hub, then to my xp box(via Ethernet). The XP box has a wireless card, which is how it connects to the internet. 

The xp box is running  XP Home SP2

XP box's ip is assigned by the DHCP - 192.168.xx.x

I have not been able to get either box to see each other, and both are on the same domain(mshome).

I have bridged the two connections( wireless and the LAN) on the xp box, but do not know how to configure ubuntu.

Any help would be great! Thanks...

---

### Post by dbbolton on 2006-12-27
try samba ?

---

### Post by retardedhobo on 2006-12-27
I installed samba, told it what folder to share, put the same domain as the xp box, but XP just wont see it.

---

### Post by retardedhobo on 2006-12-27
Just installed NetworkManager, and it said i could not find a network device ( but the light on the nic card is on and blinks).

I ran 'lspci' and the output included this:
```
01:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
```

I then ran 'lsmod' to look for the module, but im not sure what im suppose to look for because i did not see any of the above in the output.  :confused:

---

