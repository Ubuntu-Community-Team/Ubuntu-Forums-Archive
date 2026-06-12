---
title: "Cant change my wireless network adapers channel?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by rom3lol on 2010-12-29
I am currently trying to crack my wep at home and the adapter I am using wont match the network's channel?
This is what I tried

```
sudo iwconfig mon0 chanel 6
```And airodump-ng keeps saying my adapter is on channel -1 and my network is on channel 6.

---

### Post by rom3lol on 2010-12-30
Fixed it. I use this thread
[http://ubuntuforums.org/showpost.php?p=9985581&postcount=1](http://ubuntuforums.org/showpost.php?p=9985581&postcount=1)

But I believe that it caused some problems, and my desktop would freeze and go black so I had too reinstall Ubuntu. But then again im unsure..

---

### Post by appolons on 2011-10-26
> **rom3lol said:**
> Fixed it. I use this thread
[http://ubuntuforums.org/showpost.php?p=9985581&postcount=1](http://ubuntuforums.org/showpost.php?p=9985581&postcount=1)

But I believe that it caused some problems, and my desktop would freeze and go black so I had too reinstall Ubuntu. But then again im unsure..
   

After comand Make i get errors!!

/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:55:2: error: too many arguments to function &#8216;tty->driver->ops->tiocmget&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:66:2: error: too many arguments to function &#8216;tty->driver->ops->tiocmget&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: warning: passing argument 2 of &#8216;tty->driver->ops->tiocmset&#8217; makes integer from pointer without a cast [enabled by default]
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: note: expected &#8216;unsigned int&#8217; but argument is of type &#8216;void *&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:67:2: error: too many arguments to function &#8216;tty->driver->ops->tiocmset&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:71:2: error: too many arguments to function &#8216;tty->driver->ops->tiocmget&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: warning: passing argument 2 of &#8216;tty->driver->ops->tiocmset&#8217; makes integer from pointer without a cast [enabled by default]
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: note: expected &#8216;unsigned int&#8217; but argument is of type &#8216;void *&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:72:2: error: too many arguments to function &#8216;tty->driver->ops->tiocmset&#8217;
/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.c:75:2: error: too many arguments to function &#8216;tty->driver->ops->tiocmget&#8217;
make[3]: *** [/home/boss/compat-wireless-2010-10-16/drivers/bluetooth/hci_ath.o] Error 1
make[2]: *** [/home/boss/compat-wireless-2010-10-16/drivers/bluetooth] Error 2
make[1]: *** [_module_/home/boss/compat-wireless-2010-10-16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2

---

### Post by Drowz0r on 2011-10-26
> **rom3lol said:**
> I am currently trying to crack my wep at home and the adapter I am using wont match the network's channel?
This is what I tried

```
sudo iwconfig mon0 chanel 6
```And airodump-ng keeps saying my adapter is on channel -1 and my network is on channel 6.

Hey

The default wireless network channel is channel 11 and it's what things revert to if you reset them. So resetting the switch and the card should put them both back on 11.

Although you shouldn't need to change the channel on the card, as you just change it on the switch and the card picks up _all_ channels and adapts to the one you pick as your network.

---

