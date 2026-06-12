---
title: "Boot delay with wireless"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by seeklinux on 2007-04-20
I had this problem in Edgy and now have the same problem with Feisty. It is not a major problem, just a slight annoyance.

At boot-up time it hangs a while trying to connect to wireless I guess. If I disable the wireless radio then this delay does not occur because wireless is not available. I *think* it is trying to bring up the wireless, but this won't happen until after I log in and enter the password for the keyring (via Network Manager and WPA). I don't mind entering the keyring password at start-up, I just would like to eliminate or reduce the time spent during start-up (prior to login) unsuccessfully trying to create a wireless connection.

Anyone know how to reduce or eliminate the attempt to create a wireless connection during the boot/start-up process?

Thanks.

---

### Post by JohnUK89 on 2007-04-20
Have you commented out the entry for your wireless adapter in your /etc/network/interfaces file? This could be the reason for it.

1. gksudo gedit /etc/network/interfaces

2. Comment all the lines except the following:

```
auto lo
iface lo inet loopback

```

3. Reboot and check if it helped

---

### Post by seeklinux on 2007-04-20
Yes, thanks, I had originally commented out all but l0 but after I got things working I uncommented the eth0, eth1, etc.  Commenting them back out seems to have solved the problem. Oddly wlan0 was commented out all along, so it was the existence of the eth ones leading to the delay I guess.

Thanks again.  It is booting much faster now.

---

### Post by samopal on 2007-04-22
ok... booting much faster for me too, but you must enable network manually then after boot :( 

could I do this?  >>> 

1, comment out all except loopback in /etc/network/interfaces 

2, make a script: 
```
#!/bin/bash 
echo "Resetting network..."
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo cp /etc/network/interfacesMSI /etc/network/interfaces
sudo /etc/init.d/networking restart
sudo cp /etc/network/interfaces.bak /etc/network/interfaces
echo "[ OK ]"
```

and this script will run after boot-up and login. 
does this approach harm anything in OS?

---

### Post by samopal on 2007-04-22
tried to add it to my /etc/rc.local and seems to work perfectly :guitar:

---

