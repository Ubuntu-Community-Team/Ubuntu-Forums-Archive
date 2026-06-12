---
title: "iwconfig but not ifconfig?"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by DuplexEmotions on 2006-08-26
Greetings!

I'm installing ubuntu as a server and setting up wireless from the command line. I'm having no problems setting up essid or the like, my issue is that ra0 (my wireless card uses the rt2500 module) shows up fine on iwconfig, but not at all on ifconfig. My guess is I'm doing something stupid, but I'd really like this box running so I can use naim or the like while watching TV.

It's a PII toshiba satellite with 64 MB of ram. I had xubuntu running on it, but decided to reinstall using the server settings because I really didn't need the gui, which was running incredibly slowly.

Anyway, whatever help you can lend would be appreciated; I don't have a wired network connection for that laptop so I can't apt-get any additional packages. I'm pretty much stuck with what is on there.

Thanks for the help!

John

---

### Post by DuplexEmotions on 2006-08-26
an update... it shows up in ifconfig -a , but if I try to ifup or ifconfig up the ra0 it says "ignoring unknown interface ra0=ra0"

Edit: I am stupid, all it needed was a "sudo dhclient ra0"

Thanks for taking the time to read!

---

### Post by ddales on 2006-08-29
It doesn't necessarily need to be DHCP but if that's what you want that's Ok too.

What I did, after f'ing with ndiswrapper for hours was edit your /etc/network/interfaces and enter your preferences.  If you want DHCP just use "auto wlan0 inet dhcp" for the device line.

Mine looks like this:

auto wlan0
iface wlan0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid WLAN

---

