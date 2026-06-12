---
title: "Need help to get wlan working again."
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by haaglin on 2005-07-21
Hi. 

Everytime i start my computer i have to manually type:
```

$sudo ifconfig ath0 up
$sudo dhclient ath0

```
to get my wlan working. 
It has been working fine for a long time, i got this problem just a few days ago. 
during boot, it fails in configuring network devices. And if i try to enable it in Control Center in KDE, it gets disabled again. the only way i can get connection is to do this manually. Anyone know what te problem might be?

---

### Post by haaglin on 2005-07-22
bump.

---

### Post by odin on 2005-07-25
I am not completely sure if this is what you need but it could be a solution for your problem.Why dont you make a small script so every time you boot is executed?

For example if you want try this:

first create a file called whatever_you_want.sh for example.Then edit it and write:

#!/bin/bash 

sudo ifconfig ath0 up 
sudoi dhclient ath0 

after this do:

wget [http://www.nitrogeno.org/dnkinit_1.2-5_i386.deb](http://www.nitrogeno.org/dnkinit_1.2-5_i386.deb) 

when it is downloaded do:

dpkg -i dnkinit_1.2-5_i386.deb 


and finally edit /etc/dnkinit/start and write the full path where the script is located(for example /home/john/scripts/myscript.sh)

That shoul configure it every time you boot but If you try and it doesnt work just post it and will try to find another solution.,

 :grin:

---

### Post by MartenH on 2005-07-26
I'm not sure if this is the solution, but maybe if you add to /etc/network/interfaces

auto ath0

---

### Post by majikstreet on 2005-07-26
This is what you want to do
Put this in /etc/network/interfaces:
iface ath0 inet dhcp
auto ath0

And it should load on boot.

---

