---
title: "[SOLVED] Network doesn't start on reboot; works with networking restart or ifdown/ifu"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by sceo on 2008-01-14
I have looked at existing threads, but still have this seemingly common problem.  I wanted to ditch network-manager because 1.) I use wireless, but it's a desktop computer so I never roam or anything, and 2.) I want network to start before login so I can use x11vnc to connect to a gdm session ([http://ubuntuforums.org/showthread.php?p=4131703](http://ubuntuforums.org/showthread.php?p=4131703)).  So, I used "manual configuration" from network manager (which just starts System -> Admin -> Network) and manually specified all my settings for my wireless.

The problem is that the network doesn't seem to be working on startup.  If I drop off to a different tty (Ctrl-F1) and do a "dhclient" or "networking restart" or "ifdown && ifup" (my wireless interface is eth0), then it works (I actually tested my x11vnc config this way and it works).

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-passphrase MYPASSPHRASEISHERE
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MYSSIDISHERE

```

I have tried:
[LIST]
[*]moving auto eth0 to be the last line
[*]inserting 'ifconfig eth0 up' after the 'iface' line
[/LIST]

Dropping off to tty1 and doing a "ps axf | grep suppl" shows me that wpa_supplicant is running; so I don't think it's a problem with that.  When I try to do a "sudo ifup eth0" it tells me it's already up.  So maybe it's just that dhclient isn't running or something?  Or running too early?  It's a zd1211rw (USB Wifi NIC) so I thought maybe it was trying to start wireless BEFORE starting the USB or something - but my dmesg seems to indicate that that's NOT the problem.

I'd really like to fix the problem, whatever it may be.  One option, I suppose, is to write my own startup script which does a "networking restart" late in the chain, but I feel like there's a "cleaner" fix -- like a problem with my config or something.  If anyone can help, I'd appreciate it.  I'm happy to provide any further information/config files, etc.

---

### Post by sqrt2 on 2008-01-14
I've had a similar problem recently. Something that worked for me, is adding
[indent]pre-up sleep 20[/indent]
to the device in /etc/network/interfaces. However, I couldn't figure out the real cause of the problem either.

---

### Post by sceo on 2008-01-14
This is good.  It seems to confirm my suspicion that it was somehow starting too early.  Delaying the network start by 20 (seconds?) definitely made it work.  Thanks!  I like this solution because it's a non-blocking sleep, so it doesn't affect bootup times (ex.g. by 20 seconds) and because the fix is contained in /etc/network/interfaces, which I already needed to touch anyway for this config.

---

### Post by randyrick on 2008-02-06
I was having the same problem with a laptop running Gutsy, adding the pre-up line worked, thanks!

---

