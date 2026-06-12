---
title: "my dad's account has no network manager!"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Absolome on 2010-03-28
My account has a nice little network manager applet on the top bar, but when my dad trys to use the computer there is none!

This wouldn't be a problem, but every time the computer is put into standby mode (closing the laptop) it looses connection, I have to go into network manager and change the connection (It says it's connected to my network, but the same network name is in the list of connections and I have to click it to get internet working.)

How do I fix this so the internet is always working, or at least get a newtwork manager on the second account?

---

### Post by Kafubie on 2010-03-28
Go to your dad's account, then go to one of your panels and right click.
-"Add to panel"
- Possibly add Notification area.
Or just look around and try some.
I had the exact same problem, it's in there.

---

### Post by Absolome on 2010-03-28
It doesn't appear to be in "add to panel", I went through everything there

Also when  right click on it in my account it doesn't allow me to move it or anything like that

any other suggestions?

---

### Post by 2hot6ft2 on 2010-03-28
Right click on an "empty" spot on the top panel and click "Add to Panel" then select "Notification Area", click on "Add" then "Close".

To move one you right click on it and clear the "Lock to Panel" box, then right click and select "Move", move your mouse to the left or right and left click to drop it where it is. Then right click and "Lock to Panel"

---

### Post by ajgreeny on 2010-03-28
It should certainly be in the Notification Area on the panel.  If it still does not appear, check that network manager is running in system monitor, or using ```
ps aux | grep Network
```

---

### Post by Absolome on 2010-03-29
```
root       779  0.0  0.2  18712  3732 ?        Ssl  Mar25   0:24 NetworkManager
root      7571  0.0  0.0   2144   956 ?        S    17:19   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-d5c294d7-2852-4f04-a301-6cbcca21a111-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
cvt       9356  0.0  0.0   3044   872 pts/0    R+   17:21   0:00 grep --color=auto Network
```

Theres my output for ```
ps aux | grep Network
```

I have a notification area, it tells me the volume, just no network manager

---

### Post by rbc on 2010-03-29
Absolome,
I don’t know if you want to test this, because it’s probably not going to solve your problem, but….the one computer in my house that has multiple users seems to act like this……after booting up, or after every user has logged off, the first user to log on gets the network manager. Unless that initial user logs off, all other users do not get a network icon in the notification area. I don’t know if that’s a bug or a security feature, so that subsequent users don’t change the network settings

---

### Post by blur xc on 2010-03-29
> **rbc said:**
> Absolome,
I don’t know if you want to test this, because it’s probably not going to solve your problem, but….the one computer in my house that has multiple users seems to act like this……after booting up, or after every user has logged off, the first user to log on gets the network manager. Unless that initial user logs off, all other users do not get a network icon in the notification area. I don’t know if that’s a bug or a security feature, so that subsequent users don’t change the network settings

+2- mine does the same thing and I find it really annoying.  I mean, the fast user switcher is great- but it sucks when I need to access the network manager when my wife was the first user that logged on.  My only solution is to log out both user accounts, and then log myself back in.  

BM

---

