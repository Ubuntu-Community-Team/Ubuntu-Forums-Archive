---
title: "Wired network problems"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by aldhar on 2007-05-07
Hi,
I have a laptop ASUS A8H with an onboard ethernet card. I guess it's realtek. 
Most of the time everything works just fine. I use network manager applet that takes care of my wired and wireless connections. However from time to time the wired connection in nm-applet stays gray after the boot even though the wire is plugged in. The switch I am connected to blinks on my port but with orange (and not yellow) light which is supposed to mean some connection problems. This "grey" state occurs as if the cable was unplugged - i can see the eth0 interface with ifconfig, set the address, mask, etc. but am unable to send or receive anything including using DHCP. 
Now this could look like some sort of hardware problem but:
[LIST]
[*]it happens from time to time
[*]when I reboot to Windows everything works fine and after another reboot back to Ubuntu everything is fine too! (I have to add that I noticed that Windows boots longer than normally -  the tray icon for ethernet connection doesn't show up for a long time and it takes longer for the internet-rely tray programs to load)
[/LIST]
It is pretty annoying to switch to windows and back to Ubuntu every time the eth0 acts strange.
I would appreciate any help.
Regards.

---

### Post by loserboy on 2007-05-07
you have a router?   are you running dapper by any chance

i have no proof to back this up, but my router did screwy things like that when I had dapper installed on 2 different computers/ 2 different routers, it

---

### Post by aldhar on 2007-05-08
No, I don't have a router, just a simple switch and I'm running feisty. I had similar problems on edgy.

---

### Post by aldhar on 2007-05-10
48h bump
Anybody? There is a pair of lights on the switch - one indicating the speed, second indicating that there is a link.
When encountering this problem first light says 10MBit (normally it's 100) and second is off as if the card was disabled.

---

