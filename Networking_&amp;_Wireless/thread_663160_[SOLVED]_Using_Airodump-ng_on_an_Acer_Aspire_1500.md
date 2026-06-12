---
title: "[SOLVED] Using Airodump-ng on an Acer Aspire 1500"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by scott_ttocs46 on 2008-01-09
I attempted this and got this error:

```

administrator@administrator-laptop:~$ sudo airodump-ng -w Out ath0
[sudo] password for administrator:
ioctl(SIOCSIWMODE) failed: Invalid argument
Error setting monitor mode on ath0
administrator@administrator-laptop:~$ 


```

Does anyone know how to capture packets with airodump-ng on an Acer Aspire 1500?


Thanks,
Scott

---

### Post by Junglizer on 2008-01-10
Post your lspci output if you can please, we'll need to know what sort of wireless radio you've got.

---

### Post by Junglizer on 2008-01-10
On second thought, seeing how you've got "ath0" as a nice keyword in your post, you're clearly running an Atheros chipped card. If you are using the Madwifi drivers, you'll want to do the following to set your card into RFMon mode:
```
root@box~#ifconfig ath0 down
root@box~# wlanconfig ath0 destroy
root@box~#wlanconfig ath0 create wlandev wifi0 wlanmode monitor

```
Then follow up with your set commands based on your output/logging preferences with Airodump. You can do that all as sudo if you like, you just need to have root perms. I prefer to be logged in as root, or use su perms on my regular user as you have to change quite a lot of stuff to default the card back to its normal STA mode and vice versa.

---

### Post by scott_ttocs46 on 2008-01-10
It is an Atheros Card.

I did this:

```


administrator@administrator-laptop:~$ sudo ifconfig ath0 down
[sudo] password for administrator:
administrator@administrator-laptop:~$ sudo wlanconfig ath0 destroy
administrator@administrator-laptop:~$ sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ath0
administrator@administrator-laptop:~$ sudo airodump-ng -w Out ath0
ath0 is not a network interface.
administrator@administrator-laptop:~$ 



```


Any ideas? :confused:

---

### Post by scott_ttocs46 on 2008-01-10
The model number for the aspire is 5100, not 1500. Forgive my disdexiyyya  ):P

---

### Post by Junglizer on 2008-01-10
Let me whip out my lappy and see what procedure works for me.

---

### Post by Junglizer on 2008-01-10
alright, looks like its this, since linux is very keen on assigning profiles to devices, you may actually be using ath1. Once you do "wlanconfig ath0 create wlandev wifi0 wlanmode monitor" take a look at "iwconfig' and see which label you've got with the ath prefix. ath0, ath1, ath2, etc... then try changing the airodump parameters to fit what you've got listed in iwconfig.

---

### Post by the_darkside_986 on 2008-01-10
i tried something like this in Ubuntu to see if i could crack my own WEP key lol. But ifconfig showed "ath3" after i did the Atheros monitor mode thingy. But when I tried to use ath3 as the device, it launched the packet sniffer but I got no beacons at all picked up :(

---

### Post by scott_ttocs46 on 2008-01-10
> **Junglizer said:**
> alright, looks like its this, since linux is very keen on assigning profiles to devices, you may actually be using ath1. Once you do "wlanconfig ath0 create wlandev wifi0 wlanmode monitor" take a look at "iwconfig' and see which label you've got with the ath prefix. ath0, ath1, ath2, etc... then try changing the airodump parameters to fit what you've got listed in iwconfig.

Thanks. This was the case. Linux renamed it to ath4 on my laptop.

My only other question is how to reset my wireless setup without having to reboot my laptop. Whenever I use the destroy command, it disables my GNOME wireless connection.

---

### Post by Junglizer on 2008-01-11
> **scott_ttocs46 said:**
> Thanks. This was the case. Linux renamed it to ath4 on my laptop.

My only other question is how to reset my wireless setup without having to reboot my laptop. Whenever I use the destroy command, it disables my GNOME wireless connection.

I don't know any specifics for the GUI apps for managing network connections, as I do all of that through the command line anyways. However, you should be able to recreate a valid connection mode with ```
root@box~#wlanconfig create athX wlandev wifiX wlanmode sta
``` the STA mode will remove it from RF Mon (as you cannot connect to networks while in that mode) and put it back into the default mode.

---

### Post by Junglizer on 2008-01-11
> **the_darkside_986 said:**
> i tried something like this in Ubuntu to see if i could crack my own WEP key lol. But ifconfig showed "ath3" after i did the Atheros monitor mode thingy. But when I tried to use ath3 as the device, it launched the packet sniffer but I got no beacons at all picked up :(

Well a few things on this, make sure you have the right options passing to the sniffer app regarding, band, channel and device, as well as what sort of packets you wish to capture. Secondly, most declarations of WEP being easy to crack are misleading. The actual crack time is very small yes, however that is only after you have gathered enough packets. Somewhere in, I believe 250-500 for a 40-bit WEP key, and 800+ for a 104-bit key. Those are also IVS packets, containing key information, not beacon packets.  An average home network, is going to be, oh I'd say at max 3-5 clients connected at any given time. (kismet is a great program for finding number of clients connected, as well as other info) The more clients connected, the more packets being sent, and thus the more likely you will receive/intercept IVS/secure packets. To put all of this into perspective, let me explain that not too long ago I was monitoring packets from a network with no more then 1-2 clients connected at irregular intervals. Over the course of six to seven hours I only received 53 IVS packets. 

So yes, WEP is easily cracked, but it is only going to be efficiently cracked on home networks using constant monitoring or ARP/packet injection procedures.

---

