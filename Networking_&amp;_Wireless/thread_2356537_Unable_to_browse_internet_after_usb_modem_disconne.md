---
title: "Unable to browse internet after usb modem disconnects and reconnect"
date: 2017-03-24
forum: Networking &amp; Wireless
---

### Post by georgewsmit on 2017-03-24
Greetings,

I have done a fresh install Ubuntu 16.04. Usb modem works fine after boot up, but if modem is disconnected, I have to restart in order to get to browse the net again. If I just re-connect the mobile network, the icon in the task bar shows that the pc is connected to the internet, but the browsers say that thereare no internet connection.

I have searched the net for few days now to no avail.

I need help with this please!

Thanks

---

### Post by georgewsmit on 2017-04-04
Ok, after some extensive searches and a lot of hours I have found a temporary solution,
I have to restart modem manager service in order to re-connect to the internet correctly. 

I used this code:

```
sudo service network-manager restart
```

Any ideas how I can solve this permanently?

---

### Post by mexen on 2017-04-04
> **georgewsmit said:**
> Ok, after some extensive searches and a lot of hours I have found a temporary solution,
I have to restart modem manager service in order to re-connect to the internet correctly. 

I used this code:

```
sudo service network-manager restart
```

Any ideas how I can solve this permanently?
I have the same problem on 16.10 so I will give this a try, thanks.

---

### Post by georgewsmit on 2017-04-04
Please let us know if this worked for you Mexen!

---

### Post by georgewsmit on 2017-04-18
Ok, the network-manager thing doesn't help anymore. I have tried to set up manually but nothing, instead I managed to break Ubuntu. Is there really no one that can help with this?

---

