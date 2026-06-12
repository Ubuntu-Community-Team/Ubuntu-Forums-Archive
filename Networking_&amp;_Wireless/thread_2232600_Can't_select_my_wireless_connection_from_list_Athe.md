---
title: "Can't select my wireless connection from list Atheros"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by ariel5 on 2014-07-03
Hello. I'm new at this so please be patient... Also English is not my native language so I apologize for the trouble it might cause.

Here is my problem I can see my network on the list but is darkened. I can see other networks -password protected- and they're clickeable...

I attached the .txt file that appears when you run the script some post make us read -hoping we understand what we are reading (which I didn't, sadly)-.

---

### Post by praseodym on 2014-07-03
Hi,

deactivate the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Please understand that monitor mode is not suported here!

---

### Post by ariel5 on 2014-07-03
Hi, I tried that and I still can't select my network. Btw, I don't know what you mean with "monitor mode".

---

### Post by praseodym on 2014-07-03
Please remove all wireless connection in the network-manager applet and reboot. Then try to connect again

---

### Post by ariel5 on 2014-07-03
Now I can't even enable wireless is not there anymore. I don't see wireless networks at all. When I reboot my OS says "ath5k: Invalid parameter nohwcrypt=1"

---

### Post by praseodym on 2014-07-03
Ok, remove the file and reload the driver:
```

sudo rm /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
sudo service network-manager restart
```

---

### Post by ariel5 on 2014-07-03
Yeah! Now I see 4 wireless networks but I can't click on mine.

---

### Post by praseodym on 2014-07-03
Start the applet from terminal
```

gksudo nm-connection-editor
```
Checked this one?

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by ariel5 on 2014-07-03
I deleted my network from applet? and rebooted but can't connect to it.

---

### Post by praseodym on 2014-07-04
Lets check
```
iwconfig
iwlist chan
sudo iwlist scan
```
On which channel does the router send? Is there a MAC-address filter turned on? Check the manual how to enter the router interface

---

