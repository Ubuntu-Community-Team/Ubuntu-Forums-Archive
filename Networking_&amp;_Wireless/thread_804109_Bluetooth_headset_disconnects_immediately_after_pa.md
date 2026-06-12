---
title: "Bluetooth headset disconnects immediately after pair, using Blueman, maybe DHCP error"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by se2131 on 2008-05-22
I posted this on the forums at blueman.tuxfamily.com , but those forums aren't that active so hopefully someone here can help me out. I started following the instructions at [http://ubuntuforums.org/showthread.php?t=786640&highlight=skype+bluetooth](http://ubuntuforums.org/showthread.php?t=786640&highlight=skype+bluetooth) . But when I get this step:

> 10) turn on the headset and hit volume up on the headset which should cause your PC to ask for the passkey to pair with the headset

nothing happens when I press the volume keys.

So at the suggestion of another poster in that thread, I installed an application called Blueman. Now I'll just copy-paste from my thread on those forums:

I can discover my headset fine (It's an Ativa AT-BT220), but when I press the "Bond" button and enter my passkey (0000), the device says "Bonding successful" immediately followed by "Device disconnected." If I look at the properties for the headset, it says "Bonded: Yes", "Connected: No"

The strange thing is that the very first time I used Blueman, it worked perfectly. I was able to use Skype with my headset even. Then it stopped working (for no reason that I can think of), and then it hasn't worked ever since.

I should also mention that there's something wrong with the dhcp server related to blueman. When I try and uninstall Blueman, it says:

Removing dhcp3-server...
* Stopping DHCP server dhcpd3 [fail]

and if I try and re-install it, it says:

Setting up dhcp3-server (3.0.6.dfsg-1ubuntu9) ...
* Starting DHCP server dhcpd3 [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.

I didn't notice these errors the first time I installed blueman, but they may have been there, not sure. I don't really know much about DHCP servers, so maybe it's unrelated (but I think it is).

---

### Post by se2131 on 2008-05-23
DHCP probably has nothing to do w/ it actually, I installed the 0.3 version of Blueman which doesn't deal w/ DHCP and I still have the same problems.

Also, if I do something like look at the AT-BT220 properties, it will connect and disconnect.

---

### Post by se2131 on 2008-05-24
bump

---

### Post by blom on 2008-05-26
I'm in the same boat here, as mentioned in another thread, this all worked fine in previous release of Ubuntu

---

### Post by se2131 on 2008-06-07
The developer responded to my question at [http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=50](http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=50)

---

### Post by priegog on 2008-06-07
Hi. Yeah as the developer told you in that other thread, the disconnecting issue is normal. When I had it working, the headset would be on standby and then when skype tried to acces the audio devices it would connect. I can't figure out why it doesn't work on hardy tho. 
Let me plug a little question of my own here: does anyone know what package is necesary for the pairing-pin code prompt to appear? It's just that since I haven't needed to pair anything in a long while I hadn't noticed somewhere along the upgrades I lost this functionalyty now that I need it.

---

