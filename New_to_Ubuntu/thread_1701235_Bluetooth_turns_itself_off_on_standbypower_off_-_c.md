---
title: "Bluetooth turns itself off on standby/power off - can't turn it back on"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Avidon on 2011-03-06
Hi,

I have a Packard Bell DOT S netbook and have installed the desktop version of Ubuntu 10.04. This was installed alongside the Windows 7 installation that was already installed.

When I first started ubuntu, I couldn't for the life of me figure out where the bluetooth is. It's not listed in the hardware or anything. I restarted the netbook into Windows to see if it actually has built-in bluetooth and it does! Pressing fn-F3 brings up a windows which allows me to separately turn on/off wi-fi and bluetooth. I made sure these were both set to 'on' and restarted into ubuntu.

Once I was back to the ubuntu desktop, I noticed there was suddenly a bluetooth icon in the indicator applet part of the panel.

This is great, but unfortunately, whenever I shut down the computer or put the computer to stand-by, then start the computer up again into ubuntu, the bluetooth disappears again.

It seems to me like it's a power-saving feature; the bluetooth will turn off when in stand-by or when you turn the computer off. Then it will be off by default until turned on explicitly. Of course it looks like Packard Bell only implemented this switch in Windows...

Pressing fn-F3 controls the wi-fi in ubuntu (in a weird way). However this also turns bluetooth off, and subsequent presses never turn it back on again

If anyone has any ideas on how I can implement some kind of switch in ubuntu or somehow make it work without having to rely on Windows I would much appreciate it.

If I must buy a bluetooth dongal, then so be it. But it would obviously be much nicer to get the built-in bluetooth working.

Thanks very much in advance!

---

### Post by turtle153 on 2011-03-06
Go to **System > Preferences > Bluetooth**. Does it say you have a Bluetooth adapter after the computer has been sleeping?

---

### Post by matthewbpt on 2011-03-06
Open the Terminal from Applications >> Accesories, and type in
```
rfkill list
```
and press enter. Paste the output here.

---

### Post by Avidon on 2011-03-12
Sorry about the late reply! Been moving into a new flat. Thanks very much for your replies, I'll do my best to reply in a much more timely fashion in the future...

OK, so in system > preferences > bluetooth, it says 'No Bluetooth adapters present'

and:

$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

It's as if the bluetooth adapter vanished off the face of the Earth :/

---

### Post by Avidon on 2011-03-12
I've just restarted the netbook into Windows and restarted back into ubuntu...

The bluetooth icon is back again :)

System > preferences > bluetooth, works fine.

$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Until the next time I put it to stand-by or turn it off, when bluetooth will disappear again :/ I've actually resorted to leaving it on 24/7 for now :P

---

### Post by i4n on 2011-06-27
same problem on google cr-48. but there is no way i can recover ive found besides factory reset & reinstall ubuntu...

found [https://bugs.launchpad.net/system76/+bug/762964](https://bugs.launchpad.net/system76/+bug/762964) but i dont have success with any suggested command prompt workaround

---

