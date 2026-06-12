---
title: "Wireless (ipw3945) disconnects when using Kismet/Aircrack-ng"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by bistrototal on 2006-11-16
Everytime i try to start up aircrack or kismet, i lose the connection to my wireless router.

For example:```
sudo airodump-ng eth1
```

I get a list of available networks and then i lose the connection to my router. This also happens everytime i fire up kismet. And i'm unable to restore the connection. I try with both gnome network manager and iwconfig eth1.

I have a Dell D420 Latitude and i'm using the ipw3945 driver.

I suspect that it might have to do with the ipw3945 driver being installed from deb-package and not compiled with CONFIG_IPW3945_MONITOR.

Will it eventually be easy to reinstall/substitute a self compiled version of the ipw3945 driver?

Thanks in advance for all responses!

---

### Post by iconoclast44 on 2006-11-18
Yes, I have the same problem. I have a broadcom chip, bcm43xx. After installing the driver, ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)) in Edgy, I have to start ny wifi every time I login by "sudo mopdprobe bcm43xx" then I have connection. 

Anyways, when I use 

airodump-ng eth1

I am able to successfully scan wireless networks...BUT

I am then disconnected from using the internet...I've tried "sudo /etc/init.d/networking restart", "sudo if eth1 down", "sudo if eth1 up", and "sudo modprobe bcm43xx" again with no luck. I can't recover. I reboot, modprobe again, and then I'm working. Any idea how to fix this one?

---

### Post by steampunk on 2006-11-21
This is probably due to the fact that your card is placed into Monitor mode when it uses Kismet. You can change this setting with iwconfig.

---

