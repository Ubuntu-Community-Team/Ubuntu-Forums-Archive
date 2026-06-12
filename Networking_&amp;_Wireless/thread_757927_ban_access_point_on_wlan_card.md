---
title: "ban access point on wlan card"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by natirips on 2008-04-17
Is there a way to stop my computer from connecting to a specific WLAN access point? (because my computer desperately attempts to connect to an AP which is not mine despite it's low signal). It happens at every boot and I have to manually select my own AP...

---

### Post by dstew on 2008-04-17
Connect to the access point you want, then disable roaming.

---

### Post by natirips on 2008-04-17
When I turn off roaming mode it won't connect at all! :(
Edit: The above statement is based on an attempt to do so.

Besides, I'd like to ban a single specific network.

---

### Post by dstew on 2008-04-17
OK, lets do this. Open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
iwconfig
```Look at the interface name for your wireless device (it might be wlan0, or eth0, or ath0) and use it in this command:```
sudo iwlist wlan0 scan
```That will list information about the available access points. I don't know how to ban one, but to limit access to one, you can use the cell address of the one you like in this command```
sudo iwconfig wlan0 ap *<cell address>*
```There might be some way to ban one, but I couldn't see one in the [iwconfig man page]("http://linux.die.net/man/8/iwconfig").

---

### Post by natirips on 2008-04-17
From past experience my card/driver seems to be resistant to "sudo iwconfig lalala" commands, and moreover, the physical address of my local AP changes quite frequently due to frequent voltage dropping thus router restarting.

I already tried limiting the card to use only my ESSID (using sudo iwconfig), but when I check iwconfig after that, nothing has been changed. I thought there was maybe some 'blacklist' or something like the one modprobe has to ban faulty/buggy/unused drivers.

Well, it's not going to kill me, but sometimes I forget to change to my network, or it switches in the middle of my work to that other network which is not mine, I don't really think it is polite of me to be using someone's network without their approval...

---

