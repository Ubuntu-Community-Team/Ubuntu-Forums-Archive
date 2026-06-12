---
title: "bad wireless connection"
date: 2014-10-16
forum: Networking &amp; Wireless
---

### Post by geordiejohn on 2014-10-16
lspci -nn -d 14e4:
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)

i have got the wireless info text on my desktop but it is too big to paste here and i did not know how to attach it in this post.
i am running lubuntu 14.04.1 on my acer aspire 5536 laptop and i have got a new sky hub router,about 2 weeks ago i started to have to keep rebooting to get a connection,my router is in the front room and i use my laptop about 10 foot away from the router,at the moment i am getting %73
upstairs i have got an apple macmini and i have no problems with a connection.
i used to get a laptop connection in the kitchen but i cannot anymore.
any ideas please?
thank you.

---

### Post by Hadaka on 2014-10-16
Hi, see if this helps .
please do.
#Per the wireless report you dont have your country code.
```
sudo apt-get install iw
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sudo iw reg set GB 
```

#These are good to the first boot..run them awhile and see if things impove.
```
sudo modprobe -rfv acer_wmi
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1
```

#If the above helped, to make persistant please do.
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
``` 

#Please set your network mgr. settings like the attached.
[ATTACH=CONFIG]257274[/ATTACH][ATTACH=CONFIG]257275[/ATTACH]
thanks.

---

### Post by geordiejohn on 2014-10-16
i am in the u.k and i get this msg

Invalid operation iw

---

### Post by Hadaka on 2014-10-16
My error..sorry. Correct command is..
```
sudo apt-get install iw
sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sudo iw reg set GB 
```

---

### Post by geordiejohn on 2014-10-16
sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sed: couldn't open temporary file /etc/default/sedocbFyR: Permission denied

---

### Post by geordiejohn on 2014-10-16
i put in sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda

and it did not bring an error back so it might of worked,i will carry on with your other commands

---

### Post by Hadaka on 2014-10-16
again,sorry. You are correct.,sudo was missing
i have corrected that. thank you for making me aware.

---

### Post by geordiejohn on 2014-10-16
i have entered all your commands and i will see what it is like tomorrow and then i will report back.
rhank you.

---

### Post by geordiejohn on 2014-10-17
i got a signal in the kitchen this morning which i have not been able to do for about 2 weeks so i have made your commands permanent.
thank you very much for your help.

---

### Post by Hadaka on 2014-10-17
Glad that worked for you !
thanks.

---

