---
title: "Wireless doesn't connect on boot"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by rushdy on 2006-07-26
Ok, my problem is with my wireless interface not connecting to my router on boot (though it does try), but when I ifdown/ifup (or do not use auto and just ifup once booted) it works fine. I've had the identical problem with an ndiswrapper supported card, and now an atheros card which I replaced that with. I'll give some more details:

Using the following /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wpa-driver madwifi
wpa-ssid RushNet
wpa-key-mgmt WPA-PSK
wpa-psk ...

iface eth0 inet dhcp

```
My laptop boots as expected, no delays or anything like that. Once it's booted and I'm logged in, I find there is no network connectivity. Ifconfig shows the interface ath0 is up, and assigned the static ip 192.168.0.3 as I would expect, however, iwconfig shows no association and a blank ESSID.

If I now ifdown ath0 the interface goes down, then using ifup ath0 after about 8 seconds it returns to the prompt fully connected, working flawlessly.

If I omit auto ath0 from interfaces after boot the interface is down and unconfigured as you would expect. If I run ifup ath0, then it comes up after a few seconds and again works perfectly. I have got ath_pci in /etc/modules but it behaves the same way if I don't.

So it's a bit of a puzzle why it works manually, but doesn't when it boots ](*,)

---

### Post by rushdy on 2006-07-27
Well I've solved it, although I don't know why ;)

First I created a file /etc/network/wpa.conf.

My /etc/network/interfaces reads:
```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wpa-driver madwifi
wpa-conf /etc/network/wpa.conf

iface eth0 inet dhcp

```
So all I changed was removing the wpa settings and directing it to the newly created config file.

/etc/network/wpa.conf contains:
```

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="RushNet"
    psk=...
}

```

Hey presto, it works! It's weird that it works in one file but not in the other, but if my wireless comes up right on boot, and ifup/ifdown manage it correctly plus it's not a hack, then thats fine by me!

Also whilst I was trying to fix it, I found using wireless_essid RushNet instead of the WPA settings (with my AP set to be open) worked too, so I guess it's just the WPA.

---

### Post by TrinitronX on 2007-06-28
This fixed my networking!

Before upgrading to feisty, I had been using a rather hackish way of getting wpa_supplicant to run on boot.  I had a script in /etc/init.d called wpasupplicant which started it... and added a symlink to it in /etc/rcS.d/
Since upgrading to feisty, dhcp stopped working for me, since they revamped the core networking ifupdown stuff to use avahi and added support for starting wpasupplicant from within /etc/network/if-pre-up.d

I read the documentation for wpasupplicant in /usr/share/doc/wpasupplicant/  (specifically README.modes.gz and README.Debian) and figured out how to use the new wpa-* settings from within /etc/network/interfaces
I haven't tried setting all options within the interfaces file, because I had a previously made wpa_supplicant.conf file that I knew worked.
The key problem with my file was I didn't have the line "auto ath0".

Also, I found that if another problem with it arises ever, you can debug wpa_supplicant, by editing the wpasupplicant script in /etc/network/if-pre-up.d/wpasupplicant (it's a symlink for me) and add this line at the very beginning:

```
IF_WPA_MAINT_DEBUG=true
```

Then when you do /etc/init.d/networking [stop|start|restart], it will show debug info for the script.

If you read the docs maybe now it can make sense as to why it works :D

---

