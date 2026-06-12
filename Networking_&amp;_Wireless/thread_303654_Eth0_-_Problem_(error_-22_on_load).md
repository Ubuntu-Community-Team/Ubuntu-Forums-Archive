---
title: "Eth0 - Problem (error -22 on load)"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by Xanath on 2006-11-20
Hi, first off ill start by saying im a linux newbie so go easy.

no my problem started when i had no network connection even though Eth0 was up no ping or arp to anything after a reboot the Eth0 device Vanished here are the current settings.

```
dmesg | grep 3c
```
[1717959591.600000] 3c95x: vortex_probe1 fails returns -22
[1717959591.600000] 3c95x: probe of 0000:00:0d.0 failed with error -22

```
lspci | grep 3c 
```
0000:00:0d.0 Ethernet Controller: 3Com Corporation 3c905B 100baseTX [Cyclone] (rev 30) 

```
lsmod | grep 3c  
```
3c95x 45608 0
mii 5888 1 3c95x

```
ifconfig -a
```
shows only lo and Sit0 devices.

my /etc/iftab file is clean and /etc/network/interfaces has eth0 on auto.

trying to reload network i get an error stating eth0 device does not exist. 

i want to add that this network card worked on this installation and i made absolutely no changes before this problem appeared.

Any assistance is welcomed
thanks in advance,
Xanath

---

### Post by DaveBorealis on 2006-11-20
> **Xanath said:**
> no ping or arp to anything after a reboot the Eth0 device Vanished

Sounds like your eth0 might have lost its IRQ.  When you do a cat '/proc/interrupts' do you see a listing for eth0?  Should look something like:
```
201:    3786860   IO-APIC-level  eth0
```

Best regards,
Dave

---

### Post by lance bermudez on 2007-05-07
i do not get that. so what do i do?
first let me say im using kernel-image-2.4.26-1-386 and im moving down from linux-image-2.6.8.1-3-386. the change is for the less room it take up. i followed [http://occy.net/node/142](http://occy.net/node/142) on how the remove the 2.6 /lib/modules. the network card is the 3c905c-tx-mx and the module 3c59x works for it tested out with the live cd of dam small linux and also worked with the 2.6 image. when i do a modprobe ne 3c59x  i get the 

/lib/modules/2.4.26-1-386/kernel/driver/net/ne.o:
init_module: no such device o
r address
hit: ismod errors can be caused by incorrect module
parameters, including inva
lid IO or IRQ parameter

dhcp does not work it error out

your command from above give me
       cpu
0     77381    xt-pic  timer
1     1817      xt-pic  keyboard
2      0           xt-pic  cascade
8      4           xt-pic  vtc
9      0           xt-pic  usb-hbci
11     0          xt-pic  usb-hbci
14     8119    xt-pic  ide0
15     68         xt-pic ide1
nmi    0
loc     0
err    0
mis


how do i fix this so i can get on the network to finish bulding my system

---

