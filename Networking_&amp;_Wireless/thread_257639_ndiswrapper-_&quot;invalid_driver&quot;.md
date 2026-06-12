---
title: "ndiswrapper- &quot;invalid driver&quot;"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by el_ricardo on 2006-09-14
this is weird, and annoying! I am trying to configure ndiswrapper to get my netgear WG111 usb adapter working, after reinstalling ndiswrapper, twice, its still not working. When i give the command "ndiswrapper -l" it says:

```

installed ndis drivers:
netwg111      invalid driver!

```

i used the same driver file (netwg111.inf) as i used on my other PC, on which the adapter works fine, and the same USB ID (0846:4240) which i checked with lsusb. the only difference betweeen PCs is that one is running the latest ubuntu, and the other is running xubuntu (i had to use the alternate install CD because its an old machine that crashed the installer- this is the one that gives me the "invalid driver" error)

anyone got anything?

cheers

---

### Post by wieman01 on 2006-09-14
When installing the *.inf file, make sure the other driver-related files that come along with it (*.cab or similar?) are in the same directory as the *.inf file. I had an issue not dissimilar to this one but could resolve it this way.

Give it a go.

---

### Post by el_ricardo on 2006-09-14
yeah there was a .sys file that it needed too, that made ndiswrapper happy at least, the network still isn't coming up though, the driver works, it recognises the hardware, its just not connecting to my network! i've enabled the wireless connection, put all the right info in the network prefs (network ID, hexidecimal key, DHCP etc) and got the default gateway set to the right address, just not working! when i turn the computer on, the light on the adapter flashes ONCE, when it gets to "starting network devices" or whatever, and then stops flashing, won't flash when i give the modprobe ndiswrapper command either (which i found it did on my other machine) anyway this is really pissing me off because i'm having to climb up 2 sets of stairs every time i need anything off the internet to get this other computer working! (or post my problems on here lol)

anyway, any advice will be appreciated, and thanks wieman01 for your input :)

---

### Post by wieman01 on 2006-09-14
Just post **"etc/network/interfaces"** and we'll see what's wrong with it. :-)

---

### Post by el_ricardo on 2006-09-19
all it says is:

```

# this file describes tje network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback interface
auto lo
iface lo inet loppback

iface eth0 inet dhcp
wireless-essid john

auto eth0

```

PS i apologise for the delay, the router was playing up, i fixed it and thought the wireless might therefore be working on this system but evidently not!

---

### Post by jISh on 2006-09-19
It doesn't look like the network settings box worked. I hate that thing anyways, and will always use the interfaces file to configure mine.

Your driver is alised as eth0? It's possible, but more likely that it's wlan0. I'd try that.

Don't forget to do *sudo ndiswrapper -m *.

Also you should add the
```
[wireless_mode managed
```
line to the interfaces file.

---

### Post by el_ricardo on 2006-09-19
where should i put the "wireless mode managed bit? and should i change auto eth0 to auto wlan0?

---

### Post by el_ricardo on 2006-09-19
another thing, when i do "ndiswrapper -m" i'm told "modprobe config already contains alias directive"

---

### Post by wieman01 on 2006-09-19
I don't think your network adapter has been recognized. "eth0" is likely to be your ethernet adapter, am I mistaken?

Try this (sudo gedit /etc/network/interfaces):
> # this file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]your_essid[/COLOR]
wireless-key [COLOR="Red"]your_wep_hex_key[/COLOR]
Delete the remaining lines for the time being and restart your network:
> sudo /etc/init.d/networking restart
I am a bit worried about the warning message you have mentioned. Also, if that does not work, try to replace "wlan0" with "eth0"

---

### Post by el_ricardo on 2006-09-19
got it working now, as you said in your first post there should be a .cat file somewhere, turns out i was missing that, and also there was a pile of stuff that needed blacklisting

thanks!

---

