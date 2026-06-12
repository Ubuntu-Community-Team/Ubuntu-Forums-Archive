---
title: "Wireless Gone on Reboot"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by chalewa on 2007-12-23
I have a ar5006eg atheros wireless card. Works great with ndiswrapper, however, i can never get it to come up consistently on reboot. 

what i mean is this. i use wicd to manage my network settings, but only 1 out of about every 10 times will wicd recognize that there is a wireless network around me. basically i just have to keep rebooting until it does recognize that it is there and i will have internet again. 


i have also tried to manually associate my wireless card with the wireless network using iwconfig

```
 sudo iwconfig wlan0 essid 'network name'
```

doesn't associate the connection with the network, it is still just listed as off/any


if anyone has any ideas, it would be greatly appreciated. 




im using xubuntu 7.10.

---

### Post by kevdog on 2007-12-23
Do the following

echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by chalewa on 2007-12-23
ndiswrapper is listed

---

### Post by reckless2k2 on 2007-12-23
well that is just the case with the nature of wifi drivers especially through ndiswrapper. atheros does have restricted driver support in gusty but i'm not sure what version you're running. as far as rebooting, you don't have to do that. you could just restart networking:

```
sudo /etc/init.d/networking restart

```

wifi will always be problematic especially with wifi nature in linux. you could always hard code your network in the interfaces file.

---

### Post by chalewa on 2007-12-24
> **reckless2k2 said:**
> well that is just the case with the nature of wifi drivers especially through ndiswrapper. atheros does have restricted driver support in gusty but i'm not sure what version you're running. as far as rebooting, you don't have to do that. you could just restart networking:

```
sudo /etc/init.d/networking restart

```

wifi will always be problematic especially with wifi nature in linux. you could always hard code your network in the interfaces file.



tried this as well...

i don't think that it is a matter of the card being recognized or the driver loading but rather not being able to set the essid for some reason.

---

