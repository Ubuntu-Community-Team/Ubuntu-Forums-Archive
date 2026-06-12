---
title: "adding a persistent route"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by kirky3000 on 2005-06-01
I can add a route using something like:

route add -net 192.168.0.0 netmask 255.255.0.0 gw 10.0.0.1 dev eth0

but how do I make it persistent, because it goes away when i reboot at the moment.

Cheers

---

### Post by Mez on 2005-06-01
```
sudo gedit /etc/rcS.d/S99route
```

Add your code in there and reboot ;)

---

### Post by lreyes6 on 2005-06-16
this didn't work... any other sugestion?

thanks

---

### Post by hw-tph on 2005-06-17
Create a file called myroute in /etc/init.d and make it executable (chmod +x /etc/init.d/myroute). Add your route commands there and then add startup links to your startup directories, either by hand or by using update-rc.d:
```
update-rc.d myroute defaults 99
``` (where 99 is the scheduling - 99 means it will start last). Also read up on /etc/init.d/README and the links found therein.


Håkan

---

### Post by lreyes6 on 2005-06-17
:grin: this works great! thanks

---

### Post by str1der on 2007-01-06
Hi there!

I was looking for the same thing and I think I found a better solution!
```

sudo vi /etc/network/interfaces

```
add your command here at the end of the file, eg
```

up route add -net 192.168.0.0 netmask 255.255.0.0 gw 10.0.0.1 dev eth0

```
Notice the 'up' part, it is important to include it before your command.

Thats it! Now you can restart the network to activate the changes
```

sudo /etc/init.d/networking restart

```

---

### Post by AnRkey on 2007-04-16
Wow, this is brilliant!

Now my routes are in place as my interface comes up :)

Thanks very much!

---

### Post by www.rzr.online.fr on 2008-03-20
looks good, by the way do you know a way to force ethernet card order ?
i mean i want my Nth physical card to be assigned to ethM logical interface ?

Later

---

