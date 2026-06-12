---
title: "Here's a NEW one:  Wireless works - Wired doesn't"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by KrazyPenguin on 2007-04-28
I'm using Feisty and my wireless works.

How do you switch it to wired??

Should I try a reboot???

I have it setup so that when my laptop starts, it automatically logs in , connects to my wireless network, and automatically enters the keyring password.

I've tried all different settings and it doesn't want to switch.

Any ideas??

Edited:
Firestarter setting was causing the problem.

Thanks to all the people that helped!!!

;-)

---

### Post by Iarwain ben-adar on 2007-04-28
Hi there,
do you have Networkmanager? (try clicking there, and choosing your wired)


Iarwain

---

### Post by agurk on 2007-04-28
Right-click on the Network Manager applet in your panel and unselect 'Enable Wireless'.
If that doesn't work, please post the contents of your /etc/network/interfaces file.

---

### Post by KrazyPenguin on 2007-04-28
> **Iarwain ben-adar said:**
> Hi there,
do you have Networkmanager? (try clicking there, and choosing your wired)


Iarwain

The problem is I can't choose my wired.
It is disabled for some reason.
I can see it back it won't let me choose it.


Any ideas on how to enable it??

Thanks in advance!!!

(PS.  had to go back to windows to play pokerstars - bad connection today even in xp and wired)

---

### Post by KrazyPenguin on 2007-04-28
Ok here is the /etc/network/interfaces file:
> 
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp
address 192.168.0.1
netmask 255.255.255.0




Thanks again 
;-)

---

### Post by Iarwain ben-adar on 2007-04-29
And what about augurk's advice? Can you unselect something?


Iarwain

---

### Post by KrazyPenguin on 2007-04-29
> **Iarwain ben-adar said:**
> And what about augurk's advice? Can you unselect something?


Iarwain

 Yes, unselect "Wireless" in the Network Manager Icon in the panel.
Then because I installed Firestarter, I must make a change in Firestarter -> Preferences -> Network Settings and then change eth1 to eth0 to enable "Wired Mode".

I figured something out myself 
:shock: 

Thanks
;-)

---

