---
title: "RT73 hangs at boot"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by dmub82 on 2008-05-17
Trying out the [serialmonkey RT73 driver]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads") in Hardy with my Belkin F5D7050 v3000. (The rt73usb included with Hardy works OK, but the serialmonkey includes a few more features like monitor mode and packet injection.) The driver works, but two problems:

1) My computer hangs during the boot process if the stick is plugged in. Orange bar stops moving pretty early and I get a text screen that looks like (from memory so not exact, but I know only the first two say OK):

```
Something I forget                   [OK]
Preparing restricted drivers               [OK]
Setting system clock                       
Something like starting networking         
Starting Firestarter
``` and that's where it stops. If I leave the stick unplugged when I boot then plug it in when it gets to the desktop, it seems to work fine. Here's my /etc/modprobe.d/blacklists, cause I assume I'm missing something there. The last section was copied from the RT73 Serialmonkey HOWTO in the archives of this forum.

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```

Once I get that resolved my next issue is that I can't get /etc/network/interfaces configured properly to connect at boot (when it's not hanging) and allow "sudo ifup wlan0" to work. I can only connect to my network using Rutilt. I also copied the /etc/network/interfaces from that HOWTO, and it looks like this, with my ESSID and PSK substituted:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set SSID="my essid"
    pre-up iwpriv wlan0 set WPAPSK="the output of wpa_passphrase with my essid and password and I'm absolutely sure this is the correct value"
    pre-up iwpriv wlan0 set NetworkType=Infra
```

Rutilt's Site Survey shows my network with AES listed under Cipher but to make it work I have to select TKIP in the Profile section for that network. In case this helps, here's my known good wpa_supplicant.conf from when I used that with the rt73usb driver, my router is still configured the same, maybe someone will see a something inconsistent between the two configurations:

```
network={
       ssid="my essid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=that same passkey from wpa_passphrase
}
```

Any ideas?

---

