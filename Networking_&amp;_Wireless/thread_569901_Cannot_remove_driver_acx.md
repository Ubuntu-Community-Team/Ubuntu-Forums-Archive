---
title: "Cannot remove driver acx"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by cthulhufhtagn on 2007-10-07
I'm trying to install a linksys wpc54g PCMCIA wifi card on my wife's laptop. She's running Feisty. The problem seems to be that Ubuntu thinks that the wifi card is a Texas Instruments wifi card and loads the acx drivers. 
```
araminta@lappy386:~$ ndiswrapper -l
lstinds : driver installed
        device (104C:9066) present (alternate driver: acx)
```

I blacklisted it with the code below and rebooted. 
```
echo 'blacklist acx' | sudo tee -a /etc/modprobe.d/blacklist
```

It seems to still be loading because I still get the same message as above when I use "ndiswrapper -l".

When I try to 'rmmod acx' i get:
```
araminta@lappy386:~$ rmmod acx
ERROR: Module acx does not exist in /proc/modules
```

So I guess I'm not sure if the acx driver is loaded or not and if it is loaded, I already tried to get rid of it so how do I get rid of it? Any advice or a shove in the right direction would be very much appreciated.

---

### Post by kevdog on 2007-10-07
Is this module actually loaded and running:

lsmod | egrep '{ndiswrapper|acx}'

---

### Post by cthulhufhtagn on 2007-10-07
```
araminta@lappy386:~$ lsmod | egrep '{ndiswrapper|acx}'
ndiswrapper           193116  0 
usbcore               134280  3 ndiswrapper,uhci_hcd
```

---

### Post by kevdog on 2007-10-07
So from what you posted the acx driver isnt even loading -- only ndiswrapper.  So I wouldnt worry about it!!

---

### Post by cthulhufhtagn on 2007-10-07
Oh, heh. Thanks for the help.

---

