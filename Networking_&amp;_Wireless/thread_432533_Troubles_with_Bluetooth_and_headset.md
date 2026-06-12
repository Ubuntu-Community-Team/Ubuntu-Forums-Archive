---
title: "Troubles with Bluetooth and headset"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by RedFoxy on 2007-05-04
Hi all!
I'm tring to configure my to configure my bluetooth (Dlink DBT-120) with my headset, I've readed a lot of guide and wiki but nothig!

I can only connect to my headset but i dont' hear nothing and noone can hear me, I tried to use 2 different headset but nothing... I do paring with headset, when I run skype (I use /dev/dsp1(or bluetooth audio) in skype) and start an audio connection (like with skype or with other programs like aplay from shell) the bluetooth connection will be activated but nothing, the connections is ok, if i push volume buttons on headset i see the command in the shell and i can see the sliders of mixer that move up or down...

If I'm sure that my bluetooth dongle is ok because if I try to connect to my mobile i can transfer files and use other bluetooth services without troubles...

I tried to follow some guides that use konqueror to explore bluetooth device's services, when I scan my bluetooth network, I found my mobile (clicking on it i see all mobile services) and my headset, but my headset have a DVD icon and if i click on it konqueror ask me if i want save it or open with a program... I think that it have troubles to right recognize audio devices...

My standard installation of bluetooth is realy simple, I just install about all package of bluez (bluez-gnome, bluez-pin, bluez-utils, libbluetooth2, bluetooth, bluez-btsco, bluez-hcidump), then I edit my /etc/modules to add snd_bt_sco at the end, then i reboot and when ubuntu is started i turn on my headset, when i turn it on, bluez ask me pin to paring the device, I insert my code (classical 0000) then i open a shell and type "hciconfig hci0 voice 0x0060" and now i'm ready to use my headset with "btsco -v headset_mac" then the connection is on!

I logged a connection with hcidump and -v in btsco, you can read it here:

BTSco connection and call with Skype with volume buttons test, skype disconnection and bluetooth disconnection (ctrl+c):
[http://paste.ubuntu-nl.org/18862/](http://paste.ubuntu-nl.org/18862/)

Log of connection usinng hcidump of previous connection (call with Skype with volume buttons test, skype disconnection and bluetooth disconnection (ctrl+c)):
[http://paste.ubuntu-nl.org/18861/](http://paste.ubuntu-nl.org/18861/)

I hope that you can help me!

thank you for all

---

### Post by RedFoxy on 2007-05-05
no one can help me? is it so hard to resolve?

---

### Post by RedFoxy on 2007-05-07
There is no way to use it -.-

---

### Post by RedFoxy on 2007-05-10
no ideas about that troubles?

---

### Post by bielinek on 2007-05-14
i've got the same problem, working on it, I'll let u know if I'll be sucesfull

---

### Post by RedFoxy on 2007-05-15
> **bielinek said:**
> i've got the same problem, working on it, I'll let u know if I'll be sucesfullThank you!
I'm tring to fix it too and I've a test to do, I think that can be a trouble at audio protocol through bluetooth, or just it's wronge or it's no started or not appropriate... With my phone I've no troubles!

---

### Post by samskpun on 2008-04-03
you need the A2DP to get audio work..i 've just order the same adapter and i am going to return it now

---

