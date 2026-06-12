---
title: "How to pair two bluetooth adapters with same name..?"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2014-10-11
Evening, all.

I've hit a slight snag. I'm trying to pair my desktop PC (running Ubuntu 14.04) with a laptop on which I've just installed the same distro.

Now, the snag mentioned is that BOTH Bluetooth adapters have the same name; 'ubuntu-0'. I've successfully paired with my old Dell laptop, which is running Lubuntu; that's named as 'lubuntu-0'. 

Am I right in thinking that you can't pair two adapters with exactly the same name? And, if so, how can I, if necessary, edit the name of one of them, to change it to, say, 'ubuntu-1'?

Any help would be appreciated. ;)

Regards,

Mike.

---

### Post by jeremy31 on 2014-10-11
If the bluetooth device is hci0 ```
sudo hciconfig hci0 name <new name>
``` if I wanted to change mine to dog it would be ```
sudo hciconfig hci0 name dog
```
And you can check the name with ```
hciconfig hci0 name
```

---

### Post by Mike_Walsh on 2014-10-11
Hi, Jeremy.

Thanks very much for that. All changed!

Am I correct in my assumption, that you can't pair two adapters with exactly the same name? It's not a problem I've encountered before, since I've paired to different distros in the past; normally, they find each other within a matter of seconds, as you probably know. :p

Regards,

Mike.

---

### Post by jeremy31 on 2014-10-11
> **Mike_Walsh said:**
> Hi, Jeremy.

Thanks very much for that. All changed!

Am I correct in my assumption, that you can't pair two adapters with exactly the same name? It's not a problem I've encountered before, since I've paired to different distros in the past; normally, they find each other within a matter of seconds, as you probably know. :p

Regards,

Mike.

I renamed my phone to ubuntu-1 and was able to pair and transfer a file, it must use the hardware address to differentiate

---

### Post by Mike_Walsh on 2014-10-12
Well, I still can't get them to pair, so something else must be going on; but you HAVE answered my question, so I'm going to mark this as 'solved'.

Thanks, Jeremy.

Regards,

Mike.

---

### Post by jeremy31 on 2014-10-12
So what chipset is it ```
lspci
``````
lsusb
```

I have an Atheros Wifi/BT card that the bluetooth on works only when it wants to(AR3012) that is with the AR9485

---

