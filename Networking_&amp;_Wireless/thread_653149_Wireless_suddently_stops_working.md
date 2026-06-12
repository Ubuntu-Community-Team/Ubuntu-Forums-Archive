---
title: "Wireless suddently stops working"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by MaxTeel on 2007-12-29
Hello.

I bought a new laptop and it gives me some problems. The most important is wireless.
I installed my device using ndiswrapper. Aand everything works, but about 2 hours later (or maybe less) I lose the connection and can't connect again. I have to reboot my computer for it to work again.
The problem isn't with the router, as it also happens at school and at friends homes. Also, it doesn't happen in Windows.


My computer and important info:

LG E500 SP21
wireless - AR5006EG 802.11 b/g Wireless PCI Express Adapter

Ubuntu 7.10
I use the network manager that come with ubuntu.


If you can't provide the solution, at least could you tell me how to manually restore the connection/device? Thanks in advance.

---

### Post by kevdog on 2007-12-29
Try this when the network goes down and you cant restart

sudo ifconfig ath0 down
sudo modprobe -r ath_pci
sudo modprobe ath_pci
sudo ifconfig ath0 up

Then see if you can use network manager to restablish the connection.

---

### Post by MaxTeel on 2007-12-29
> **kevdog said:**
> Try this when the network goes down and you cant restart

sudo ifconfig ath0 down
sudo modprobe -r ath_pci
sudo modprobe ath_pci
sudo ifconfig ath0 up

Then see if you can use network manager to restablish the connection.

that worked, although i tried it without the connection going down (the problem I have). I still have to try it that  way.

when I run ifconfig ii lists eth0, lo and wlan0. wlan0 is the one being used, so, to run what you posted I changed ath0 to wlan0 and ath_pci to ndiswrapper. 
I don't know if this helps, but at least is here for anyone to see ;)

---

