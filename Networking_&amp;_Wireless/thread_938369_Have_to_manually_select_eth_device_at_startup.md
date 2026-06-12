---
title: "Have to manually select eth device at startup"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by zer0efx on 2008-10-04
I just installed Ubuntu on my new system and am in the process of configuring everything. When I login for the first time, my network connection is not set. I have to dbl click on the warning icon in the top right corner and select which eth device to use.

Is there a way I can set this up so it defaults to the one I have my cable plugged into? I have a Maximus Extreme MB which has 2 on-board network devices.

TIA

---

### Post by Prospero2006 on 2008-10-04
> **zer0efx said:**
> I just installed Ubuntu on my new system and am in the process of configuring everything. When I login for the first time, my network connection is not set. I have to dbl click on the warning icon in the top right corner and select which eth device to use.

Is there a way I can set this up so it defaults to the one I have my cable plugged into? I have a Maximus Extreme MB which has 2 on-board network devices.

TIA

/etc/rc.local is the last file to be run when the system starts up.
If you add a line like this:

```

ifconfig ethx up

```

It will bring up the device. You may need to either set a static ip or use dhcpcd as well.

---

### Post by zer0efx on 2008-10-05
Hey thanks for the reply prospero, I tried that out but it didn't set when I restarted. I still had to manually set my eth controller.

I'll keep trying out some other options.

---

### Post by mlnsharma on 2008-10-05
Hey i too face the same problem...

---

### Post by Iowan on 2008-10-05
What's in your **/etc/network/interfaces**?  The interface(s) that should be activated on startup should have an "auto" line. Depending on what kind of "setting" you must do, that information might be included in the file, too.

---

### Post by zer0efx on 2008-10-05
Thanks for the reply Iowan, i opened up my interfaces file and it shows this:
```
auto lo
iface lo inet loopback
```

should I try setting auto to eth0 ?

---

### Post by Iowan on 2008-10-05
No, you'll need **lo**, too. Instead, add the following to your **/etc/network/interfaces**:```
auto eth0
iface eth0 inet dhcp
``` If you have static address, you'll need slightly different information.  I won't bore you with details on how to edit the file, unless you ask.

You might need to add a second  entry for the other interface. ```
auto eth1
iface eth1 inet dhcp
```
All those "auto's" *could* go on one line.```
auto lo eth0 eth1
```

---

