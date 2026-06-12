---
title: "ndiswrapper wlan connect on boot problems"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by MWP on 2008-11-18
Hi all,

Im trying to get my Ubuntu (Intrepid) box to connect to a wireless AP on boot so i can mount some samba shares from another box.

This is a clean install of Ubuntu, so the first thing i did was to install and setup ndiswarpper. All good.

As a quick test nw-applet will connect to the AP when in "Roaming" mode, but not if i set the settings up manually in nw-applet (they have been tripple checked as correct).

I have now removed nw-applet (removed net-management-gnome) and am trying to get ifup/ifdown to manage the interface.

I have /etc/network/interface setup correctly, and on trying ifup, DHCP discovery doesnt work.
When i check iwconfig, it shows that the essid, etc are blank... not what i set interfaces up to use.

Anyone know whats going on here??

Thanks!

---

### Post by caljohnsmith on 2008-11-18
I think [this thread]("http://ubuntuforums.org/showthread.php?t=974382") might be what you are looking for; let me know if that helps. :)

---

### Post by MWP on 2008-11-18
Nope, didnt help :(

/etc/network/interfaces now stay as they are set after reboot.
ifconfig for wlan0 is set correctly.
iwconfig shows no connection for the interface.
cant ping any ip's.

/etc/network/interfaces:
```

auto lo wlan0
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.60
netmask 255.255.255.0
gateway 192.168.0.254
wireless-essid homeap
wireless-key s:key-text-blah
```

ndiswrapper -l:
```

mrv8335 : driver installed
	device (11AB:1FAA) present

```

iwconfig:
```

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:6D77-7073-7265-6433-6661-6365-73   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Any ideas?

Thanks again...

---

### Post by MWP on 2008-11-19
Fixed...

I had to change "wireless-key s:key-text-blah" to "wireless-key open :key-text-blah".

---

