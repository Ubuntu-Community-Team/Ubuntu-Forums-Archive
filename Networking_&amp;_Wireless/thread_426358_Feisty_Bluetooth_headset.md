---
title: "Feisty: Bluetooth headset"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-04-28
Hi,

I am not sure if this is the right forum.

I am trying to pair my Scala 500 bluetooth headset with my laptop so that I can use it with Skype.

```
sudo hidd --search
``` comes up with nothing.

```
hcitool scan
``` finds the MAC address of my bluetooth headset.

However ```
sudo hidd --connect aa:bb:cc:dd:ee:ff
``` gives me the following message:

> Can't get device information: Invalid exchange

I have already successfuly paired my SonyEricsson phone with Ubuntu and use it often to sync so I know the method should work.

This is the How To I am following:
[https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)

---

### Post by Roner on 2007-04-29
I just wrote a howto for this. Check it out [here]("http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth+headset").

---

