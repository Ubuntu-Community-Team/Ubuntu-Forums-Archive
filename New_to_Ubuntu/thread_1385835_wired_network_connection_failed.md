---
title: "wired network connection failed"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by a-marquardt on 2010-01-20
I have just installed Ubuntu 9.1 on one hard drive and windows on another. I boot switch through bios. There is a network connection through windows but not 9.1. When I boot 9.1 I get no network connection it says network disconnected. When I first installed 9.1 it had no problem auto-detecting the wired network connection. I am a newbie to linux and not sure how to fix this?

---

### Post by FreezWay on 2010-01-20
i had the same problem.... it just started working again for me. try rebooting.

---

### Post by a-marquardt on 2010-01-20
Tried rebooting repeatedly with no success.

---

### Post by lotharmat on 2010-01-20
Could you post the output of the following command?

```
lshw -C network
```

---

### Post by a-marquardt on 2010-01-20
I think this is what you wanted me to post it took me a while because I had to save in Office then transfer to flashdrive then transport to a working computer.  WARNING: you should run this program as super-user.    *-network                       description: Ethernet interface         product: RTL-8139/8139C/8139C+         vendor: Realtek Semiconductor Co., Ltd.         physical id: e         bus info: pci@0000:00:0e.0         logical name: eth0         version: 10         serial: 00:10:dc:c7:26:c7         width: 32 bits         clock: 33MHz         capabilities: bus_master cap_list rom ethernet physical         configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes         resources: irq:17 ioport:a000(size=256) memory:e3000000-e30000ff memory:40000000-4000ffff(prefetchable)

---

### Post by lotharmat on 2010-01-20
Hmmm, well it looks like ubuntu has identified it but I'm not sure why it is not working..

Someone with more experience of this will no doubt be along in a while to help.

---

### Post by Cheezespread on 2010-01-20
Is it like " The network is shown in the n/w list , but not getting connected at times" .

This happens a bit for me that the network doesnt connect at times. I remove the wired connection or switch off the wifi switch incase of wifi. Click on the edit connections in the Network manager and set it up again with the password and all ( again ) . Works for me . ( never really bothered why it happens . My bad )

---

### Post by a-marquardt on 2010-01-20
"This happens a bit for me that the network doesnt connect at times. I remove the wired connection or switch off the wifi switch incase of wifi."  WIFI is not on.   "Click on the edit connections in the Network manager and set it up again with the password and all ( again ) ."   Grey area for me in that network managers asks questions I don't know the answer to. Is there a way to access network info through Vista which is also connected to the network? Problem persists should I completely reload ubuntu it worked initially then failed to connect to the network? I am on ATT Uverse. No password is asked for.

---

### Post by Calorus on 2010-03-12
Dear All: Same issue - has anyone got any ideas as to how to solve it?
Any assistance greatly appreciated, 
Many thanks in advance!

---

### Post by rockerphil on 2010-03-12
to the original poster, could you please post the output of this command? it will help determine if you are indeed pulling down an IP address.

```
sudo ifconfig
```

---

