---
title: "WEP Key Problems"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by Toby2 on 2006-08-17
Hello, just so you know, I'm relatively new to Linux/Ubuntu.

I've just done a fresh install of Ubuntu Dapper and after hours of frustration, Ubuntu started picking up my Netgear WG511v2 wireless card with the help of ndiswrapper. Now I'm stuck with another problem: I can't connect to my router.

I have identified the problem, which appears to be the WEP key I enter. When I turned WEP security off on the router, my wireless card could connect ok. But when I turn it on, enter* A1 B2 C3 D4 E5* in the field, and enter A1B2C3D4E5 in the field for the wireless card as Hexadecimal *or *ASCII, I can't connect.

Any ideas on where I'm going wrong?

I have a wired Internet access. I've tried installing and using gtkwifi, and it gave me a prompt to enter my WEP key, so I entered A1B2C3D4E5. However, after a while, the little tool panel thing said "DHCP failed" then failed to even pick up my router. Help!

Thanks in advance,
- Toby

---

### Post by wieman01 on 2006-08-17
Can I ask you to post this file, please? 
> /etc/network/interfaces
Just to see what's going on... Hard to tell without any additional information.

---

### Post by Toby2 on 2006-08-18
Sure:
```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid wireless
wireless-key A1B2C3D4E5



auto wlan0

auto eth0

```

---

### Post by wieman01 on 2006-08-18
Would you mind sharing your real key? I think that may be the problem. You can change it later on. :-)

---

### Post by Toby2 on 2006-08-18
Uhh, well, that is actually the real key. :) At least for now. Currently though, I've disabled the WEP security on the router, and I'm connected wirelessly.

I also worked out the gtkwifi was sort of screwing it up; I booted up with a successful connection to the router, then as soon as gtkwifi loaded up in the tool panel, I lost the connection. I'll remove that.

I also changed the settings to have a static IP, this is the /etc/network/interfaces file after re-enabling the security on the router and entering a WEP key for the wireless interface:

> auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet static
wireless-essid wireless
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key A1B2C3D4E5



auto wlan0

auto eth0


Oh, and if it helps, I've attached a pic of the router's WEP key screen thing.
[ATTACH]14475[/ATTACH]

---

### Post by wieman01 on 2006-08-18
Mate (my boss is Australian), could you try this again:
> auto wlan0
iface wlan0 inet static
wireless-essid wireless
wireless-key s:your_ascii_key
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

Put an "s:" in front of your (ASCII) key and restart the computer. Believe or not, restarting your machine sometimes does the job.

Option 2 is to try the HEX once again (of course without the "s:") and then to restart. 

You are definitely on the right track.

---

### Post by Toby2 on 2006-08-18
Thanks for the help, but I didn't even need to do that! It turns out that it was a weird problem with the router. I went to the screenshot above, changed that dropdown that says 'Authentication Type' to 'Both', and it works!

Problem solved. :D

---

### Post by wieman01 on 2006-08-18
Great, happy to hear that. If you need help with better encryption (WPA, WPA2), send me a note.

---

