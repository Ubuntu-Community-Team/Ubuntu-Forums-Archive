---
title: "Restarting a wired NIC"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by Nightwalker07 on 2007-09-14
I was wondering whats the best method for restarting my wired network connection. Earlier I used the command:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```It seemed to do the job I asked (connectivity wise I could ping out etc. but the problem was I couldnt get firefox to load any pages after performing the above. I tried closing Firefox and reopening but still no joy. Not sure if it makes a difference but I use a perminant proxy setting within firefox. Is this a ubuntu/firefox bug? Or am I not restarting the connection in the best way? Thanks for your time.

---

### Post by noob12 on 2007-09-14
When you put the interface down, you will lose the default route associated with the interface but bringing it back up with **ifconfig** alone doesn't reinstall it because you don't get the DHCP or even static configuration accomplished that way.

Instead use
```

sudo ifdown eth0
sudo ifup eth0

```

Note that you must have an **iface** line for eth0 in your /etc/network/interfaces file for this to work.

---

### Post by Ted_Smith on 2007-09-14
> sudo /etc/init.d/networking restart will restart all the networking effectively 'rebooting' it all.

---

### Post by Nightwalker07 on 2007-09-15
Thanks! :)

---

